# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 019M

# input:input0

| Team:Str | Player:Str |
|---|---|
| 1 | Dillan |
| 1 | Brady |
| 1 | Brady |
| 1 | Player1 |
| 2 | John |
| 2 | Billy |
| 2 | Player2 |
| 3 | Player3 |
| 4 | Gary |
| 4 | Gary |
| 5 | Brady |
| 5 | Brady |
| 5 | Brady |
| 5 | Gary |
| 5 | Gary |
| 5 | Gary |

# constraint

{
  "constants": [
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| c1:Str |
|---|
| 1 |
| 4 |
| 5 |

# solution

```sql
SELECT DISTINCT Team
FROM TeamPlayer
GROUP BY Team, Player
HAVING COUNT(*) > 1;
```
