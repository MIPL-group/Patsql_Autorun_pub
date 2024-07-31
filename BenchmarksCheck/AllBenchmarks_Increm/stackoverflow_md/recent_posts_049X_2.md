# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 049X

# input:input0

| id:Str | type:Str | sum:Str |
|---|---|---|
| 1 | a | 100 |
| 2 | a | 200 |
| 3 | b | 500 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| t_sum:Str | type:Str | history:Str |
|---|---|---|
| 300 | a | ['id' => 1, 'sum' => 100], ['id' => 2, 'sum' => 200] |
| 500 | b | ['id' => 3, 'sum' => 500] |

# solution

```sql
SELECT sum(sum) AS t_sum,
       type,
       array_to_json(
          array_agg(
             json_build_object('id', id, 'sum', sum)
          )
       ) history
FROM history
GROUP BY type
ORDER BY type;
```
