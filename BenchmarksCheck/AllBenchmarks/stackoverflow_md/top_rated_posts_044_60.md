# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 044

# input:input0

| id:Str | count:Str |
|---|---|
| 1 | 100 |
| 2 | 50 |
| 3 | 10 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | count:Str | cumulative_sum:Str |
|---|---|---|
| 1 | 100 | 100 |
| 2 | 50 | 150 |
| 3 | 10 | 160 |

# solution

```sql
SELECT
    id,
    count,
    sum(count) OVER (ORDER BY id ASC) 
FROM
    input1 
ORDER BY
    id ASC
```
