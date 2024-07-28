# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 002M

# input:input0

| locId:Str | dtg:Str | temp:Str |
|---|---|---|
| 100 | 2009-02-27 | 12 |
| 100 | 2009-02-26 | 14 |
| 200 | 2009-02-28 | 20 |
| 200 | 2009-02-25 | 19 |
| 300 | 2009-02-28 | 23 |
| 300 | 2009-02-25 | 24 |
| 300 | 2009-02-26 | 21 |
| 100 | 2009-02-24 | 13 |
| 300 | 2009-02-24 | 16 |
| 200 | 2009-02-24 | 18 |
| 400 | 2009-02-24 | 12 |
| 100 | 2009-02-23 | 11 |
| 300 | 2009-02-23 | 14 |
| 200 | 2009-02-23 | 15 |
| 400 | 2009-02-23 | 10 |

# constraint

{
  "constants": [
    "2009-02-24"
  ],
  "aggregation_functions": []
}

# output:output

| locID:Str | dtg:Str | tmp:Str |
|---|---|---|
| 100 | 2009-02-27 | 12 |
| 200 | 2009-02-28 | 20 |
| 300 | 2009-02-28 | 23 |

# solution

```sql
SELECT t2.* FROM (
    SELECT locId, MAX(dtg) AS maxdtg 
    FROM temperatures
    WHERE dtg > DATE '2009-02-24' 
    GROUP BY locId
) t1 INNER JOIN temperatures t2
  ON t2.locId = t1.locId 
    AND t2.dtg = t1.maxdtg
```
