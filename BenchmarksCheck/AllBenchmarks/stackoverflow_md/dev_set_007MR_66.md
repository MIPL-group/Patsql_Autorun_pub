# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 007MR

# input:input0

| id:Str | home:Str | datetime:Str | player:Str | resource:Str |
|---|---|---|---|---|
| 1 | 10 | 2009/03/04 | john | 199 |
| 2 | 11 | 2009/03/04 | juliet | 244 |
| 5 | 12 | 2009/03/04 | borat | 555 |
| 3 | 10 | 2009/03/03 | john | 300 |
| 4 | 11 | 2009/03/03 | juliet | 200 |
| 6 | 12 | 2009/03/03 | borat | 500 |
| 7 | 13 | 2008/12/24 | borat | 600 |
| 8 | 13 | 2009/01/01 | borat | 700 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id:Str | home:Str | datetime:Str | player:Str | resource:Str |
|---|---|---|---|---|
| 1 | 10 | 2009/03/04 | john | 199 |
| 2 | 11 | 2009/03/04 | juliet | 244 |
| 5 | 12 | 2009/03/04 | borat | 555 |
| 8 | 13 | 2009/01/01 | borat | 700 |

# solution

```sql
SELECT tt.*
FROM topten tt
INNER JOIN
    (SELECT home, MAX(datetime) AS MaxDateTime
    FROM topten
    GROUP BY home) groupedtt 
ON tt.home = groupedtt.home 
AND tt.datetime = groupedtt.MaxDateTime
```
