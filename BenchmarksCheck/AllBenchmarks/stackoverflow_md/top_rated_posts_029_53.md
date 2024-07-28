# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 029

# input:input0

| TicketID:Str | Person:Str |
|---|---|
| T0001 | Alice |
| T0001 | Bob |
| T0002 | Catherine |
| T0002 | Doug |
| T0003 | Elaine |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| TicketID:Str | People:Str |
|---|---|
| T0001 | Alice Bob |
| T0002 | Catherine Doug |
| T0003 | Elaine |

# solution

```sql
SELECT
    TicketID,
    string_agg(Person, ' ') 
FROM
    input1 
GROUP BY
    TicketID 
ORDER BY
    TicketID ASC
```
