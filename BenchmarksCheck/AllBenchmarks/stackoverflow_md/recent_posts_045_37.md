# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 045

# input:input1

| ID:Str | Quantity:Str | Menu_id:Str |
|---|---|---|
| 1 | 3 | 1 |
| 2 | 2 | 1 |
| 3 | 4 | 3 |

# input:input0

| ID:Str | Name:Str |
|---|---|
| 1 | Menu One |
| 2 | Menu Two |
| 3 | Menu Three |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| MenuName:Str | Quantity:Str |
|---|---|
| Menu One | 5 |
| Menu Three | 4 |
| Menu Two | NULL |

# solution

```sql
SELECT menu.name, sum(orderregel.quantity)    as quantity
  FROM `menu` 
  LEFT JOIN orderregel
  on menu.menu_id = orderregel. menu_id
  group by menu_id
```
