# Influence of Weather on Covid Spread


## Overview

The pursose of this project is to analyse data on weather and covid cases data from two cities so as to determine if weather plays a key role in the raise of covid positives.

## Data
Data Source:
- [New York Covid cases data set](https://health.data.ny.gov/Health/New-York-State-Statewide-COVID-19-Testing/xdss-u53e)
- [NYC Weather data](https://www.wunderground.com/history/daily/us/ny/new-york-city/KLGA/date/2020-3-1)
- [Sao Paulo Covid cases data set](https://covid.saude.gov.br/)
- [Sau Paulo Weather data](https://www.worldweatheronline.com/sao-paulo-weather-history/sao-paulo/br.aspx)

## Variables:
- Dependent Variable -Covid-19 count
- Independent Variables -Average temperatures, Average Humidity, Average precipitation


## Definations
Covid 19 count: Day to day Count of new Covid 19 cases from the selected cities 
Weather: Daily Average of temperatures, Humidity, Precipitation
Comparing cities: based on positive cases and population of both the cities

## Machine Learning Model

- Assess the impact of various weather related variables on covid cases using hypothesis testing and evaluating p-values
- Build machine learning model such as XGBoost, Random Forest to estimate how accurately weather data can be used to predict covid cases
- Independent variables are weather information such as humidity, precipitation, temperature for each selected cities
- Depedent/Target variable - Covid cases per 100K total population for each cities

## Assumptions
- Tests were conducted similarly for the whole population at both the cities
- Weather Changes were not drast at both the cities

## Tools
Datbase: PostGres database  
ETL: Python or SQl  
Machine Learning Model: Python  
Visualization: Tableau or Python  




