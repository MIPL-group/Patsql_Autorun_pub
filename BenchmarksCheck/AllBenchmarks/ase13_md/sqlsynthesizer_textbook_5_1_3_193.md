# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_1_3

# input:input1

| ID_key_student:Str | ID_key:Str |
|---|---|
| S1 | C1 |
| S1 | C2 |
| S2 | C1 |
| S2 | C3 |
| S2 | C4 |
| S3 | C2 |
| S3 | C4 |
| S4 | C1 |
| S4 | C5 |
| S5 | C5 |
| S6 | C1 |
| S6 | C5 |
| S7 | C2 |
| S7 | C3 |
| S7 | C5 |
| S8 | C1 |
| S9 | C5 |
| S10 | C5 |
| S10 | C6 |
| S9 | C7 |
| S8 | C8 |
| S8 | C9 |
| S10 | C10 |
| S1 | C11 |
| S2 | C11 |
| S3 | C11 |
| S4 | C11 |
| S5 | C11 |
| S7 | C12 |
| S8 | C12 |
| S7 | C13 |
| S1 | C13 |
| S2 | C13 |
| S4 | C13 |
| S9 | C14 |
| S10 | C14 |
| S5 | C14 |
| S6 | C14 |

# input:input0

| ID_key:Str | Room:Str |
|---|---|
| C1 | R102 |
| C2 | R120 |
| C3 | R128 |
| C4 | R127 |
| C5 | R131 |
| C6 | R128 |
| C7 | R130 |
| C8 | R130 |
| C9 | R128 |
| C10 | R102 |
| C11 | R120 |
| C12 | R131 |
| C13 | R127 |
| C14 | R131 |

# constraint

{
  "constants": [
    "R128",
    "5"
  ],
  "aggregation_functions": []
}

# output:output

| ID_key:Str |
|---|
| C1 |
| C11 |
| C6 |
| C3 |
| C9 |
| C5 |

# solution

```sql
SELECT
    T0.ID_key 
FROM
    input1 AS T0 
JOIN
    input2 AS T1 
        ON T0.ID_key = T1.ID_key 
GROUP BY
    T0.ID_key 
HAVING
    max(T0.Room) = 'R128' 
    OR count(T0.ID_key) >= 5
```