# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 011

# input:input0

| ID:Str | Name:Str | Value:Str |
|---|---|---|
| 123 | Manufacturer | Dell |
| 123 | Model | Latitude E5450 |
| 456 | Manufacturer | HP |
| 456 | Model | ProBook 450 G3 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| ID:Str | ManufacturerModel:Str |
|---|---|
| 123 | Dell, Latitude E5450 |
| 456 | HP, ProBook 450 G3 |

# solution

```sql
select ID, Name, string_agg(Value, ', ')
from t
group by ID
order by ID
```
