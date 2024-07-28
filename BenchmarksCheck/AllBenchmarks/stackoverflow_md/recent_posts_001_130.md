# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 001

# input:input0

| id_invitation:Str | id_demand:Str | partner_company:Str | concurrent_company:Str |
|---|---|---|---|
| 1 | 1 | google | facebook |
| 2 | 1 | NULL | linkedin |
| 3 | 2 | google | NULL |
| 4 | 2 | NULL | yahoo |
| 5 | 3 | google | NULL |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Company:Str | id_demand:Str |
|---|---|
| facebook | 1 |
| google | 1 |
| google | 2 |
| google | 3 |
| linkedin | 1 |
| yahoo | 2 |

# solution

```sql
select partner_company , id_demand
From invitation 
Where partner_company is not null
Union All
select concurrent_company , id_demand
From invitation 
Where concurrent_company is not null
```
