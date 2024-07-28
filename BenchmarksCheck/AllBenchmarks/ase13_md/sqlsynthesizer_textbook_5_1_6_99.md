# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_6

# input:input2

| F_key:Str | F_name:Str |
|---|---|
| f1 | faculty1 |
| f2 | faculty2 |
| f3 | faculty3 |
| f4 | faculty4 |

# input:input1

| S_key:Str | C_name:Str |
|---|---|
| S1 | class2 |
| S1 | class3 |
| S2 | class1 |
| S2 | class4 |
| S2 | class7 |
| S3 | class2 |
| S3 | class4 |
| S3 | class5 |
| S4 | class1 |
| S4 | class2 |
| S4 | class4 |
| S4 | class5 |
| S5 | class3 |
| S5 | class4 |
| S5 | class6 |
| S5 | class7 |
| S6 | class3 |
| S6 | class4 |
| S6 | class9 |
| S7 | class1 |
| S7 | class3 |
| S7 | class5 |
| S7 | class6 |
| S8 | class2 |
| S8 | class3 |
| S8 | class4 |
| S8 | class5 |
| S8 | class6 |
| S8 | class8 |

# input:input0

| C_name:Str | F_key:Str |
|---|---|
| class1 | f1 |
| class2 | f2 |
| class3 | f2 |
| class4 | f3 |
| class5 | f3 |
| class6 | f3 |
| class7 | f4 |
| class8 | f4 |
| class9 | f1 |

# constraint

{
  "constants": [
    "5"
  ],
  "aggregation_functions": []
}

# output:output

| F_name:Str |
|---|
| faculty1 |
| faculty4 |

# solution

```sql
SELECT
    max(T2.F_name) 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.C_name = T1.C_name 
JOIN
    input3 AS T2 
        ON T0.F_key = T2.F_key 
GROUP BY
    T0.F_key 
HAVING
    count(T0.C_name) < 5 
ORDER BY
    max(T2.F_name) ASC
```
