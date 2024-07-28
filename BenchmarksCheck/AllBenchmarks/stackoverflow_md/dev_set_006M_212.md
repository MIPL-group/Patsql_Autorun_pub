# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 006M

# input:t

| message_id:Str | conversation_id:Str | from_user:Str | timestamp:Str | message:Str |
|---|---|---|---|---|
| 6 | 1743 | yyy | 999 | message |
| 2 | 145 | xxx | 10000 | message |
| 7 | 14 | bbb | 899 | message |
| 8 | 14 | bbb | 799 | message |
| 1 | 145 | xxx | 9000 | message |
| 5 | 1743 | me | 1200 | message |
| 3 | 14 | ccc | 899 | message |
| 4 | 14 | aaa | 899 | message |

# constraint

{
  "constants": [
    "me"
  ],
  "aggregation_functions": []
}

# output:output

| c1:Str | c2:Str | c3:Str | c4:Str | c5:Str |
|---|---|---|---|---|
| 2 | 145 | xxx | 10000 | message |
| 6 | 1743 | yyy | 999 | message |
| 7 | 14 | bbb | 899 | message |

# solution

```sql
SELECT 
    m.message_timestamp, 
    m.message_id, 
    m.message_text,
    m.message_conversationId
FROM 
    ( SELECT message_conversationId         -- for every conversation
      FROM messages as m
      WHERE message_from <> 'me'            
      GROUP BY message_conversationId
    ) AS mc
  JOIN 
    messages AS m                           -- join to the messages
      ON  m.message_id =        
          ( SELECT mi.message_id            -- and find one message id
            FROM messages AS mi
            WHERE mi.message_conversationId      -- for that conversation
                  = mc.message_conversationId
              AND mi.message_from <> 'me'
            ORDER BY mi.message_timestamp DESC,  -- according to the
                     mi.message_id DESC          -- specified order
            LIMIT 1                              -- (this is the one part)
          )
```
