# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 058M

# input:input0

| app_name:Str | app_platform:Str | post_created:Str | post_id:Str |
|---|---|---|---|
| Photoshop | Windows | 10/20/2009 | 1 |
| Photoshop | Windows | 12/01/2009 | 3 |
| Photoshop | Macintosh | 11/10/2009 | 2 |
| Photoshop | Linux | 11/10/2009 | 4 |
| Photoshop | Windows | 11/10/2009 | 5 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| app_name:Str | app_platform:Str | post_created:Str | post_id:Str |
|---|---|---|---|
| Photoshop | Windows | 12/01/2009 | 3 |
| Photoshop | Macintosh | 11/10/2009 | 2 |
| Photoshop | Linux | 11/10/2009 | 4 |

# solution

```sql
SELECT
  t1.app_name,t1.app_platform,t1.post_created,t1.post_id
FROM
  (SELECT app_platform, MAX(post_created) As MaxPostCreated
   FROM T
   GROUP BY app_platform) AS t2 JOIN 
  T AS t1
WHERE
  t1.app_platform = t2.app_platform1
   AND t2.MaxPostCreated = t1.post_created
```
