# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 038

# input:input0

| id:Str | name:Str | city:Str |
|---|---|---|
| 904822 | pete | Berlin |
| 904825 | pete | London |
| 904829 | jim | London |
| 904834 | jime | London |
| 904835 | jime | London |
| 904835 | jime | Paris |
| 90145 | Fred | Paris |
| 90132 | Fred | Paris |
| 90133 | Fred | Paris |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | name:Str | city:Str |
|---|---|---|
| 904834 | jime | London |
| 904835 | jime | London |
| 90145 | Fred | Paris |
| 90132 | Fred | Paris |
| 90133 | Fred | Paris |

# solution

```sql
SELECT
    T0.id,
    T1.name,
    T1.city 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            name,
            city,
            count(id) AS count_id 
        FROM
            input1 
        GROUP BY
            name,
            city
    ) AS T1 
        ON T1.name = T0.name 
        AND T1.city = T0.city 
WHERE
    T1.count_id > 1 
ORDER BY
    T1.name DESC,
    T0.id ASC
```
