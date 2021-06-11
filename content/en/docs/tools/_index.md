
---
title: "Tools"
linkTitle: "Tools"
weight: 20
menu:
  main:
    weight: 20
---

## New Relic

### Average duration nrql

```SQL
SELECT average(duration) FROM Transaction WHERE <params> Since 1 week ago TIMESERIES 1 hour FACET <param>
```

### 99th Percentile

```sql
SELECT percentile(duration,99) FROM Transaction WHERE <params> Since 1 week ago TIMESERIES 1 hour FACET <param>
```

### Traffic Levels

```sql
SELECT count(*) FROM Transaction WHERE <params> Since 1 week ago TIMESERIES 1 hour FACET <param>
