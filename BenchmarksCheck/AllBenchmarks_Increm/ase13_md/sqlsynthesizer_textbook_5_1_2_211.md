# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_2

# input:input2

| F_key:Str | F_name:Str |
|---|---|
| f1 | faculty1 |
| f2 | faculty2 |
| f3 | faculty3 |
| f4 | faculty4 |

# input:input3

| S_key:Str | major:Str | age:Str |
|---|---|---|
| S1 | History | 18 |
| S2 | Computer | 19 |
| S3 | Computer | 20 |
| S4 | Math | 21 |
| S5 | Computer | 22 |
| S6 | Math | 23 |
| S7 | English | 24 |
| S8 | English | 25 |
| S9 | English | 26 |
| S10 | English | 27 |

# input:input1

| S_key:Str | C_name:Str |
|---|---|
| S1 | class1 |
| S2 | class1 |
| S3 | class1 |
| S4 | class2 |
| S4 | class4 |
| S5 | class4 |
| S6 | class3 |
| S6 | class2 |
| S7 | class5 |
| S7 | class3 |
| S8 | class4 |
| S9 | class5 |
| S9 | class2 |
| S10 | class5 |

# input:input0

| C_name:Str | F_key:Str |
|---|---|
| class1 | f1 |
| class2 | f2 |
| class3 | f2 |
| class4 | f3 |
| class5 | f4 |
| class6 | f4 |

# constraint

{
  "constants": [
    "History",
    "faculty1"
  ],
  "aggregation_functions": []
}

# output:output

| age:Str |
|---|
| 20 |

# solution

```sql
SELECT
    max(T3.age) 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.C_name = T1.C_name 
JOIN
    input3 AS T2 
        ON T0.F_key = T2.F_key 
JOIN
    input4 AS T3 
        ON T1.S_key = T3.S_key 
WHERE
    T3.major = 'History' 
    OR T2.F_name = 'faculty1'
```
