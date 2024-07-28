# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 019

# input:input0

| CustomerID:Str | Balance:Str | Date:Str |
|---|---|---|
| 1 | 100.00 | 09/07/2016 |
| 1 | -50.00 | 09/08/2016 |
| 1 | -60.00 | 09/09/2016 |
| 1 | 500.00 | 09/10/2016 |
| 1 | 600.00 | 09/11/2016 |
| 1 | -100.00 | 09/12/2016 |
| 1 | -200.00 | 09/13/2016 |
| 1 | -400.00 | 09/14/2016 |
| 1 | -500.00 | 09/15/2016 |

# constraint

{
  "constants": [
    "0:Dbl"
  ],
  "aggregation_functions": []
}

# output:output

| CustomerID:Str | Balance:Str | Date:Str |
|---|---|---|
| 1 | -100.00 | 09/12/2016 |
| 1 | -200.00 | 09/13/2016 |
| 1 | -400.00 | 09/14/2016 |
| 1 | -500.00 | 09/15/2016 |

# solution

```sql
select *
from tablename
where date > (select max(date) from tablename where balance > 0)
```
