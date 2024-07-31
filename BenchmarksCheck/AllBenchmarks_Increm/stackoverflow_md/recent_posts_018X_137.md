# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 018X

# input:tab

| OrderID:Str | CustomerID:Str | Date:Str | Course:Str |
|---|---|---|---|
| 14954 | 13440 | 10/16/2016 | Zürich |
| 14955 | 13441 | 10/17/2016 | Bern |
| 14956 | 13441 | 10/17/2016 | Aargau |
| 14957 | 13442 | 10/17/2016 | Bern |
| 14958 | 10483 | 10/17/2016 | Zürich |
| 14959 | 13442 | 10/18/2016 | Solothurn |

# constraint

{
  "constants": [
    "10/17/2016"
  ],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str |
|---|---|
| Bern | 2 |
| Aargau | 0 |
| Zürich | 1 |

# solution

```sql
SELECT t1.Course, count(t2.min_order_id)
FROM tab AS t1
LEFT JOIN (SELECT min(OrderID) AS min_order_id FROM tab WHERE Date = DATE '2016-10-17' GROUP BY CustomerId) AS t2
  ON t1.OrderID = t2.min_order_id
WHERE t1.Date = DATE '2016-10-17'
GROUP BY Course
```
