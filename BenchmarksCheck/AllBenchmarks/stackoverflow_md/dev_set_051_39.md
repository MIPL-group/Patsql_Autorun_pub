# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 051

# input:input0

| ID:Str | P_Id:Str | room:Str |
|---|---|---|
| 1 | 8 | A |
| 2 | 8 | A |
| 3 | 8 | B |
| 4 | 9 | B |
| 5 | 9 | B |
| 6 | 10 | C |
| 7 | 10 | C |
| 8 | 10 | D |
| 9 | 7 | B |
| 11 | 10 | B |

# constraint

{
  "constants": [
    "B"
  ],
  "aggregation_functions": []
}

# output:output

| P_Id:Str |
|---|
| 7 |
| 9 |

# solution

```sql
SELECT
    P_Id 
FROM
    input1 
GROUP BY
    P_Id 
HAVING
    max(room) = 'B' 
    AND min(room) = 'B' 
ORDER BY
    P_Id ASC
```
