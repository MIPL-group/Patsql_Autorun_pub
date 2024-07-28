# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 017

# input:input0

| ID:Str | Name:Str | Age:Str | Parent:Str |
|---|---|---|---|
| 1 | Bob | 50 | -1 |
| 2 | Matt | 20 | 1 |
| 3 | Rick | 18 | 1 |
| 4 | Alice | 48 | 2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | Name:Str |
|---|---|
| 1 | Bob |
| 2 | Matt |

# solution

```sql
SELECT DISTINCT p.ID, p.Name
FROM family AS p
INNER JOIN family AS c ON p.ID = c.Parent
```
