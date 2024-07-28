# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_5

# input:input2

| F_key:Str | F_name:Str |
|---|---|
| F1 | teach1 |
| F2 | teach2 |
| F3 | teach3 |
| F4 | teach4 |
| F5 | teach5 |

# input:input1

| c:Str |
|---|
| R101 |
| R102 |
| R103 |

# input:input0

| C_name:Str | F_key:Str | Room:Str |
|---|---|---|
| C1 | F1 | R101 |
| C2 | F1 | R102 |
| C3 | F1 | R103 |
| C4 | F2 | R103 |
| C7 | F2 | R101 |
| C5 | F3 | R101 |
| C6 | F4 | R101 |
| C8 | F4 | R102 |
| C9 | F4 | R103 |
| C10 | F5 | R101 |
| C11 | F5 | R102 |
| C12 | F5 | R103 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| F_name:Str |
|---|
| teach1 |
| teach4 |
| teach5 |

# solution

```sql
SELECT
    T0.F_name 
FROM
    input3 AS T0 
LEFT JOIN
    (
        SELECT
            F_key,
            count(C_name) AS count_C_name 
        FROM
            input1 
        GROUP BY
            F_key
    ) AS T1 
        ON T0.F_key = T1.F_key 
JOIN
    (
        SELECT
            count(c) AS count_c 
        FROM
            input2
    ) AS T2 
        ON T1.count_C_name = T2.count_c 
ORDER BY
    T0.F_name ASC
```
