# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 056

# input:input0

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| a | b | c |
| d | e | f |
| g | h | i |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str | c4:Str | c5:Str |
|---|---|---|---|---|
| c |  |  |  |  |
| b | f |  |  |  |
| a | e | i |  |  |
| d | h |  |  |  |
| g |  |  |  |  |

# solution

```sql
create table t45 (id int identity, colA char(1), colX char(1), colZ char(1))
insert t45 select 'a','b','c'
insert t45 select 'd','e','f'
insert t45 select 'g','h','i'
GO
```
