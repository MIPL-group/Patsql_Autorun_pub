# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 015X

# input:input0

| CriteriaID:Str | KSB_Requirement:Str | ModuleID:Str | Module_Title:Str |
|---|---|---|---|
| 1 | Understand something | 5 | Principles 1 |
| 1 | Understand something | 6 | Principles 2 |
| 1 | Understand something | 7 | Principles 3 |
| 2 | Learn something | 5 | Principles 1 |
| 2 | Learn something | 6 | Principles 2 |

# constraint

{
  "constants": [
    "Principles 1",
    "Principles 2",
    "Principles 3"
  ],
  "aggregation_functions": []
}

# output:output

| KSB_Requirement:Str | Principle 1:Str | Principle 2:Str | Principle 3:Str |
|---|---|---|---|
| Understand something | 1 | 1 | 1 |
| Learn something | 1 | 1 | 0 |

# solution

```sql
DECLARE 
  @cols AS NVARCHAR(MAX),
  @query  AS NVARCHAR(MAX)
```
