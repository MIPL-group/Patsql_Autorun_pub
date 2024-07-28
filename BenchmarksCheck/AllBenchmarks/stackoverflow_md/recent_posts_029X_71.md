# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 029X

# input:table1

| Pre:Str | Ba:Str | pre-Ba:Str | kgs:Str | fl:Str |
|---|---|---|---|---|
| 6L34 | 1523726 | 6L34-1523726 | 0.01 | Bm1 |
| 6L34 | 1523726 | 6L34-1523726 | 0.04 | Bm1 |
| 6L34 | 1523726 | 6L34-1523726 | 0.06 | Bm1 |
| BM51 | 13K732 | BM51-13K732 | 0 | Bm1 |
| BM51 | 13K732 | BM51-13K732 | 8 | Bm1 |

# input:table2

| Pre:Str | Ba:Str | pre-Ba:Str | kgs:Str | fl:Str |
|---|---|---|---|---|
| 6L34 | 1523726 | 6L34-1523726 | 0.01 | Bm2 |
| BM51 | 13K732 | BM51-13K732 | 0.02 | Bm2 |
| BM51 | 13K732 | BM51-13K732 | 8 | Bm2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Pre:Str | Ba:Str | pre-Ba:Str | kgs:Str | fl:Str |
|---|---|---|---|---|
| 6L34 | 1523726 | 6L34-1523726 | 0.01 | Bm1&Bm2 |
| 6L34 | 1523726 | 6L34-1523726 | 0.04 | Bm1 |
| 6L34 | 1523726 | 6L34-1523726 | 0.06 | Bm1 |
| BM51 | 13K732 | BM51-13K732 | 0 | Bm1 |
| BM51 | 13K732 | BM51-13K732 | 0.02 | Bm2 |
| BM51 | 13K732 | BM51-13K732 | 8 | Bm1&Bm2 |

# solution

```sql
// the expected output and the answer on the stack overflow post are incorrect
```
