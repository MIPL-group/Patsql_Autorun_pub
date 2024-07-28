# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 032M

# input:input0

| Id:Str | crit1:Str | crit2:Str | value:Str |
|---|---|---|---|
| 1 | 11 | 2 | a |
| 2 | 21 | 2 | b |
| 3 | 11 | 3 | c |
| 4 | 11 | 1 | d |
| 5 | 21 | 2 | e |
| 6 | 11 | 2 | f |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| crit1:Str | crit2:Str | value:Str |
|---|---|---|
| 11 | 1 | d |
| 11 | 2 | f |
| 11 | 3 | c |
| 21 | 2 | e |

# solution

```sql
SELECT
    crit1,
    crit2,
    max(value) 
FROM
    input1 
GROUP BY
    crit1,
    crit2 
ORDER BY
    crit1 ASC,
    crit2 ASC
```
