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

# Conclusions and Recommendations
Casual riders differ from member riders in the following ways:

**Trip Duration + Time**
- Longer trips
- Ride frequency increases at a greater rate in the summer months than member rides increase *

**Bike Type**
- Use docked bikes for 14.14% of rides

**Trip Location**
- Strong preference for the station at Streeter Dr & Grand Ave, accounting for 75.96% of casual rides
- The most popular stations also had the highest percentage of docked bike usage
   
   
## Recommendations + Next Steps:
- Determine incentive for annual memberships and docked bikes.
- Collect data on why members take shorter trips and casual riders take shorter trips.
- Collect data on where riders live.
        For example, do tourists make up a large portion of casual riders? 
        Are there shorter membership options that would appeal to tourists withou an annual commitment?)
- Determine if certain days of the week are more popular among casual riders vs members.
        For example, if weekends are significantly more popular for casual riders, consider offering a weekend-oriented membership plan.
- Consider analysing where docked bikes are located and on average how many of each type of bike is located at each station.
- Analyze whether casual riders are more likely than members to ride in summer months.
