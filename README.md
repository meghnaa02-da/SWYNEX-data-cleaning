# SWYNEX-data-cleaning
TASK - 1 
-- creating database
create database bank;
use bank;
select * from bank_churn;

-- data validation
select distinct Geography from bank_churn;

-- hanbdle missing values
select * from bank_churn
where age is null or balance is null;

select  distinct gender from bank_churn;

-- fix data types
alter table bank_churn
modify column balance decimal(10,2);

-- Remove outliers
Delete from bank_churn
where balance < 0 and age < 18 and age >100;
set sql_safe_updates = 0;

-- trim whitespaces
update bank_churn
set Surname = trim(Surname);

-- Creating columns
-- Flag high-value customers
ALTER TABLE Bank_Churn 
ADD HighValue int;

UPDATE Bank_Churn
SET HighValue = CASE WHEN Balance > 100000 THEN 1 ELSE 0 END;

select HighValue from Bank_Churn;

-- Flag senior citizens
ALTER TABLE Bank_Churn 
ADD SeniorCitizen int;

UPDATE Bank_Churn
SET SeniorCitizen = CASE WHEN Age >= 50 THEN 1 ELSE 0 END;

select SeniorCitizen from Bank_Churn;

TASK-2
Customer Churn Analysis – EDA Dashboard
📌 Project Overview
This project explores customer churn patterns using an interactive Excel dashboard. The goal is to identify key factors influencing churn and provide actionable insights for retention strategies.

🎯 Objectives
Perform Exploratory Data Analysis (EDA) on customer churn dataset

Visualize churn vs non‑churn distribution

Analyze demographic and behavioral factors (Gender, Geography, Tenure, Products, Activity status)

Build an interactive dashboard with slicers for dynamic filtering

📂 Dataset
Source: Customer churn dataset (banking domain)

Key Features:

CustomerId
Gender

Geography

Tenure

NumOfProducts

IsActiveMember

Exited (Churn indicator)

📈 Dashboard Highlights
Slicers for filtering by Gender, Geography, Activity, and Products

Bar Chart: Churn vs Non‑churn counts

Pie Chart: Customer distribution by Geography

Pie Chart: Average Tenure segmented by Gender

Line Chart: Churn trend across Tenure values

Key Insights
Higher churn observed among certain geographies (Germany shows higher churn rate)

Tenure plays a role in churn probability – early tenure customers are more likely to exit

Active members tend to have lower churn compared to inactive ones

Product holding patterns influence churn behavior
