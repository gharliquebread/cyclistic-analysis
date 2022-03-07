# Additional SQL Code
The code provided below are queries I ran but did not end up using for my analysis. Ultimately, the code below helped me practice writing queries, and I got to better understand the data. Further, it helped me reframe my questions and how I approached them, letting me reach a more concise and meaningful analysis.

**Previous:** [Conclusions and Recommendations](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Conclusions%20and%20Recommendations.md)

**Top:** [README/Overview](https://github.com/gharliquebread/cyclistic-analysis/blob/main/README.md)


**Creating temporary tables using WITH**
I did not end up using this because I combined all of the data into one comprehensive table instead.
```sql
WITH 
    casual_rider AS (
        SELECT *
        FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_01`
            UNION ALL
            SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_02` 
            UNION ALL
            SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_03`
        WHERE
            member_casual = "casual"
            ),

    member_rider AS (
    SELECT *
        FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_01`
            UNION ALL
            SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_02` 
            UNION ALL
            SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_03`
        WHERE
            member_casual = "member"    
            ),

    station_names AS (
        SELECT
            DISTINCT(start_station_name)
        FROM 
            (SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_01`
                UNION ALL
                SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_02` 
                UNION ALL
                SELECT * FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_03`
            )
        WHERE
            start_station_name is not null
        ORDER BY 
            start_station_name ASC
            )
```            

**Rideable Types - Counting Use**
```sql
SELECT
   rideable_type,
   COUNT(rideable_type) AS times_used

FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`

GROUP BY 
    rideable_type
```

**Stations - Counting How Many Total**

* Total start stations: 840
* Total end stations: 839
```sql
SELECT
    COUNT(DISTINCT(start_station_name)) AS number_of_start_stations,
    COUNT(DISTINCT end_station_name) AS number_of_end_stations
FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`
WHERE 

    start_station_name is not null
    OR
    end_station_name is not null 
```

# Failed SQL Code
This section contains some queries that I tried but failed to solve in the end.

**Erros: Scalar query returned more than one element - Nesting and Trying to Pull Data Showing Calcuations Across Rows and Columns**
This was probably the most upsetting failure to me. I hope to find the solution for pulling tables that show calcuations grouped by columns/rows.
```sql
SELECT 
    EXTRACT(MONTH FROM start_date) AS month,
    AVG(trip_duration) AS avg_trip_duration,
    (
        SELECT
            AVG(trip_duration)
        FROM `project.divvy_bike_share.divvy_2021_all`
        WHERE 
            member_casual = "member"
        GROUP BY 
            month
    ) AS avg_member_trip,
    (
        SELECT
            AVG(trip_duration)
        FROM `project.divvy_bike_share.divvy_2021_all`
        WHERE 
            member_casual = "casual"
    ) AS avg_casual_trip
FROM `project.divvy_bike_share.divvy_2021_all`
GROUP BY 
    month
ORDER BY 
    month
```

**Are there any trips where the start and end stations were the same?**

```sql
SELECT
    COUNT(DISTINCT(start_station_name)) AS number_of_start_stations,
    COUNT(DISTINCT end_station_name) AS number_of_end_stations
FROM `project.divvy_bike_share.divvy_2021_all`
WHERE 
    start_station_name is not null
    OR
    end_station_name is not null
```
