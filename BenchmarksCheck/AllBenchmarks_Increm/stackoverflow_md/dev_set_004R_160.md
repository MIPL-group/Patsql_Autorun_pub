# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 004R

# input:input0

| Id:Str | Name:Str | Other_Columns:Str |
|---|---|---|
| 1 | A | A_data_1 |
| 2 | A | A_data_2 |
| 3 | A | A_data_3 |
| 4 | B | B_data_1 |
| 5 | B | B_data_2 |
| 6 | C | C_data_1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| col1:Str | col2:Str | col3:Str |
|---|---|---|
| 3 | A | A_data_3 |
| 5 | B | B_data_2 |
| 6 | C | C_data_1 |

# solution

```sql
SELECT m1.*
FROM messages m1 LEFT JOIN messages m2
 ON (m1.name = m2.name AND m1.id < m2.id)
WHERE m2.id IS NULL;
```
