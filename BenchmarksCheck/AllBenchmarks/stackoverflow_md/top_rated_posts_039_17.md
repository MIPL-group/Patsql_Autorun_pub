# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 039

# input:input0

| c:Str |
|---|
| one |
| two |
| three |
| three |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| c:Str |
|---|
| three |

# solution

```sql
SELECT
    T2.c 
FROM
    (SELECT
        max(T0.count_c) AS max_T0_count_c 
    FROM
        (SELECT
            count(c) AS count_c 
        FROM
            input1 
        GROUP BY
            c) AS T0) AS T1 
    JOIN
        (
            SELECT
                c,
                count(c) AS count_c 
            FROM
                input1 
            GROUP BY
                c
        ) AS T2 
            ON T1.max_T0_count_c = T2.count_c
```
