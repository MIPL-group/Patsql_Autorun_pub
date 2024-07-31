# Source: PATSQL-StackOverflow
## Group: recent_posts
### ID: 031

# input:ChatChannels

| channelID:Str | channelName:Str | type:Str |
|---|---|---|
| 0 | Public 0 | public |
| 1 | Public Channel | public |
| 2 | Private Channel | private |
| 3 | Public 2 | public |

# input:ChatChannelMembers

| channelID:Str | accountID:Str | role:Str |
|---|---|---|
| 1 | Bob | 100 |
| 2 | Bob | 100 |
| 3 | Bob | 100 |
| 2 | Dave | 101 |
| 3 | Dave | 101 |
| 0 | Wilma | 100 |
| 1 | Wilma | 100 |
| 2 | Wilma | 100 |
| 3 | Wilma | 100 |

# constraint

{
  "constants": [
    "public",
    "Dave"
  ],
  "aggregation_functions": []
}

# output:output

| channelID:Str | channelName:Str | type:Str |
|---|---|---|
| 0 | Public 0 | public |
| 1 | Public Channel | public |

# solution

```sql
SELECT
    T0.channelID,
    T0.channelName,
    T0.type 
FROM
    ChatChannels AS T0 
LEFT JOIN
    (
        SELECT
            channelID 
        FROM
            ChatChannelMembers 
        WHERE
            accountID = 'Dave'
    ) AS T1 
        ON T0.channelID = T1.channelID 
WHERE
    T0.type = 'public' 
    AND T1.channelID IS NULL 
ORDER BY
    T0.channelID ASC
```
