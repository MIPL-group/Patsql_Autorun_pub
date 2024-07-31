# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 005

# input:input0

| id:Str | customer:Str | total:Str |
|---|---|---|
| 1 | Joe | 20 |
| 2 | Sally | 50 |
| 3 | Joe | 50 |
| 4 | Sally | 10 |
| 5 | abc | 10 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| FIRST_id:Str | customer:Str | FIRST_total:Str |
|---|---|---|
| 1 | Joe | 20 |
| 2 | Sally | 50 |
| 5 | abc | 10 |

# solution

```sql
SELECT
    T1.min_id,
    T1.customer,
    T0.total 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            customer,
            min(id) AS min_id 
        FROM
            input1 
        GROUP BY
            customer
    ) AS T1 
        ON T1.min_id = T0.id 
ORDER BY
    T1.customer ASC
```
