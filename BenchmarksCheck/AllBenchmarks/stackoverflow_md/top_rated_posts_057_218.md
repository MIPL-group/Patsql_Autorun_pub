# Source: PATSQL-StackOverflow
## Group: top_rated_posts
### ID: 057

# input:input0

| ID:Str | Name:Str | City:Str | Birthyear:Str |
|---|---|---|---|
| 1 | Egon Spengler | New York | 1957 |
| 2 | Mac Taylor | New York | 1955 |
| 3 | Sarah Connor | Los Angeles | 1959 |
| 4 | Jean-Luc Picard | La Barre | 2305 |
| 5 | Ellen Ripley | Nostromo | 2092 |
| 6 | James T. Kirk | Riverside | 2233 |
| 7 | Henry Jones | Chicago | 1957 |
| 8 | Henry Jones2 | Chicago | 1960 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Name:Str | City:Str | Birthyear:Str |
|---|---|---|
| Mac Taylor | New York | 1955 |
| Sarah Connor | Los Angeles | 1959 |
| Jean-Luc Picard | La Barre | 2305 |
| Ellen Ripley | Nostromo | 2092 |
| James T. Kirk | Riverside | 2233 |
| Henry Jones | Chicago | 1957 |

# solution

```sql
SELECT
    T0.Name,
    T1.City,
    T0.Birthyear 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            City,
            min(Birthyear) AS min_Birthyear 
        FROM
            input1 
        GROUP BY
            City
    ) AS T1 
        ON T1.City = T0.City 
        AND T1.min_Birthyear = T0.Birthyear
```
