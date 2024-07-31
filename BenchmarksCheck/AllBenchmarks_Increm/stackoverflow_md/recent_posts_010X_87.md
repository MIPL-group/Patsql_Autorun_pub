# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 010X

# input:certif_span

| Robot_ID:Str | Certif_ID:Str | d_Start:Str | d_End:Str |
|---|---|---|---|
| 210 | 1 | 2000-01-01 | 2001-02-02 |
| 210 | 1 | 2001-02-03 | 2001-12-31 |
| 210 | 1 | 2000-01-01 | 2000-12-31 |
| 880 | 1 | 2001-01-01 | 2001-12-31 |
| 880 | 1 | 2002-02-02 | 2003-02-01 |
| 880 | 1 | 2003-01-01 | 2004-12-31 |
| 880 | 7 | 2010-05-05 | 2011-05-04 |
| 880 | 7 | 2011-05-05 | 2012-02-10 |
| 880 | 7 | 2013-03-03 | 2013-04-04 |
| 880 | 7 | 2013-04-01 | 2013-05-05 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Robot_ID:Str | Certif_ID:Str | d_Start:Str | d_End:Str |
|---|---|---|---|
| 210 | 1 | 2000-01-01 | 2001-12-31 |
| 880 | 1 | 2002-02-02 | 2004-12-31 |
| 880 | 7 | 2013-03-03 | 2013-05-05 |

# solution

```sql
Declare @certif_span TABLE(Robot_ID CHAR(3), Certif_ID SMALLINT, StartDate date, EndDate date);
```
