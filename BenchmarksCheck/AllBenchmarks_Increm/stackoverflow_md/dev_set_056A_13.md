# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 056A

# input:input0

| suburb:Str | client:Str | fk_food:Str |
|---|---|---|
| 6000 | "4" | 2 |
| 6000 | "4" | 2 |
| 6000 | "4" | 3 |
| 6000 | "4" | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| item:Str |
|---|
| 2 |

# solution

```sql
SELECT
    T2.fk_food 
FROM
    (SELECT
        max(T0.count_suburb) AS max_T0_count_suburb 
    FROM
        (SELECT
            count(suburb) AS count_suburb 
        FROM
            input1 
        GROUP BY
            fk_food) AS T0) AS T1 
JOIN
    (
        SELECT
            fk_food,
            count(suburb) AS count_suburb 
        FROM
            input1 
        GROUP BY
            fk_food
    ) AS T2 
        ON T1.max_T0_count_suburb = T2.count_suburb
```
