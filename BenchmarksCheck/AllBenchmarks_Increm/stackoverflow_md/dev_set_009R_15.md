# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 009R

# input:input0

| ID:Str | NAME:Str | EMAIL:Str |
|---|---|---|
| 1 | John | asd@asd.com |
| 2 | Sam | asd@asd.com |
| 3 | Tom | asd@asd.com |
| 5 | Tom | asd@asd.com |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| c:Str |
|---|
| Tom |

# solution

```sql
SELECT
    name, email, COUNT(*)
FROM
    users
GROUP BY
    name, email
HAVING 
    COUNT(*) > 1
```
