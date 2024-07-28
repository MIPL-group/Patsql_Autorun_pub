# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 005M

# input:events

| g_event_id:Str | prim_cid:Str | event_id:Str | event_time:Str |
|---|---|---|---|
| 1 | 111 | 16 | 2016-10-21 16:00:00 |
| 2 | 111 | 17 | 2016-10-22 16:00:01 |
| 3 | 111 | 18 | 2016-10-23 16:00:02 |
| 4 | 222 | 15 | 2016-10-24 16:01:01 |
| 5 | 222 | 17 | 2016-10-25 16:01:02 |
| 6 | 333 | 16 | 2016-10-26 16:02:01 |
| 7 | 333 | 17 | 2016-10-27 16:02:02 |
| 8 | 333 | 18 | 2016-10-28 16:02:38 |
| 9 | 444 | 99 | 2016-11-01 16:00:00 |
| 10 | 444 | 16 | 2016-11-02 16:00:01 |
| 11 | 444 | 17 | 2016-11-03 16:00:02 |

# constraint

{
  "constants": [
    "17:Str"
  ],
  "aggregation_functions": []
}

# output:output

| g_event_id:Str | prim_cid:Str | event_id:Str | event_time:Str |
|---|---|---|---|
| 5 | 222 | 17 | 2016-10-25 16:01:02 |
| 11 | 444 | 17 | 2016-11-03 16:00:02 |

# solution

```sql
SELECT t1.*
FROM events AS t1
  JOIN (
    SELECT prim_cid, max(g_event_id) AS max_g_event_id
    FROM events
    GROUP BY prim_cid
  ) AS t2 ON t1.g_event_id = t2.max_g_event_id
WHERE t1.event_id = '17'
ORDER BY t1.g_event_id
```
