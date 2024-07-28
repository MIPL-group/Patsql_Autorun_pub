# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 036

# input:input1

| ID:Str | Name:Str |
|---|---|
| 1 | Box |
| 2 | XXX |

# input:input0

| Account:Str | Sen1:Str | Sen2:Str |
|---|---|---|
| 1234 | 1 | 0 |
| 1235 | 0 | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Account:Str | Name:Str |
|---|---|
| 1234 | Box |
| 1235 | Box |

# solution

```sql
SELECT m.Account, k.Name FROM Table_1 m 
INNER JOIN Table_2 k ON k.ID = m.Sen1 OR k.ID = m.Sen2
```
