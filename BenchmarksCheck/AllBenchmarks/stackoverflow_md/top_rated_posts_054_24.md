# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 054

# input:input0

| created_at:Str | count:Str |
|---|---|
| 04-04-2011 | 100 |
| 05-04-2011 | 50 |
| 06-04-2011 | 50 |
| 07-04-2011 | 300 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| created_at:Str | count:Str |
|---|---|
| 04-04-2011 | 100 |
| 05-04-2011 | 150 |
| 06-04-2011 | 200 |
| 07-04-2011 | 500 |

# solution

```sql
SELECT
    created_at,
    sum(count) OVER (ORDER BY created_at ASC) 
FROM
    input1 
ORDER BY
    created_at ASC
```
