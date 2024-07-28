# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 003

# input:input0

| c:Str |
|---|
| shopping |
| fishing |
| coding |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c:Str |
|---|
| shopping, fishing, coding |

# solution

```sql
SELECT
    string_agg(c, ', ') 
FROM
    input1
```
