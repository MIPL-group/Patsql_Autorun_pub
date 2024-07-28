# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 011R

# input:input0

| username:Str | date:Str | value:Str |
|---|---|---|
| brad | 2010-01-02 | 1.1 |
| fred | 2010-02-03 | 1.0 |
| bob | 2009-08-04 | 1.5 |
| brad | 2010-02-03 | 1.2 |
| fred | 2009-12-02 | 1.4 |
| fred | 2010-01-03 | 1.1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| username:Str | date:Str | value:Str |
|---|---|---|
| fred | 2010-02-03 | 1.0 |
| bob | 2009-08-04 | 1.5 |
| brad | 2010-02-03 | 1.2 |

# solution

```sql
select t.username, t.date, t.value
from MyTable t
inner join (
    select username, max(date) as MaxDate
    from MyTable
    group by username
) tm on t.username = tm.username and t.date = tm.MaxDate
```
