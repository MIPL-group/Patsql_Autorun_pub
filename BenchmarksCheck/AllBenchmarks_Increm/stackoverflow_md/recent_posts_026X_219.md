# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 026X

# input:person

| name:Str | age:Str | hair_color:Str |
|---|---|---|
| Tom | 12 | Brown |
| Bob | 27 | Black |
| Sam | 20 | Red |
| Ann | 15 | Blonde |
| John | 30 | Blonde |

# constraint

{
  "constants": [
    25,
    "Blonde"
  ],
  "aggregation_functions": []
}

# output:output

| name:Str | age:Str | hair_color:Str | clause_1:Str | clause_2:Str |
|---|---|---|---|---|
| Bob | 27 | Black | true | false |
| Ann | 15 | Blonde | false | true |
| John | 30 | Blonde | true | true |

# solution

```sql
select *
from (
  select p.*, 
         (age >= 25) as condition_1, 
         (hair_color = 'Blonde') as condition_2
  from person p
) t
where condition_1 or condition_2
```
