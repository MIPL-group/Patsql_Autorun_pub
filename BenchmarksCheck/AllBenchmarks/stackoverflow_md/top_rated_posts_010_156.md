# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 010

# input:input1

| id:Str | date:Str | phone_number:Str |
|---|---|---|
| 1a | 09-45 | "111111111111 |
| 2a | 09-50 | "222222222222 |
| 3a | 10-45 | "333333333333 |

# input:input0

| id:Str | name:Str | phone_number:Str |
|---|---|---|
| 1a | John | "111111111111 |
| 2a | Jane | "222222222222 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | date:Str | phone_number:Str |
|---|---|---|
| 3a | 10-45 | "333333333333 |

# solution

```sql
SELECT
    T0.id,
    T0.date,
    T0.phone_number 
FROM
    input2 AS T0 
LEFT JOIN
    input1 AS T1 
        ON T0.id = T1.id 
WHERE
    T1.id IS NULL
```
