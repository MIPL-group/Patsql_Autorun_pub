# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 004A

# input:input0

| id:Str | call_ref:Str | job_num:Str |
|---|---|---|
| 1 | 123445 | 2389 |
| 2 | 342537 | 0 |
| 3 | 876483 | 2389 |
| 4 | 644686 | 5643 |
| 5 | 654532 | 0 |

# constraint

{
  "constants": [
    "0"
  ],
  "aggregation_functions": []
}

# output:output

| call_ref:Str | job_num:Str |
|---|---|
| 342537 | 0 |
| 876483 | 2389 |
| 644686 | 5643 |
| 654532 | 0 |

# solution

```sql
SELECT max(call_ref), job_num
FROM input1
WHERE job_num <> 0
GROUP BY job_num
UNION ALL
SELECT call_ref, job_num
FROM input1
WHERE job_num = 0
```
