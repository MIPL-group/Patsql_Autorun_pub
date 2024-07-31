# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 032X

# input:input0

| firstname:Str | lastname:Str | nb_payments:Str |
|---|---|---|
| a | b | 10 |
| a | b | 20 |
| b | a | 30 |
| b | a | 40 |
| b | b | 50 |
| c | d | 10 |

# constraint

{
  "constants": [
    "3"
  ],
  "aggregation_functions": []
}

# output:output

| firstname:Str | lastname:Str | top3:Str |
|---|---|---|
| b | a | 70 |
| b | b | 50 |
| a | b | 30 |

# solution

```sql
SELECT   firstname, lastname , SUM(nb_payments) 
FROM     account 
GROUP BY firstname, lastname
ORDER BY 3 DESC LIMIT 3;
```
