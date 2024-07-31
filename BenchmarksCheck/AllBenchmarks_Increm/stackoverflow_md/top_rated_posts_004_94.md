# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 004

# input:input0

| id:Str | rev:Str | content:Str |
|---|---|---|
| 1 | 1 | A |
| 2 | 1 | B |
| 1 | 3 | C |
| 1 | 2 | D |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 1 | 3 | C |
| 2 | 1 | B |

# solution

```sql
SELECT
    T1.id,
    T1.max_rev,
    T0.content 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            id,
            max(rev) AS max_rev 
        FROM
            input1 
        GROUP BY
            id
    ) AS T1 
        ON T1.id = T0.id 
        AND T1.max_rev = T0.rev 
ORDER BY
    T1.id ASC
```
