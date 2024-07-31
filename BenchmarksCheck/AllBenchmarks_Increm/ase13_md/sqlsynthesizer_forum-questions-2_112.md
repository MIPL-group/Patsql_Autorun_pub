# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: forum-questions-2

# input:input0

| project_code:Str | invoice_key:Str | invoice_amount:Str |
|---|---|---|
| proj1 | inv1 | 100 |
| proj1 | inv2 | 200 |
| proj2 | inv3 | 300 |
| proj2 | inv4 | 400 |
| proj3 | inv5 | 500 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| project_code:Str | sum_invoice:Str |
|---|---|
| proj1 | 300 |
| proj2 | 700 |
| proj3 | 500 |

# solution

```sql
SELECT
    project_code,
    sum(invoice_amount) 
FROM
    input1 
GROUP BY
    project_code 
ORDER BY
    project_code ASC
```
