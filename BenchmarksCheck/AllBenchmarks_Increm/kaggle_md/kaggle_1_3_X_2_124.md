# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 1_3_X_2

# input:comments

| id:Int | by:Str | author:Str | time:Int | time_ts:Date | text:Str | parent:Int | deleted:Str | dead:Str | ranking:Int |
|---|---|---|---|---|---|---|---|---|---|
| 2701393 | 5l | 5l | 1309184881 | 2011-06-27 | And the glazier who fixed all the broken windo... | 286450 | NULL | NULL | 0 |
| 5811403 | 99 | 99 | 1370234048 | 2013-06-03 | Does canada have the equivalent of H1B/Green c... | 5804452 | NULL | NULL | 0 |
| 21623 | AF | AF | 1178992400 | 2007-05-12 | Speaking of Rails, there are other options in ... | 286450 | TRUE | NULL | 0 |
| 10159727 | EA | EA | 1441206574 | 2015-09-02 | Humans and large livestock (and maybe even pet... | 286450 | NULL | NULL | 0 |
| 2988424 | Iv | Iv | 1315853580 | 2011-09-12 | I must say I reacted in the same way when I re... | 286450 | NULL | NULL | 0 |
| 2701394 | 5l | 5l | 1309184881 | 2011-06-27 | And the glazier who fixed all the broken windo... | 2701243 | NULL | NULL | 0 |
| 5811404 | 99 | 99 | 1370234048 | 2013-06-03 | Does canada have the equivalent of H1B/Green c... | 286450 | NULL | NULL | 0 |
| 21624 | AF | AF | 1178992400 | 2007-05-12 | Speaking of Rails, there are other options in ... | 286450 | TRUE | NULL | 0 |
| 10159728 | EA | EA | 1441206574 | 2015-09-02 | Humans and large livestock (and maybe even pet... | 286450 | TRUE | NULL | 0 |
| 2988425 | Iv | Iv | 1315853580 | 2011-09-12 | I must say I reacted in the same way when I re... | 286450 | NULL | NULL | 0 |
| 2701395 | 5l | 5l | 1309184881 | 2011-06-27 | And the glazier who fixed all the broken windo... | 286450 | NULL | NULL | 0 |
| 5811405 | 99 | 99 | 1370234048 | 2013-06-03 | Does canada have the equivalent of H1B/Green c... | 5804452 | NULL | NULL | 0 |
| 21625 | AF | AF | 1178992400 | 2007-05-12 | Speaking of Rails, there are other options in ... | 286450 | NULL | NULL | 0 |
| 10159729 | EA | EA | 1441206574 | 2015-09-02 | Humans and large livestock (and maybe even pet... | 286450 | NULL | NULL | 0 |

# constraint

{
  "constants": [
    "TRUE"
  ],
  "aggregation_functions": []
}

# output:output

| num_deleted_posts:Int |
|---|
| 3 |

# solution

```sql
SELECT COUNT(1) AS num_deleted_posts
FROM `bigquery-public-data.hacker_news.comments`
WHERE deleted = True
```
