# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 037X

# input:input0

| Region:Str | Area:Str | StartDate:Str | EndDate:Str |
|---|---|---|---|
| A | 1 | 01/01/2016 | 03/31/2016 |
| A | 1 | 04/01/2016 | 05/31/2016 |
| A | 1 | 07/01/2016 | 09/30/2016 |
| A | 1 | 10/01/2016 | 01/31/2017 |
| A | 1 | 02/01/2017 | 12/31/2017 |
| B | 2 | 01/01/2016 | 04/30/2016 |
| B | 2 | 05/01/2016 | 09/30/2016 |
| A | 4 | 01/01/2016 | 05/31/2016 |
| A | 4 | 06/01/2016 | 12/31/2016 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| Region:Str | Area:Str | StartDate:Str | EndDate:Str |
|---|---|---|---|
| A | 1 | 01/01/2016 | 05/31/2016 |
| A | 1 | 07/01/2016 | 12/31/2017 |
| B | 2 | 01/01/2016 | 09/30/2016 |
| A | 4 | 01/01/2016 | 12/31/2016 |

