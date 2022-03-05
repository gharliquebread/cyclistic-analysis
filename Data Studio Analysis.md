# Creating Visualizatoins and Conducting Further Analysis - Data Studio
I exported my data from BigQuery to Data Studio. I was able to further explore my data by creating various charts, which allowed me to quickly identify trends.

The attached PDF includes the final version of my visualizations, accompanied with conclusions:
[Cyclistic_Bike_Share_Analysis__Capstone_Case_Study.pdf](https://github.com/gharliquebread/cyclistic-analysis/files/8191517/Cyclistic_Bike_Share_Analysis__Capstone_Case_Study.pdf)

The report does not include notes on my data or modifications, which I have instead tracked in this project.

## Notes on Data Studio

Data Studio did not recognize the interval data, so I was uanble to create visualzations with my `trip_duration` column. To remedy this, I created additional tables in 
BigQuery to show average trip duration in Data Studio.

I did not find how to update the data labels, which I suspect has to do with the original data itself. A final version of thsi report would show labels in proper case and without
underscores.

I created a heat map, for which reason I combined the latitude and longitude columns, but I did not include it in my final report, finding that the most popular stations themselves
provided more insightful data - though the map was fun to look at!

My final charts did not include filters because I could not find a clean way to include them, but I would like to explore more interactive visualizations further in Data Studio
or Tableau.

## Cyclistic Bike Share Analysis: Capstone Case Study Data Studio Report
<img width="912" alt="01  Overview" src="https://user-images.githubusercontent.com/100979159/156901018-4cc655aa-a69c-4159-be10-3fd8aad84c06.PNG">
<img width="908" alt="02  Ride Frequency" src="https://user-images.githubusercontent.com/100979159/156901025-5e7d46e5-9d47-4c83-a1fb-dee164ed6f3b.PNG">
<img width="913" alt="03  Ride Frequncy - Further Questions" src="https://user-images.githubusercontent.com/100979159/156901029-b402f611-5842-4ee5-9169-cb283fea7ada.PNG">
<img width="905" alt="04  Ride Duration" src="https://user-images.githubusercontent.com/100979159/156901030-9ead9758-0aa4-4c04-8c87-37e30d0b8669.PNG">
<img width="913" alt="05  Ride Type" src="https://user-images.githubusercontent.com/100979159/156901031-c1cd6ad8-2ef1-418c-9f6b-724a331c14ce.PNG">
<img width="910" alt="06  Station Preference" src="https://user-images.githubusercontent.com/100979159/156901061-95c4cfad-40b8-4cfe-9dfa-c0cba242d615.PNG">
<img width="906" alt="07  Station Preference Cont" src="https://user-images.githubusercontent.com/100979159/156901062-883c79e3-e0c4-463e-893c-6f09cb126840.PNG">
<img width="911" alt="07  Station Preference + Rideable Type" src="https://user-images.githubusercontent.com/100979159/156901033-69e44aed-c23e-4648-b3de-1193215de86d.PNG">
<img width="914" alt="08  Ride Frequency + Rideable Type" src="https://user-images.githubusercontent.com/100979159/156901034-8ed6a4f1-d8dd-414d-91bb-e6ed4832f8fe.PNG">
