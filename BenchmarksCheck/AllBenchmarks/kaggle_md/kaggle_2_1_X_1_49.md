# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 2_1_X_1

# input:posts_questions

| id:Int | title:Str | body:Str | accepted_answer_id:Int | answer_count:Int | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Int | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Str | post_type_id:Int | score:Int | tags:Str | view_count:Int |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57422054 | title1 | body1 | NULL | 1 | 0 | NULL | 2017-12-31 23:59:59 | NULL | 2018-01-01 1:01:01 | 2017-12-31 23:59:59 | NULL | 876298 | NULL | 2698795 | NULL | 1 | 2 | tag1 | 256 |
| 57422055 | title2 | body2 | NULL | 2 | 0 | NULL | 2018-01-01 0:00:00 | NULL | 2019-01-01 1:01:01 | 2018-01-01 0:00:00 | NULL | 876299 | NULL | 2698796 | NULL | 1 | 2 | tag2 | 256 |
| 57422056 | title3 | body3 | NULL | 1 | 0 | NULL | 2018-02-01 0:00:00 | NULL | 2018-02-01 1:00:00 | 2018-02-01 0:00:00 | NULL | 876300 | NULL | 2698797 | NULL | 1 | 2 | tag3 | 256 |
| 57422057 | title4 | body4 | NULL | 1 | 0 | NULL | 2018-01-11 0:00:00 | NULL | 2018-01-11 0:00:01 | 2018-01-11 0:00:00 | NULL | 876301 | NULL | 2698798 | NULL | 1 | 2 | tag4 | 256 |

# input:posts_answers

| id:Int | title:Str | body:Str | accepted_answer_id:Str | answer_count:Str | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Str | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Int | post_type_id:Int | score:Int | tags:Str | view_count:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57160995 | NULL | body1 | NULL | NULL | 0 | NULL | 2018-01-01 1:01:01 | NULL | 2018-01-01 1:01:01 | NULL | NULL | NULL | NULL | 11690962 | 57422054 | 2 | 0 | NULL | NULL |
| 57160996 | NULL | body2 | NULL | NULL | 0 | NULL | 2018-01-01 1:01:01 | NULL | 2018-01-01 1:01:01 | NULL | NULL | NULL | NULL | 11690963 | 57422055 | 2 | 0 | NULL | NULL |
| 57160997 | NULL | body3 | NULL | NULL | 0 | NULL | 2019-01-01 1:01:01 | NULL | 2019-01-01 1:01:01 | NULL | NULL | NULL | NULL | 11690964 | 57422055 | 2 | 0 | NULL | NULL |
| 57160998 | NULL | body4 | NULL | NULL | 0 | NULL | 2018-02-01 1:00:00 | NULL | 2018-02-01 1:00:00 | NULL | NULL | NULL | NULL | 11690965 | 57422056 | 2 | 0 | NULL | NULL |
| 57160999 | NULL | body5 | NULL | NULL | 0 | NULL | 2018-01-11 0:00:01 | NULL | 2018-01-11 0:00:01 | NULL | NULL | NULL | NULL | 11690966 | 57422057 | 2 | 0 | NULL | NULL |

# constraint

{
  "constants": [
    "2018-01-01",
    "2018-02-01"
  ],
  "aggregation_functions": []
}

# output:output

| q_id:Int | time_to_answer:Int |
|---|---|
| 57422057 | 1 |
| 57422055 | 3661 |

# solution

```sql
-- MIN(EXTRACT(EPOCH FROM a.creation_date) - EXTRACT(EPOCH FROM q.creation_date)) in PostgreSQL
SELECT q.id AS q_id,
    MIN(TIMESTAMP_DIFF(a.creation_date, q.creation_date, SECOND)) as time_to_answer
FROM `bigquery-public-data.stackoverflow.posts_questions` AS q
    LEFT JOIN `bigquery-public-data.stackoverflow.posts_answers` AS a
ON q.id = a.parent_id
WHERE q.creation_date >= '2018-01-01' and q.creation_date < '2018-02-01'
GROUP BY q_id
ORDER BY time_to_answer
```
