# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 2_2_X_3

# input:taxi_trips

| unique_key:Str | taxi_id:Str | trip_start_timestamp:Date | trip_end_timestamp:Date | trip_seconds:Int | trip_miles:Dbl | pickup_census_tract:Int | dropoff_census_tract:Int | pickup_community_area:Int | dropoff_community_area:Int | fare:Dbl | tips:Dbl | tolls:Dbl | extras:Dbl | trip_total:Dbl | payment_type:Str | company:Str | pickup_latitude:Dbl | pickup_longitude:Dbl | pickup_location:Str | dropoff_latitude:Dbl | dropoff_longitude:Dbl | dropoff_location:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| unique_key_0 | taxi_id_0 | 2017-04-30 23:59 | 2017-05-01  0:00 | 60 | 0.0 | NULL | NULL | NULL | NULL | 5.00 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |
| unique_key_1 | taxi_id_0 | 2017-05-01  0:00 | 2017-05-01  0:30 | 1800 | 2.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 12.34 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |
| unique_key_2 | taxi_id_1 | 2017-05-01  0:00 | 2017-05-01  0:30 | 1800 | 2.0 | NULL | NULL | 1 | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 12.34 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |
| unique_key_3 | taxi_id_2 | 2017-05-01  0:00 | 2017-05-01  0:30 | 1800 | 2.0 | NULL | NULL | 1 | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 12.34 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |
| unique_key_4 | taxi_id_1 | 2017-05-01  1:00 | 2017-05-01  1:30 | 1800 | 2.0 | NULL | NULL | 1 | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 12.34 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |
| unique_key_5 | taxi_id_0 | 2017-05-02  0:00 | 2017-05-02  0:01 | 60 | 0.0 | NULL | NULL | NULL | NULL | 5.00 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | company1 | NULL | NULL | NULL | NULL | NULL | NULL |

# constraint

{
  "constants": [
    "2017-05-01"
  ],
  "aggregation_functions": []
}

# output:output

| taxi_id:Str | trip_start_timestamp:Str | trip_end_timestamp:Str | prev_break:Str |
|---|---|---|---|
| taxi_id_0 | 2017-05-01 00:00:00 | 2017-05-01 00:30:00 | NULL |
| taxi_id_1 | 2017-05-01 00:00:00 | 2017-05-01 00:30:00 | NULL |
| taxi_id_1 | 2017-05-01 01:00:00 | 2017-05-01 01:30:00 | 30 |
| taxi_id_2 | 2017-05-01 00:00:00 | 2017-05-01 00:30:00 | NULL |

# solution

```sql
-- prev_break is CAST(EXTRACT(EPOCH FROM trip_start_timestamp) - EXTRACT(EPOCH FROM LAG(trip_end_timestamp, 1) OVER (PARTITION BY taxi_id ORDER BY trip_start_timestamp)) AS bigint) / 60 in PostgreSQL
SELECT taxi_id,
    trip_start_timestamp,
    trip_end_timestamp,
    TIMESTAMP_DIFF(
        trip_start_timestamp,
        LAG(trip_end_timestamp, 1) OVER (PARTITION BY taxi_id ORDER BY trip_start_timestamp),
        MINUTE) as prev_break
FROM `bigquery-public-data.chicago_taxi_trips.taxi_trips`
WHERE DATE(trip_start_timestamp) = '2017-05-01'
```
