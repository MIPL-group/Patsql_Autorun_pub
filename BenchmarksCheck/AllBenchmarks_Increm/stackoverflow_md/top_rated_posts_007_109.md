# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 007

# input:input0

| id:Str | home:Str | datetime:Str | player:Str | resource:Str |
|---|---|---|---|---|
| 1 | 10 | 03/04/2009 | john | 199 |
| 2 | 11 | 03/04/2009 | juliet | 244 |
| 5 | 12 | 03/04/2009 | borat | 555 |
| 3 | 10 | 03/03/2009 | john | 300 |
| 4 | 11 | 03/03/2009 | juliet | 200 |
| 6 | 12 | 03/03/2009 | borat | 500 |
| 7 | 13 | 01/01/2008 | borat | 600 |
| 8 | 13 | 01/01/2009 | borat | 700 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | home:Str | datetime:Str | player:Str | resource:Str |
|---|---|---|---|---|
| 1 | 10 | 03/04/2009 | john | 199 |
| 2 | 11 | 03/04/2009 | juliet | 244 |
| 5 | 12 | 03/04/2009 | borat | 555 |
| 8 | 13 | 01/01/2009 | borat | 700 |

# solution

```sql
SELECT
    T0.id,
    T1.home,
    T0.datetime,
    T0.player,
    T0.resource 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            home,
            max(datetime) AS max_datetime 
        FROM
            input1 
        GROUP BY
            home
    ) AS T1 
        ON T1.home = T0.home 
        AND T1.max_datetime = T0.datetime 
ORDER BY
    T0.id ASC
```
