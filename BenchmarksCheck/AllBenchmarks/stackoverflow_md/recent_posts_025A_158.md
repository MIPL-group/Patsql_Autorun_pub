# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 025A

# input:input0

| id:Str | gallery_id:Str | path:Str |
|---|---|---|
| 58 | NULL | 58.jpg |
| 59 | NULL | 59.jpg |
| 66 | 9 | 9-001.jpg |
| 67 | 9 | 9-002.jpg |
| 68 | 10 | 10-001.jpg |
| 69 | 10 | 10-002.jpg |
| 70 | 10 | 10-003.jpg |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | gallery_id:Str | path:Str |
|---|---|---|
| 58 | NULL | 58.jpg |
| 59 | NULL | 59.jpg |
| 66 | 9 | 9-001.jpg |
| 68 | 10 | 10-001.jpg |

# solution

```sql
select i.*
from images i
where i.gallery_id is null or
      i.id in (select min(i2.id) from images i2 group by i2.gallery_id);
```
