# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 039A

# input:input0

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 9 | 51 | 21 |
| 9 | 75 | 45 |
| 9 | 74 | 34 |
| 10 | 75 | 4 |
| 10 | 72 | 63 |
| 10 | 85 | 22 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str |
|---|---|
| 3 | 100 |
| 3 | 89 |
| 6 | 189 |

# solution

```sql
select zoom, point, size
FROM (
  SELECT zoom::text as zoom,
         zoom as zoom_value,
         count(*) AS point,
         SUM(size) AS size, 
         1 as sort_order
  FROM total
  GROUP BY zoom
  UNION ALL
  SELECT 'Total', 
         null,
         count(*) AS point,
         SUM(size) AS size, 
         2 as sort_order
  FROM total
) t
order by sort_order, zoom_value;
```
