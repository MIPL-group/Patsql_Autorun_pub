# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_6

# input:input1

| sid:Str | sname:Str |
|---|---|
| S1 | SN1 |
| S2 | SN2 |
| S3 | SN3 |
| S4 | SN4 |

# input:input0

| sid:Str | part_key:Str | cost:Str |
|---|---|---|
| S1 | P1 | 1 |
| S2 | P1 | 2 |
| S1 | P2 | 3 |
| S2 | P2 | 2 |
| S3 | P2 | 2 |
| S3 | P3 | 4 |
| S1 | P4 | 2 |
| S4 | P3 | 5 |
| S2 | P5 | 1 |
| S3 | P5 | 2 |
| S3 | P6 | 3 |
| S1 | P7 | 2 |
| S2 | P8 | 4 |
| S4 | P9 | 4 |
| S3 | P9 | 5 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| part_key:Str | sname:Str |
|---|---|
| P1 | SN2 |
| P2 | SN1 |
| P3 | SN4 |
| P4 | SN1 |
| P5 | SN3 |
| P6 | SN3 |
| P7 | SN1 |
| P8 | SN2 |
| P9 | SN3 |

# solution

```sql
SELECT
    T0.part_key,
    T1.sname 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.sid = T1.sid 
JOIN
    (
        SELECT
            part_key,
            max(cost) AS max_cost 
        FROM
            input1 
        GROUP BY
            part_key
    ) AS T2 
        ON T0.part_key = T2.part_key 
        AND T0.cost = T2.max_cost 
ORDER BY
    T0.part_key ASC
```
