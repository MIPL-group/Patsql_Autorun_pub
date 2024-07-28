# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 006

# input:input0

| Id:Str | Name:Str | Other_Columns:Str |
|---|---|---|
| 1 | A | A_data_1 |
| 2 | A | A_data_3 |
| 3 | A | A_data_2 |
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
| 3 | A | A_data_2 |
| 5 | B | B_data_2 |
| 6 | C | C_data_1 |

# solution

```sql
SELECT
    T1.max_Id,
    T1.Name,
    T0.Other_Columns 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            Name,
            max(Id) AS max_Id 
        FROM
            input1 
        GROUP BY
            Name
    ) AS T1 
        ON T1.max_Id = T0.Id 
ORDER BY
    T1.Name ASC
```
