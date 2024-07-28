# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 030

# input:input0

| Person:Str | Grp:Str | Age:Str |
|---|---|---|
| Bob | 1 | 32 |
| Jill | 1 | 34 |
| Shawn | 1 | 42 |
| XSWwe | 1 | 30 |
| Jake | 2 | 29 |
| Paul | 2 | 36 |
| Laura | 2 | 39 |
| YYYY | 2 | 31 |
| XXXX | 2 | 20 |

# constraint

{
  "constants": [
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| Person:Str | Grp:Str | Age:Str |
|---|---|---|
| Shawn | 1 | 42 |
| Jill | 1 | 34 |
| Laura | 2 | 39 |
| Paul | 2 | 36 |

# solution

```sql
SELECT
    T0.Person,
    T0.Grp,
    T0.Age 
FROM
    (SELECT
        Person,
        Grp,
        Age,
        rank() OVER (PARTITION BY Grp ORDER BY Age DESC) AS rank_over_part_by_grp_order_by_age_desc 
    FROM
        input1) AS T0 
WHERE
    T0.rank_over_part_by_grp_order_by_age_desc <= 2 
ORDER BY
    T0.Grp ASC,
    T0.Age DESC
```
