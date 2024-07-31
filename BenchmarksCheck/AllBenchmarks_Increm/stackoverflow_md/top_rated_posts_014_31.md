# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 014

# input:input0

| id:Str | string:Str |
|---|---|
| 1 | A |
| 1 | B |
| 2 | C |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | string:Str |
|---|---|
| 1 | A, B |
| 2 | C |

# solution

```sql
SELECT
    id,
    string_agg(string, ', ') 
FROM
    input1 
GROUP BY
    id 
ORDER BY
    id ASC
```
