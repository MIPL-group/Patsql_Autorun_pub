# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 049

# input:input0

| UserId:Str | Alias:Str |
|---|---|
| 1 | MrX |
| 1 | MrY |
| 1 | MrA |
| 2 | Abc |
| 2 | Xyz |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| UserId:Str | Alias:Str |
|---|---|
| 1 | MrX, MrY, MrA |
| 2 | Abc, Xyz |

# solution

```sql
SELECT
    UserId,
    string_agg(Alias, ', ') 
FROM
    input1 
GROUP BY
    UserId 
ORDER BY
    UserId ASC
```
