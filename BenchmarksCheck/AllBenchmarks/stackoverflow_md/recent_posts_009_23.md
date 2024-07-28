# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 009

# input:t_documents

| id:Str | user_id:Str | submitted_date:Str | text:Str | status:Str |
|---|---|---|---|---|
| 1 | 1234 | 2016-07-05 | "this is a test" | 3 |
| 2 | 1234 | 2016-07-06 | "this is a test" | 3 |
| 3 | 5678 | 2016-07-07 | "this is another test" | 3 |
| 4 | 5678 | 2016-07-08 | "this is another test" | 3 |
| 5 | 5678 | 2016-07-09 | "this is a test" | 3 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| user_id:Str | text:Str | dups:Str |
|---|---|---|
| 1234 | "this is a test" | 2 |
| 5678 | "this is another test" | 2 |
| 5678 | "this is a test" | 1 |

# solution

```sql
SELECT user_id, COUNT(*) AS dup_count
FROM t_documents
GROUP BY user_id, text
```
