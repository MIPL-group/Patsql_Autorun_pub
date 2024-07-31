# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 036

# input:input0

| username:Str | date:Str | value:Str |
|---|---|---|
| brad | 2010-05-10 | 1.8 |
| fred | 2012-03-04 | 1.0 |
| bob | 2012-03-04 | 1.5 |
| brad | 2013-02-02 | 1.2 |
| fred | 2014-11-01 | 1.3 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| username:Str | date:Str | value:Str |
|---|---|---|
| bob | 2012-03-04 | 1.5 |
| brad | 2013-02-02 | 1.2 |
| fred | 2014-11-01 | 1.3 |

# solution

```sql
SELECT
    T1.username,
    T0.date,
    T0.value 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            username,
            max(date) AS max_date 
        FROM
            input1 
        GROUP BY
            username
    ) AS T1 
        ON T1.username = T0.username 
        AND T1.max_date = T0.date 
ORDER BY
    T1.username ASC
```
