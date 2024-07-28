# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_8

# input:input0

| S_key:Str | level:Str | age:Str |
|---|---|---|
| S1 | JR | 18 |
| S2 | SR | 24 |
| S3 | JR | 21 |
| S4 | SR | 22 |
| S5 | JR | 18 |
| S6 | SO | 20 |
| S7 | SO | 22 |

# constraint

{
  "constants": [
    "JR"
  ],
  "aggregation_functions": []
}

# output:output

| level:Str | aveage:Dbl |
|---|---|
| SO | 21 |
| SR | 23 |

# solution

```sql
SELECT
    level,
    avg(age) 
FROM
    input1 
WHERE
    level <> 'JR' 
GROUP BY
    level 
ORDER BY
    level ASC
```
