# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 023X

# input:input0

| child1:Str | name1:Str | child2:Str | name2:Str | child3:Str | name3:Str | child4:Str | name4:Str |
|---|---|---|---|---|---|---|---|
| 1 | A |  |  |  |  |  |  |
| 1-10 | G | 1-3 | D | 1 | A |  |  |
| 1-10 | G | 1-3 | D | 2 | B |  |  |
| 1-10 | G | 1-3 | D | 3 | C |  |  |
| 1-10 | G | 3-5 | E |  |  |  |  |
| 1-10 | G | 6-10 | F |  |  |  |  |
| 1-100 | root | 1-10 | G | 1-3 | D | 1 | A |
| 1-100 | root | 1-10 | G | 1-3 | D | 2 | B |
| 1-100 | root | 1-10 | G | 1-3 | D | 3 | C |
| 1-100 | root | 1-10 | G | 3-5 | E |  |  |
| 1-100 | root | 1-10 | G | 6-10 | F |  |  |
| 1-3 | D | 1 | A |  |  |  |  |
| 1-3 | D | 2 | B |  |  |  |  |
| 1-3 | D | 3 | C |  |  |  |  |
| 2 | B |  |  |  |  |  |  |
| 200-210 | z | 201 | w |  |  |  |  |
| 200-210 | z | 202 | x |  |  |  |  |
| 200-210 | z | 203 | y |  |  |  |  |
| 200-300 | root | 200-210 | z | 201 | w |  |  |
| 200-300 | root | 200-210 | z | 202 | x |  |  |
| 200-300 | root | 200-210 | z | 203 | y |  |  |
| 201 | w |  |  |  |  |  |  |
| 202 | x |  |  |  |  |  |  |
| 203 | y |  |  |  |  |  |  |
| 3 | C |  |  |  |  |  |  |
| 3-5 | E |  |  |  |  |  |  |
| 6-10 | F |  |  |  |  |  |  |

# constraint

{
  "constants": [
    "root"
  ],
  "aggregation_functions": []
}

# output:output

| child1:Str | name1:Str | child2:Str | name2:Str | child3:Str | name3:Str | child4:Str | name4:Str |
|---|---|---|---|---|---|---|---|
| 1-100 | root | 1-10 | G | 1-3 | D | 1 | A |
| 1-100 | root | 1-10 | G | 1-3 | D | 2 | B |
| 1-100 | root | 1-10 | G | 1-3 | D | 3 | C |
| 1-100 | root | 1-10 | G | 3-5 | E |  |  |
| 1-100 | root | 1-10 | G | 6-10 | F |  |  |
| 200-300 | root | 200-210 | z | 201 | w |  |  |
| 200-300 | root | 200-210 | z | 202 | x |  |  |
| 200-300 | root | 200-210 | z | 203 | y |  |  |

# solution

```sql
SELECT *
FROM input1
WHERE name1 = 'root'
```
