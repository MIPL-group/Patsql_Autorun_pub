# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_12

# input:input0

| S_key:Str | age:Str | level:Str |
|---|---|---|
| S0 | 19 | JR |
| S0 | 19 | JR |
| S0 | 20 | SO |
| S0 | 20 | SO |
| S0 | 20 | JR |
| S0 | 21 | SO |
| S0 | 21 | SO |
| S0 | 21 | JR |
| S0 | 21 | JR |
| S0 | 21 | JR |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| age:Str | level:Str |
|---|---|
| 19 | JR |
| 20 | SO |
| 21 | JR |

# solution

```sql
SELECT
    T1.T0_age,
    T2.level 
FROM
    (SELECT
        T0.age AS T0_age,
        max(T0.count_S_key) AS max_T0_count_S_key 
    FROM
        (SELECT
            age,
            count(S_key) AS count_S_key 
        FROM
            input1 
        GROUP BY
            age,
            level) AS T0 
    GROUP BY
        T0.age) AS T1 
    JOIN
        (
            SELECT
                age,
                level,
                count(S_key) AS count_S_key 
            FROM
                input1 
            GROUP BY
                age,
                level
        ) AS T2 
            ON T1.T0_age = T2.age 
            AND T1.max_T0_count_S_key = T2.count_S_key 
    ORDER BY
        T1.T0_age ASC
```
