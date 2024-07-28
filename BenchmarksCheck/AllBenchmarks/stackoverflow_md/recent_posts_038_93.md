# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 038

# input:input1

| Date:Str | Tapped:Str |
|---|---|
| 10.08 | 23 |
| 10.09 | 31 |
| 10.10 | 0 |
| 10.11 | 54 |

# input:input0

| Date:Str | Sold:Str |
|---|---|
| 10.08 | 22 |
| 10.09 | 31 |
| 10.11 | 54 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Date:Str | Tapped:Str | Sold:Str |
|---|---|---|
| 10.08 | 23 | 22 |
| 10.09 | 31 | 31 |
| 10.10 | 0 | NULL |
| 10.11 | 54 | 54 |

# solution

```sql
SELECT t2.Date,t2.Tapped,t1.sold sold,t2.Tapped
FROM Table1 t1 
 RIGHT JOIN Table2  t2 
   ON t1.Date=t2.Date
```
