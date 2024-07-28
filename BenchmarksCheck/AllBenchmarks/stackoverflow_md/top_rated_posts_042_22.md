# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 042

# input:input0

| :Str | Paul:Str | John:Str | Tim:Str | Eric:Str |
|---|---|---|---|---|
| Red | 1 | 5 | 1 | 3 |
| Green | 8 | 4 | 3 | 5 |
| Blue | 2 | 2 | 9 | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| :Str | Red:Str | Green:Str | Blue:Str |
|---|---|---|---|
| Paul | 1 | 8 | 2 |
| John | 5 | 4 | 2 |
| Tim | 1 | 3 | 9 |
| Eric | 3 | 5 | 1 |

# solution

```sql
select name,
  sum(case when color = 'Red' then value else 0 end) Red,
  sum(case when color = 'Green' then value else 0 end) Green,
  sum(case when color = 'Blue' then value else 0 end) Blue
from
(
  select color, Paul value, 'Paul' name
  from yourTable
  union all
  select color, John value, 'John' name
  from yourTable
  union all
  select color, Tim value, 'Tim' name
  from yourTable
  union all
  select color, Eric value, 'Eric' name
  from yourTable
) src
group by name
```
