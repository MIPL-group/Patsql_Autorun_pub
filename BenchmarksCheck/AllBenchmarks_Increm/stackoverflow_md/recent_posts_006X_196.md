# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 006X

# input:products_table

| ID:Str | code:Str | product_variants_id:Str | product_name:Str | variants:Str | variants_value:Str |
|---|---|---|---|---|---|
| 2 | 1 | 123451 | beer cake | temperature | hot |
| 3 | 1 | 123451 | beer cake | weight | 0.5 |
| 4 | 2 | 123453 | ad wrap | color | green |
| 5 | 2 | 123453 | ad wrap | weight | 1 |

# constraint

{
  "constants": [
    "hot"
  ],
  "aggregation_functions": []
}

# output:output

| code:Str | product_variants_id:Str | product_name:Str | variants_and_values:Str |
|---|---|---|---|

# solution

```sql
SELECT T1.code,
       product_variants_id,
       product_name,
       string_agg(variants || ':' || variants_value, ', ' ORDER BY id) as variants_and_values
FROM products_table as T1
JOIN (SELECT code FROM products_table WHERE variants_value = 'hot') as T2
  ON T1.code = T2.code
GROUP BY product_variants_id, product_name, T1.code
```
