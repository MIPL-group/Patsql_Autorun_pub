# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_1

# input:supplier

| supplier_key:Str | part_id:Str |
|---|---|
| S1 | P1 |
| S1 | P4 |
| S2 | P2 |
| S2 | P3 |
| S3 | P5 |

# input:parts

| part_id:Str | part_name:Str |
|---|---|
| P1 | PN1 |
| P2 | PN2 |
| P3 | PN3 |
| P4 | PN4 |
| P5 | PN5 |
| P6 | PN6 |
| P7 | PN7 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| part_name:Str |
|---|
| PN1 |
| PN2 |
| PN3 |
| PN4 |
| PN5 |

# solution

```sql
SELECT
    T1.part_name 
FROM
    supplier AS T0 
JOIN
    parts AS T1 
        ON T0.part_id = T1.part_id 
ORDER BY
    T1.part_name ASC
```
