# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 031

# input:input0

| id:Str | name:Str | name_ascii:Str |
|---|---|---|
| 5 | Alpha | 100 |
| 7 | Beta | 101 |
| 3 | Delta | 102 |
| 1 | Zed | 103 |

# constraint

{
  "constants": [
    "Beta"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | position:Str | name:Str |
|---|---|---|
| 7 | 2 | Beta |

# solution

```sql
SELECT
    T0.id,
    T0.rank_over_order_by_name_asc,
    T0.name 
FROM
    (SELECT
        id,
        name,
        rank() OVER (ORDER BY name ASC) AS rank_over_order_by_name_asc 
    FROM
        input1) AS T0 
WHERE
    T0.name = 'Beta'
```
