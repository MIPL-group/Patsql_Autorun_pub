# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 021

# input:input0

| Customer:Str | email:Str | ZIP:Str | shop:Str |
|---|---|---|---|
| John Smith | js@mail.com | 75016 | 1 |
| Mary King | mary@ymail.com | 97430 | 2 |
| John Smith | js@mail.com | 75016 | 3 |
| Ivan Turtle | ivan@mail.com | 56266 | 5 |
| Ivan T | iT@mail.com | 56266 | 5 |
| Mary King | mary@ymail.com | 97430 | 5 |
| John Smith | js@mail.com | 75016 | 5 |
| John Smith | js@ymail.com | 75016 | 5 |
| John Smith | js@example.com | 75016 | 5 |
| Ivan Smith | is@ymail.com | 12345 | 6 |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| Customer:Str | email:Str | ZIP:Str | shop:Str |
|---|---|---|---|
| John Smith | js@mail.com | 75016 | 1 |
| Mary King | mary@ymail.com | 97430 | 2 |
| John Smith | js@mail.com | 75016 | 3 |
| Mary King | mary@ymail.com | 97430 | 5 |
| John Smith | js@mail.com | 75016 | 5 |

# solution

```sql
SELECT a.*
FROM Customers a
INNER JOIN 
(SELECT email
FROM Customers
GROUP BY email
HAVING COUNT(shop) > 1) b
ON a.email = b.email
```
