# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 008X

# input:input0

| InspectYear:Str | Part:Str | Pos1:Str | Pos2:Str | Pos3:Str | Pos4:Str |
|---|---|---|---|---|---|
| 2009 | 001 | 8 | 8 | 9 | 7 |
| 2009 | 002 | 9 | 7 | 8 | 6 |
| 2011 | 001 | 9 | 9 | 8 | 7 |
| 2011 | 002 | 7 | 8 | 6 | 8 |
| 2013 | 001 | 8 | 9 | 7 | 9 |
| 2013 | 002 | 7 | 7 | 8 | 8 |
| 2015 | 001 | 8 | 8 | 7 | 4 |
| 2015 | 002 | 7 | 6 | 9 | 8 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Part:Str | Pos:Str | 2009:Str | 2011:Str | 2013:Str | 2015:Str | Calc1:Str | Calc2:Str |
|---|---|---|---|---|---|---|---|
| 001 | Pos1 | 8 | 9 | 8 | 8 | 0 | 0 |
| 001 | Pos2 | 8 | 9 | 9 | 8 | -1 | 0 |
| 001 | Pos3 | 9 | 8 | 7 | 7 | 0 | -2 |
| 001 | Pos4 | 7 | 7 | 9 | 4 | -5 | -3 |

# solution

```sql
declare @inspectyear as nvarchar(max), @calc as nvarchar(max), @query as nvarchar(max);
```
