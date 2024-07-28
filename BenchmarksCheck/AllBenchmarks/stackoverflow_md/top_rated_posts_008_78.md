# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 008

# input:input1

| LineItemGUID:Str | OrderID:Str | Quantity:Str | Description:Str |
|---|---|---|---|
| {098FBE3...} | 1 | 7 | prefabulated amulite |
| {1609B09...} | 2 | 32 | spurving bearing |
| {A58A1...} | 6784329 | 5 | pentametric fan |
| {0E9BC...} | 6784329 | 5 | differential girdlespring |

# input:input0

| OrderID:Str | OrderGUID:Str | OrderNumber:Str |
|---|---|---|
| 1 | {FFB2...} | STL-7442-1 |
| 2 | {3EC6...} | MPT-9931-8A |
| 6784329 | {A1...} | KSG-0619-81 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| OrderNumber:Str | Quantity:Str | Description:Str |
|---|---|---|
| STL-7442-1 | 7 | prefabulated amulite |
| MPT-9931-8A | 32 | spurving bearing |
| KSG-0619-81 | 5 | pentametric fan |

# solution

```sql
SELECT
    max(T0.OrderNumber),
    max(T1.Quantity),
    max(T1.Description) 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.OrderID = T1.OrderID 
GROUP BY
    T0.OrderID 
ORDER BY
    max(T0.OrderNumber) DESC
```
