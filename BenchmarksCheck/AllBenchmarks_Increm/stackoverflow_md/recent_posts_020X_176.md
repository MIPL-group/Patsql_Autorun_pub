# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 020X

# input:input0

| uid:Str | timestamp:Str | action:Str |
|---|---|---|
| 1 | 2016-01-01 12:00 | login |
| 3 | 2016-01-01 12:30 | login |
| 1 | 2016-01-01 12:05 | click |
| 2 | 2016-01-01 13:00 | login |
| 2 | 2016-01-01 13:05 | logout |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| uid:Str | result:Str |
|---|---|
| 1 | [<2016-01-01 12:00, login>, <2016-01-01 12:05, click>] |
| 2 | [<2016-01-01 13:00, login>, <2016-01-01 13:05, logout>] |
| 3 | [<2016-01-01 12:30, login>] |

# solution

```sql
// This is a HiveQL question.
```
