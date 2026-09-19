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
