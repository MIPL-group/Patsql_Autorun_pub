# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 048XX

# input:input0

| c1:Str | c2:Str | c3:Str |
|---|---|---|
| 100 | 2 | 10 |
| 101 | 12 | 20 |
| 102 | 5 | 10 |
| 103 | 1 | 8 |
| 104 | 13 | 15 |
| 105 | 25 | 30 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| test_letter:Str | d1:Str | d2:Str | overlap_letter:Str | overlap_d1:Str | overlap_d2:Str |
|---|---|---|---|---|---|
| 100 | 2 | 10 | 103 | 1 | 8 |
| 100 | 2 | 10 | 102 | 5 | 10 |
| 101 | 12 | 20 | 104 | 13 | 15 |
| 102 | 5 | 10 | 103 | 1 | 8 |

# solution

```sql
SELECT basetable.letter as test_letter, basetable.d1, basetable.d2,
       overlaptable.letter as overlap_letter, overlaptable.d1 as overlap_d1, overlaptable.d2 as overlap_d2
FROM test basetable JOIN
     test overlaptable
     ON basetable.d1 <= overlaptable.d2 AND
        basetable.d2 >= overlaptable.d1
WHERE basetable.letter < overlaptable.letter  -- This is the change
ORDER BY basetable.letter, basetable.d1;
```
