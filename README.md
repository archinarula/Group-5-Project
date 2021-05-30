# Impact of climate variables on Covid 19 cases
## Introduction 

The new novel corona virus known as Covid19 (SARS CoV-2), has caused one of the most serious health crises globally. Since its global spread last year, we've seen multiple news article around the impact of temperature and humidity on the speed of spread and whetheer or not virus thrive in colder temerpatur.
A simple Google search using term "covid spread cold and dry weather news" will yelid multiple articles from credible news outlet and statiscal and scentfice websites in favor or against. 

Some of the key one published over the year are:
1.  www.cebm.net on Mar 23,2020 [Do weather conditions influence the transmission of the coronavirus (SARS-CoV-2)?](https://www.cebm.net/covid-19/do-weather-conditions-influence-the-transmission-of-the-coronavirus-sars-cov-2/)
2.  www.medicalnewstoday.com on Aug. 15,2010 [How does weather affect COVID-19?](https://www.medicalnewstoday.com/articles/how-does-weather-affect-covid-19)
3.  www.statenews.com on Oct. 21,2020 [Covid-19’s wintry mix](https://www.statnews.com/2020/10/21/covid19-winter-dry-indoor-air-helps-coronavirus-spread/)
4. www.sciencedaily.com on Nov. 2,2020 [Hot or cold, weather alone has no significant effect on COVID-19 spread](https://www.sciencedaily.com/releases/2020/11/201102155409.htm)
5.  www.cbc.ca on Nov. 7, 2020 [Winter will help COVID-19 spread more easily](https://www.cbc.ca/news/canada/manitoba/covid-19-winter-tips-1.5788154)
6. www.huffingtonpost.ca on Jan.7,2021 [Does Cold Weather Make COVID-19 Spread More Easily?](https://www.huffingtonpost.ca/entry/cold-weather-spread-covid-explainer_ca_5ff78146c5b612d958ea6d29)
7.  www.ctvnews.ca on Sep. 20,2020 [COVID-19 appears to spread less in warm and wet climates](https://www.statnews.com/2020/10/21/covid19-winter-dry-indoor-air-helps-coronavirus-spread/)

The first link is a study done at the beigning of 2020 by University of Oxford and its reuslt around this topic.

## Purpose

The purpose of this study is to analyse if colder and dryer weather increases the spread of Covid-19 virus. More specificaly find the realtion and quatify the increase in spread with temperature drop of every x degree celsius or percipatation dropped by y%.

## Data

**Data Source:**  

1.  [Weather Data]( https://history.openweathermap.org/storage/fa037ddb81b7f7f0a0d1a0ebd131858e.csv)
2.  [New York Covid data](https://github.com/nychealth/coronavirus-data/blob/master/trends/data-by-day.csv)
3.  [Sao Paulo daily covid data](https://raw.githubusercontent.com/seade-R/dados-covid-sp/master/data/dados_covid_sp.csv)

**Data Collection:** Secondary Data Collected from openweathermap and other international observatories

**Variables:** 
1.  Dependent: One of the following:
    -   7day moving avg new cases per 100,000 population: mavg_7day_per_100k_new_cases
2.  Inependent Variables:
    - Moving 15 day average of daily temperature  I,e from reported -14  to reported date -1: mavg_15_temp
    - Moving 15 day average of daily humdity I,e from reported -14 to reported date -1: mavg_15_humidity

**Scope of project:** The selected cities are New York, and Sao Paulo. Cities are selected based on similar population per 100,000, covid cases, weather differences covid response. 

## ETL: 01_ETL_FullRefresh.ipynb

## Data Definition

1. Covid metrcis:
    -   Covid19 rate: Total number of Covid cases by 100k inhabitants reported in selected cities per capital population (New daily case / City Population) 
2.  Weather metrics: A combination of variables like daily Average Temperature,Average Humidity.
    -   Average daily temparture in celsius: daily_humidity
    -   Average daily humidity: daily_temp 
3. Final Combine Data dictionary

![data dict](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/Data_Dict.png)


## Methodology

To analyse the impact of weather on Covid19 rate of new cases, we shall be doing hypothesis testing and try to find out whether factors like temperature, humidity and their averages have any relationship with the rate of Covid19 infections.

H0: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have no effect on the rate of new Covid19 cases in 2 cities

H1: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have effect on the rate of new Covid19 cases in 2 cities

To test our hypothesis, we shall be utilizing one or more of the following models: 
-  Correlation
-  Linear Regression Model


We are following the considerations below to complete the analysis:

- 15 days average temperature and humidity up to the day before  as this is usually the virus incubation period
- New cases per 100K to compare same size of population
- Moving 7 days average of new cases per 100K to smooth out any reporting anomalies 
- We ran correlations to validate the strength of the relationship between the variables. 
- We ran 3 different regressions , one for each city and one combined. For the combined, we added “is_New York flag” (1= NY, 0=SP)

**Assumptions:** For our modelling purpose we are taking into consideration following assumptions:
-   There are no extreme deviations in daily average weather parameters
-   Covid testing was available with similar opportunities to the residents of both cities
-   All or none Covid19 precautions were followed by residents of both of the cities 

## Data exploratory Analysis

**First Analysis:**
- Started with 4 data sets 
1.  [Kaggle Weather Data]( https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities)
2.  [Major Cities Covid Data]( https://saludata.saludcapital.gov.co/osb/index.php/datos-de-salud/enfermedades-trasmisibles/covid19/)
3.  [New York Covid data](https://github.com/nychealth/coronavirus-data)
4.  [Sao Paulo daily covid data](https://github.com/wcota/covid19br/blob/master/DESCRIPTION.en.md)  
- Performed ETL to get the final variables for city data  like combining two city data set with variables total confirmed cases,cases per million 
- Weather data was transformed average temperature, average humidity, 1-7 day average, 8-14 day average, percentage change for temperature and humidity variables

![NYC](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/newyork_totalconfirmdataset.png)![SP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_totalconfirmdataset.png)

![SPNew](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_newcases_outliers.png)![SPAveNew](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_Ave_7day_count.png)

**Result**
- Some of the transformed new case values were incorrect and Outliers were many 
- We found other data sources that are more reliable repeated exploratory analysis in Excel

**Second Analysis**
- We used different data sources
1.  [Weather Data]( https://history.openweathermap.org/storage/fa037ddb81b7f7f0a0d1a0ebd131858e.csv)
2.  [New York Covid data](https://github.com/nychealth/coronavirus-data/blob/master/trends/data-by-day.csv)
3.  [Sao Paulo daily covid data](https://raw.githubusercontent.com/seade-R/dados-covid-sp/master/data/dados_covid_sp.csv)

- Source for Data exploration in: [Excel Analysis](https://github.com/archinarula/Group-5-Project/blob/main/aisha_working_folder/Comparativo-ciudades%20vs%20github%20data%20source%20comparison.xlsx) 

- Instead of using raw daily new cases, we are using moving average (for 7 days including current day) to remove any anomalies for the city data.

![NYC](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/NYC_7day_Avg.png)

![SP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_7day_Avg.png)

- To further smoothen the city data 100k population was considered 7 day average per 100k population

![7_AVG_100k](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/7-day_avg_100k_newcases.png)

- The new weather data includes variables like average and 15 average for temperature and humidity as incubation period is 15 days 

![15_Ave_temp](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/15day_avg_temp.png)

![15_Ave_humidity](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/15day_avg_humidity.png)


- Pairplot to see relationship on the various columns in 2 cities i.e between Moving Average New Cases per 100k with Moving Avg 15 days Tempreture and Humidity

![PP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/pairplot.png)

**Statistical Analysis**
- Sources: [Correlation](https://github.com/archinarula/Group-5-Project/blob/Archana/Archana_WorkingFolder/NewData_Model_Analysis_Regression.ipynb), [Regression](https://github.com/archinarula/Group-5-Project/blob/Archana/Archana_WorkingFolder/NewData_Model_Analysis_Regression.ipynb)

**Correlation**
- New York Correlation 

![NYC_C](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/NYC_MNew_Correlation.png)

- Sau Paulo Correlation

![SP_C](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/NYC_MNew_Correlation.png)

- Correlation between the new transformed data 

![New_Variables](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/Correlation_finaldataset.png)

**Regression Model** 

![NYC_Regression](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/NYC_MNew_Regression.png)

![SP_Regression](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_MNew_Regression.png)

![SP_NYC_Regression](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_NYC_MNew_Regression.png)


## Analysis of Project using Google sheets:
[**Google sheets**](https://docs.google.com/presentation/d/1ZVr5sjjc9tDzyN3UlWber7vavX04F2WQ1VslqYYOfDA/edit?usp=sharing)

## Tools:
1.  **Data Analysis:** Python
2.  **Data Storage (Database):** PostgreSQL but later we did not use database as the data set size was small
3.  **Visualization:** Google Sheets

## Communication Protocols:
- **Slack group** created for coordination and exchange of ideas/information
- **Weekdays daily calls** to syncup progress and define next steps
- **Weekend calls** to refine outputs and prepare submission for the week
