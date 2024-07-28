# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 035

# input:input0

| Name:Str | Maths:Str | Science:Str | English:Str |
|---|---|---|---|
| Tilak | 90 | 40 | 60 |
| Raj | 30 | 20 | 10 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Name:Str | Subject:Str | Marks:Str |
|---|---|---|
| Tilak | Maths | 90 |
| Tilak | Science | 40 |
| Tilak | English | 60 |

# solution

```sql
select Name, Marks from studentmarks
Unpivot
(
  Marks for details in (Maths, Science, English)
```
