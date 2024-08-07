# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 034

# input:input0

| MATERIAL:Str | DISCO_DATE:Str | DATE_UPDATE:Str |
|---|---|---|
| T6C25AW#ABC | NULL | 2016-07-30 |
| T6C25AW#ABC | 2016-10-28 | 2016-09-23 |
| T6C25AW#ABC | 2016-10-21 | 2016-09-30 |
| T6C25AW#DEF | 2016-07-21 | 2016-07-30 |
| T6C25AW#DEF | 2016-07-10 | 2016-07-12 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c:Str | c:Str | c:Str |
|---|---|---|
| T6C25AW#ABC | 2016-10-21 | 2016-09-30 |
| T6C25AW#DEF | 2016-07-21 | 2016-07-30 |

# solution

```sql
SELECT
    T1.MATERIAL,
    T0.DISCO_DATE,
    T1.max_DATE_UPDATE 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            MATERIAL,
            max(DATE_UPDATE) AS max_DATE_UPDATE 
        FROM
            input1 
        GROUP BY
            MATERIAL
    ) AS T1 
        ON T1.MATERIAL = T0.MATERIAL 
        AND T1.max_DATE_UPDATE = T0.DATE_UPDATE 
ORDER BY
    T1.MATERIAL ASC
```
