# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 067X

# input:input1

| Date:Str | Item2:Str |
|---|---|
| 11/03 | aaaa |
| 12/03 | aaaa |
| 13/03 | bbbb |
| 14/03 | aaaa |
| 15/03 | cccc |
| 16/03 | bbbb |

# input:input0

| Date:Str | Item:Str |
|---|---|
| 12/03 | aaaa |
| 12/03 | aaaa |
| 14/03 | bbbb |
| 14/03 | aaaa |
| 15/03 | cccc |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Date:Str | Count(Item1):Str | Count(Item2):Str |
|---|---|---|
| 11/03 | 0 | 1 |
| 12/03 | 2 | 1 |
| 13/03 | 0 | 1 |
| 14/03 | 2 | 1 |
| 15/03 | 1 | 1 |
| 16/03 | 0 | 1 |

# solution

```sql
select t2.date, count(t1.cnt), count(t2.cnt)
from (select date, count(*) cnt from input2 group by date) t2
left join (select date, count(*) cnt from input1 group by date) t1
  on t2.date = t1.date
group by t2.date
```
