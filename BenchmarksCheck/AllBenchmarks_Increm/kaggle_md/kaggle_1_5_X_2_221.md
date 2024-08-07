# Source: PATSQL-Kaggle
## Group: kaggle
### ID: 1_5_X_2

# input:taxi_trips

| unique_key:Str | taxi_id:Str | trip_start_timestamp:Date | trip_end_timestamp:Date | trip_seconds:Int | trip_miles:Dbl | pickup_census_tract:Int | dropoff_census_tract:Int | pickup_community_area:Int | dropoff_community_area:Int | fare:Dbl | tips:Dbl | tolls:Dbl | extras:Dbl | trip_total:Dbl | payment_type:Str | company:Str | pickup_latitude:Dbl | pickup_longitude:Dbl | pickup_location:Str | dropoff_latitude:Dbl | dropoff_longitude:Dbl | dropoff_location:Str |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ade155d8f730a13006affc42f26dbd82b0d83ea9 | f3e1a9085537bee3447c67580b4d30b827f97b8a3fa638d276e60d6798bb9a677a8ac6875a6f05e992831e09dcee103c00426846179e320fcf7727522b6c7a1f | 2017-07-12 | 2017-07-12 | 480 | 0.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | Chicago Elite Cab Corp. | NULL | NULL | NULL | NULL | NULL | NULL |
| ade155d8f730a13006affc42f26dbd82b0d83ea9 | f3e1a9085537bee3447c67580b4d30b827f97b8a3fa638d276e60d6798bb9a677a8ac6875a6f05e992831e09dcee103c00426846179e320fcf7727522b6c7a1f | 2017-07-13 | 2017-07-13 | 480 | 0.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | Chicago Elite Cab Corp. | NULL | NULL | NULL | NULL | NULL | NULL |
| ade155d8f730a13006affc42f26dbd82b0d83ea9 | f3e1a9085537bee3447c67580b4d30b827f97b8a3fa638d276e60d6798bb9a677a8ac6875a6f05e992831e09dcee103c00426846179e320fcf7727522b6c7a1f | 2017-06-11 | 2017-06-11 | 480 | 0.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | Chicago Elite Cab Corp. | NULL | NULL | NULL | NULL | NULL | NULL |
| ade155d8f730a13006affc42f26dbd82b0d83ea9 | f3e1a9085537bee3447c67580b4d30b827f97b8a3fa638d276e60d6798bb9a677a8ac6875a6f05e992831e09dcee103c00426846179e320fcf7727522b6c7a1f | 2016-06-12 | 2016-06-12 | 480 | 0.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | Chicago Elite Cab Corp. | NULL | NULL | NULL | NULL | NULL | NULL |
| ade155d8f730a13006affc42f26dbd82b0d83ea9 | f3e1a9085537bee3447c67580b4d30b827f97b8a3fa638d276e60d6798bb9a677a8ac6875a6f05e992831e09dcee103c00426846179e320fcf7727522b6c7a1f | 2018-07-13 | 2018-07-13 | 480 | 0.0 | NULL | NULL | NULL | NULL | 9.05 | 1.81 | 0.0 | 0.0 | 10.86 | Credit Card | Chicago Elite Cab Corp. | NULL | NULL | NULL | NULL | NULL | NULL |

# constraint

{
  "constants": [
    "2017"
  ],
  "aggregation_functions": []
}

# output:output

| month:Int | num_trips:Int |
|---|---|
| 6 | 1 |
| 7 | 2 |

# solution

```sql
SELECT EXTRACT(MONTH FROM trip_start_timestamp) AS month, 
       COUNT(1) AS num_trips
FROM `bigquery-public-data.chicago_taxi_trips.taxi_trips`
WHERE EXTRACT(YEAR FROM trip_start_timestamp) = 2017
GROUP BY month
ORDER BY month
```
