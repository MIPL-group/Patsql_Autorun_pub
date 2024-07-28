# Source: PATSQL-ASE13
## Group: sqlsynthesizer
### ID: textbook_5_2_3

# input:input1

| part_id:Str | color:Str |
|---|---|
| P1 | red |
| P2 | green |
| P3 | yellow |
| P4 | red |
| P5 | green |
| P6 | yellow |
| P7 | red |

# input:input0

| supplier_key:Str | part_id:Str |
|---|---|
| S1 | P1 |
| S1 | P4 |
| S1 | P7 |
| S2 | P1 |
| S2 | P3 |
| S3 | P1 |
| S4 | P4 |
| S5 | P1 |
| S5 | P2 |
| S5 | P4 |
| S5 | P7 |
| S6 | P5 |
| S7 | P6 |
| S7 | P1 |
| S7 | P1 |
| S7 | P3 |
| S7 | P7 |
| S8 | P1 |
| S8 | P4 |
| S8 | P6 |
| S8 | P7 |

# constraint

{
  "constants": [
    "red"
  ],
  "aggregation_functions": []
}

# output:output

| sname:Str |
|---|
| S1 |
| S5 |
| S8 |

