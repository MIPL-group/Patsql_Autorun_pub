# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_4

# input:input2

| sid:Str | sname:Str |
|---|---|
| S1 | B |
| S2 | A |
| S3 | AWS |
| S4 | AWS |

# input:input1

| part_key:Str | pname:Str |
|---|---|
| P1 | PN1 |
| P2 | PN2 |
| P3 | PN3 |
| P4 | PN4 |
| P5 | PN5 |
| P6 | PN6 |
| P7 | PN7 |
| P8 | PN8 |
| P9 | PN9 |

# input:input0

| sid:Str | part_key:Str |
|---|---|
| S1 | P1 |
| S3 | P1 |
| S2 | P2 |
| S3 | P2 |
| S3 | P3 |
| S1 | P4 |
| S3 | P3 |
| S2 | P5 |
| S3 | P5 |
| S3 | P6 |
| S1 | P7 |
| S2 | P8 |
| S4 | P9 |
| S3 | P9 |

# constraint

{
  "constants": [
    "AWS"
  ],
  "aggregation_functions": []
}

# output:output

| pname:Str |
|---|
| PN3 |
| PN6 |
| PN9 |

# solution

```sql
SELECT
    max(T1.pname) 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.part_key = T1.part_key 
JOIN
    input3 AS T2 
        ON T0.sid = T2.sid 
GROUP BY
    T0.part_key 
HAVING
    max(T2.sname) = 'AWS' 
    AND min(T2.sname) = 'AWS' 
ORDER BY
    max(T1.pname) ASC
```
