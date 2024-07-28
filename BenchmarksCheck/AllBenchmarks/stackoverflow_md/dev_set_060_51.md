# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 060

# input:input0

| ID:Str | GroupNumber:Str | FirstName:Str |
|---|---|---|
| 1 | 1 | Peter |
| 2 | 1 | Bob |
| 3 | 1 | Peter |
| 4 | 2 | Rosemary |
| 5 | 2 | Jamie |
| 6 | 3 | Peter |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| GroupNumber:Str | FirstNames:Str |
|---|---|
| 1 | Peter |
| 1 | Bob |
| 2 | Rosemary |
| 2 | Jamie |
| 3 | Peter |

# solution

```sql
Select GroupNumber,  FirstName
From input
Group By GroupNumber, FirstName
```
