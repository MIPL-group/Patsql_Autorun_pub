# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 055AM

# input:input0

| Product_ID:Str | Client_ID:Str |
|---|---|
| 21 | 233 |
| 21 | 133 |
| 22 | 233 |
| 22 | 233 |
| 23 | 233 |
| 24 | 433 |
| 24 | 233 |

# constraint

{
  "constants": [
    "233"
  ],
  "aggregation_functions": []
}

# output:output

| c1:Str |
|---|
| 22 |
| 23 |

# solution

```sql
SELECT
    Product_ID 
FROM
    input1 
GROUP BY
    Product_ID 
HAVING
    max(Client_ID) = 233 
    AND min(Client_ID) = 233 
ORDER BY
    Product_ID ASC
```
