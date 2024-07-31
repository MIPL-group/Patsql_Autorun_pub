# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 035X

# input:percentage

| zoom:Str | x:Str | y:Str |
|---|---|---|
| 0 | 5 | 20 |
| 0 | 5 | 21 |
| 0 | 5 | 21 |
| 0 | 5 | 22 |
| 0 | 5 | 22 |
| 0 | 5 | 22 |
| 0 | 5 | 23 |
| 0 | 5 | 23 |
| 0 | 5 | 23 |
| 0 | 5 | 23 |
| 0 | 5 | 24 |
| 0 | 5 | 24 |
| 0 | 5 | 24 |
| 0 | 5 | 24 |
| 0 | 5 | 24 |
| 1 | 5 | 20 |
| 1 | 5 | 21 |
| 1 | 5 | 21 |
| 1 | 5 | 22 |
| 1 | 5 | 22 |
| 1 | 5 | 22 |
| 1 | 5 | 23 |
| 1 | 5 | 23 |
| 1 | 5 | 23 |
| 1 | 5 | 23 |
| 1 | 5 | 24 |
| 1 | 5 | 24 |
| 1 | 5 | 24 |
| 1 | 5 | 24 |
| 1 | 5 | 24 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| zoom:Str | x:Str | y:Str | amount:Str | percentage:Str |
|---|---|---|---|---|
| 0 | 5 | 20 | 1 | 6.667 |
| 0 | 5 | 21 | 2 | 13.333 |
| 0 | 5 | 22 | 3 | 20 |
| 0 | 5 | 23 | 4 | 26.667 |
| 0 | 5 | 24 | 5 | 33.333 |
| 1 | 5 | 20 | 1 | 6.667 |
| 1 | 5 | 21 | 2 | 13.333 |
| 1 | 5 | 22 | 3 | 20 |
| 1 | 5 | 23 | 4 | 26.667 |
| 1 | 5 | 24 | 5 | 33.333 |

# solution

```sql
SELECT zoom,x,y,
       amount,
       ( amount / Cast(Sum(amount) OVER(partition BY zoom) AS FLOAT) ) * 100 as amt_percentage
FROM   (SELECT zoom,x, y,
               Count(*) AS amount
        FROM   percentage
        GROUP  BY zoom,x,y) a
```