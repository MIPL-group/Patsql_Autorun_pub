# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 027X

# input:mytable1

| ts:Str | s_no:Str | calls:Str |
|---|---|---|
| 2016-10-14 10:04:01.000 | 3 | 56 |
| 2016-10-14 10:04:01.000 | 4 | 145 |
| 2016-10-14 10:09:00.000 | 3 | 143 |
| 2016-10-14 10:09:00.000 | 4 | 329 |
| 2016-10-14 10:14:01.000 | 3 | 0 |
| 2016-10-14 10:14:01.000 | 4 | 49 |
| 2016-10-14 10:19:00.000 | 3 | 6 |
| 2016-10-14 10:19:00.000 | 4 | 16 |
| 2016-10-14 10:24:01.000 | 3 | 22 |
| 2016-10-14 10:24:01.000 | 4 | 28 |
| 2016-10-14 10:29:00.000 | 3 | 4 |
| 2016-10-14 10:29:00.000 | 4 | 7 |
| 2016-10-14 10:34:00.000 | 3 | 14 |
| 2016-10-14 10:34:00.000 | 4 | 9 |
| 2016-10-14 10:38:59.000 | 3 | 39 |
| 2016-10-14 10:38:59.000 | 4 | 391 |
| 2016-10-14 10:44:01.000 | 3 | 3 |
| 2016-10-14 10:44:01.000 | 4 | 31 |
| 2016-10-14 10:49:01.000 | 3 | 116 |
| 2016-10-14 10:49:01.000 | 4 | 52 |
| 2016-10-14 10:54:00.000 | 3 | 75 |
| 2016-10-14 10:54:00.000 | 4 | 8 |
| 2016-10-14 10:59:00.000 | 3 | 16 |
| 2016-10-14 10:59:00.000 | 4 | 8 |
| 2016-10-14 11:04:01.000 | 3 | 23 |
| 2016-10-14 11:04:01.000 | 4 | 13 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| s_no:Str | bucket_window:Str | ts:Str | calls:Str |
|---|---|---|---|
| 3 | 20 | 2016-10-14 10:29:00.000 | 4 |
| 4 | 20 | 2016-10-14 10:29:00.000 | 7 |
| 3 | 21 | 2016-10-14 10:59:00.000 | 16 |
| 4 | 21 | 2016-10-14 10:59:00.000 | 8 |
| 3 | 22 | 2016-10-14 11:04:01.000 | 23 |
| 4 | 22 | 2016-10-14 11:04:01.000 | 13 |

# solution

```sql
SELECT M1.*,
(SELECT calls From mytable1 M2 where M2.ts=M1.ts and M2.s_no=M1.s_no) as calls
FROM
(
    select m.s_no, m.bucket_window, max(m.ts) ts
    from (
        select m.*, datepart(hour, m.ts)*2 + floor(datepart(minute, m.ts)/30) bucket_window
        from mytable1 m
        where m.ts >= DATEADD(dd, DATEDIFF(dd, 0, GETDATE()), 0)
    ) m
    group by m.s_no, m.bucket_window
) M1
```
