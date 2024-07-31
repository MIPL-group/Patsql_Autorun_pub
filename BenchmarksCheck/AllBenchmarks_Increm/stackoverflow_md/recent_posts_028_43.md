# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 028

# input:t1

| Member:Str | Element:Str |
|---|---|
| 1 | A |
| 1 | B |
| 1 | C |
| 1 | E |
| 22 | A |
| 22 | B |
| 22 | C |
| 22 | D |
| 3 | A |
| 3 | D |
| 4 | A |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| member:Str | total:Str |
|---|---|
| 22 | 3 |
| 3 | 1 |
| 4 | 1 |

# solution

```sql
SELECT
    T1.Member,
    count(T0.Member) 
FROM
    (SELECT
        Member,
        Element 
    FROM
        t1) AS T0 
LEFT JOIN
    (
        SELECT
            Member,
            Element 
        FROM
            t1
    ) AS T1 
        ON T0.Element = T1.Element 
WHERE
    T0.Member = '1' 
    AND T1.Member <> '1' 
GROUP BY
    T1.Member 
ORDER BY
    T1.Member ASC
```
