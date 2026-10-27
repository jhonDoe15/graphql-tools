---
'@graphql-tools/executor': patch
---

Reduce retained storage for small synchronous result lists and avoid indexed-path allocation for successful scalar list items, preserving input iteration, serialization, errors and incremental delivery.
