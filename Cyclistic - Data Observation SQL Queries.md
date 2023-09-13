## Size of Data (Rows & Column)
There are 5829030 no of rows and 13 no of columns observed in 'combined_Table' table
```sql
SELECT COUNT(*) AS total_rows
FROM combined_table;
```
![Pasted image 20230724165105](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/346de0ab-cfb6-44a1-a880-fc9b9fc3236c)

## Data types of all columns in combined_table 
```sql
DESCRIBE combined_Table;
```
![Pasted image 20230724145734](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/cb8b1164-a396-4c23-b62e-50a64dc839ec)

## All Null and Blank values in combined_table
- ### No of Null Values in each columns
```sql
SELECT 'blank_count_ride_id' AS column_name, COUNT(*) AS count_value FROM combined_Table WHERE ride_id IS NULL
UNION ALL
SELECT 'blank_count_rideable_type', COUNT(*) FROM combined_Table WHERE rideable_type IS NULL
UNION ALL
SELECT 'null_count_started_at', COUNT(*) FROM combined_Table WHERE started_at IS NULL
UNION ALL
SELECT 'null_count_ended_at', COUNT(*) FROM combined_Table WHERE ended_at IS NULL
UNION ALL
SELECT 'blank_count_start_station_name', COUNT(*) FROM combined_Table WHERE start_station_name IS NULL
UNION ALL
SELECT 'blank_count_start_station_id', COUNT(*) FROM combined_Table WHERE start_station_id IS NULL
UNION ALL
SELECT 'blank_count_end_station_name', COUNT(*) FROM combined_Table WHERE end_station_name IS NULL
UNION ALL
SELECT 'blank_count_end_station_id', COUNT(*) FROM combined_Table WHERE end_station_id IS NULL
UNION ALL
SELECT 'blank_count_start_lat', COUNT(*) FROM combined_Table WHERE start_lat IS NULL
UNION ALL
SELECT 'blank_count_start_lng', COUNT(*) FROM combined_Table WHERE start_lng IS NULL
UNION ALL
SELECT 'blank_count_end_lat', COUNT(*) FROM combined_Table WHERE end_lat IS NULL
UNION ALL
SELECT 'blank_count_end_lng', COUNT(*) FROM combined_Table WHERE end_lng IS NULL
UNION ALL
SELECT 'blank_count_member_casual', COUNT(*) FROM combined_Table WHERE member_casual IS NULL;
```
![Pasted image 20230725152217](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/06fb4729-eeb6-4fd5-9609-40c9baf4abde)


- ### No of Blank Values in each columns
```sql
SELECT 'blank_count_ride_id' AS column_name, COUNT(*) AS count_value FROM combined_Table WHERE ride_id = ''
UNION ALL
SELECT 'blank_count_rideable_type', COUNT(*) FROM combined_Table WHERE rideable_type = ''
UNION ALL
SELECT 'null_count_started_at', COUNT(*) FROM combined_Table WHERE started_at IS NULL
UNION ALL
SELECT 'null_count_ended_at', COUNT(*) FROM combined_Table WHERE ended_at IS NULL
UNION ALL
SELECT 'blank_count_start_station_name', COUNT(*) FROM combined_Table WHERE start_station_name = ''
UNION ALL
SELECT 'blank_count_start_station_id', COUNT(*) FROM combined_Table WHERE start_station_id = ''
UNION ALL
SELECT 'blank_count_end_station_name', COUNT(*) FROM combined_Table WHERE end_station_name = ''
UNION ALL
SELECT 'blank_count_end_station_id', COUNT(*) FROM combined_Table WHERE end_station_id = ''
UNION ALL
SELECT 'blank_count_start_lat', COUNT(*) FROM combined_Table WHERE start_lat = ''
UNION ALL
SELECT 'blank_count_start_lng', COUNT(*) FROM combined_Table WHERE start_lng = ''
UNION ALL
SELECT 'blank_count_end_lat', COUNT(*) FROM combined_Table WHERE end_lat = ''
UNION ALL
SELECT 'blank_count_end_lng', COUNT(*) FROM combined_Table WHERE end_lng = ''
UNION ALL
SELECT 'blank_count_member_casual', COUNT(*) FROM combined_Table WHERE member_casual = '';
```
![Pasted image 20230725132207](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/cbf175ed-69bf-40e8-b3ff-1e0d9278fd56)


- ### Total no of blank or null values in combined_Table table
```sql
SELECT
    COUNT(*) AS total_blank_rows_count
FROM (
    SELECT
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        start_station_name,
        start_station_id,
        end_station_name,
        end_station_id,
        start_lat,
        start_lng,
        end_lat,
        end_lng,
        member_casual
    FROM combined_Table
    WHERE
        ride_id = '' OR
        rideable_type = '' OR
        started_at IS NULL OR
        ended_at IS NULL OR
        start_station_name = '' OR
        start_station_id = '' OR
        end_station_name = '' OR
        end_station_id = '' OR
        start_lat = '' OR
        start_lng = '' OR
        end_lat = '' OR
        end_lng = '' OR
        member_casual = ''
) AS distinct_blank_rows;

```
![Pasted image 20230725172601](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/c98f4e43-82cc-4c85-8439-89393b9b2940)


- ### Percentage of Blank Values in each columns
```sql
SELECT
  column_name,
  (count_value / (SELECT COUNT(*) FROM combined_Table)) * 100 AS percentage_of_blank
FROM (
  SELECT 'blank_count_ride_id' AS column_name, COUNT(*) AS count_value FROM combined_Table WHERE ride_id = ''
  UNION ALL
  SELECT 'blank_count_rideable_type', COUNT(*) FROM combined_Table WHERE rideable_type = ''
  UNION ALL
  SELECT 'blank_count_started_at', COUNT(*) FROM combined_Table WHERE started_at IS NULL
  UNION ALL
  SELECT 'blank_count_ended_at', COUNT(*) FROM combined_Table WHERE ended_at IS NULL
  UNION ALL
  SELECT 'blank_count_start_station_name', COUNT(*) FROM combined_Table WHERE start_station_name = ''
  UNION ALL
  SELECT 'blank_count_start_station_id', COUNT(*) FROM combined_Table WHERE start_station_id = ''
  UNION ALL
  SELECT 'blank_count_end_station_name', COUNT(*) FROM combined_Table WHERE end_station_name = ''
  UNION ALL
  SELECT 'blank_count_end_station_id', COUNT(*) FROM combined_Table WHERE end_station_id = ''
  UNION ALL
  SELECT 'blank_count_start_lat', COUNT(*) FROM combined_Table WHERE start_lat = ''
  UNION ALL
  SELECT 'blank_count_start_lng', COUNT(*) FROM combined_Table WHERE start_lng = ''
  UNION ALL
  SELECT 'blank_count_end_lat', COUNT(*) FROM combined_Table WHERE end_lat = ''
  UNION ALL
  SELECT 'blank_count_end_lng', COUNT(*) FROM combined_Table WHERE end_lng = ''
  UNION ALL
  SELECT 'blank_count_member_casual', COUNT(*) FROM combined_Table WHERE member_casual = ''
) AS count_data;
```
![Pasted image 20230725143231](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/47a6618e-9a78-4b4b-8975-9d9973b22f76)


- ### Total Percentage of Blank Values
```sql
SELECT
    ((COUNT(*)/(SELECT COUNT(*) from combined_Table)) * 100) AS count_distinct_blank_rows
FROM (
    SELECT
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        start_station_name,
        start_station_id,
        end_station_name,
        end_station_id,
        start_lat,
        start_lng,
        end_lat,
        end_lng,
        member_casual
    FROM combined_Table
    WHERE
        ride_id = '' OR
        rideable_type = '' OR
        started_at IS NULL OR
        ended_at IS NULL OR
        start_station_name = '' OR
        start_station_id = '' OR
        end_station_name = '' OR
        end_station_id = '' OR
        start_lat = '' OR
        start_lng = '' OR
        end_lat = '' OR
        end_lng = '' OR
        member_casual = ''
) AS distinct_blank_rows;
```
![Pasted image 20230725172313](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/f56271ba-5f61-4483-a460-666f42fdf90b)


## Checking Duplicates in combined_Table
- ### Count of total duplicate rows
```sql
SELECT COUNT(*) AS total_duplicates 
FROM combined_Table 
GROUP BY 
ride_id,
rideable_type,
started_at,
ended_at,
start_station_name,
start_station_id,
end_station_name,
end_station_id,
start_lat,
start_lng,
end_lat,
end_lng,
member_casual
HAVING COUNT(*) > 1;
```
![image](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/c28dbca7-2373-4c87-9aef-d54deed28660)


## Checking outlier or false data in combined_Table
### Outlier or false value in ride length (ended_at - started_at)
- #### Longer than a day
```sql
SELECT COUNT(*) AS longer_than_a_day
FROM combined_Table
WHERE TIMESTAMPDIFF(HOUR, started_at, ended_at) >= 24;
```
![Pasted image 20230731153601](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/c6168cad-ea82-4f03-8c06-2ae7ad56b3fc)


- #### Less than a minute
```sql
SELECT COUNT(*) AS less_than_a_minute
FROM combined_Table
WHERE TIMESTAMPDIFF(SECOND, started_at, ended_at) <= 60;
```
![Pasted image 20230731153704](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/a010ea32-c092-4fd8-9138-bc8271af4a4c)


## Total count and percent of inconsistent values
### Total inconsistent values count
Total count of rows including *'Total no of blank or null values'*, *'Outlier or false value of ride length longer than a day'* and *'Outlier or false value of ride length less than a minute'*.
```sql
SELECT
    COUNT(*) AS total_inconsistent_count
FROM (
    SELECT
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        start_station_name,
        start_station_id,
        end_station_name,
        end_station_id,
        start_lat,
        start_lng,
        end_lat,
        end_lng,
        member_casual
    FROM combined_Table
    WHERE
        ride_id = '' OR
        rideable_type = '' OR
        started_at IS NULL OR
        ended_at IS NULL OR
        start_station_name = '' OR
        start_station_id = '' OR
        end_station_name = '' OR
        end_station_id = '' OR
        start_lat = '' OR
        start_lng = '' OR
        end_lat = '' OR
        end_lng = '' OR
        member_casual = '' OR
        TIMESTAMPDIFF(HOUR, started_at, ended_at) >= 24 OR
		TIMESTAMPDIFF(SECOND, started_at, ended_at) <= 60
) AS distinct_blank_rows;
```
![Pasted image 20230731154619](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/ac017dfa-a2fa-4606-b5cc-386dc116a9ba)


### Total inconsistent values percentage
Percent of rows including *'Total no of blank or null values'*, *'Outlier or false value of ride length longer than a day'* and *'Outlier or false value of ride length less than a minute'*.
```sql
SELECT
    (COUNT(*)/(SELECT COUNT(*) FROM combined_Table) * 100) AS percent_inconsistent_count
FROM (
    SELECT
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        start_station_name,
        start_station_id,
        end_station_name,
        end_station_id,
        start_lat,
        start_lng,
        end_lat,
        end_lng,
        member_casual
    FROM combined_Table
    WHERE
        ride_id = '' OR
        rideable_type = '' OR
        started_at IS NULL OR
        ended_at IS NULL OR
        start_station_name = '' OR
        start_station_id = '' OR
        end_station_name = '' OR
        end_station_id = '' OR
        start_lat = '' OR
        start_lng = '' OR
        end_lat = '' OR
        end_lng = '' OR
        member_casual = '' OR
        TIMESTAMPDIFF(HOUR, started_at, ended_at) >= 24 OR
		TIMESTAMPDIFF(SECOND, started_at, ended_at) <= 60
) AS distinct_blank_rows;
```
![Pasted image 20230731155116](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/bc621860-be53-40a4-8703-31da03089d12)


---
## Field specific observations of 'combined_Table' table
### Characteristics and data format of field 'ride_id'
- Data type: VARCHAR(255) 
- Constraints applied: 
	- Primary Key
	- Unique
	- Not Null
```sql
-- Primary Key constraints added to ride_id column
ALTER TABLE combined_Table
MODIFY COLUMN ride_id VARCHAR(255) PRIMARY KEY UNIQUE NOT NULL;
```
- Length of field: 
```sql
SELECT LENGTH(ride_id) AS length_ride_id, COUNT(ride_id) AS no_of_rows
FROM combined_Table
GROUP BY length_ride_id;
```
![Pasted image 20230728153059](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/d89b148c-e8a1-49a2-a658-4e0ce16f1136)

### Characteristics and data format of Field 'rideable_type'
- Data type: MEDIUMTEXT
- Data format: Categorical
- All Categories:
```sql
SELECT rideable_type, COUNT(rideable_type) AS no_of_rides
FROM combined_Table
GROUP BY rideable_type;
```
![Pasted image 20230728152935](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/a38b4ef5-e6ae-475d-9132-e111250cf7be)

### Characteristics and data format of Field 'started_at' & 'ended_at'
- Data type: DATETIME -- (YYYY-MM-DD hh:mm:ss)

### Characteristics and data format of Field 'start_station_name', 'end_station_name', 'start_station_id' & 'end_station_id
- Data type: MEDIUMTEXT
- Blank values were found in all four columns.

### Characteristics and data format of Field 'start_lat', 'start_lng', 'end_lat' & 'end_lng'
- Data type: Double
- Blank values were found in 'end_lat' & 'end_lng' columns

### Characteristics and data format of Field 'member_casual'
- Data type: MEDIUMTEXT
- Data format: Categorical
- All Categories:
```sql
SELECT member_casual, COUNT(member_casual) AS no_of_rides
FROM combined_Table
GROUP BY member_casual;
```
![Pasted image 20230728152823](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/80b0ab9d-d468-4158-a271-c5da7c286b1c)

