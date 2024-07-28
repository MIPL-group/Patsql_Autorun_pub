# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_10

# input:input1

| S_key:Str | sname:Str |
|---|---|
| S1 | stu1 |
| S2 | stu2 |
| S3 | stu3 |
| S4 | stu4 |
| S5 | stu5 |
| S6 | stu6 |

# input:input0

| S_key:Str | cname:Str |
|---|---|
| S1 | class1 |
| S1 | class2 |
| S2 | class3 |
| S2 | class4 |
| S2 | class5 |
| S3 | class6 |
| S4 | class7 |
| S4 | class8 |
| S5 | class9 |
| S5 | class10 |
| S5 | class11 |
| S6 | class12 |
| S6 | class13 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| sname:Str |
|---|
| stu2 |
| stu5 |

# solution

```sql
SELECT
    T3.max_T1_sname 
FROM
    (SELECT
        max(T1.sname) AS max_T1_sname,
        count(T0.S_key) AS count_T0_S_key 
    FROM
        input1 AS T0 
    JOIN
        input2 AS T1 
            ON T0.S_key = T1.S_key 
    GROUP BY
        T0.S_key) AS T3 
JOIN
    (
        SELECT
            max(T2.count_S_key) AS max_T2_count_S_key 
        FROM
            (SELECT
                count(S_key) AS count_S_key 
            FROM
                input1 
            GROUP BY
                S_key) AS T2) AS T4 
                ON T3.count_T0_S_key = T4.max_T2_count_S_key 
        ORDER BY
            T3.max_T1_sname ASC
```
