# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 042

# input:input0

| id:Str | name:Str | school:Str |
|---|---|---|
| 1 | Joe | ODU |
| 3 | Ane | ODU |
| 4 | Trevor | VT |
| 5 | Cools | VCU |
| 2 | Mike | VCU |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | name:Str | school:Str |
|---|---|---|
| 1 | Joe | ODU |
| 3 | Ane | ODU |
| 2 | Mike | VCU |
| 5 | Cools | VCU |
| 4 | Trevor | VT |

# solution

```sql
SELECT id, name
FROM dbo.NerdsTable
ORDER BY school ASC, id ASC
```
