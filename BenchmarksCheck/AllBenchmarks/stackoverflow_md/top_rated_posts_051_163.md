# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 051

# input:input0

| id:Str | category:Str | date:Str |
|---|---|---|
| 1 | a | 2013-01-01 |
| 2 | b | 2013-01-04 |
| 3 | c | 2013-01-02 |
| 4 | a | 2013-01-02 |
| 5 | b | 2013-01-02 |
| 6 | c | 2013-01-03 |
| 7 | a | 2013-01-03 |
| 8 | b | 2013-01-01 |
| 9 | c | 2013-01-01 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | category:Str | date:Str |
|---|---|---|
| 2 | b | 2013-01-04 |
| 6 | c | 2013-01-03 |
| 7 | a | 2013-01-03 |

# solution

```sql
SELECT
    T0.id,
    T1.category,
    T0.date 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            category,
            max(date) AS max_date 
        FROM
            input1 
        GROUP BY
            category
    ) AS T1 
        ON T1.category = T0.category 
        AND T1.max_date = T0.date 
ORDER BY
    T0.id ASC
```
