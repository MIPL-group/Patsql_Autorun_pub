# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 003

# input:tblB

| f1:Str | f2:Str |
|---|---|
| a | NULL |
| b | a |
| c | a |
| d | NULL |
| e | NULL |
| f | d |
| g | d |
| h | d |
| I | NULL |

# input:tblA

| ID:Str | item:Str |
|---|---|
| 1 | c |
| 2 | a |
| 3 | b |
| 4 | e |
| 5 | d |
| 6 | f |
| 7 | a |
| 8 | c |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | item:Str |
|---|---|
| 2 | b |
| 2 | c |
| 5 | f |
| 5 | g |
| 5 | h |
| 7 | b |
| 7 | c |

# solution

```sql
select a.id, b.f1 
from tblA as a inner join
     tblB as b
     on b.f2 = a.item
order by a.id;
```
