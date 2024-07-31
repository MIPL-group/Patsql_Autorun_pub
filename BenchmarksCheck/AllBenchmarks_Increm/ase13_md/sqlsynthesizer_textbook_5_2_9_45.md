# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_9

# input:input2

| supplier_key:Str | sname:Str |
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

# input:input1

| part_id:Str | color:Str |
|---|---|
| P1 | red |
| P2 | green |
| P3 | yellow |
| P4 | red |
| P5 | green |
| P6 | blue |

# input:input0

| supplier_key:Str | part_id:Str |
|---|---|
| S1 | P1 |
| S1 | P4 |
| S1 | P2 |
| S2 | P2 |
| S2 | P3 |
| S3 | P5 |
| S4 | P3 |
| S4 | P6 |
| S5 | P4 |
| S5 | P2 |
| S6 | P4 |
| S7 | P6 |
| S8 | P5 |
| S8 | P2 |
| S9 | P1 |
| S9 | P2 |
| S9 | P6 |
| S10 | P6 |

# constraint

{
  "constants": [
    "red",
    "green"
  ],
  "aggregation_functions": []
}

# output:output

| sname:Str |
|---|
| SN1 |
| SN1 |
| SN1 |
| SN2 |
| SN3 |
| SN5 |
| SN5 |
| SN6 |
| SN8 |
| SN8 |
| SN9 |
| SN9 |

# solution

```sql
SELECT
    T2.sname 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.part_id = T1.part_id 
JOIN
    input3 AS T2 
        ON T0.supplier_key = T2.supplier_key 
WHERE
    T1.color = 'red' 
    OR T1.color = 'green' 
ORDER BY
    T2.sname ASC
```
