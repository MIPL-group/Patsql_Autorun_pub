# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 047X

# input:input0

| ID:Str | Payment_type:Str | Time:Str |
|---|---|---|
| A | X | 2014/01/01 |
| A | Y | 2014/08/01 |
| B | X | 2013/10/01 |
| A | Y | 2014/08/01 |
| B | Z | 2013/09/01 |
| A | Y | 2012/01/01 |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| ID:Str | Payment_type:Str |
|---|---|
| A | Y |
| B | X |

# solution

```sql
select id, payment_type, time
from (select id, payment_type, time, count(*) as cnt,
             row_number() over (partition by id order by time desc, cnt desc) as seqnum
      from t
      group by id, payment_type, time
     ) ipt
where seqnum = 1;
```
