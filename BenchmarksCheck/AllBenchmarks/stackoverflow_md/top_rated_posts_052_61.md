# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 052

# input:input0

| rowInt:Str | Value:Str |
|---|---|
| 2 | 23 |
| 3 | 45 |
| 17 | 10 |
| 9 | 0 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| rowInt:Str | Value:Str | Diff:Str |
|---|---|---|
| 2 | 23 | 22 |
| 3 | 45 | -45 |
| 9 | 0 | 10 |
| 17 | 10 | -10 |

# solution

```sql
SELECT
   [current].rowInt,
   [current].Value,
   ISNULL([next].Value, 0) - [current].Value
FROM
   sourceTable       AS [current]
LEFT JOIN
   sourceTable       AS [next]
      ON [next].rowInt = (SELECT MIN(rowInt) FROM sourceTable WHERE rowInt > [current].rowInt)
```
