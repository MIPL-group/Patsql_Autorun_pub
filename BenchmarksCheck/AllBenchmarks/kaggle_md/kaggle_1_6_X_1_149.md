# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 1_6_X_1

# input:posts_questions

| id:Int | title:Str | body:Str | accepted_answer_id:Int | answer_count:Int | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Int | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Str | post_type_id:Int | score:Int | tags:Str | view_count:Int |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57422054 | title1 | body1 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876298 | NULL | 2698795 | NULL | 1 | 2 | 'tag11-tag12-tag13' | 256 |
| 57422055 | title2 | body2 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876299 | NULL | 2698796 | NULL | 1 | 2 | 'tag21-bigquery-tag23' | 256 |
| 57422056 | title3 | body3 | NULL | 2 | 0 | NULL | 2019-08-09 | NULL | 2019-08-22 | 2019-08-09 | NULL | 876300 | NULL | 2698797 | NULL | 1 | 2 | 'tag31-tag32-bigquery' | 256 |

# constraint

{
  "constants": [
    "%bigquery%"
  ],
  "aggregation_functions": []
}

# output:output

| id:Int | title:Str | owner_user_id:Int |
|---|---|---|
| 57422055 | title2 | 2698796 |
| 57422056 | title3 | 2698797 |

# solution

```sql
SELECT id, title, owner_user_id
FROM `bigquery-public-data.stackoverflow.posts_questions`
WHERE tags LIKE '%bigquery%'
```
