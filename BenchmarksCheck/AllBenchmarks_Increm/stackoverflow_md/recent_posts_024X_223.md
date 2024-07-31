# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 024X

# input:BALL

| Id:Str | Color:Str | Month:Str |
|---|---|---|
| 1 | blue | October |
| 2 | red | January |
| 3 | green | September |
| 4 | red | October |
| 5 | red | March |
| 6 | blue | March |
| 7 | red | March |
| 8 | red | March |

# constraint

{
  "constants": [
    "blue"
  ],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str |
|---|---|
| October | 0.5 |
| January | 0 |
| September | 0 |
| March | 0.25 |

# solution

```sql
-- MySQL
SELECT BALL.Month, avg(BALL.Color='Blue') 
FROM BALL    
GROUP BY BALL.Month;
```
