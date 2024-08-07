# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 063A

# input:input0

| id:Str | column1:Str | column2:Str |
|---|---|---|
| 11 | 31 | 3 |
| 12 | 32 | 3 |
| 14 | 34 | 3 |
| 16 | 36 | 3 |
| 18 | 22 | 4 |
| 13 | 33 | 4 |
| 15 | 35 | 4 |
| 17 | 36 | 5 |

# constraint

{
  "constants": [
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | column1:Str | column2:Str |
|---|---|---|
| 11 | 31 | 3 |
| 12 | 32 | 3 |
| 13 | 33 | 4 |
| 15 | 35 | 4 |
| 17 | 36 | 5 |

# solution

```sql
select id, column1, column2
from (
  select id, column1, column2, 
         row_number() over (partition by column2 order by id) as rn
  from demo_table
) t 
where rn <= 2
```
