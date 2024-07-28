# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 017

# input:input0

| ID:Str | SKU:Str | PRODUCT:Str |
|---|---|---|
| 1 | FOO-23 | Orange |
| 2 | BAR-23 | Orange |
| 3 | FOO-24 | Apple |
| 4 | FOO-25 | Orange |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | SKU:Str | PRODUCT:Str |
|---|---|---|
| 1 | FOO-23 | Orange |
| 3 | FOO-24 | Apple |

# solution

```sql
SELECT
    T0.ID,
    T0.SKU,
    T1.PRODUCT 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            PRODUCT,
            min(ID) AS min_ID 
        FROM
            input1 
        GROUP BY
            PRODUCT
    ) AS T1 
        ON T1.min_ID = T0.ID 
ORDER BY
    T0.ID ASC
```
