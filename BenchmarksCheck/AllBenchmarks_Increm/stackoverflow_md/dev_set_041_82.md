# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 041

# input:input0

| NBR:Str | ID:Str | DT:Str |
|---|---|---|
| 1 | 1 | 12/31/2001 |
| 1 | 2 | 08/07/2001 |
| 2 | 3 | 08/07/2001 |
| 2 | 4 | 09/12/2001 |
| 3 | 5 | 09/11/2001 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| NBR:Str | ID:Str | DT:Str |
|---|---|---|
| 1 | 2 | 08/07/2001 |
| 2 | 3 | 08/07/2001 |
| 3 | 5 | 09/11/2001 |

# solution

```sql
SELECT t.*
FROM
    tablename t
    INNER JOIN 
    (
       SELECT
          NBR
          ,MIN(DT) AS DT
       FROM
          tablename
       GROUP BY
          NBR
    ) g
    ON t.NBR = g.NBR
    AND t.DT = g.DT
```
