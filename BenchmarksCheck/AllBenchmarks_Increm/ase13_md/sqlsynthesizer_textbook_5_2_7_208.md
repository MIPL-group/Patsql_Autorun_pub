# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_7

# input:input1

| part_id:Str | color:Str |
|---|---|
| P1 | red |
| P2 | green |
| P3 | yellow |
| P4 | red |
| P5 | green |
| P6 | yellow |

# input:input0

| supplier_key:Str | part_id:Str |
|---|---|
| S1 | P1 |
| S1 | P4 |
| S2 | P1 |
| S2 | P3 |
| S3 | P1 |
| S4 | P4 |
| S5 | P4 |
| S5 | P2 |
| S6 | P5 |
| S7 | P6 |
| S8 | P4 |

# constraint

{
  "constants": [
    "red"
  ],
  "aggregation_functions": []
}

# output:output

| sname:Str |
|---|
| S1 |
| S3 |
| S4 |
| S8 |

# solution

```sql
SELECT
    T0.supplier_key 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.part_id = T1.part_id 
GROUP BY
    T0.supplier_key 
HAVING
    max(T1.color) = 'red' 
    AND min(T1.color) = 'red' 
ORDER BY
    T0.supplier_key ASC
```
