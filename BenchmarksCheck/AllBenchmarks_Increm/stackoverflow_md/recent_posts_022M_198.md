# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 022M

# input:Tracks

| TrackId:Str | UserId:Str | SongTitle:Str |
|---|---|---|
| 1 | 11 | Some song title |

# input:Followers

| FolloweeId:Str | FollowerId:Str |
|---|---|
| 72 | 11 |
| 73 | 11 |
| 74 | 11 |
| 73 | 41 |
| 74 | 21 |
| 74 | 31 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| TrackId:Str | UserId:Str | MostPopularFolloweeId:Str |
|---|---|---|
| 1 | 11 | 74 |

# solution

```sql
SELECT t0.TrackId, t0.UserId, t2.FolloweeId
FROM Tracks AS t0
CROSS JOIN (
  SELECT count(*) AS value, FolloweeId
  FROM Followers AS t1
  GROUP BY FolloweeId
  ORDER BY count(*) DESC
  FETCH FIRST ROW ONLY
) AS t2
```
