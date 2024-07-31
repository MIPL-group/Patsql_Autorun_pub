# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 053AM

# input:input0

| NAME:Str | SCORE:Str |
|---|---|
| willy | 11 |
| willy | 12 |
| willy | 13 |
| zoe | 14 |
| zoe | 15 |
| zoe | 16 |
| d | 11 |

# constraint

{
  "constants": [
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| NAME:Str | SCORE:Str |
|---|---|
| willy | 12 |
| willy | 13 |
| zoe | 15 |
| zoe | 16 |
| d | 11 |

# solution

```sql
SELECT
    T0.NAME,
    T0.SCORE 
FROM
    (SELECT
        NAME,
        SCORE,
        rank() OVER (PARTITION BY NAME ORDER BY SCORE DESC) AS rank_over_part_by_name_order_by_score_desc 
    FROM
        input1) AS T0 
WHERE
    T0.rank_over_part_by_name_order_by_score_desc <= 2
```
