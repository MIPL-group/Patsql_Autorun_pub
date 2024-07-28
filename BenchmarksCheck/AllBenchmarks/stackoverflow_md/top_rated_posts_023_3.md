# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 023

# input:input0

| itemID:Str | ordercount:Str |
|---|---|
| 388 | 3 |
| 234 | 2 |
| 3432 | 1 |
| 693 | 1 |
| 3459 | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| rank:Str | itemID:Str | ordercount:Str |
|---|---|---|
| 1 | 388 | 3 |
| 2 | 234 | 2 |
| 3 | 3432 | 1 |
| 4 | 693 | 1 |
| 5 | 3459 | 1 |

# solution

```sql
SELECT @rank:=@rank+1 AS rank, itemID, COUNT(*) as ordercount
  FROM orders
  GROUP BY itemID
  ORDER BY ordercount DESC;
```
