# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_7

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
  "constants": [],
  "aggregation_functions": []
}

# output:output

| level:Str | aveage:Dbl |
|---|---|
| JR | 19 |
| SO | 21 |
| SR | 23 |

# solution

```sql
SELECT
    level,
    avg(age) 
FROM
    input1 
GROUP BY
    level 
ORDER BY
    level ASC
```
