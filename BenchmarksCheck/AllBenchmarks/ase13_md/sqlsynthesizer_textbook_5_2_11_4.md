# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_11

# input:input2

| supplier_key:Str | sname:Str |
|---|---|
| S1 | SN1 |
| S2 | SN2 |
| S3 | SN3 |
| S4 | SN4 |

# input:input1

| part_id:Str | color:Str |
|---|---|
| P1 | red |
| P2 | green |
| P3 | yellow |

# input:input0

| supplier_key:Str | part_id:Str | cost:Str |
|---|---|---|
| S1 | P1 | 10 |
| S1 | P2 | 20 |
| S2 | P1 | 14 |
| S2 | P3 | 12 |
| S3 | P1 | 4 |
| S3 | P2 | 15 |
| S3 | P3 | 30 |
| S4 | P2 | 21 |
| S4 | P3 | 13 |

# constraint

{
  "constants": [
    "green",
    "red"
  ],
  "aggregation_functions": []
}

# output:output

| sname:Str | max_cost:Str |
|---|---|
| SN1 | 20 |
| SN3 | 30 |

# solution

```sql
SELECT
    max(T2.sname),
    max(T0.cost) 
FROM
    input1 AS T0 
LEFT JOIN
    (
        SELECT
            part_id,
            color 
        FROM
            input2 
        WHERE
            color = 'green' 
            OR color = 'red'
    ) AS T1 
        ON T0.part_id = T1.part_id 
JOIN
    input3 AS T2 
        ON T0.supplier_key = T2.supplier_key 
GROUP BY
    T0.supplier_key 
HAVING
    max(T1.color) = 'red' 
    AND min(T1.color) = 'green' 
ORDER BY
    max(T2.sname) ASC
```
