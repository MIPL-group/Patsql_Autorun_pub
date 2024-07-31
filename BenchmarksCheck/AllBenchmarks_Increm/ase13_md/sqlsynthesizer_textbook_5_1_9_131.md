# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_9

# input:input1

| ID_key:Str | fname:Str |
|---|---|
| F1 | teach1 |
| F2 | teach2 |
| F3 | teach3 |
| F4 | teach4 |
| F5 | teach5 |
| F6 | teach6 |
| F7 | teach7 |
| F8 | teach8 |
| F9 | teach9 |

# input:input0

| ID_class:Str | ID_key:Str | room:Str |
|---|---|---|
| C1 | F1 | R101 |
| C2 | F1 | R128 |
| C3 | F1 | R103 |
| C4 | F2 | R103 |
| C5 | F3 | R101 |
| C6 | F4 | R128 |
| C7 | F2 | R101 |
| C9 | F5 | R128 |
| C10 | F6 | R102 |
| C11 | F7 | R128 |
| C12 | F7 | R103 |
| C13 | F8 | R102 |
| C14 | F8 | R128 |
| C15 | F8 | R128 |
| C16 | F4 | R128 |
| C17 | F5 | R128 |
| C18 | F5 | R128 |
| C19 | F9 | R128 |
| C19 | F9 | R129 |

# constraint

{
  "constants": [
    "R128"
  ],
  "aggregation_functions": []
}

# output:output

| fname:Str | count:Str |
|---|---|
| teach4 | 2 |
| teach5 | 3 |

# solution

```sql
SELECT
    max(T1.fname),
    count(T0.ID_class) 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.ID_key = T1.ID_key 
GROUP BY
    T0.ID_key 
HAVING
    max(T0.room) = 'R128' 
    AND min(T0.room) = 'R128' 
ORDER BY
    max(T1.fname) ASC
```