# Impact of climate variables on Covid 19 cases

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

