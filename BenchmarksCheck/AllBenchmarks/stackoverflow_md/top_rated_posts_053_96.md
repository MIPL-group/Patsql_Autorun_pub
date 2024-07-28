# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 053

# input:input0

| Status:Str |
|---|
| a1 |
| i |
| t |
| a2 |
| a3 |

# constraint

{
  "constants": [
    "a1",
    "a2",
    "a3",
    "Active",
    "Inactive",
    "Terminated"
  ],
  "aggregation_functions": []
}

# output:output

| Status:Str | STATUSTEXT:Str |
|---|---|
| a1 | Active |
| i | Inactive |
| t | Terminated |
| a2 | Active |
| a3 | Active |

# solution

```sql
SELECT
  status,
  CASE
    WHEN STATUS IN('a1','a2','a3')
    THEN 'Active'
    WHEN STATUS = 'i'
    THEN 'Inactive'
    WHEN STATUS = 't'
    THEN 'Terminated'
  END AS STATUSTEXT
FROM
  STATUS
```
