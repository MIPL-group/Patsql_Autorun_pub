# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 037

# input:input0

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 1 | item1 | data2 |
| 2 | item1 | data1 |
| 3 | item2 | data3 |
| 4 | item2 | data5 |
| 5 | item3 | data4 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 1 | item1 | data2 |
| 3 | item2 | data3 |
| 5 | item3 | data4 |

# solution

```sql
SELECT
    T0.c1,
    T1.c2,
    T0.c3 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            c2,
            min(c1) AS min_c1 
        FROM
            input1 
        GROUP BY
            c2
    ) AS T1 
        ON T1.min_c1 = T0.c1 
ORDER BY
    T0.c1 ASC
```
