# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 021

# input:input0

| CHARGEID:Str | CHARGETYPE:Str | SERVICEMONTH:Str |
|---|---|---|
| 102 | R | 08/01/2008 |
| 162 | N | 08/01/2008 |
| 161 | N | 09/01/2008 |
| 101 | R | 02/01/2008 |
| 103 | R | 03/01/2008 |
| 104 | R | 04/01/2008 |
| 105 | R | 05/01/2008 |
| 106 | R | 06/01/2008 |
| 107 | R | 07/01/2008 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| CHARGEID:Str | CHARGETYPE:Str | SERVICEMONTH:Str |
|---|---|---|
| 102 | R | 08/01/2008 |
| 161 | N | 09/01/2008 |

# solution

```sql
SELECT
    T0.CHARGEID,
    T1.CHARGETYPE,
    T0.SERVICEMONTH 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            CHARGETYPE,
            max(SERVICEMONTH) AS max_SERVICEMONTH 
        FROM
            input1 
        GROUP BY
            CHARGETYPE
    ) AS T1 
        ON T1.CHARGETYPE = T0.CHARGETYPE 
        AND T1.max_SERVICEMONTH = T0.SERVICEMONTH 
ORDER BY
    T0.CHARGEID ASC
```
