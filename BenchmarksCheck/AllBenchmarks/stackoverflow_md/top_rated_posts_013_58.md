# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 013

# input:input0

| orgName:Str | id:Str |
|---|---|
| ABC Corp | 34 |
| ABC Corp | 5 |
| Widget Company | 10 |
| Widget Company | 2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| orgName:Str | dupcount:Str | id:Str |
|---|---|---|
| ABC Corp | 1 | 34 |
| ABC Corp | 2 | 5 |
| Widget Company | 1 | 10 |
| Widget Company | 2 | 2 |

# solution

```sql
SELECT
    orgName,
    rank() OVER (PARTITION BY orgName ORDER BY id DESC),
    id 
FROM
    input1 
ORDER BY
    orgName ASC
```
