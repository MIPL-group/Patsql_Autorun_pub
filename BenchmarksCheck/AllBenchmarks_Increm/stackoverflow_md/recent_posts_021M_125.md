# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 021M

# input:input0

| id_order:Str | id_product:Str |
|---|---|
| a | 22 |
| a | 32 |
| b | 22 |
| b | 42 |
| b | 52 |
| b | 32 |
| c | 22 |
| c | 12 |
| d | 22 |
| d | 32 |
| d | 12 |
| e | 12 |

# constraint

{
  "constants": [
    "22"
  ],
  "aggregation_functions": []
}

# output:output

| product_id:Str | count-od2:Str |
|---|---|
| 32 | 3 |
| 12 | 2 |
| 42 | 1 |
| 52 | 1 |

# solution

```sql
select od.product_id, count(od2.id_order) as NumTimesWith2
from ps_order_detail od left join
     ps_order_detail od2
     on od.id_order = od2.id_order and
        od2.product_id = 22
where od.product_id <> 22
group by od.product_id
order by count(od2.id_order) desc;
```