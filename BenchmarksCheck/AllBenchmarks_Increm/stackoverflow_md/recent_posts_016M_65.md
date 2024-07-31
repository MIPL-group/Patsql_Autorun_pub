# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 016M

# input:Customer

| CustomerId:Str |
|---|
| C1 |
| C2 |
| C3 |
| C4 |

# input:ReportPull

| CustomerId:Str | ReportDt:Str |
|---|---|
| C1 | 10/19/2016 |
| C1 | 10/01/2016 |
| C1 | 09/17/2016 |
| C2 | 10/18/2016 |
| C2 | 09/01/2016 |
| C3 | 10/19/2016 |
| C4 | 10/19/2016 |
| C4 | 10/18/2016 |

# constraint

{
  "constants": [
    "10/19/2016",
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| CustomerId:Str | LastReportPullDt:Str | ReportCount:Str |
|---|---|---|
| C1 | 10/19/2016 | 3 |
| C4 | 10/19/2016 | 2 |

# solution

```sql
SELECT C.Id,
       MAX(RP.PullDt) as LastReportPullDt, 
       COUNT(*) AS ReportCount
FROM Customer C
INNER JOIN ReportPull RP ON C.CustomerId = RP.CustomerId
GROUP BY C.CustomerId
HAVING COUNT(*) > 1
AND MAX(RP.PullDt) >= "10/19/2016"
```
