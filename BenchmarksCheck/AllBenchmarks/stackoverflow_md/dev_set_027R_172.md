# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 027R

# input:input0

| Train:Str | Dest:Str | Time:Str |
|---|---|---|
| 1 | HK | 10 |
| 1 | SH | 12 |
| 1 | SZ | 14 |
| 2 | HK | 13 |
| 2 | SH | 09 |
| 2 | SZ | 07 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Train:Str | Dest:Str | Time:Str |
|---|---|---|
| 1 | SZ | 14 |
| 2 | HK | 13 |

# solution

```sql
SELECT t.Train, t.Dest, r.MaxTime
FROM (
      SELECT Train, MAX(Time) as MaxTime
      FROM TrainTable
      GROUP BY Train
) r
INNER JOIN TrainTable t
ON t.Train = r.Train AND t.Time = r.MaxTime
```
