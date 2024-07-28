# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 025

# input:input0

| Id:Str | Value:Str |
|---|---|
| 1 | a |
| 2 | b |
| 3 | c |
| 4 | d |
| 5 | e |
| 6 | f |

# constraint

{
  "constants": [
    "3",
    "5"
  ],
  "aggregation_functions": []
}

# output:output

| Id:Str | Value:Str |
|---|---|
| 3 | c |
| 4 | d |

# solution

```sql
SELECT
    T0.Id,
    T0.Value 
FROM
    (SELECT
        Id,
        Value,
        rank() OVER (ORDER BY Id ASC) AS rank_over_order_by_id_asc 
    FROM
        input1) AS T0 
WHERE
    T0.rank_over_order_by_id_asc >= 3 
    AND T0.rank_over_order_by_id_asc < 5 
ORDER BY
    T0.Id ASC
```
