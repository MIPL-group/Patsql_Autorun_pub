# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 017A

# input:input0

| emp_id:Str | emp_sal:Str | emp_grp:Str |
|---|---|---|
| 1 | 5 | HMCCR |
| 1 | 10 | HMCPR |
| 1 | 20 | HMCPR |
| 1 | 30 | HMCPR |
| 1 | 40 | HMCRR |
| 2 | 40 | HMCRR |
| 2 | 50 | HMCCR |

# constraint

{
  "constants": [
    "HMCPR"
  ],
  "aggregation_functions": []
}

# output:output

| emp_id:Str | emp_sal:Str | emp_grp:Str |
|---|---|---|
| 1 | 10 | HMCPR |
| 2 | 40 | HMCRR |

# solution

```sql
select t0.*
from input1 as t0
join (
  select t1.emp_id, min(emp_sal) as min_emp_sal
  from input1 as t1
  where t1.emp_grp = 'HMCPR' or not exists(select * from input1 as t2 where t1.emp_id = t2.emp_id and t2.emp_grp = 'HMCPR') 
  group by t1.emp_id) as t3
  on t0.emp_id = t3.emp_id and t0.emp_sal = t3.min_emp_sal
```
