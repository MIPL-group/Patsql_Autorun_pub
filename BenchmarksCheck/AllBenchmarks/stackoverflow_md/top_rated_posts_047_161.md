# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 047

# input:input0

| id:Str | user:Str | time:Str | io:Str |
|---|---|---|---|
| 1 | 9 | 1370931202 | out |
| 2 | 9 | 1370931664 | out |
| 3 | 6 | 1370931664 | out |
| 6 | 6 | 1370932121 | out |
| 5 | 10 | 1370932128 | out |
| 4 | 10 | 1370933037 | out |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | user:Str | time:Str | io:Str |
|---|---|---|---|
| 2 | 9 | 1370931664 | out |
| 6 | 6 | 1370932121 | out |
| 4 | 10 | 1370933037 | out |

# solution

```sql
SELECT
    T0.id,
    T1.user,
    T0.time,
    T0.io 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            user,
            max(time) AS max_time 
        FROM
            input1 
        GROUP BY
            user
    ) AS T1 
        ON T1.user = T0.user 
        AND T1.max_time = T0.time 
ORDER BY
    T0.time ASC
```
