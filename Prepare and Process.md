# Preparing and Processing the Divvy Trip Data
I downloaded and unzipped the following files from [Divvy Bike's trip data](https://divvy-tripdata.s3.amazonaws.com/index.html):
* 202101-divvy-tripdata
* 202102-divvy-tripdata
* 202103-divvy-tripdata
* 202104-divvy-tripdata
* 202105-divvy-tripdata
* 202111-divvy-tripdata
* 202112-divvy-tripdata

I did download the data for the missing months June - October, but the data was too large to work with in BigQuery. Therefore I only used the files listed above.

To start, I previewed the .csv's in Microsoft Excel. The data for each month was too large to easily manipulate in Excel, so I uploaded each sheet to BigQuery under a dataset I named "divvy_bike_share". Once I uploaded the tables, I previewed each table's schema. Each 2021 table has the same scheme, so I did not need to rename or join any tables.

Given that each table had the same schema, I combined all tables into one inclusive table. I also made the following modifications to the table's structure:
* I seperated out the `started_at` and `ended_at` columns to be individual date and time columns. --> New column `start_time`, `start_date`, `end_time`, `end_date`
* I combined the latitude and longitude columns. (I did this because geo latitude and longitude data in Data Studio is combined and not separated.) --> New column `start_map` and `end_map`
* Probably most importantly, I created a trip duration column by subtracting `start_time` from `end_time`. --> New column `trip_duration`
* I considered removing some extranneous columns, but ended up leaving each column in since I learned I would not be able to donwload the data as a .csv anyways, because it was still too big, even with columns removed.

```sql
SELECT
  *,
  CAST (started_at AS date) AS start_date,
  CAST (started_at AS time) AS start_time,
  CAST (ended_at AS date) AS end_date,
  CAST (ended_at AS time) AS end_time,
  CAST (ended_at AS time) AS end_time,
  CONCAT(start_lat, ", ", start_lng) AS start_map,
  CONCAT(end_lat, ", ", end_lng) AS end_map,
  (end_time - start_time) AS trip_duration
FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_01`
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_2021_02` 
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_2021_03`
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_2021_04`
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_05`
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_2021_11`
        UNION ALL
        SELECT * FROM `project.divvy_bike_share.divvy_trips_2021_12`
```
*Note that this is the final version of all changes made. In reality, I made several amendments and tried creating more condensed tables with certain information,
such as a table that only contains trip location information. While this was a good exercise in writing queries, I did not end up using these smaller tables in my
final analysis. *

Station names contained many null values, so I wrote a query to determine if missing names had a non-null `station_id` that could be used to fill in the blanks for missing data. After running the code below, however, all station names with null values also had null station IDs.
```sql
SELECT 
    DISTINCT(start_station_id),
    start_station_name
    
     FROM `level-harbor-337222.divvy_bike_share.divvy_trips_2021_11` 
    WHERE start_station_name is null
``` 
From here, I was able to query all of the data to pull answers to questions such as 'How many rideable types are there?' and count null values.

```sql
SELECT
   DISTINCT(rideable_type)

FROM `project.divvy_bike_share.divvy_2021_all`
```
```sql
SELECT
   DISTINCT(member_casual)

FROM `project.divvy_bike_share.divvy_2021_all`
```
```sql
SELECT
   DISTINCT(start_station_name)

FROM `project.divvy_bike_share.divvy_2021_all`
```
And so on.

## Creating Average Trip Duration Tables for Data Studio
I created my visualizations in Data Studio and to include visualizations reflecting average trip durations of members vs casual riders, I ended up creating two additional tables that calculated the average trip duration by month:

**Casual Average Trip Duration by Month**
```sql
SELECT
   EXTRACT( month FROM start_date) AS trip_month,
    AVG(trip_duration) AS avg_trip_duration

FROM `project.divvy_bike_share.divvy_2021_all`

WHERE
    member_casual = "casual"
GROUP BY 
    trip_month

ORDER BY 
    trip_month
```
**Member Average Trip Duration by Month**
```sql
SELECT
   EXTRACT( month FROM start_date) AS trip_month,
    AVG(trip_duration) AS avg_trip_duration

FROM `project.divvy_bike_share.divvy_2021_all`

WHERE
    member_casual = "member"
GROUP BY 
    trip_month

ORDER BY 
    trip_month
```
## Processing the Data - Road Bumps
What I was unable to accomplish that would have strengthened the analysis:
* Reflect on which day of the week the ride occurred.
* Write queries that reflect calculations filtered by metric.
*   Ex. Total count of member trips by rideable type AND total count of casual trips by rideable type.
*   When I attempted to write these queries, the error code "Scalar subquery produced more than one element" was returned.
*   See Additional SQL code for my attempts at creating these kinds of tables.

```
