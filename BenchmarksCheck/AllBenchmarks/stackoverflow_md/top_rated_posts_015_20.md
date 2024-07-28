# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 015

# input:input0

| Id:Str | Value:Str | ColumnName:Str |
|---|---|---|
| 1 | John | FirstName |
| 1 | 2.4 | Amount |
| 1 | ZH1E4A | PostalCode |
| 1 | Fork | LastName |
| 1 | 857685 | AccountNumber |

# constraint

{
  "constants": [
    "Amount",
    "PostalCode",
    "FirstName",
    "LastName",
    "AccountNumber"
  ],
  "aggregation_functions": []
}

# output:output

| FirstName:Str | Amount:Str | PostalCode:Str | LastName:Str | AccountNumber:Str |
|---|---|---|---|---|
| John | 2.4 | ZH1E4A | Fork | 857685 |

# solution

```sql
select fn.value as FirstName,
  a.value as Amount,
  pc.value as PostalCode,
  ln.value as LastName,
  an.value as AccountNumber
from yourtable fn
left join yourtable a
  on fn.somecol = a.somecol
  and a.columnname = 'Amount'
left join yourtable pc
  on fn.somecol = pc.somecol
  and pc.columnname = 'PostalCode'
left join yourtable ln
  on fn.somecol = ln.somecol
  and ln.columnname = 'LastName'
left join yourtable an
  on fn.somecol = an.somecol
  and an.columnname = 'AccountNumber'
where fn.columnname = 'Firstname'
```
