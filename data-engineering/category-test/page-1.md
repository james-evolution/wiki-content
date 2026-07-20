---
title: Page 1
---
# Page 1

Edit made by user #1.

Edit made by user #2.

```typescript
export interface PageSummary {
  slug: string;
  title: string;
  /** Path to the page relative to the wiki root, e.g. "onboarding/setup.md". */
  path: string;
  order?: number;
}
```
