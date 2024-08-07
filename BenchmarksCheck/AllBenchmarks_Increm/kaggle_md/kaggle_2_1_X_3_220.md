# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 2_1_X_3

# input:posts_questions

| id:Int | title:Str | body:Str | accepted_answer_id:Int | answer_count:Int | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Int | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Str | post_type_id:Int | score:Int | tags:Str | view_count:Int |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57422053 | title0 | qbody0 | NULL | 0 | 0 | NULL | 2018-12-31 | NULL | 2018-12-31 | 2018-12-31 | NULL | 1999 | NULL | 1001 | NULL | 1 | 2 | tag1 | 256 |
| 57422056 | title3 | qbody3 | NULL | 0 | 0 | NULL | 2019-02-01 | NULL | 2019-02-01 | 2019-02-01 | NULL | 1999 | NULL | 1002 | NULL | 1 | 2 | tag1 | 256 |
| 57422058 | title5 | qbody5 | NULL | 0 | 0 | NULL | 2019-01-01 | NULL | 2019-01-01 | 2019-01-01 | NULL | 1999 | NULL | 1004 | NULL | 1 | 2 | tag1 | 256 |
| 57422059 | title6 | qbody6 | NULL | 0 | 0 | NULL | 2019-01-23 | NULL | 2019-01-23 | 2019-01-23 | NULL | 1999 | NULL | 1005 | NULL | 1 | 2 | tag1 | 256 |
| 57422060 | title7 | qbody7 | NULL | 0 | 0 | NULL | 2019-01-23 | NULL | 2019-01-23 | 2019-01-23 | NULL | 1999 | NULL | 1005 | NULL | 1 | 2 | tag1 | 256 |

# input:users

| id:Int | display_name:Str | about_me:Str | age:Str | creation_date:Date | last_access_date:Date | location:Str | reputation:Int | up_votes:Int | down_votes:Int | views:Int | profile_image_url:Str | website_url:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1002 | user1002 | I'm user1002. | NULL | 2018-12-31 | 2019-01-01 | Sydney, Australia | 70088 | 707 | 34 | 4624 | NULL | https://user1002.example.com |
| 1000 | user1000 | I'm user1000. | NULL | 2019-01-01 | 2019-02-01 | Tokyo, Japan | 12345 | 432 | 10 | 1234 | NULL | https://user1000.example.com |
| 1003 | user1003 | I'm user1003. | NULL | 2019-01-23 | 2019-01-23 | Chiba, Japan | 12345 | 432 | 10 | 1234 | NULL | https://user1003.example.com |
| 1004 | user1004 | I'm user1004. | NULL | 2019-02-01 | 2019-02-01 | Osaka, Japan | 12345 | 432 | 10 | 1234 | NULL | https://user1004.example.com |
| 1005 | user1005 | I'm user1005. | NULL | 2019-01-23 | 2019-02-01 | Gunma, Japan | 12345 | 432 | 10 | 1234 | NULL | https://user1005.example.com |

# input:posts_answers

| id:Int | title:Str | body:Str | accepted_answer_id:Str | answer_count:Str | comment_count:Int | community_owned_date:Date | creation_date:Date | favorite_count:Str | last_activity_date:Date | last_edit_date:Date | last_editor_display_name:Str | last_editor_user_id:Int | owner_display_name:Str | owner_user_id:Int | parent_id:Int | post_type_id:Int | score:Int | tags:Str | view_count:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 57160998 | NULL | abody4 | NULL | NULL | 0 | NULL | 2019-01-01 | NULL | 2019-01-01 | NULL | NULL | NULL | NULL | 1003 | 10000004 | 2 | 0 | NULL | NULL |
| 57160997 | NULL | abody3 | NULL | NULL | 0 | NULL | 2019-01-01 | NULL | 2019-01-01 | NULL | NULL | NULL | NULL | 1002 | 10000003 | 2 | 0 | NULL | NULL |
| 57160999 | NULL | abody5 | NULL | NULL | 0 | NULL | 2019-01-01 | NULL | 2019-01-01 | NULL | NULL | NULL | NULL | 1004 | 10000005 | 2 | 0 | NULL | NULL |
| 57161000 | NULL | abody6 | NULL | NULL | 0 | NULL | 2019-01-23 | NULL | 2019-01-23 | NULL | NULL | NULL | NULL | 1005 | 10000006 | 2 | 0 | NULL | NULL |
| 57161001 | NULL | abody7 | NULL | NULL | 0 | NULL | 2019-01-23 | NULL | 2019-01-23 | NULL | NULL | NULL | NULL | 1005 | 10000007 | 2 | 0 | NULL | NULL |

# constraint

{
  "constants": [
    "2019-01-01",
    "2019-02-01"
  ],
  "aggregation_functions": []
}

# output:output

| owner_user_id:Int | q_creation_date:Date | a_creation_date:Date |
|---|---|---|
| 1001 | 2018-12-31 | NULL |
| 1000 | NULL | NULL |
| 1003 | NULL | NULL |
| 1005 | 2019-01-23 | 2019-01-23 |

# solution

```sql
-- left join is enough instead of full join.
-- PostgreSQL's execution plan is a right join on a.owner_user_id = q.owner_user_id.
-- id is ambigous.
SELECT u.id AS id,
    MIN(q.creation_date) AS q_creation_date,
    MIN(a.creation_date) AS a_creation_date
FROM `bigquery-public-data.stackoverflow.posts_questions` AS q
    FULL JOIN `bigquery-public-data.stackoverflow.posts_answers` AS a
        ON q.owner_user_id = a.owner_user_id 
    RIGHT JOIN `bigquery-public-data.stackoverflow.users` AS u
        ON q.owner_user_id = u.id
WHERE u.creation_date >= '2019-01-01' and u.creation_date < '2019-02-01'
GROUP BY id
```
