# SQL-data-cleaning
This is educational project on data cleaning and preparation using SQL. The original database in CSV format is lacated in the file club_member_info.csv. Here, we will explore the steps that need to be applied to obtain a cleansed version of daraset.
Let's inspect the initial rows to analyze the data in its original format.

CREATE TABLE club_member_info (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone VARCHAR(50),
	full_address VARCHAR(50),
	job_title VARCHAR(50),
	membership_date VARCHAR(50)
);
## Get the 10 first rows from the table using SQL console

SELECT *
FROM club_member_info cmic 
limit 10

**The result:**

|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|Wanda del mar       |44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|Joann Kenealy|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|   Joete Cudiff|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|mendie alexandrescu|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
| fey kloss|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|

## Cleaning and documenting

### Step 1: Make a copy of your table
- Right click on the table name -> Choose the "Generate SQL" option -> Choose the "DDL" option
- Copy the SQL code that is generated for you
- Put this code to SQL console, change the table name to "club_member_info_cleaned" and run it

CREATE TABLE club_member_info_cleaned (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone VARCHAR(50),
	full_address VARCHAR(50),
	job_title VARCHAR(50),
	membership_date VARCHAR(50)
);

- Copy all values from original table:
  
INSERT INTO club_member_info_cleaned 
select * FROM club_member_info ;

- Refresh database to get updates

### Step 2: Clean data and document it
Some issues with data:
- Leading and trailing whitespaces

UPDATE club_member_info_cleaned 
SET full_name = ltrim(full_name)

UPDATE club_member_info_cleaned 
SET full_name = rtrim(full_name)

- Inconsistent letter case

 UPDATE club_member_info_cleaned 
SET full_name = UPPER(full_name) 

- Age out of realistic range

UPDATE club_member_info_cleaned 
SET age = CASE 
	WHEN age > 99 THEN 99
	ELSE age 
END

**The result:**

|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|ADDIE LUSH|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|SYDEL SHARVELL|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|CONSTANTIN DE LA CRUZ|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|GAYLOR REDHOLE|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|WANDA DEL MAR|44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|JOANN KENEALY|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|JOETE CUDIFF|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|MENDIE ALEXANDRESCU|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
|FEY KLOSS|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|


# Project 2 - Carbon Emission Analysis
## Project's objective
Online SQL Console: [https://api.swisscoding.edu.vn/sqlexec/?database=carbon_emissions&standalone=true]
### Why
### What
### How
## Mining
### Data parterns
Data have 171 Duplicate, query:
SELECT id, company_id,country_id,industry_group_id,year,product_name,weight_kg,carbon_footprint_pcf,upstream_percent_total_pcf,operations_percent_total_pcf,
downstream_percent_total_pcf
FROM product_emissions
GROUP BY id, company_id,country_id,industry_group_id,year,product_name,weight_kg,carbon_footprint_pcf,upstream_percent_total_pcf,operations_percent_total_pcf,
downstream_percent_total_pcf
having count(*) > 1

Data have N/A values

Data structure
### Solution
Write a query of group by and condition to filter out the value we dont want to have write the reason why we have the solution
## Findings
Most contributed carbon emissions product
AVG, sum: carbon
product name
### 1. Which products contribute the most to carbon emissions?
most contributed carbon emissions product
avg,sum: carbon
product name
### 2. What are the industry groups of these products?
product name, industry group name
select industry_group, product_name
from product_emissions
left join industry
group by industry_group, product_name

### 3. What are the industries with the highest contribution to carbon emissions?

SELECT 
    industry_groups.industry_group,
    SUM(product_emissions.carbon_footprint_pcf) AS total_carbon_emissions
FROM 
    product_emissions
JOIN 
    industry_groups ON product_emissions.industry_group_id = industry_groups.id
GROUP BY 
    industry_groups.industry_group
ORDER BY 
    total_carbon_emissions DESC
LIMIT 10

Here the result:
 | industry_group                                   | total_carbon_emissions | 
| -----------------------------------------------: | ---------------------: | 
| Electrical Equipment and Machinery               | 9801558                | 
| Automobiles & Components                         | 2582264                | 
| Materials                                        | 577595                 | 
| Technology Hardware & Equipment                  | 363776                 | 
| Capital Goods                                    | 258712                 | 
| "Food, Beverage & Tobacco"                       | 111131                 | 
| "Pharmaceuticals, Biotechnology & Life Sciences" | 72486                  | 
| Chemicals                                        | 62369                  | 
| Software & Services                              | 46544                  | 
| Media                                            | 23017                  | 

### 4. What are the companies with the highest contribution to carbon emissions?
SELECT 
    companies.company_name,
    SUM(product_emissions.carbon_footprint_pcf) AS total_carbon_emissions
FROM 
    product_emissions
JOIN 
    companies ON product_emissions.company_id = companies.id
GROUP BY 
    companies.company_name
ORDER BY 
    total_carbon_emissions DESC
	limit 10 
 
 Here the result:
 | company_name                            | total_carbon_emissions | 
| --------------------------------------: | ---------------------: | 
| "Gamesa Corporación Tecnológica, S.A."  | 9778464                | 
| Daimler AG                              | 1594300                | 
| Volkswagen AG                           | 655960                 | 
| "Mitsubishi Gas Chemical Company, Inc." | 212016                 | 
| "Hino Motors, Ltd."                     | 191687                 | 
| Arcelor Mittal                          | 167007                 | 
| Weg S/A                                 | 160655                 | 
| General Motors Company                  | 137007                 | 
| "Lexmark International, Inc."           | 132012                 | 
| "Daikin Industries, Ltd."               | 105600                 | 

### 5. What are the countries with the highest contribution to carbon emissions?

SELECT 
    countries.country_name,
    SUM(product_emissions.carbon_footprint_pcf) AS total_carbon_emissions
FROM 
    product_emissions
JOIN 
    countries ON product_emissions.country_id = countries.id
GROUP BY 
    countries.country_name
ORDER BY 
    total_carbon_emissions DESC
	limit 10 

Here the result:
| country_name | total_carbon_emissions | 
| -----------: | ---------------------: | 
| Spain        | 9786130                | 
| Germany      | 2251225                | 
| Japan        | 653237                 | 
| USA          | 518381                 | 
| South Korea  | 186965                 | 
| Brazil       | 169337                 | 
| Luxembourg   | 167007                 | 
| Netherlands  | 70417                  | 
| Taiwan       | 62875                  | 
| India        | 24574                  | 

### 6. What is the trend of carbon footprints (PCFs) over the years?
SELECT 
    year,
    SUM(carbon_footprint_pcf) AS total_carbon_emissions
FROM 
    product_emissions
GROUP BY 
    year
ORDER BY 
    year 

Here the result:
| year | total_carbon_emissions | 
| ---: | ---------------------: | 
| 2013 | 503857                 | 
| 2014 | 624226                 | 
| 2015 | 10840415               | 
| 2016 | 1640182                | 
| 2017 | 340271                 | 

### 7. Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?

min(year), max(year)
carbon of max(year)/carbon of min(year)
group by industry group

(carbon of max(year) - carbon of min(year))/((carbon of max(year) + carbon of min(year))

select from 
left join(select from) on year, industry = industry

select case when

max(year): current year
min(year): past year

SELECT 
	product_emissions.year,
	industry_groups.industry_group,
	sum(product_emissions.carbon_footprint_pcf) as total_carbon_emissions
FROM 
    product_emissions
JOIN 
	industry_groups ON product_emissions.industry_group_id = industry_groups.id
GROUP BY 
	industry_groups.industry_group,
	product_emissions.year
ORDER BY 
	industry_groups.industry_group,
	product_emissions.year 

 

## Conclution




