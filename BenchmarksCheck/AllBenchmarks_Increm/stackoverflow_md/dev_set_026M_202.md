# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 026M

# input:input0

| acct_id:Str | Bill_Id:Str | Bill_dt:Str | alt_bill_id:Str |
|---|---|---|---|
| 12345 | 123451 | 2014-01-02 | 101 |
| 12345 | 123452 | 2014-01-02 | 102 |
| 12346 | 123461 | 2014-01-02 | 103 |
| 12347 | 123470 | 2014-01-02 | 102 |
| 12347 | 123471 | 2014-01-02 | 101 |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| acct_id:Str | Bill_Id:Str | Bill_dt:Str | alt_bill_id:Str |
|---|---|---|---|
| 12345 | 123452 | 2014-01-02 | 102 |
| 12346 | 123461 | 2014-01-02 | 103 |
| 12347 | 123470 | 2014-01-02 | 102 |

# solution

```sql
SELECT
    T1.acct_id,
    T0.Bill_Id,
    T0.Bill_dt,
    T0.alt_bill_id 
FROM
    input1 AS T0 
JOIN
    (
        SELECT
            acct_id,
            max(alt_bill_id) AS max_alt_bill_id 
        FROM
            input1 
        GROUP BY
            acct_id
    ) AS T1 
        ON T1.acct_id = T0.acct_id 
        AND T1.max_alt_bill_id = T0.alt_bill_id 
ORDER BY
    T1.acct_id ASC
```
