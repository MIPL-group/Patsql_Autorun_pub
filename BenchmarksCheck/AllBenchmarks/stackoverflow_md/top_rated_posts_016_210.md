# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 016

# input:input0

| ID:Str | COMPANY_ID:Str | EMPLOYEE:Str |
|---|---|---|
| 1 | 1 | Anna |
| 2 | 1 | Bill |
| 3 | 2 | Carol |
| 4 | 2 | Dave |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| COMPANY_ID:Str | EMPLOYEE:Str |
|---|---|
| 1 | Anna, Bill |
| 2 | Carol, Dave |

# solution

```sql
SELECT
    COMPANY_ID,
    string_agg(EMPLOYEE, ', ') 
FROM
    input1 
GROUP BY
    COMPANY_ID 
ORDER BY
    COMPANY_ID ASC
```
