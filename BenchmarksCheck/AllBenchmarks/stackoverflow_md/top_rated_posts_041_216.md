# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 041

# input:input0

| col1:Str | col2:Str | col3:Str |
|---|---|---|
| 1 | a | 5 |
| 5 | d | 3 |
| 3 | k | 2 |
| 2 | x | 8 |
| 8 | y | 7 |
| 6 | o | 10 |
| 10 | 0 | 0 |
| 0 | x | 12 |
| 12 | s | 11 |
| 11 | t | 17 |

# constraint

{
  "constants": [
    "1:Str"
  ],
  "aggregation_functions": []
}

# output:output

| col1:Str | col2:Str | col3:Str |
|---|---|---|
| 1 | a | 5 |
| 5 | d | 3 |
| 3 | k | 2 |
| 2 | x | 8 |
| 8 | y | 7 |

# solution

```sql
WITH RECURSIVE tbl AS (
  SELECT * FROM t WHERE col1 = 1
  UNION ALL
  SELECT t.* FROM t, tbl WHERE t.col1 = tbl.col3
)
SELECT * FROM tbl;
```
