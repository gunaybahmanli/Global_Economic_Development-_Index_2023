# Global Economic Development Index 2023
Project Overview
This project analyzes global performance indicators, providing insights into various factors such as governance, human development, economic performance, and environmental sustainability across countries and regions. By using SQL for data preparation and Power BI for interactive visualizations, the project answers crucial questions on country rankings, regional trends, and the interrelationships between different performance indicators.
# Key Questions:
Global Overview:
1. Which countries rank highest and lowest in AverageScore?
2. How do regions perform on average in Overall Score and its sub-indicators?
3. What are the regional distributions of countries by performance?
   
Social & Governance:
1. How do countries perform in SafetySecurity, PersonalFreedom, and Governance?
2. Which regions are the safest, most free, or best governed?
3. How does governance impact personal freedom and safety?

Human Development: 
1. What are the global trends in LivingConditions, Health, and Education?
2. Which regions excel in human development, and where is improvement needed?
3. How do human development indicators correlate with overall scores?

Economic Performance: 
1. Which countries lead in EconomicQuality, MarketAccessInfrastructure, and EnterpriseConditions?
2. Are there significant regional differences in economic performance?
3. How does economic quality correlate with governance and market access?

Investment & Environment: 
1. What are the trends in InvestmentEnvironment and NaturalEnvironment?
2. Which regions have the best investment environments, and how does this relate to economic performance?
3. Which countries and regions are most environmentally sustainable?

# Tools Used:
__SQL:__ For data extraction, preparation, and cleaning.

__Power BI:__ For data visualization and creating the interactive dashboard.

# SQL:
The SQL queries used in this project include:

__Data Preparation and Cleaning:__
* Data extraction from the source database.
* Handling missing data and duplicates.
* Creating calculated columns like Overall_Score, Economic_Performance, etc.
* Joining data tables to consolidate indicators.

__Sample SQL Queries:__

`SELECT Region, Country, RANK() OVER (PARTITION BY Region ORDER BY AveragScore DESC) AS RegionalRank
FROM countries_development;`

`sql
SET SQL_SAFE_UPDATES = 0;
UPDATE countries_development 
SET Country = TRIM(REPLACE(Country, 'Â', ''));`

`UPDATE countries_development 
SET Country = REGEXP_REPLACE(Country, '^[[:space:]]+', '') -- Removes leading spaces 
WHERE Country REGEXP '^[[:space:]]+';`

__Calculations:__

Average Score Calculation: Calculation of the average scores of countries across different indicators like HDI, SafetySecurity, etc.

Performance Categorization: Identifying top and bottom countries based on overall performance scores.

# Power BI Dashboard:
__Page 1: Global Overview__

Key Questions:

* Which countries rank highest and lowest in AverageScore?
* How do regions perform on average in Overall Score and its sub-indicators?
* What are the regional distributions of countries by performance?

Visuals:

__Choropleth Map:__ Displays the global distribution of AverageScore by country.

__Bar Chart:__ Shows the average AverageScore by region.

__KPI Cards:__ Display global averages for key indicators like AverageScore, HDI, and SafetySecurity.

__Bar Chart:__ Ranks the top 10 and bottom 10 countries by AverageScore.

__Slicer Visual:__ Allows users to filter and view data for individual countries

![image](https://github.com/user-attachments/assets/f3a71468-268b-42e2-a23f-2b865485bffa)

__Page 2: Social & Governance__

Key Questions: 

* How do countries perform in SafetySecurity, PersonalFreedom, and Governance? 
* Which regions are the safest, most free, or best governed? 
* How does governance impact personal freedom and safety?

Visuals:

__Radar Chart:__ Displays the average values of PersonalFreedom, SafetySecurity, and Governance by region.

__Bubble/Scatter Chart:__ Shows the correlation between Governance and SafetySecurity, with an additional impact of Personal Freedom.

![image](https://github.com/user-attachments/assets/eda189ec-03c6-48b2-a5a0-8498f8051a32)

__Page 3: Human Development__

Key Questions: 

* What are the global trends in LivingConditions, Health, and Education?
* Which regions excel in human development, and where is improvement needed?
* How do human development indicators correlate with overall scores?

Visuals:

__Clustered Column Chart:__ Shows the correlation between LivingConditions, Health, and Education.

__Clustered Bar Chart:__ Displays the top and bottom 5 countries by HDI.

__Scatter Chart:__ Shows the correlation between Living Conditions and Education across countries.

![image](https://github.com/user-attachments/assets/cf82ccd4-a768-43f9-adf1-fb9c89000881)

__Page 4: Economic Performance__

Key Questions: 

* Which countries lead in EconomicQuality, MarketAccessInfrastructure, and EnterpriseConditions?
* Are there significant regional differences in economic performance?
* How does economic quality correlate with governance and market access?

Visuals:

__Scatter Chart:__ Compares EconomicQuality with MarketAccess by country.

__Clustered Column Chart:__ Displays the top 10 countries by EconomicQuality and EnterpriseConditions.

__Clustered Bar Chart:__ Shows the top 10 countries by EconomicPerformance, where EconomicPerformance is calculated as:

`EconomicPerformance = ('countries_development'[EconomicQuality] + 'countries_development'[MarketAccessInfrastructure] + 'countries_development'[EnterpriseConditions]) / 3`

![image](https://github.com/user-attachments/assets/ae82e1fb-dfa4-482e-9944-1a73cf0152bb)

__Page 5: Investment & Environment__

Key Questions:

* What are the trends in InvestmentEnvironment and NaturalEnvironment?
* Which regions have the best investment environments, and how does this relate to economic performance?
* Which countries and regions are most environmentally sustainable?

Visuals:

__Waterfall Chart:__ Displays the balance between economic growth and environmental sustainability by region using the EcoEnvGap column.

__Donut Charts:__ Show the average of NaturalEnvironment and InvestmentEnvironment by region.

__Clustered Column Chart:__ Displays the top and bottom 10 countries for each region based on Natural Environment and Investment Environment.

![image](https://github.com/user-attachments/assets/c41677f4-4240-43cf-a8f2-6f04e6245970)

__Conclusion__

This project provides a comprehensive, interactive dashboard that offers deep insights into global performance, focusing on governance, human development, economic performance, and environmental sustainability. By using SQL for efficient data preparation and Power BI for intuitive visualizations, the dashboard answers critical questions about the state of countries across the world and helps identify regional and global trends that are valuable for policymakers and analysts alike.


