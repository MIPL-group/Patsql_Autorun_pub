# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 001R

# input:input0

| id:Str | rev:Str | content:Str |
|---|---|---|
| 01 | 1 | A |
| 01 | 2 | C |
| 01 | 3 | D |
| 02 | 1 | E |
| 02 | 3 | B |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 01 | 3 | D |
| 02 | 3 | B |

# solution

```sql
Select t1.id, t1.rev, t1.content
From t As t1 Join (
    Select id, Max(rev) As maxrev
    From t
    Group By id
) As t2
On t1.id = t2.id And t1.rev = t2.maxrev
```
