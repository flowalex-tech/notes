+++
title = "New Relic"
path = "new-relic"
date = 2019-02-02

[taxonomies]
tags = ["observaility", "monitoring"]
+++

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
```

### Percent of Errors (eg 500s)

```sql
SELECT percentage(count(*), WHERE httpResponseCode LIKE '5%%') FROM Transaction  SINCE 1 hour ago TIMESERIES FACET name
```
