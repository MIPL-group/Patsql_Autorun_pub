# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 016

# input:input1

| staff_id:Str | forename:Str | school_id:Str | wage:Str |
|---|---|---|---|
| 11 | Peter1 | 400 | 5000 |
| 12 | Peter2 | 400 | 4000 |
| 21 | Peter3 | 401 | 6000 |

# input:input0

| school_id:Str | class_id:Str | school_location:Str |
|---|---|---|
| 400 | 50 | Arizona1 |
| 401 | 51 | Arizona2 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| school_id:Str | numberofstaff:Str | salary:Str |
|---|---|---|
| 400 | 2 | 9000 |
| 401 | 1 | 6000 |

# solution

```sql
SELECT sc.school_id, 
   COUNT(*) as numberofstaff,
   SUM(st.wage) as salary
FROM school sc
INNER JOIN staff st
ON sc.school_id = st.school_id
GROUP BY sc.school_id
```
