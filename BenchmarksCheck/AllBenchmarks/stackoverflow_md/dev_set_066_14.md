# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 066

# input:input0

| tranid:Str | item:Str | startdate:Str | enddate:Str |
|---|---|---|---|
| 1 | A | 1/1/2000 | 2/2/2005 |
| 2 | A | 5/1/2000 | 2/2/2005 |
| 3 | B | 7/8/2015 | 9/8/2015 |
| 4 | C | 4/10/2007 | 7/20/2008 |
| 5 | C | 4/10/2003 | 7/20/2005 |
| 6 | C | 4/10/2003 | 7/20/2008 |
| 7 | B | 5/1/2000 | 9/8/2015 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| tranid:Str | item:Str | startdate:Str | enddate:Str |
|---|---|---|---|
| 2 | A | 5/1/2000 | 2/2/2005 |
| 3 | B | 7/8/2015 | 9/8/2015 |
| 4 | C | 4/10/2007 | 7/20/2008 |

# solution

```sql
SELECT b.tranid, b.item, a.maxstartdate, b.enddate
FROM
  (SELECT t.item, MAX(t.startdate) maxstartdate
   FROM t
   GROUP BY t.item) a
JOIN t b
ON a.maxstartdate = b.startdate AND a.item = b.item;
```
