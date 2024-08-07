# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 1_6_X_2

# input:posts_questions

| id:Int | title:Str | body:Str | accepted_answer_id:Int | answer_count:Int | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Int | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Str | post_type_id:Int | score:Int | tags:Str | view_count:Int |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57422054 | title1 | body1 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876298 | NULL | 2698795 | NULL | 1 | 2 | 'tag11-tag12-tag13' | 256 |
| 57422055 | title2 | body2 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876299 | NULL | 2698796 | NULL | 1 | 2 | 'tag21-bigquery-tag23' | 256 |
| 57422056 | title3 | body3 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876300 | NULL | 2698797 | NULL | 1 | 2 | 'tag31-tag32-bigquery' | 256 |

# input:posts_answers

| id:Int | title:Str | body:Str | accepted_answer_id:Str | answer_count:Str | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Str | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Int | post_type_id:Int | score:Int | tags:Str | view_count:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57160995 | NULL | body1 | NULL | NULL | 0 | NULL | 2019-08-23 | NULL | 2019-08-23 | NULL | NULL | NULL | NULL | 11690962 | 57422054 | 2 | 0 | NULL | NULL |
| 57160996 | NULL | body2 | NULL | NULL | 0 | NULL | 2019-08-23 | NULL | 2019-08-23 | NULL | NULL | NULL | NULL | 11690963 | 57422055 | 2 | 0 | NULL | NULL |
| 57160997 | NULL | body3 | NULL | NULL | 0 | NULL | 2019-08-23 | NULL | 2019-08-23 | NULL | NULL | NULL | NULL | 11690964 | 57422056 | 2 | 0 | NULL | NULL |

# constraint

{
  "constants": [
    "%bigquery%"
  ],
  "aggregation_functions": []
}

# output:output

| id:Int | body:Str | owner_user_id:Int |
|---|---|---|
| 57160996 | body2 | 11690963 |
| 57160997 | body3 | 11690964 |

# solution

```sql
SELECT a.id, a.body, a.owner_user_id
FROM `bigquery-public-data.stackoverflow.posts_questions` AS q 
INNER JOIN `bigquery-public-data.stackoverflow.posts_answers` AS a
    ON q.id = a.parent_id
WHERE q.tags LIKE '%bigquery%'
```
