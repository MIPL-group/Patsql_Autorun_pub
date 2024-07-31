# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 050

# input:input2

| org_id:Str | org_name:Str | org_max:Str |
|---|---|---|
| 4 | Google | "45" |
| 5 | Yahoo | "300" |

# input:input1

| employee_id:Str | employee_name:Str | joining_date:Str |
|---|---|---|
| 1 | Einstein | "01/24/1998" |
| 2 | Maxwell | "03/16/2002" |

# input:input0

| role_id:Str | role_type:Str | company:Str | ref_id:Str |
|---|---|---|---|
| 1 | A | X | 1 |
| 2 | B | Y | 4 |
| 3 | A | Z | 2 |
| 4 | B | X | 5 |

# constraint

{
  "constants": [
    "A",
    "B"
  ],
  "aggregation_functions": []
}

# output:output

| role_id:Str | role_type:Str | ref_id:Str | ref_name:Str | ref_joining_date:Str |
|---|---|---|---|---|
| 1 | A | 1 | Einstein | "01/24/1998" |
| 2 | B | 4 | Google | "45" |
| 3 | A | 2 | Maxwell | "03/16/2002" |
| 4 | B | 5 | Yahoo | "300" |

# solution

```sql
SELECT t1.role_id,
       t1.role_type,
       t1.company,
       t1.ref_id,
       COALESCE(e.employee_name, o.org_id) AS ref_name,
       e.joining_date                      AS ref_joining_date,
       o.org_max                           AS ref_org_max
FROM   roles t1
       LEFT JOIN employee
              ON e.employee_id = t1.ref_id
                 AND t1.role_type = 'A'
       LEFT JOIN organisations o
              ON o.org_id = t1.ref_id
                 AND t1.role_type = 'B'
```
