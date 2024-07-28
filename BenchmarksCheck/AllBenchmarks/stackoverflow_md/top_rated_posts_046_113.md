# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 046

# input:input0

| id:Str | x_field:Str |
|---|---|
| 123 | a |
| 124 | a |
| 125 | a |
| 126 | b |
| 127 | f |
| 128 | b |
| 129 | a |
| 130 | x |
| 131 | x |
| 132 | b |
| 133 | p |
| 134 | p |
| 135 | i |

# constraint

{
  "constants": [
    "f",
    "p",
    "i",
    "a"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | x_field:Str |
|---|---|
| 127 | f |
| 133 | p |
| 134 | p |
| 135 | i |
| 123 | a |
| 124 | a |
| 125 | a |
| 129 | a |

# solution

```sql
select id, x_field
from t
  join (values ('f',1),('p',2),('a',3),('i',4)) t2(x_field, p)
    USING(x_field)
ORDER BY p
```
