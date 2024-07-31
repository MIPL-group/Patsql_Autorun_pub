# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 040

# input:call

| id:Str | date:Str | phone_number:Str |
|---|---|---|
| 1 | 0945 | 111111111111 |
| 2 | 0950 | 222222222222 |
| 3 | 1045 | 333333333333 |
| 4 | 1055 | 444444444444 |

# input:phone_book

| id:Str | name:Str | phone_number:Str |
|---|---|---|
| 2 | John | 111111111111 |
| 3 | Jane | 222222222222 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | date:Str | phone_number:Str |
|---|---|---|
| 3 | 1045 | 333333333333 |
| 4 | 1055 | 444444444444 |

# solution

```sql
SELECT * 
FROM   Call
LEFT OUTER JOIN Phone_Book
  ON (Call.phone_number = Phone_book.phone_number)
  WHERE Phone_book.phone_number IS NULL
```
