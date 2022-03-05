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
    
