# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 009

# input:input0

| username:Str | ip:Str | time_stamp:Str |
|---|---|---|
| ted | 8.8.8.8 | 10 |
| jerry | 5.6.6.7 | 12 |
| ted | 1.2.3.4 | 30 |
| ted | 0.8.8.8 | 12 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| username:Str | ip:Str | time_stamp:Str |
|---|---|---|
| jerry | 5.6.6.7 | 12 |
| ted | 1.2.3.4 | 30 |

# solution

```sql
SELECT
    T1.username,
    T0.ip,
    T0.time_stamp 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            username,
            max(time_stamp) AS max_time_stamp 
        FROM
            input1 
        GROUP BY
            username
    ) AS T1 
        ON T1.username = T0.username 
        AND T1.max_time_stamp = T0.time_stamp 
ORDER BY
    T1.username ASC
```
