---
title: Key Datasets
order: 1
---

The most-used datasets in the warehouse, and who to ask when something looks wrong.

| Dataset                    | Grain          | Refresh   | Owner            |
| --------------------------- | -------------- | --------- | ---------------- |
| `warehouse.orders_fact`     | one row/order  | Nightly   | Data Eng          |
| `warehouse.customers_dim`   | one row/customer | Nightly | Data Eng          |
| `warehouse.sessions_fact`   | one row/session | Hourly   | Growth Analytics  |
| `warehouse.billing_events`  | one row/event  | Real-time | Billing Team      |

`orders_fact` is the most depended-on table in the warehouse — check the **Orders ETL Job** page
before assuming a problem downstream is in your own query rather than upstream data.

New datasets should be registered here as part of the PR that adds them; an unregistered dataset
is one nobody outside its creating team knows exists, which tends to produce duplicate work.
