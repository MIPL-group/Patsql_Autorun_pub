# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 003MR

# input:input0

| id:Str | customer:Str | total:Str |
|---|---|---|
| 1 | Joe | 5 |
| 2 | Joe | 6 |
| 3 | Joe | 6 |
| 4 | Joe | 6 |
| 5 | Sally | 3 |
| 6 | Joe | 2 |
| 7 | Sally | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| FIRST(id):Str | customer:Str | FIRST(total):Str |
|---|---|---|
| 2 | Joe | 6 |
| 5 | Sally | 3 |

# solution

```sql
SELECT MIN(x.id),
         x.customer, 
         x.total
    FROM PURCHASES x
    JOIN (SELECT p.customer,
                 MAX(total) AS max_total
            FROM PURCHASES p
        GROUP BY p.customer) y ON y.customer = x.customer
                              AND y.max_total = x.total
GROUP BY x.customer, x.total
```
