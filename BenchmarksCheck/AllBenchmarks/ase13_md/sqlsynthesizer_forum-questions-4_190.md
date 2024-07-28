# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: forum-questions-4

# input:input2

| T2Column1:Str | T3Column2:Str |
|---|---|
| 20011 | Site |
| 20012 | Site |
| 20013 | Site |

# input:input1

| T2Column1:Str | T1Column2:Str | T2Column3:Str |
|---|---|---|
| 20011 | 2001 | 200131 |
| 20012 | 2001 | 200132 |
| 20013 | 2001 | 200133 |

# input:input0

| T1Column1:Str | T1Column2:Str | T1Column3:Str | T1Column4:Str |
|---|---|---|---|
| 101 | 2001 | 3020 | 01-01-11 |
| 101 | 2002 | 3002 | 02-01-11 |
| 101 | 2001 | 3001 | 03-01-11 |
| 102 | 2002 | 3002 | 01-01-11 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| T1Column1:Str | T2Column3:Str | T1Column4:Str | T3Column2:Str |
|---|---|---|---|
| 101 | 200131 | 01-01-11 | Site |
| 101 | 200132 | 01-01-11 | Site |
| 101 | 200133 | 01-01-11 | Site |

# solution

```sql
SELECT
    T2.min_T1Column1,
    T0.T2Column3,
    T2.min_T1Column4,
    T1.T3Column2 
FROM
    input2 AS T0 
JOIN
    input3 AS T1 
        ON T0.T2Column1 = T1.T2Column1 
JOIN
    (
        SELECT
            min(T1Column1) AS min_T1Column1,
            min(T1Column2) AS min_T1Column2,
            min(T1Column4) AS min_T1Column4 
        FROM
            input1
    ) AS T2 
        ON T0.T1Column2 = T2.min_T1Column2 
ORDER BY
    T0.T2Column3 ASC
```
