# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 013

# input:tbl_1

| ID:Str | Name:Str |
|---|---|
| 1 | Company1 |
| 2 | Company2 |
| 3 | Company3 |

# input:tbl_2

| ID:Str | Company_group:Str |
|---|---|
| 1 | Company3 |
| 2 | Company2 |
| 3 | Company2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | Name:Str | RootName:Str | RootId:Str |
|---|---|---|---|
| 1 | Company1 | Company3 | 3 |
| 3 | Company3 | Company2 | 2 |

# solution

```sql
select      t1.ID
           ,t1.Name
           ,t2.Company_group    as RootName
           ,t1_b.ID             as RootId
from                    tbl_1   t1
            join        tbl_2   t2
            on          t2.ID   =
                        t1.ID
            join        tbl_1   t1_b
            on          t1_b.Name   =
                        t2.Company_group
where       t1.ID <> t1_b.ID;
```
