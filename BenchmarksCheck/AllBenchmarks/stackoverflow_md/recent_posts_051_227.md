# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 051

# input:input1

| Isbn_id:Str | Author:Str |
|---|---|
| 9780195153446 | mark p. o. morford |
| 9780195153446 | robert j. lenardon |
| 9780374157067 | gina kolata |

# input:input0

| isbn:Str | title:Str |
|---|---|
| 9780195153446 | classical |
| 9780374157067 | flu: the stor |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| isbn:Str | title:Str | author:Str |
|---|---|---|
| 9780195153446 | classical | mark p. o. morford, robert j. lenardon |
| 9780374157067 | flu: the stor | gina kolata |

# solution

```sql
Select a.isbn, a.title, group_concat(b.author )
from Book_title, 
INNER JOIN Book_authoron a.isbn = b.isbn_id
group by a.isbn, a.title
```
