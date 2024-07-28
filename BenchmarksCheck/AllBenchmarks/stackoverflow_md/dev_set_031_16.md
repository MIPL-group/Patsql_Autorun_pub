# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 031

# input:input1

| id:Str | name:Str |
|---|---|
| 1 | john |
| 2 | joe |

# input:input0

| id:Str | amount:Str | id_waiter:Str |
|---|---|---|
| 1 | 20 | 1 |
| 2 | 25 | 2 |
| 3 | 50 | 2 |
| 4 | 50 | 1 |
| 5 | 60 | 1 |
| 6 | 10 | 2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| name:Str | waiter:Str | maxamount:Str | bill:Str |
|---|---|---|---|
| john | 1 | 60 | 5 |
| joe | 2 | 50 | 3 |

# solution

```sql
SELECT waiter.id AS waiter, maxamount, bills.id AS bill
FROM waiter
JOIN (
  SELECT id_waiter, max(amount) AS maxamount
  FROM bills
  GROUP BY id_waiter) AS maxis ON maxis.id_waiter = waiter.id
JOIN bills ON maxis.maxamount = bills.amount AND waiter.id =     bills.id_kellner
```
