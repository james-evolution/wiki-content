---
title: Orders ETL Job
order: 1
---

Nightly job that extracts order events from the production event queue, transforms them into the
warehouse schema, and loads them into `warehouse.orders_fact`.

## Schedule

Runs at 02:00 UTC via Airflow, DAG id `orders_etl_nightly`. Typical runtime is 12–18 minutes;
anything over 40 minutes should page the data on-call.

## Transform logic

The core transform normalizes currency to USD at the historical exchange rate and deduplicates
by `order_id` before the merge step:

```python
def transform(order_events: pd.DataFrame) -> pd.DataFrame:
    df = order_events.drop_duplicates(subset="order_id", keep="last")
    df["amount_usd"] = df.apply(
        lambda row: convert_to_usd(row["amount"], row["currency"], row["event_time"]),
        axis=1,
    )
    return df[["order_id", "amount_usd", "status", "event_time"]]
```

## Common failure

The most frequent failure is a schema drift in the upstream event — a new field added to the
producer without a corresponding transform update. Check the DAG's `schema_validation` task logs
first; it fails fast with the exact field that changed before the transform step even runs.
