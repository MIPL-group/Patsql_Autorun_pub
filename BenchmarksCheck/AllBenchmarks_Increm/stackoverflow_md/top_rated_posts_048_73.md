# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 048

# input:input0

| CName:Str | AddressID:Str | AddressLine:Str |
|---|---|---|
| John Smith | 123 | Nowheresville |
| Jane Doe | 456 | Evergreen Terrace |
| John Smith | 999 | Somewhereelse |
| Joe Bloggs | 120 | XXX |
| Joe Bloggs | 123 | Second Ave |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| CName:Str | AddressID:Str | AddressLine:Str |
|---|---|---|
| John Smith | 123 | Nowheresville |
| Jane Doe | 456 | Evergreen Terrace |
| Joe Bloggs | 120 | XXX |

# solution

```sql
SELECT
    T1.CName,
    T0.AddressID,
    T0.AddressLine 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            CName,
            min(AddressID) AS min_AddressID 
        FROM
            input1 
        GROUP BY
            CName
    ) AS T1 
        ON T1.CName = T0.CName 
        AND T1.min_AddressID = T0.AddressID
```
