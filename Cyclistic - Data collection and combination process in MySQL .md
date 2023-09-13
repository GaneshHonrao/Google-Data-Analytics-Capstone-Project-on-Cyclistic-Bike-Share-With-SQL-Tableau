# 1. Initial database setup in MySQL

### 1.1 Database creation in MySQL workbench
```sql
-- Database Creation 
CREATE DATABASE Cyclistic; 

-- Display Database 
SHOW databases; 

-- use cyclistic database 
USE Cyclistic;
```

### 1.2 Table creation in MySQL workbench
```sql
CREATE TABLE `202206-divvy` (
	ride_id VARCHAR(255),
	rideable_type MEDIUMTEXT,
	started_at DATETIME,
	ended_at DATETIME,
	start_station_name MEDIUMTEXT,
	start_station_id MEDIUMTEXT,
	end_station_name MEDIUMTEXT,
	end_station_id MEDIUMTEXT,
	start_lat DOUBLE,
	start_lng DOUBLE,
	end_lat DOUBLE,
	end_lng DOUBLE,
	member_casual MEDIUMTEXT
);
```

---
# 2. Data Import

### 2.1 Import file in MySQL via command prompt (Initial Setup)

##### Step 1: Provide MySQL bin directory path
- Copy MySQL bin directory path as shown in below image,
![Pasted image 20230726143843](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/963128d6-fe67-4789-bead-624925a202a1)

- And paste it in command prompt after cd *(space)* path
```shell
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```

##### Step 2: Connect to MySQL database
- Connect to MySQL database,
```shell
mysql -u root -p
```
- and provide our password
![Pasted image 20230726150719](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/376c265e-2d89-43ea-82b6-a7d6bc4bd61e)

##### Step 3: Set global variables to import data form local computer folder and quit the server connection
- Set the global variables by using below command so that the data can be imported from local computer folder.
```shell
SET GLOBAL local_infile=1;
```

> **Note:**
> You have just instructed MySQL server to allow local file upload form your computer 

![Pasted image 20230726153306](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/3dd3cb44-dc2c-4d09-9f94-6edf998af3a9)

- Quit current server connection,
```shell
quit;
```


![Pasted image 20230726154542](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/49313d12-c20a-460c-900a-03001e67390c)

##### Step 4: Connect MySQL server again with the local-infile system variable

> **Note:**
> We'll connect with the MySQL server again with the local-infile system variable. This basically means you want to upload data into a file from a local machine.

- In order to do this, please follow the following commands,
```shell
mysql --local-infile=1 -u root -p
```
- And enter the password
![Pasted image 20230726155935](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/6ef78ec4-ab45-4798-81d6-197bd03aa6dc)


##### Step 5: Upload data
- Now provide the file path of our .csv file and table name in below chunk and execute,
```shell
LOAD DATA LOCAL INFILE 'F:\\IT\\Data Analytics\\$ Google Data Analytics\\8) Google Data Analytics - Capstone Complete a Case Study\\week 2\\DAC8-Case-Study-1\\Prepare\\Dataset\\CSV\\Final csv dataset for Analysis (Last 12 months)\\202206-divvy.csv' 
INTO TABLE cyclistic.`202206-divvy` 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"' 
LINES TERMINATED BY '\r\n' IGNORE 1 ROWS;
```

> **Note:**
> Please replace single backward ( \ ) slash in the path with double back slashes( \\\ ) instead of single slash

- once executed your output will look like this,
![Pasted image 20230726160938](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/dcd138d2-001f-40b1-9bd1-b1b7e8e5b935)

Now first file of 202206-divvy.csv has been uploaded into our cyclistic database. To check in MySQL workbench, refresh the database and it will appear.

---
### 2.2 Upload remaining .csv files (After initial setup)

##### Step 6.1: Copy table structure and create remaining tables in MySQL workbench
As we know our dataset has the same type of table structure, instead of recreating the table manually we will copy existing table structure (from 202206-divvy) to new one (202207-divvy),
```sql
CREATE TABLE cyclistic.`202207-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202208-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202209-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202210-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202211-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202212-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202301-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202302-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202303-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202304-divvy` LIKE cyclistic.`202206-divvy`;
CREATE TABLE cyclistic.`202305-divvy` LIKE cyclistic.`202206-divvy`;
```

##### Step 6.2: Repeat uploading remaining files via command prompt
Now provide the file path of our next .csv file and next table name in below chunk and execute. Repeat this same step till we upload all files.
```shell
LOAD DATA LOCAL INFILE 'F:\\IT\\Data Analytics\\$ Google Data Analytics\\8) Google Data Analytics - Capstone Complete a Case Study\\week 2\\DAC8-Case-Study-1\\Prepare\\Dataset\\CSV\\Final csv dataset for Analysis (Last 12 months)\\202207-divvy.csv' 
INTO TABLE cyclistic.`202207-divvy` 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"' 
LINES TERMINATED BY '\r\n' IGNORE 1 ROWS;
```

---
# 3. Combine all tables into one in mysql workbench

- Create 'combined_Table' table, combination of all 12 tables we created
```sql
CREATE TABLE IF NOT EXISTS cyclistic.`combined_Table` AS ( 
	SELECT * FROM cyclistic.`202206-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202207-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202208-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202209-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202210-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202211-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202212-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202301-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202302-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202303-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202304-divvy` 
	UNION ALL 
	SELECT * FROM cyclistic.`202305-divvy` 
);
```

- View the table,
```sql
SELECT *
FROM combined_Table
LIMIT 10;
```

![Pasted image 20230726183516](https://github.com/GaneshHonrao/Google-Data-Analytics-Capstone-Project-on-Cyclistic-Bike-Share-With-SQL-Tableau/assets/144705832/13feadc7-d2e4-4cb0-8421-c74de6c23b89)


---
