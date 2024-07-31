# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 027

# input:input0

| cname:Str | wmname:Str | avg:Str |
|---|---|---|
| canada | zoro | 3.0000000000000000 |
| canada | aaaa | 1.0000000000000000 |
| spain | zzzz | 3.0000000000000000 |
| spain | aaaa | 5.0000000000000000 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| cname:Str | wmname:Str | max:Str |
|---|---|---|
| canada | zoro | 3.0000000000000000 |
| spain | aaaa | 5.0000000000000000 |

# solution

```sql
SELECT
    T1.cname,
    T0.wmname,
    T1.max_avg 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            cname,
            max(avg) AS max_avg 
        FROM
            input1 
        GROUP BY
            cname
    ) AS T1 
        ON T1.cname = T0.cname 
        AND T1.max_avg = T0.avg 
ORDER BY
    T1.cname ASC
```
