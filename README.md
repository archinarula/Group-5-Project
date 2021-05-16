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

The purpose of this study is to analyse if colder and dryer weather increases the spredh of Covid-19 virus. More specificaly find the realtion and quatify the increase in spread with temperature drop of every x degree celsius or percipatation dropped by y%.

## Data

**Data Source:**  

1.  [Kaggle Weather Data]( https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities)
2.  [Major Cities Covid Data]( https://saludata.saludcapital.gov.co/osb/index.php/datos-de-salud/enfermedades-trasmisibles/covid19/)
3.  [New York Covid data](https://github.com/nychealth/coronavirus-data)
4.  [Sao Paulo daily covid data](https://github.com/wcota/covid19br/blob/master/DESCRIPTION.en.md)

**Data Collection:** Secondary Data Collected from Kaggle and other international observatories

**Variables:** 
1.  Dependent: One of the following:
    -   Covid 19 new cases per 100,000 population: Covid19NewCases:
    -   Percent Positive aka Positivy Rate: per_positive [What is the "percent postive" and why does it matter](https://www.jhsph.edu/covid-19/articles/covid-19-testing-understanding-the-percent-positive.html#:~:text=The%20percent%20positive%20is%20exactly,total%20tests%20x%20100%25.)
2.  Independent Variables: 
    - Average daily temparture in celsius: Avg_Temperature
    - Average daily percepitation: Avg_Precipitation 
 
**Scope of project:** Limited to 2 cities data (in future may expand the scope), for given weather variables only. Cities are slected based on similar population, covid cases, weather differences covid response. The selected cities are New York, and Sao Paulo

**Data clean-up:** If required, using pandas libraries 

## Data Definition

1. Covid metrcis:
    -   Covid19 rate: New daily covid19 cases reported in selected cities per capita population (New daily case / City Population) **Or option 2 is Total number of cases by 100k inhabitants**
    - Percent Postive: The percentage of all coronavirus tests performed that are actually positive, or: (positive tests)/(total tests) x 100%. The percent positive (sometimes called the “percent positive rate” or “positivity rate”) helps public health officials answer questions such as:
        -   What is the current level of SARS-CoV-2 (coronavirus) transmission in the community?
        -   Are we doing enough testing for the amount of people who are getting infected?

2.  Weather metrics: A combination of variables like daily Average Temperature,Average Precipitation .
    -   Average daily temparture in celsius: Avg_Temperature
    -   Average daily percepitation: Avg_Precipitation 


## Methodology

To analyse the impact of weather on Covid19 rate of new cases, we shall be doing hypothesis testing and try to find out whether factors like temperature, humidity and precipitation have any relationship with the rate of Covid19 infections.

H0: Weather conditions such as average daily temperature, humidity, precipitation and wind rate have no effect on the rate of new Covid19 cases in 2 cities

H1: Weather conditions such as average daily temperature,  precipitation have effect on the rate of new Covid19 cases in 2 cities

To test our hypothesis, we shall be utilizing one or more of the following models: 
-   Linear Regression Model
-   Support Vector Machines
-   XG Boosting (Gradient Boosting)

**Assumptions:** For our modelling purpose we are taking into consideration following assumptions:
-   There are no extreme deviations in daily average weather parameters
-   Covid testing was available with similar opportunities to the residents of both cities
-   All or none Covid19 precautions were followed by residents of both of the cities 



## Tools:
1.  **Data Analysis:** Python
2.  **Data Storage (Database):** PostgreSQL or SQLite
3.  **Visualization:** Python Libraries or Tableau

## Communication Protocols:
- **Slack group** created for coordination and exchange of ideas/information
- **Weekdays daily calls** to syncup progress and define next steps
- **Weekend calls** to refine outputs and prepare submission for the week
=======

## Introduction 

The new novel corona virus known as Covid19 (SARS CoV-2), has caused one of the most serious health crises globally. There has been lots of word of mouth that, there is some or more impact of weather conditions on the rise of cases of Covid 19 infections. In this project, we shall try to analyse the impact of weather conditions on Covid 19 rates in different cities across the globe. For the purpose of the study, we shall be concentrating on the cities which have similar populations, similar public sentiments towards Covid19 preventions, government measures and vaccination rate.  For the climate factors affecting the Covid19 rate, we shall be considering metrices such as temperature, humidity, precipitation and wind speed.

## Purpose

The purpose of this study is to analyse if there is any impact of weather on Covid19 cases

## Data

**Data Source:**  [Kaggle Weather Data]( https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities) , [Covid Data]( https://saludata.saludcapital.gov.co/osb/index.php/datos-de-salud/enfermedades-trasmisibles/covid19/)

**Data Collection:** Secondary Data Collected from Kaggle and other international observatories

**Variables:** Dependent: Covid19Rate || Independent: Avg_Temperature, Avg_Humiditiy, Avg_Precipitation, Avg_WindSpeed
 
**Scope of project:** Limited to 2 cities data (in future may expand the scope), for given weather variables only

**Data clean-up:** If required, using pandas libraries 

## Definition

- **Covid19 rate**: New daily covid19 cases reported in selected cities per capita population (New daily case / City Population)

- **Weather**: A combination of variables like daily Average Temperature, Average Humidity, Average Precipitation & Average Windspeed 


## Methodology

To analyse the impact of weather on Covid19 rate of new cases, we shall be doing hypothesis testing and try to find out whether factors like temperature, humidity and precipitation have any relationship with the rate of Covid19 infections.

H0: Weather conditions such as average daily temperature, humidity, precipitation and wind rate have no effect on the rate of new Covid19 cases in 2 cities

H1: Weather conditions such as average daily temperature, humidity, precipitation and wind rate have effect on the rate of new Covid19 cases in 2 cities

To test our hypothesis, we shall be utilizing one or more of the following models: 
- Linear Regression Model
- Support Vector Machines
- XG Boosting (Gradient Boosting)

**Assumptions:** For our modelling purpose we are taking into consideration following assumptions:
- There are no extreme deviations in daily average weather parameters
- Covid testing was available with similar opportunities to the residents of both cities
- All or none Covid19 precautions were followed by residents of both of the cities 



## Tools:
- **Data Analysis:** Python
- **Data Storage (Database):** PostgreSQL or SQLite
- **Visualization:** Python Libraries or Tableau

## Communication Protocols:
- **Slack group** created for coordination and exchange of ideas/information
- **Weekdays daily calls** to syncup progress and define next steps
- **Weekend calls** to refine outputs and prepare submission for the week


