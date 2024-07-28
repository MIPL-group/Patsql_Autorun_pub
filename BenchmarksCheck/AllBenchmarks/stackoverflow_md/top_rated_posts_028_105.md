# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 028

# input:input1

| PID:Str | SEQ:Str | Descr:Str |
|---|---|---|
| A | 1 | Have |
| A | 2 | a nice |
| A | 3 | day. |
| B | 1 | Nice Work. |
| C | 1 | Yes |
| C | 2 | we can |
| C | 3 | do |
| C | 4 | this work! |

# input:input0

| PID:Str |
|---|
| A |
| B |
| C |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| PID:Str | Descr:Str |
|---|---|
| A | Have a nice day. |
| B | Nice Work. |
| C | Yes we can do this work! |

# solution

```sql
SELECT
    T0.PID,
    string_agg(T1.Descr, ' ') 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.PID = T1.PID 
GROUP BY
    T0.PID 
ORDER BY
    T0.PID ASC
```
