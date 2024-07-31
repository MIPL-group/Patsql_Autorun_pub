# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 055

# input:input0

| ID:Str | User:Str | Activity:Str | PageURL:Str |
|---|---|---|---|
| 1 | Me | act1 | ab |
| 2 | Me | act1 | cd |
| 3 | You | act2 | xy |
| 4 | You | act2 | st |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| User:Str | Activity:Str | PageURL:Str |
|---|---|---|
| Me | act1 | ab cd |
| You | act2 | xy st |

# solution

```sql
SELECT
    User,
    max(Activity),
    string_agg(PageURL, ' ') 
FROM
    input1 
GROUP BY
    User 
ORDER BY
    User ASC
```
