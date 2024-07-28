# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 033

# input:input0

| CustomerID:Str | DBColumnName:Str | Data:Str |
|---|---|---|
| 1 | FirstName | Joe |
| 1 | MiddleName | S |
| 1 | LastName | Smith |
| 1 | Date | 12/12/2009 |
| 2 | FirstName | Sam |
| 2 | MiddleName | S |
| 2 | LastName | Freddrick |
| 2 | Date | 1/12/2009 |
| 3 | FirstName | Jaime |
| 3 | MiddleName | S |
| 3 | LastName | Carol |
| 3 | Date | 12/1/2009 |

# constraint

{
  "constants": [
    "FirstName",
    "MiddleName",
    "LastName",
    "Date"
  ],
  "aggregation_functions": []
}

# output:output

| CustomerID:Str | FirstName:Str | MiddleName:Str | LastName:Str | Date:Str |
|---|---|---|---|---|
| 1 | Joe | S | Smith | 12/12/2009 |
| 2 | Sam | S | Freddrick | 1/12/2009 |
| 3 | Jaime | S | Carol | 12/1/2009 |

# solution

```sql
SELECT
main.CustomerID,
f.Data AS FirstName,
m.Data AS MiddleName,
l.Data AS LastName,
d.Data AS Date
FROM table main
INNER JOIN table f on f.CustomerID = main.CustomerID
INNER JOIN table m on m.CustomerID = main.CustomerID
INNER JOIN table l on l.CustomerID = main.CustomerID
INNER JOIN table d on d.CustomerID = main.CustomerID
WHERE f.DBColumnName = 'FirstName' 
AND m.DBColumnName = 'MiddleName' 
AND l.DBColumnName = 'LastName' 
AND d.DBColumnName = 'Date'
```
