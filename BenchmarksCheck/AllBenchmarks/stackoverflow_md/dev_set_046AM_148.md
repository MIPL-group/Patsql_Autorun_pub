# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 046AM

# input:input0

| comp:Str | Subcomp:Str | Lognum:Str | id:Str | Firname:Str | LAstname:Str |
|---|---|---|---|---|---|
| AK | AK-G | NULL | 3897 | ABC | DEF |
| AB | AK-G | NULL | 5432 | mark | ray |
| MC | MC-A | NULL | 1234 | john | steve |
| MC | MC-A | NULL | 5678 | dan | pitcher |
| MC | MC-A | NULL | 9843 | james | robin |
| MC | MC-A | "83" | 1234 | john | steve |
| MC | MC-A | "84" | 5678 | dan | pitcher |
| MC | MC-A | "85" | 9843 | james | robin |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| comp:Str | Subcomp:Str | Lognum:Str | id:Str | Firname:Str | LAstname:Str |
|---|---|---|---|---|---|
| AK | AK-G | NULL | 3897 | ABC | DEF |
| AB | AK-G | NULL | 5432 | mark | ray |
| MC | MC-A | "83" | 1234 | john | steve |
| MC | MC-A | "84" | 5678 | dan | pitcher |
| MC | MC-A | "85" | 9843 | james | robin |

# solution

```sql
select *
from input1 t0
where lognum is null and not exists (select * from input1 t1
  where t0.comp = t1.comp and t0.subcomp = t1.subcomp and t0.id = t1.id and
  t0.firname = t1.firname and t0.lastname = t1.lastname and
  t1.lognum is not null) or
  lognum is not null;
```
