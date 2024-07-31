# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 041X

# input:input0

| Count:Str | Pay1Click:Str | PayMailCC:Str | PayMailCheck:Str | PayPhoneACH:Str | PayPhoneCC:Str | PayWuFoo:Str |
|---|---|---|---|---|---|---|
| 8 | 0 | 0 | 0 | 0 | 0 | 1 |
| 25 | 0 | 0 | 0 | 0 | 1 | 0 |
| 8 | 0 | 0 | 0 | 1 | 0 | 0 |
| 99 | 0 | 0 | 1 | 0 | 0 | 0 |
| 11 | 0 | 1 | 0 | 0 | 0 | 0 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Count:Str | PaymentType:Str |
|---|---|
| 8 | PayWuFoo |
| 25 | PayPhoneCC |
| 8 | PayPhoneACH |
| 99 | PayMailCheck |
| 11 | PayMailCC |

# solution

```sql
Select Count,
```
