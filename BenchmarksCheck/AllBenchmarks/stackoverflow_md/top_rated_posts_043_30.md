# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 043

# input:input0

| CustomerName:Str | EmailAddress:Str |
|---|---|
| Aaron | aaron@gmail.com |
| Christy | aaron@gmail.com |
| Jason | jason@gmail.com |
| Eric | eric@gmail.com |
| EEric | eric@gmail.com |
| John | aaron@gmail.com |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| CustomerName:Str | EmailAddress:Str |
|---|---|
| Aaron | aaron@gmail.com |
| Christy | aaron@gmail.com |
| John | aaron@gmail.com |
| Eric | eric@gmail.com |
| EEric | eric@gmail.com |

# solution

```sql
SELECT
    T0.CustomerName,
    T1.EmailAddress 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            EmailAddress,
            count(CustomerName) AS count_CustomerName 
        FROM
            input1 
        GROUP BY
            EmailAddress
    ) AS T1 
        ON T1.EmailAddress = T0.EmailAddress 
WHERE
    T1.count_CustomerName > 1 
ORDER BY
    T1.EmailAddress ASC
```
