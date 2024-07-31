# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 002X

# input:input0

| Start:Str | End:Str |
|---|---|
| 1 | NULL |
| 3 | 4 |
| 6 | 9 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Start:Str | End:Str |
|---|---|
| 1 | 3 |
| 3 | 4 |
| 4 | 6 |
| 6 | 9 |
| 9 | NULL |

# solution

```sql
select start, lead(start) over (order by start)
from ((select t.start as start from likethis t
      ) union all
      (select t.end from likethis t
      )
     ) t
where start is not null
order by start;
```
