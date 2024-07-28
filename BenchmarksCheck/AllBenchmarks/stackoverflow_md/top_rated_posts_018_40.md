# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 018

# input:input0

| id:Str | section_id:Str | name:Str |
|---|---|---|
| 1 | 1 | A |
| 2 | 1 | B |
| 3 | 1 | C |
| 4 | 1 | D |
| 5 | 2 | E |
| 6 | 2 | F |
| 7 | 3 | G |
| 8 | 2 | H |

# constraint

{
  "constants": [
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | section_id:Str | name:Str |
|---|---|---|
| 1 | 1 | A |
| 2 | 1 | B |
| 5 | 2 | E |
| 6 | 2 | F |
| 7 | 3 | G |

# solution

```sql
SELECT
    T0.id,
    T0.section_id,
    T0.name 
FROM
    (SELECT
        id,
        section_id,
        name,
        rank() OVER (PARTITION BY section_id ORDER BY id ASC) AS rank_over_part_by_section_id_order_by_id_asc 
    FROM
        input1) AS T0 
WHERE
    T0.rank_over_part_by_section_id_order_by_id_asc <= 2 
ORDER BY
    T0.id ASC
```
