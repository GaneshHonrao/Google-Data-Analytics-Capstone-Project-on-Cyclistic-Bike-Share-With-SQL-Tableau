# Google Data Analytics Capstone Project on Cyclistic Bike Share

- Project Reference & Resource:  [Google Data Analytics Capstone: Complete a Case Study](https://www.coursera.org/learn/google-data-analytics-capstone)
## Project Quick Summary
- I'll be acting as a junior data analyst at Cyclistic, a fictional company.
- I'll encounter various characters and team members throughout the study.
- My goal is to address critical business questions by following the data analysis process: ask, prepare, process, analyze, share, and act.
- Tools used: MySQL, Tableau.
## Project Introduction
### Scenario
- I am a junior data analyst at Cyclistic in the marketing analyst team.
- The director of marketing thinks annual memberships are crucial for the company's success.
- My team's goal is to analyze how casual riders and annual members use Cyclistic bikes differently.
- We aim to use these insights to create a strategy for converting casual riders into annual members.
- Our recommendations need approval from Cyclistic executives and require strong data insights and professional data visualizations.
### Characters and teams
- Cyclistic is a bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can't use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

- Lily Moreno is the director of marketing and my manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. These may include email, social media, and other channels.

- The Cyclistic marketing analytics team is a group of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide Cyclistic marketing strategy. I joined this team six months ago and have been busy learning about Cyclistic's mission and business goals — as well as how I, as a junior data analyst, can help Cyclistic achieve them.
   
- The Cyclistic executive team is known for being notoriously detail-oriented. They will decide whether to approve the recommended marketing program.
# Project Kickoff 
## Ask Phase: Business Questions & Key Stakeholders

- Three questions will guide the future marketing program:  
	1. How do annual members and casual riders use Cyclistic bikes differently?  
	2. Why would casual riders buy Cyclistic annual memberships?  
	3. How can Cyclistic use digital media to influence casual riders to become members?  

Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?
## Prepare Phase: Data Gathering & EDA Report
### Data Gathering

I plan to utilize Cyclistic's archived trip information to conduct an analysis and detect patterns. This data can be obtained through the [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html) source, with permission granted by Motivate International Inc. pursuant to their [licensing agreement](https://ride.divvybikes.com/data-license-agreement).  
Note - This is public data that you can use to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit you from using riders’ personally identifiable information. This means that you won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.
#### Concerned Source Data  
1. **Data Timeframe:** June 2022 to May 2023 (Past 1 year data)
2. **Source Data Description and Structure:** 
	1. The data is organized into individual .csv files, each corresponding to a specific month.
	2. These files share common fields relevant to our analysis.
3. After our initial examination, we can confidently assert that the source data is Reliable, Original, Comprehensive, Current and Cited.
### Tool Selection for Analysis
1. **Tool for Data Cleaning, Transformation, and Processing: SQL**
	- We chose SQL for these tasks because the dataset exceeded 5.8 million rows, making it impractical to manage with Excel (which is typically suitable for datasets of less than 1 million rows). SQL's capacity to handle large volumes of data makes it the preferred choice for data wrangling.
2. **Tool for Analysis and Visualization: Tableau**
	- While there are several tools available for data visualization, including Excel and Power BI, our selection of Tableau is deliberate. Tableau offers dynamic capabilities and a diverse range of visualization options, making it the ideal choice for our analytical and visualization needs.
### Data Loading
1. **File Naming Convention:** Files are named in the format of YYYYMM-divvy.csv.
2. **Data Integration into 'combined_Table':** The data has been uploaded and consolidated into a unified table named 'combined_Table'. (To see the process of data upload and consolidation into a single table, please [click here](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/blob/main/1.%20Cyclistic%20-%20Data%20Collection%20and%20Combining%20Process%20in%20MySQL%20.md).)
### Data Observation 
[Data Observation SQL Queries](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/blob/main/2.%20Cyclistic%20-%20Data%20Observation%20SQL%20Queries.md)
#### Size of Data (Rows & Column)  
![Pasted image 20230724165105](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/2190999f-8d8c-471c-a033-ea73e6a54ec4)


There are 5829030 no of rows and 13 no of columns observed in 'combined_Table' table

#### Data types of all columns in combined_table  
![Pasted image 20230724145734](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/7b804dfc-5859-4f95-be2c-776e882bf513)


### All Null and Blank values in combined_table
#### No of Null Values in each columns  
![image](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/0a191722-0d18-4974-9daa-6c0d0d778270)

#### No of Blank Values in each columns  
![Pasted image 20230725132207](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/9eb55bb4-202b-4783-82ca-e767d55b93ca)


#### Total no of blank or null values in combined_Table table  
![Pasted image 20230725172601](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/f7aff68d-fe00-4530-bbc3-f1d7ceb804e3)


#### Percentage of Blank Values in each columns  
![Pasted image 20230725143231](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/73cf4be0-3d3a-4540-912a-de4b9414af19)


#### Total Percentage of Blank Values  
![Pasted image 20230725172313](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/a96f5a27-c227-4193-ae2a-da6dbc670b9d)


### Checking Duplicates in combined_Table
#### Count of total duplicate rows  
![image](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/0a191722-0d18-4974-9daa-6c0d0d778270)


### Checking outlier or false data in combined_Table
#### Outlier or false value in ride length (ended_at - started_at)
- **Longer than a day**  
![Pasted image 20230731153601](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/baf85bb7-59ee-44c4-b2f4-cbca24f59024)


- **Less than a minute**  
![Pasted image 20230731153704](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/7d57aa3f-5bae-41ae-8a2b-83c2b1361e74)


### Total count and percent of inconsistent values
- **Total inconsistent values count**  
Total count of rows including *'Total no of blank or null values'*, *'Outlier or false value of ride length longer than a day'* and *'Outlier or false value of ride length less than a minute'*.  
![Pasted image 20230731154619](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/f3832e5e-c41e-4ac9-8728-5abb2fa1fe49)


- **Total inconsistent values percentage**  
Percent of rows including *'Total no of blank or null values'*, *'Outlier or false value of ride length longer than a day'* and *'Outlier or false value of ride length less than a minute'*.  
![Pasted image 20230731155116](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/7c88be66-4090-487a-b14d-ccee9028d51b)


---
### Field specific observations of 'combined_Table' table
##### Characteristics and data format of field 'ride_id'
- Data type: VARCHAR(255) 
- Constraints applied: 
	- Primary Key
	- Unique
	- Not Null
- Primary Key constraints added in this field

- Length of field:  
![Pasted image 20230728153059](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/3940cd28-7a9f-40c4-9c8d-3b38fd7c519c)

##### Characteristics and data format of Field 'rideable_type'
- Data type: MEDIUMTEXT
- Data format: Categorical
- All Categories:  
![Pasted image 20230728152935](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/570904e8-21a0-4bc4-a976-03df42a7b7d5)

##### Characteristics and data format of Field 'started_at' & 'ended_at'
- Data type: DATETIME -- (YYYY-MM-DD hh:mm:ss)

##### Characteristics and data format of Field 'start_station_name', 'end_station_name', 'start_station_id' & 'end_station_id
- Data type: MEDIUMTEXT
- Blank values were found in all four columns.

##### Characteristics and data format of Field 'start_lat', 'start_lng', 'end_lat' & 'end_lng'
- Data type: Double
- Blank values were found in 'end_lat' & 'end_lng' columns

##### Characteristics and data format of Field 'member_casual'
- Data type: MEDIUMTEXT
- Data format: Categorical
- All Categories:  
![Pasted image 20230728152823](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/8b4b254e-a487-43ca-b1ce-120785033d61)


---
## Process Phase: Data Cleaning & Transformation Report
### Data Cleaning
[Data Cleaning & Transformation SQL Queries](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/blob/main/3.%20Cyclistic%20-%20Data%20Cleaning%20%26%20Transformation%20SQL%20Queries.md)
- Rows with missing values are removed.
- We excluded trips that were too short (less than a minute) or too long (more than a day).
- A total of 1426785 rows were deleted.
### Data Transformation
- Created new Columns: 
	- ride_length 
	- month
	- day_of_week
	- hour_in_day.
## Analyze, Share & Act Phase: Cyclistic Bike Share Analysis Report
- The data has been tidied and formatted for analysis. 
- I loaded it into Tableau Public and used it to create charts and graphs to visualize the data. 
- I then created a Story in Tableau to share the insights I gained from the data.

Tableau Story Link: [Cyclistic Bike Share Analysis | June 22 to May 23](https://public.tableau.com/app/profile/ganesh.honrao/viz/CyclisticBikeShareAnalysisJune22toMay/Story1#2) 

![Cyclistic data analysis report_page-0001](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/ecb654f3-b807-49ed-ae0d-76df8a7f996c)  

![Cyclistic data analysis report_page-0002](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/e68b3171-7461-4de1-acec-58c13f498da2)  

![Cyclistic data analysis report_page-0003](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/c5c9f259-cbe5-406a-8bd6-cb10599471a1)  

![Cyclistic data analysis report_page-0004](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/68318c32-eff5-4024-92da-aa5d46e9c35d)  

![Cyclistic data analysis report_page-0005](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/9e88da7b-ba68-4a33-87fe-720361b247c8)  

![Cyclistic data analysis report_page-0006](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/fee57dc6-5842-4e88-a24d-1bb76f94fed8)  

![Cyclistic data analysis report_page-0007](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/aa1d128c-f36d-44d2-aa8e-e47b39fb6462)  

![Cyclistic data analysis report_page-0008](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/2149b088-f840-4804-b8f7-fc2dae8ee491)  

---
