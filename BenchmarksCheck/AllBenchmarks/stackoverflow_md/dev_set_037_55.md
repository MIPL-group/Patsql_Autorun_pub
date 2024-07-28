# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 037

# input:input0

| chapterid:Str | xmlfile:Str |
|---|---|
| 1234 | 123.xml |
| 1234 | 123.xml |
| 1234 | 123.xml |
| 1234 | 123.xml |
| 4567 | 123.xml |
| 4567 | 123.xml |
| 6789 | 123.xml |
| 6789 | 145.xml |
| 7890 | 234.xml |
| 7890 | 234.xml |
| 7890 | 234.xml |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| chapterid:Str | xmlfile:Str |
|---|---|
| 1234 | 123.xml |
| 4567 | 123.xml |
| 6789 | 123.xml |
| 6789 | 145.xml |
| 7890 | 234.xml |

# solution

```sql
SELECT chapterid xmlfile
FROM TABLE 
GROUP BY chapterid xmlfile
```
