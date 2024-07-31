# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_2

# input:input2

| supplier_key:Str | sname:Str |
|---|---|
| S1 | SN1 |
| S2 | SN2 |
| S3 | SN3 |
| S4 | SN4 |
| S5 | SN5 |

# input:input1

| part_id:Str | color:Str |
|---|---|
| P1 | red |
| P2 | green |
| P3 | yellow |

# input:input0

| supplier_key:Str | part_id:Str |
|---|---|
| S1 | P1 |
| S1 | P2 |
| S2 | P1 |
| S2 | P2 |
| S2 | P3 |
| S3 | P3 |
| S4 | P2 |
| S5 | P1 |
| S5 | P2 |
| S5 | P3 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| sname:Str |
|---|
| SN2 |
| SN5 |

# solution

```sql
SELECT
    T0.sname 
FROM
    input3 AS T0 
LEFT JOIN
    (
        SELECT
            supplier_key,
            count(supplier_key) AS count_supplier_key 
        FROM
            input1 
        GROUP BY
            supplier_key
    ) AS T1 
        ON T0.supplier_key = T1.supplier_key 
JOIN
    (
        SELECT
            count(part_id) AS count_part_id 
        FROM
            input2
    ) AS T2 
        ON T1.count_supplier_key = T2.count_part_id 
ORDER BY
    T0.sname ASC
```
