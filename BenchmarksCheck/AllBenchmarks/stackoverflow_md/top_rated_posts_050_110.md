# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 050

# input:input0

| ID:Str | Col1:Str | Col2:Str | Col3:Str |
|---|---|---|---|
| 1 | 3 | 34 | 76 |
| 2 | 32 | 976 | 24 |
| 3 | 7 | 235 | 3 |
| 4 | 245 | 1 | 792 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | Col1:Str | Col2:Str | Col3:Str | TheMin:Str |
|---|---|---|---|---|
| 1 | 3 | 34 | 76 | 3 |
| 2 | 32 | 976 | 24 | 24 |
| 3 | 7 | 235 | 3 | 3 |
| 4 | 245 | 1 | 792 | 1 |

# solution

```sql
with cte (ID, Col1, Col2, Col3)
as
(
    select ID, Col1, Col2, Col3
    from TestTable
)
select cte.ID, Col1, Col2, Col3, TheMin from cte
join
(
    select
        ID, min(Amount) as TheMin
    from 
        cte 
        UNPIVOT (Amount for AmountCol in (Col1, Col2, Col3)) as unpvt
    group by ID
) as minValues
on cte.ID = minValues.ID
```
