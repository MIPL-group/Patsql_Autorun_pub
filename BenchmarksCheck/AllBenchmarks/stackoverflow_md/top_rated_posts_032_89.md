# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 032

# input:input0

| Section:Str | Status:Str | Count:Str |
|---|---|---|
| A | Active | 1 |
| A | Inactive | 2 |
| B | Active | 4 |
| B | Inactive | 5 |
| C | Active | 9 |
| C | Inactive | 1 |

# constraint

{
  "constants": [
    "Active",
    "Inactive"
  ],
  "aggregation_functions": []
}

# output:output

| Section:Str | Active:Str | Inactive:Str |
|---|---|---|
| A | 1 | 2 |
| B | 4 | 5 |
| C | 9 | 1 |

# solution

```sql
SELECT
    T0.Section,
    T0.Count,
    T1.Count 
FROM
    input1 AS T0 
JOIN
    input1 AS T1 
        ON T0.Section = T1.Section 
WHERE
    T0.Status = 'Active' 
    AND T1.Status = 'Inactive' 
ORDER BY
    T0.Section ASC
```
