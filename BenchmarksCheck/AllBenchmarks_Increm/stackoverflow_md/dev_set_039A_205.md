# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 039A

# input:input0

| trans:Str | user:Str | Month:Str |
|---|---|---|
| 100 | 1 | 1 |
| 102 | 2 | 1 |
| 103 | 3 | 1 |
| 100 | 1 | 2 |
| 103 | 2 | 2 |
| 103 | 3 | 2 |
| 104 | 1 | 3 |
| 104 | 2 | 3 |
| 101 | 3 | 3 |

# constraint

{
  "constants": [
    "3"
  ],
  "aggregation_functions": []
}

# output:output

| Avgtrans:Str | user3Trans:Str | Month:Str |
|---|---|---|
| 101 | 103 | 1 |
| 101.5 | 103 | 2 |
| 104 | 101 | 3 |

# solution

```sql
select Avgtrans, t2.trans, t1.month
from 
(select month, avg(trans) Avgtrans
 from t
 having user <> 3
 groupy month) t1
join
(select *
 from t
 where user = 3) t2
on t1.month = t2.month
```