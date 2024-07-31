# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 024

# input:input0

| id:Str | date:Str | Product:Str | Sales:Str |
|---|---|---|---|
| 1245 | 01/04/2013 | Toys | 1000 |
| 1245 | 01/04/2013 | Toys | 2000 |
| 1231 | 01/02/2013 | Bicycle | 50000 |
| 456461 | 01/01/2014 | Bananas | 4546 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| mon:Str | yyyy:Str | sales:Str | product:Str |
|---|---|---|---|
| Apr | 2013 | 3000 | Toys |
| Feb | 2013 | 50000 | Bicycle |
| Jan | 2014 | 4546 | Bananas |

# solution

```sql
select to_char(date,'Mon') as mon,
       extract(year from date) as yyyy,
       sum("Sales") as "Sales"
from yourtable
group by 1,2
```
