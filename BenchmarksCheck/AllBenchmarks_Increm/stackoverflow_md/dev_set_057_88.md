# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 057

# input:input0

| Name:Str | Price:Str | QTY:Str | CODE:Str |
|---|---|---|---|
| Rope | 3.6 | 35 | 236 |
| Chain | 2.8 | 15 | 237 |
| Paper | 1.6 | 45 | 124 |
| Bottle | 4.5 | 41 | 478 |
| Bottle | 1.8 | 12 | 123 |
| Computer | 1450.75 | 71 | 784 |
| Spoon | 0.7 | 10 | 412 |
| Bottle | 1.3 | 15 | 781 |
| Rope | 0.9 | 14 | 965 |
| Bottle | 5.5 | 30 | 578 |
| Rope | 0.9 | 41 | 965 |
| Apple | 1.3 | 41 | 781 |

# constraint

{
  "constants": [
    "Bottle"
  ],
  "aggregation_functions": []
}

# output:output

| val:Str |
|---|
| 478 |

# solution

```sql
Select t1.Code
From   TABL As t1 Join (
      Select Name, Max(table.QTY) as MaxQTY
      From   TABL
      Where  Name = 'Bottle'
      Group by Name
) As t2
Where t1.QTY = t2.MaxQTY And t1.Name = t2.Name
```
