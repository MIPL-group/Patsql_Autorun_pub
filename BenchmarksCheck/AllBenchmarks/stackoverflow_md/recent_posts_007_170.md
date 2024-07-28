# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 007

# input:d

| Employee:Str | FromDate:Str | ToDate:Str | Code:Str |
|---|---|---|---|
| Employee | 07/01/2016 | 07/31/2016 | 4 |
| Employee | 06/01/2016 | 06/30/2016 | 2 |
| Employee | 05/01/2016 | 05/31/2016 | 2 |
| Employee | 04/01/2016 | 04/30/2016 | 3 |
| Employee | 03/01/2016 | 03/31/2016 | 3 |
| Employee | 02/01/2016 | 02/29/2016 | 4 |
| Employee | 01/01/2016 | 01/31/2016 | 4 |
| emp | 01/01/2015 | 01/31/2016 | 2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Employee:Str | FromDate:Str | ToDate:Str | Code:Str |
|---|---|---|---|
| Employee | 05/01/2016 | 06/30/2016 | 2 |
| Employee | 03/01/2016 | 04/30/2016 | 3 |
| Employee | 01/01/2016 | 07/31/2016 | 4 |
| emp | 01/01/2015 | 01/31/2016 | 2 |

# solution

```sql
SELECT
    d.Employee,
    MIN(d.FromDate) AS FromDate,
    MAX(d.ToDate) AS ToDate,
    d.Code
FROM d
GROUP BY
    d.Code,
    d.Employee
ORDER BY
    MIN(d.FromDate) DESC
```
