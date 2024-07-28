# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 046X

# input:input0

| ID:Str | Type:Str | Value:Str |
|---|---|---|
| A | Z01 | 10 |
| A | Z09 | 20 |
| B | Z01 | 30 |
| C | Z01 | 40 |
| D | Z09 | 50 |
| F | Z09 | 50 |
| F | Z01 | 52 |
| E | Z10 | 60 |

# constraint

{
  "constants": [
    "Z01",
    "Z09"
  ],
  "aggregation_functions": []
}

# output:output

| Id:Str | Type:Str | Value:Str |
|---|---|---|
| A | Z01 | 10 |
| B | Z01 | 30 |
| C | Z01 | 40 |
| D | Z09 | 50 |
| F | Z01 | 52 |

# solution

```sql
select *
from table
where type = `Z01`
```
