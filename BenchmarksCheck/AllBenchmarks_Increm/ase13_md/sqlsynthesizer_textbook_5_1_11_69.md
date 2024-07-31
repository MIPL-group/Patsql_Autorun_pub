# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_11

# input:input1

| S_key:Str | C_name:Str |
|---|---|
| S1 | class2 |
| S2 | class1 |
| S4 | class2 |
| S4 | class4 |
| S5 | class4 |
| S7 | class5 |
| S7 | class1 |
| S8 | class4 |
| S10 | class5 |

# input:input0

| S_key:Str | S_name:Str |
|---|---|
| S1 | SN1 |
| S2 | SN2 |
| S3 | SN3 |
| S4 | SN4 |
| S5 | SN5 |
| S6 | SN6 |
| S7 | SN7 |
| S8 | SN8 |
| S9 | SN9 |
| S10 | SN10 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| S_name:Str |
|---|
| SN3 |
| SN6 |
| SN9 |

# solution

```sql
SELECT
    T0.S_name 
FROM
    input1 AS T0 
LEFT JOIN
    input2 AS T1 
        ON T0.S_key = T1.S_key 
WHERE
    T1.S_key IS NULL 
ORDER BY
    T0.S_name ASC
```
