# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 030X

# input:item_transactions

| id_type:Str | item_id:Str | qty_sold:Str | price_extended:Str | date_effective:Str |
|---|---|---|---|---|
| invoice | 18117 | 8 | 13.1600 | 2016-10-01 |
| invoice | 17473 | 1 | 2.2500 | 2016-10-01 |
| invoice | 18117 | 1 | 1.0000 | 2016-10-01 |
| invoice | 18117 | 7 | 2.0000 | 2016-10-01 |
| invoice | 18117 | 5 | 3.0000 | 2016-10-01 |
| invoice | 17473 | 3 | 4.0000 | 2016-10-01 |
| invoice | 17568 | 1 | 4.0000 | 2016-10-01 |
| invoice | 17568 | 5 | 3.0000 | 2016-10-01 |
| invoice | 18117 | 8 | 2.0000 | 2016-10-01 |
| invoice | 17473 | 1 | 1.0000 | 2016-10-01 |

# input:i_multiple_int_attributes

| type:Str | id:Str | sort_order:Str | attribute:Str | value:Str |
|---|---|---|---|---|
| items | 17473 | 1 | previous_editions | 15743 |
| items | 17568 | 1 | previous_editions | 3893 |
| items | 17568 | 2 | previous_editions | 7626 |
| items | 18117 | 1 | previous_editions | 14430 |
| items | 18117 | 2 | previous_editions | 17337 |
| items | 18117 | 3 | previous_editions | 17123 |
| items | 18117 | 4 | previous_editions | 17614 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| item_id:Str | current_id_sales:Str | previous_id_sales:Str |
|---|---|---|
| 17473 | 15743 | 9625 |
| 17568 | 3893 | 24232 |
| 18117 | 14430 | 8083 |

# solution

```sql
// this query does not give the desired output
```
