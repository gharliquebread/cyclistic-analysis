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
As a result, my analysis only covers the months January - May and October - December. I had tried to analyze the data in RStudio Cloud, but I encountered a similar issue
with file size. Because I was using RStudio Cloud and a free account, the data quickly ate up my alotment of 1GB of RAM, and the program would crash, losing all my progress.

In a future project, I would like to reanalyze the data in RStudio - using the desktop version - to include the data in the summer months, which also had the most ridership.

## Preparing, Processing, and Analyzing the Data
To see my process and SQL code, navigate to the other files of this project:
* [Prepare and Process](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Prepare%20and%20Process.md)
* [SQL Analysis](https://github.com/gharliquebread/cyclistic-analysis/blob/main/SQL%20Analysis.md)

In addition to the issues of RStudio Cloud crashing when I uploaded the data, I decided to use BigQuery SQL because the tables were structured the same way. I determined that the questions I wanted to ask involved relatively simple calcuations and that much of my analysis would come from seeing the data plotted visually. Therefore, I chose SQL because I could easily combine and clean the data and run queries to return high-level data to inform my visualizations.

Further, BigQuery allowed me to connect my data to Data Studio to create visualizations. My data was too large to download and then reupload to Tableau, but in a future project, I would like to use Tableau to reflect the data because I ran into some limitations with Data Studio, such as my column `trip_duration` not tranferring over because it is an interval data type.

## Visualizations and Final Analysis
I created a series of visualizations in Google Data Studio, which you can view as a PDF [here](https://github.com/gharliquebread/cyclistic-analysis/files/8209943/Cyclistic_Bike_Share_Analysis__Capstone_Case_Study_Daphne.Letherer.pdf).

If you have a Data Studio account, you can view the live report [here](https://datastudio.google.com/reporting/448956ec-d113-4b1b-816f-09b418c1f2fa).

To review my final analysis and recommendations, navigate to the other files of this project:
* [Data Studio Analysis](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Data%20Studio%20Analysis.md)
* [Conclusions and Recommendations](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Conclusions%20and%20Recommendations.md)

## Wrap-Up
In addition to the code provided in the Preparing, Processing, and Analyzing phases of this project, I have included the code that ended up not being used for the final analysis as well as attempted code that I did not manage to run properly, which you can review below:
* [Additional SQL Code](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Additional%20SQL%20Code.md)
