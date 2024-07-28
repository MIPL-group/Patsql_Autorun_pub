# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 002

# input:input0

| ID:Str | NAME:Str | EMAIL:Str |
|---|---|---|
| 1 | John | asd@asd.com |
| 2 | Sam | asd@asd.com |
| 3 | Tom | asd@asd.com |
| 4 | Bob | bob@asd.com |
| 5 | Tom | asd@asd.com |
| 6 | John | asd@asd.com |
| 7 | John | abc@asd.com |

# constraint

{
  "constants": [
    "1"
  ],
  "aggregation_functions": []
}

# output:output

| NAME:Str | EMAIL:Str | count:Str |
|---|---|---|
| Tom | asd@asd.com | 2 |
| John | asd@asd.com | 2 |

# solution

```sql
SELECT
    NAME,
    EMAIL,
    count(ID) 
FROM
    input1 
GROUP BY
    NAME,
    EMAIL 
HAVING
    count(ID) > 1 
ORDER BY
    NAME DESC
```
