# Cyclistic Bike-Share: How Does a Bike Share Navigate Speedy Success?
Bike Share Case Study for Google Data Analytics Capstone project
March 2022
Tools used: BigQuery Sandbox (SQL), Data Studio

## Background
**Driving question: How do annual members and casual riders use Cyclistic bikes differently?**
Cyclistic Bike-Share wants to increase member subscriptions for their services because annual members are more profitable than casual riders. 
Therefore they would like to know how member and casual riders use Cyclistic services differently. The results from this analysis may be used to guide future 
marketing programs to increase member subscriptions.

## The Data - Divvy Bike Share
The data for this project comes from Divvy Bikes, given that Cyclistic is a fictional company. I retrieved 2021 data from [Divvy trip data](https://divvy-tripdata.s3.amazonaws.com/index.html), which is available by Motivate International Inc. under [this license](https://ride.divvybikes.com/data-license-agreement).


**A Note on the Data**
Although I downloaded all files for 2021, the .csv files for the months of June - September were too large to use in BigQuery with my Sandbox account.
As a result, my analysis only covers the months January - May and October - December. I had tried to analyze the data in RStudio CLoud, but I encountered a similar issue
with file size. Because I was using RStudio Cloud and a free account, the data quickly ate up my alotment of 1GB of RAM, and the program would crash, losing all my progress.

In a future project, I would like to reanalyze the data in RStudio - using the desktop version - to include the data in the summer months, which also had the most ridership.

# Preparing, Processing, and Analyzing the Data
To see my process and SQL code, navigate to the other files of this project.

In addition to the issues of RStudio Cloud crashing when I uploaded the data, I decided to use BigQuery SQL because the tables were structered the same way. I determined that the questions I wanted to ask involved relatively simple calcuations and that much of my analysis would come from seeing the data plotted visually. Therefore, I chose SQL because I could easily combine and clean the data and run queries to return high-level data to inform my visualizations.

Further, BigQuery allowed me to connect my data to Data Studio to create visualizations. My data was too large to download and then reupload to Tableau, but in a future project, I would like to use Tableau to reflect the data because I ran into some limitations with Data Studio, such as my column `trip_duration` not tranferring over because it is an interval data type.
