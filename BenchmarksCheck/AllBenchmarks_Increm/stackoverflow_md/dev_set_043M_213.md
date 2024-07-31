# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 043M

# input:input0

| Id:Str | name:Str | type:Str | price:Str |
|---|---|---|---|
| 123451 | Park's Great Hits | Music | 19.99 |
| 123453 | Silly Puddy | Toy | 8.73 |
| 123452 | Playstation | Toy | 89.95 |
| 123454 | Men's T-Shirt | Clothing | 32.50 |
| 123455 | Blouse | Clothing | 34.97 |
| 123456 | Electronica 2002 | Music | 3.99 |
| 123457 | Country Tunes | Music | 21.55 |
| 123458 | Watermelon | Food | 8.73 |
| 123459 | Banana | Food | 1.00 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Id:Str | name:Str | type:Str | price:Str |
|---|---|---|---|
| 123455 | Blouse | Clothing | 34.97 |
| 123458 | Watermelon | Food | 8.73 |
| 123457 | Country Tunes | Music | 21.55 |
| 123452 | Playstation | Toy | 89.95 |

# solution

```sql
SELECT T1.Id, T1.name, T1.type, T1.price
FROM Table T1
LEFT OUTER JOIN Table T2
  ON (T1.type = T2.type AND T1.price < T2.price)
WHERE T2.price IS NULL;
```
