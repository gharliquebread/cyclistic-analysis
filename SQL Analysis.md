# Analyzing the Data - SQL
With the data cleaned and explored, it was ready for analysis. I wrote a variety of queries to explore identify trends.

## Question: Is there a difference in trip duration?

Findings:
* Average member rider trip duration: 0:13:17.130500621
* Average casual rider trip duration: 0:34:8.299136219
* Overall, casual riders take longer riders than member riders.

**Calculate Averages**
The code below returns the overall average trip duration for member riders.
*Change "member" to "casual" to return different results.*
```sql
SELECT
    member_casual,
    AVG(trip_duration) AS avg_trip

FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`
GROUP BY 
    member_casual
```
The code below returns the average trip duration for each month for casual riders.
*Change "casual" to "member" to return different results.*
```sql
SELECT
   EXTRACT( month FROM start_date) AS trip_month,
    AVG(trip_duration) AS avg_trip_duration

FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`

WHERE
    member_casual = "casual"
GROUP BY 
    trip_month

ORDER BY 
    trip_month
```

## Question: Is there a difference in stations used?
Station names contained many null values that could not be filled. While all ride counts were included for other questions,
null stations were ommitted from counts and visualizations centered on station names.

Findings:
* Casual and member riders most often used similar stations.
* Casual members have a strong preference for the station at Streeter Dr & Grand Ave, accounting for 75.96% of casual rides.

Most popular starter stations for casual riders:
* Lake Shore Dr & Monroe St, 2388
* Clark St & Elm St, 2133
* Millennium Park, 1921
* Streeter Dr & Grand Ave, 1891
* Dearborn St & Erie St, 1834

Most popular starter stations for member riders:
* Clark St & Elm St, 2844
* Dearborn St & Erie St, 2557
* Kingsbury St & Kinzie St, 2351
* Wells St & Huron St, 2182
* Wells St & Elm St, 2182

**Find the Most Popular Stations**
*Change member_casual to member or casual to show different results.*
*Change between start_station_name and end_station_name to show different results.*
```sql
SELECT 
    start_station_name,
    COUNT(start_station_name) AS times_start_station_used

 FROM `project.divvy_bike_share.divvy_2021_all`

 WHERE 
    member_casual = "member"

GROUP BY 
    start_station_name
ORDER BY 
    times_start_station_used DESC

LIMIT 20
```
## Question: Is there a difference in popularity of types of bikes used?
Findings:
* Member riders never used docked bikes.
* Member riders prefer classic bikes over electric bikes - 58.71% vs 41.29%.
* Casual riders have negligible preference between classic and electric bikes.
* Casual riders used docked bikes 14.14% of the time.

*Change member_casual to member or casual to show different results.
```sql
SELECT
   member_casual,
    (   
        SELECT 
            COUNT(rideable_type)
        FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`
        WHERE
            rideable_type = "classic_bike"
    ) AS classic_bike_rides,
    (
        SELECT 
            COUNT(rideable_type)
        FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`
        WHERE
            rideable_type = "electric_bike"
    ) AS electric_bike_rides,
    (
        SELECT 
            COUNT(rideable_type)
        FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`
        WHERE
            rideable_type = "docked_bike"
    ) AS docked_bike_rides

FROM `level-harbor-337222.divvy_bike_share.divvy_2021_all`

WHERE 
    member_casual = "member"

GROUP BY 
    member_casual
```

**Next:** [Data Studio Analysis](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Data%20Studio%20Analysis.md)

**Previous:** [Prepare and Process](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Prepare%20and%20Process.md)
