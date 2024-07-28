# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 040

# input:input0

| grp:Str | subGroup:Str |
|---|---|
| grp-A | sub-A |
| grp-A | sub-A |
| grp-A | sub-B |
| grp-B | sub-A |
| grp-B | sub-B |
| grp-B | sub-B |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| grp:Str | subGroup:Str | count:Str |
|---|---|---|
| grp-A | sub-A | 2 |
| grp-A | sub-B | 1 |
| grp-B | sub-A | 1 |
| grp-B | sub-B | 2 |

# solution

```sql
SELECT
    grp,
    subGroup,
    count(grp) 
FROM
    input1 
GROUP BY
    grp,
    subGroup 
ORDER BY
    grp ASC
```
