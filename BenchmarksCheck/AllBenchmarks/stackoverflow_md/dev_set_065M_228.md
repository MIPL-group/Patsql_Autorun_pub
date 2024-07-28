# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 065M

# input:input2

| id_orden:Str | edo:Str |
|---|---|
| 1 | 23 |
| 1 | 22 |
| 1 | 21 |
| 2 | 22 |
| 2 | 21 |

# input:input1

| id_usuario:Str | name:Str | phone:Str |
|---|---|---|
| 2 | abc | 999 |
| 1 | def | 888 |

# input:input0

| id_orden:Str | date:Str | total:Str | id_usuario:Str |
|---|---|---|---|
| 1 | 15-may | 50 | 2 |
| 2 | 20-may | 60 | 1 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| id_orden:Str | date:Str | total:Str | name:Str | phone:Str | maxedo:Str |
|---|---|---|---|---|---|
| 1 | 15-may | 50 | abc | 999 | 23 |
| 2 | 20-may | 60 | def | 888 | 22 |

# solution

```sql
Select a.id_orden, a.date, a.total, a.id_usuario, a.name, a.phone, b.maxestado
From (Select o.id_orden, o.date, o.total, o.id_usuario, u.name, u.phone 
From ordenes o Inner Join usuario u
On o.id_usuario = u.id_usuario ) a 
Join (Select id_orden, max(edo) maxestado
From estado
Group By id_orden) b
On a.id_orden = b.id_orden;
```
