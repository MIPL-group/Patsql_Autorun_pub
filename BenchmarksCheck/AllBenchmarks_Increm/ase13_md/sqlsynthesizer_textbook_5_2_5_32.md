# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_5

# input:input1

| sid:Str | sname:Str |
|---|---|
| S1 | SN1 |
| S2 | SN2 |
| S3 | SN3 |
| S4 | SN4 |

# input:input0

| sid:Str | part_key:Str | cost:Dbl |
|---|---|---|
| S1 | P1 | 4 |
| S2 | P1 | 2 |
| S1 | P2 | 4 |
| S2 | P2 | 2 |
| S3 | P2 | 3 |
| S3 | P3 | 4 |
| S1 | P4 | 2 |
| S4 | P3 | 6 |
| S2 | P5 | 4 |
| S3 | P5 | 2 |
| S3 | P6 | 4 |
| S1 | P7 | 2 |
| S2 | P8 | 4 |
| S4 | P9 | 4 |
| S3 | P9 | 6 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| part_key:Str | sname:Str |
|---|---|
| P1 | SN1 |
| P2 | SN1 |
| P3 | SN4 |
| P5 | SN2 |
| P9 | SN3 |

# solution

```sql
// who charge more for some part than the average cost of that part (averaged over all the suppliers who supply that part).
```
