# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 012

# input:input0

| ID:Str | code:Str | product_variants_id:Str | product_name:Str | variants:Str | variants_value:Str |
|---|---|---|---|---|---|
| 1 | 1 | 123451 | beer cake | color | blue |
| 2 | 1 | 123451 | beer cake | temperature | cold |
| 3 | 1 | 123451 | beer cake | weight | 0.5 |
| 4 | 2 | 123453 | ad wrap | color | green |
| 5 | 2 | 123453 | ad wrap | weight | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| code:Str | product_variants_id:Str | product_name:Str | variants_and_values:Str |
|---|---|---|---|
| 1 | 123451 | beer cake | color:blue, temperature:hot, weight:0.5 |
| 2 | 123453 | ad wrap | color:green, weight:1 |

# solution

```sql
SELECT xx.code, GROUP_CONCAT(concat(xx.variants,':',xx.variants_value), ', ') AS variants_and_values, xx.product_name, xx.product_variants_id
FROM products_table xx
GROUP BY xx.product_variants_id, xx.product_name, xx.code
```