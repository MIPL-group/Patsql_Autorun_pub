# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 022

# input:input0

| id:Str | val:Str |
|---|---|
| 1 | 114 |
| 1 | 117 |
| 1 | 112 |
| 1 | 112 |
| 1 | 119 |
| 1 | 119 |
| 1 | 113 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| medval:Str |
|---|
| 114 |

# solution

```sql
SELECT x.val from data x, data y
GROUP BY x.val
HAVING SUM(SIGN(1-SIGN(y.val-x.val))) = (COUNT(*)+1)/2
```
