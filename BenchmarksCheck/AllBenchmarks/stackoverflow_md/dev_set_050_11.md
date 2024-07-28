# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 050

# input:tablea

| attendee_id:Str | others1:Str |
|---|---|
| abcd | A |
| ghij | B |
| defg | C |

# input:pps

| attendee_id:Str | others2:Str | event_id:Str |
|---|---|---|
| wxyz | D | 1 |
| mlno | E | 2 |
| defg | F | 3 |
| defg | G | 2 |
| abcd | H | 1 |

# constraint

{
  "constants": [
    "3"
  ],
  "aggregation_functions": []
}

# output:output

| attendee_id:Str | others1:Str | others2:Str | event_id:Str |
|---|---|---|---|
| abcd | A | NULL | NULL |
| ghij | B | NULL | NULL |
| defg | C | F | 3 |

# solution

```sql
SELECT a.*, b.others2, b.event_id 
FROM attendees a LEFT JOIN eventattendees b ON a.attendee_id = b.attendee_id
WHERE event_id = 3
```
