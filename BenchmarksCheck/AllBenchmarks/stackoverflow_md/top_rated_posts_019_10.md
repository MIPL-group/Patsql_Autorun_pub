# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 019

# input:input0

| id:Str | age:Str |
|---|---|
| 0 | 25 |
| 1 | 25 |
| 2 | 23 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | age:Str | count:Str |
|---|---|---|
| 0 | 25 | 2 |
| 1 | 25 | 2 |
| 2 | 23 | 1 |

# solution

```sql
SELECT
    T0.id,
    T1.age,
    T1.count_id 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            age,
            count(id) AS count_id 
        FROM
            input1 
        GROUP BY
            age
    ) AS T1 
        ON T1.age = T0.age 
ORDER BY
    T0.id ASC
```
