# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 034

# input:input0

| Train:Str | Dest:Str | Time:Str |
|---|---|---|
| 1 | HK | 10:00 |
| 1 | SH | 13:00 |
| 1 | SZ | 14:00 |
| 2 | HK | 13:00 |
| 2 | SH | 09:00 |
| 2 | SZ | 07:00 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Train:Str | Dest:Str | Time:Str |
|---|---|---|
| 1 | SZ | 14:00 |
| 2 | HK | 13:00 |

# solution

```sql
SELECT
    T1.Train,
    T0.Dest,
    T0.Time 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            Train,
            max(Time) AS max_Time 
        FROM
            input1 
        GROUP BY
            Train
    ) AS T1 
        ON T1.Train = T0.Train 
        AND T1.max_Time = T0.Time 
ORDER BY
    T1.Train ASC
```
