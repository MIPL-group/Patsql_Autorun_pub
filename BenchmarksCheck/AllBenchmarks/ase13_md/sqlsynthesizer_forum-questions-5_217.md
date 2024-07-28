# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: forum-questions-5

# input:input0

| v_key:Str | entryid:Str | result:Str |
|---|---|---|
| v1 | e1 | N |
| v2 | e1 | L |
| v3 | e2 | L |
| v4 | e3 | L |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| entryid:Str | count:Str |
|---|---|
| e1 | 2 |
| e2 | 1 |
| e3 | 1 |

# solution

```sql
SELECT
    entryid,
    count(v_key) 
FROM
    input1 
GROUP BY
    entryid 
ORDER BY
    entryid ASC
```
