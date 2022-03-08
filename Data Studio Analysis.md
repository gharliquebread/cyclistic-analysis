# Creating Visualizations and Conducting Further Analysis - Data Studio
I exported my data from BigQuery to Data Studio. I was able to further explore my data by creating various charts, which allowed me to quickly identify trends.

The attached PDF includes the final version of my visualizations, accompanied with conclusions:
[Cyclistic Bike Share Capstone - Data Studio](https://github.com/gharliquebread/cyclistic-analysis/files/8209943/Cyclistic_Bike_Share_Analysis__Capstone_Case_Study_Daphne.Letherer.pdf)

If you have a Data Studio account, you can view the live report [here](https://datastudio.google.com/reporting/448956ec-d113-4b1b-816f-09b418c1f2fa).

**Next:** [Conclusions and Recommendations](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Conclusions%20and%20Recommendations.md)

**Previous** [SQL Analysis](https://github.com/gharliquebread/cyclistic-analysis/blob/main/SQL%20Analysis.md)

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
![01  Overview](https://user-images.githubusercontent.com/100979159/157334628-c1b9fcb5-724a-4de0-9036-6f14f27f93fe.png)
![02  Data Processing](https://user-images.githubusercontent.com/100979159/157334630-56978c02-3e8d-4c98-8474-9711f8d36b77.png)
![03  Ride Frequency](https://user-images.githubusercontent.com/100979159/157334634-305f88d4-4b70-4faa-97da-1ce1853e9476.png)
![04  Ride Frequency Cont](https://user-images.githubusercontent.com/100979159/157334635-50b4b25e-195f-4cee-abab-5c12df8bc5e7.png)
![05  Ride Duration](https://user-images.githubusercontent.com/100979159/157334637-24ab9867-dd58-4c79-8101-07525d5a1fd2.png)
![06  Ride Type](https://user-images.githubusercontent.com/100979159/157334638-11d1c4e6-23ec-439c-99c0-7e1e3b0f7945.png)
![07  Station Preference](https://user-images.githubusercontent.com/100979159/157334639-6c0aff12-ee33-4176-b42c-a2654126fa5c.png)
![08  Station Preference Cont](https://user-images.githubusercontent.com/100979159/157334640-668b042b-d4fa-4f19-8979-5b5aa78216f3.png)
![09  Station Preference + Rideable Type](https://user-images.githubusercontent.com/100979159/157334642-f82c76cd-d87a-42b1-8468-172607eb9e0b.png)
![10  Ride Frequency + Rideable Type](https://user-images.githubusercontent.com/100979159/157334644-6415be57-aa7e-48ba-93ea-eeb5ccb2753b.png)
![11  Conclusions](https://user-images.githubusercontent.com/100979159/157334645-77fe132c-0b85-4aeb-840e-b3ecff9b9248.png)
![12  Notes on the Data](https://user-images.githubusercontent.com/100979159/157334648-662cab4d-25a8-4ce1-a6a5-abc940918393.png)

**Next:** [Conclusions and Recommendations](https://github.com/gharliquebread/cyclistic-analysis/blob/main/Conclusions%20and%20Recommendations.md)

**Previous** [SQL Analysis](https://github.com/gharliquebread/cyclistic-analysis/blob/main/SQL%20Analysis.md)

