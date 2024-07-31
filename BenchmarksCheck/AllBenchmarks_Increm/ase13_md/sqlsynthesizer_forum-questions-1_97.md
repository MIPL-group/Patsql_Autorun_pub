# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: forum-questions-1

# input:input0

| idx_key:Str | upedonid:Str |
|---|---|
| k1 | id2 |
| k2 | id2 |
| k3 | id2 |
| k4 | NULL |
| k5 | id3 |
| k6 | id3 |
| k7 | id4 |
| k8 | id5 |
| k9 | id5 |
| k10 | NULL |
| k11 | id6 |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| upedonid:Str | count:Str |
|---|---|
| id2 | 3 |
| id3 | 2 |
| id5 | 2 |

# solution

```sql
SELECT
    upedonid,
    count(idx_key) 
FROM
    input1 
GROUP BY
    upedonid 
HAVING
    count(upedonid) > 1 
ORDER BY
    upedonid ASC
```
