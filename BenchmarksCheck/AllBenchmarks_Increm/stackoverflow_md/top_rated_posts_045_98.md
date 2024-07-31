# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 045

# input:input0

| user_id:Str | account_no:Str | zip:Str | date:Str |
|---|---|---|---|
| 1 | 123 | 55555 | 12-DEC-09 |
| 1 | 123 | 66666 | 12-DEC-09 |
| 1 | 123 | 55555 | 13-DEC-09 |
| 2 | 456 | 77777 | 14-DEC-09 |
| 2 | 456 | 77777 | 14-DEC-09 |
| 2 | 789 | 88888 | 14-DEC-09 |
| 2 | 789 | 88888 | 14-DEC-09 |
| 3 | 888 | 11111 | 14-DEC-09 |
| 3 | 888 | 22222 | 14-DEC-09 |
| 3 | 888 | 22222 | 14-DEC-09 |
| 3 | 999 | 33333 | 14-DEC-09 |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| user_id:Str | count:Str |
|---|---|
| 1 | 2 |
| 3 | 3 |

# solution

```sql
SELECT
    max(user_id),
    count(user_id) 
FROM
    input1 
GROUP BY
    account_no,
    date 
HAVING
    count(DISTINCT zip) > 1 
ORDER BY
    max(user_id) ASC
```
