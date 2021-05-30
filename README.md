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
    -   Covid 19 new cases per 100,000 population: new_cases_per_100K
2.  Independent Variables: 
    - Moving 7 day average of new cases  i,e from reported -6 to the reported date: mavg_7day_new_cases
    - Moving 7 day average of new cases per 100 K of population: mavg_7day_per_100k_new_cases
    - Average daily temparture: daily_temp
    - Average daily humidity: daily_humidity
    - Moving 15 day average of daily temperature  I,e from reported -14  to reported date -1: mavg_15_temp
    - Moving 15 day average of daily humdity (%)  I,e from reported -14 to reported date -1: mavg_15_humidity

**Scope of project:** The selected cities are New York, and Sao Paulo. Cities are selected based on similar population per 100,000, covid cases, weather differences covid response. 

**Data clean-up:** Using pandas libraries

## Data Definition

1. Covid metrcis:
    -   Covid19 rate: Total number of Covid cases by 100k inhabitants reported in selected cities per capital population (New daily case / City Population) 
2.  Weather metrics: A combination of variables like daily Average Temperature,Average Humidity.
    -   Average daily temparture in celsius: daily_humidity
    -   Average daily humidity: daily_temp 


## Methodology

To analyse the impact of weather on Covid19 rate of new cases, we shall be doing hypothesis testing and try to find out whether factors like temperature, humidity and their averages have any relationship with the rate of Covid19 infections.

H0: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have no effect on the rate of new Covid19 cases in 2 cities

H1: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have effect on the rate of new Covid19 cases in 2 cities

To test our hypothesis, we shall be utilizing one or more of the following models: 
-   Linear Regression Model

**Assumptions:** For our modelling purpose we are taking into consideration following assumptions:
-   There are no extreme deviations in daily average weather parameters
-   Covid testing was available with similar opportunities to the residents of both cities
-   All or none Covid19 precautions were followed by residents of both of the cities 

## Data exploratory Analysis

**First Analysis:**
- Started with 4 data sets and performed ETL to get the final variables for city data  like combining two city data set with variable like total confirmed cases,cases per million
- Weather data was transformed average temperature, average humidity, 1-7 day average, 8-14 day average, percentage change for temperature and humidity variables
- After analysing the data we found outliers in both of the citiy data sets 

![NYC](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/newyork_totalconfirmdataset.png)![SP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_totalconfirmdataset.png)

- Correlation between new cases and average temperature for NYC(-0.048)
- Correlation between new cases and average humidity for NYC(0.1) 
  
 NYC new cases vs Average temperature vs average humidity
  
![CNYC](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/corelation_olddataset_NYC.png)

- Correlation between new cases and average temperature for Sau Paulo(0.0041)
- Correlation between new cases and average humidity for Sau Paulo(-0.015)

Sao Paulo new cases vs Average temperature vs average humidity

![CSP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/corelation_olddataset_SP.png)

**Result**
- Outliers were many and correlation was very small 
- We found other data sources that are more reliable repeated exploratory analysis in Excel

**Second Analysis**
- We transformed new city data set to new cases and 7day average new cases 
- Sau Paulo city data set has many outliers even for new cases and 7 day average new cases

Sau Paulo new cases outliers                                                                                                        Sau Paulo 7 day average outliers
![SPNew](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_newcases_outliers.png)![SPAveNew](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/SP_Ave_7day_count.png)
**Result:
- Instead of using raw daily new cases, we are using moving average (for 7 days including current day) per 100k population to remove any anomoloies for the city data.

**Third Analysis**
Transformed city data to get 7 day average per 100k population

![7_AVG_100k](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/7-day_avg_100k_newcases.png)

- The new weather data includes variables like average and 15 average for temperature and humidity as the covid symptoms can be found 15 days after its contact  

![15_Ave_temp](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/15day_avg_temp.png)

![15_Ave_humidity](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/15day_avg_humidity.png)

- Correlation between the new transformed data 

![New_Variables](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/Correlation_finaldataset.png)

- Pairplot to see relationship on the various columns in 2 cities i.e between Moving Average New Cases per 100k with Moving Avg 15 days Tempreture and Humidity

![PP](https://github.com/archinarula/Group-5-Project/blob/Sushmita/resources/images_for_readme/pairplot.png)

## Visualization using Google sheets:
[**Google sheets**](https://docs.google.com/presentation/d/1ZVr5sjjc9tDzyN3UlWber7vavX04F2WQ1VslqYYOfDA/edit?usp=sharing)

## Tools:
1.  **Data Analysis:** Python
2.  **Data Storage (Database):** PostgreSQL but later we did not use database as the data set size was small
3.  **Visualization:** Google Sheets

## Communication Protocols:
- **Slack group** created for coordination and exchange of ideas/information
- **Weekdays daily calls** to syncup progress and define next steps
- **Weekend calls** to refine outputs and prepare submission for the week
