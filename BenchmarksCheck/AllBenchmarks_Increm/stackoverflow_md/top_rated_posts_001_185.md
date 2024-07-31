# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 001

# input:input0

| SubjectID:Str | StudentName:Str |
|---|---|
| 1 | Mary |
| 1 | John |
| 1 | Sam |
| 2 | Alaina |
| 2 | Edward |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| SubjectID:Str | StudentName:Str |
|---|---|
| 1 | Mary, John, Sam |
| 2 | Alaina, Edward |

# solution

```sql
SELECT
    SubjectID,
    string_agg(StudentName, ', ') 
FROM
    input1 
GROUP BY
    SubjectID 
ORDER BY
    SubjectID ASC
```
