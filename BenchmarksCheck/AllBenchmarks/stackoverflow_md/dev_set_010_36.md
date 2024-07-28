# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 010

# input:input0

| id:Str | country:Str | status:Str |
|---|---|---|
| 1 | SE | TREATED |
| 2 | DK | UNTREATED |
| 3 | SE | UNTREATED |
| 4 | DE | TREATED |
| 5 | JP | UNTREATED |
| 6 | JP | TREATED |

# constraint

{
  "constants": [
    "TREATED",
    "UNTREATED"
  ],
  "aggregation_functions": []
}

# output:output

| id:Str | country:Str | status:Str |
|---|---|---|
| 1 | SE | TREATED |
| 6 | JP | TREATED |

# solution

```sql
select t1.id,t1.country,t1.status
from table t1
join table t2 on t1.country=t2.country and t2.status='UNTREATED'
where t1.status='TREATED'
```
