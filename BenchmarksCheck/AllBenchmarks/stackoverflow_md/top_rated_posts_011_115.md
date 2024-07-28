# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 011

# input:input1

| LocationID:Str | VehicleID:Str | City:Str |
|---|---|---|
| 1 | 1 | New York |
| 2 | 1 | Seattle |
| 3 | 1 | Vancouver |
| 4 | 2 | Los Angeles |
| 5 | 2 | Houston |

# input:input0

| VehicleID:Str | Name:Str |
|---|---|
| 1 | Chuck |
| 2 | Larry |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| VehicleID:Str | Name:Str | Locations:Str |
|---|---|---|
| 1 | Chuck | New York, Seattle, Vancouver |
| 2 | Larry | Los Angeles, Houston |

# solution

```sql
SELECT
    T0.VehicleID,
    max(T0.Name),
    string_agg(T1.City, ', ') 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.VehicleID = T1.VehicleID 
GROUP BY
    T0.VehicleID 
ORDER BY
    T0.VehicleID ASC
```
