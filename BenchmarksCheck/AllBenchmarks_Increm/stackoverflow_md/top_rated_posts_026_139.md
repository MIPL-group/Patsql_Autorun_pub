# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 026

# input:input0

| date:Str | category:Str | amount:Str |
|---|---|---|
| 1/1/2012 | ABC | 1000.00 |
| 2/1/2012 | DEF | 500.00 |
| 2/1/2012 | GHI | 800.00 |
| 2/10/2012 | DEF | 700.00 |
| 3/1/2012 | ABC | 1100.00 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| date:Str | ABC:Str | DEF:Str | GHI:Str |
|---|---|---|---|
| 1/1/2012 | 1000.00 | NULL | NULL |
| 2/1/2012 | NULL | 500.00 | NULL |
| 2/1/2012 | NULL | NULL | 800.00 |
| 2/10/2012 | NULL | 700.00 | NULL |
| 3/1/2012 | 1100.00 | NULL | NULL |

# solution

```sql
create table temp
(
    date datetime,
    category varchar(3),
    amount money
)
```
