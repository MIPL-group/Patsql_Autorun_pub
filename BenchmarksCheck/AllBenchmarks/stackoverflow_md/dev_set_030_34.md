# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 030

# input:input1

| ID:Str | LINK:Str | LAST_DATE:Str |
|---|---|---|
| 1 | 100 | 12/12/2012 |
| 2 | 100 | 12/13/2012 |
| 3 | 100 | 12/14/2013 |
| 4 | 101 | 12/12/2012 |
| 5 | 101 | 12/13/2012 |
| 6 | 101 | 12/14/2013 |

# input:input0

| ID:Str | DESCR:Str |
|---|---|
| 100 | DESCRIPTION0 |
| 101 | DESCRIPTION1 |
| 102 | DESCRIPTION2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 100 | DESCRIPTION0 | 12/14/2013 |
| 101 | DESCRIPTION1 | 12/14/2013 |
| 102 | DESCRIPTION2 | NULL |

# solution

```sql
SELECT
    T0.ID,
    max(T0.DESCR),
    max(T1.LAST_DATE) 
FROM
    input1 AS T0 
LEFT JOIN
    input2 AS T1 
        ON T0.ID = T1.LINK 
GROUP BY
    T0.ID 
ORDER BY
    T0.ID ASC
```
