# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 044M

# input:input2

| Part:Str | OriginalID:Str |
|---|---|
| partA | 2 |
| partB | 3 |

# input:input1

| Area:Str | Part:Str |
|---|---|
| Abdomen | partA |
| Bottom | partB |

# input:input0

| OriginalID:Str | Area:Str |
|---|---|
| 2 | Abdomen |
| 3 | Abdomen |
| 2 | Bottom |
| 3 | Bottom |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| OriginalID:Str | Area:Str |
|---|---|
| 3 | Abdomen |
| 2 | Bottom |

# solution

```sql
SELECT a.originalID, b.part 
from #1 a
join #2 b
on a.area = b.area
where not exists (select * from #3 c where c.originalID = a.originalID and c.part = b.part)
```
