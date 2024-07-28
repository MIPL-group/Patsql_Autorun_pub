# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 047M

# input:PRODUCT

| PRO_ID:Str | PRO_Date:Str | PRO_Price:Str |
|---|---|---|
| 123 | 01/01/2016 | 2000 |
| 123 | 02/01/2016 | 2500 |
| 123 | 03/01/2016 | 1500 |
| 123 | 05/01/2016 | 3000 |
| 456 | 01/01/2016 | 2000 |
| 456 | 02/01/2016 | 2500 |
| 456 | 03/01/2016 | 1500 |
| 456 | 05/01/2016 | 3000 |
| 456 | 06/01/2016 | 3500 |
| 456 | 07/01/2016 | 3600 |

# constraint

{
  "constants": [
    "06/01/2016",
    "2"
  ],
  "aggregation_functions": []
}

# output:output

| PRO_ID:Str | Last_PRO_Date:Str | Second_Last_PRO_Date:Str |
|---|---|---|
| 123 | 05/01/2016 | 03/01/2016 |
| 456 | 06/01/2016 | 05/01/2016 |

# solution

```sql
select PRO_ID, MAX(PRODUCT.PRO_DATE) as Last_PRO_Date, max(t1.PRO_DATE) as Second_Last_PRO_Date
from PRODUCT
join (
  select PRO_ID, PRO_DATE, rank() over (partition by PRO_ID order by PRO_DATE desc) as seqnum
  from PRODUCT
  where PRODUCT.PRO_DATE <= DATE '2016-06-01'
) t1 USING (PRO_ID)
where PRODUCT.PRO_DATE <= DATE '2016-06-01' and seqnum = 2
group by PRO_ID
```
