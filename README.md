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

### Data Sources:  

1.  [Weather Data One time history bulk data for New York City and Sao Paulo City]( https://history.openweathermap.org/storage/fa037ddb81b7f7f0a0d1a0ebd131858e.csv)
2.  [New York daily Covid data from New York CityHealth](https://github.com/nychealth/coronavirus-data/blob/master/trends/data-by-day.csv)
3.  [Sao Paulo daily Covid data from SEADE ](https://raw.githubusercontent.com/seade-R/dados-covid-sp/master/data/dados_covid_sp.csv)


### Variables: 
1.  Dependent: After data discovery , following variable was identified to measure the spread of Covid19. 
    -   7day moving avg new cases per 100,000 population: mavg_7day_per_100k_new_cases
2.  Inependent Variables:After data discovery , following variables were identified to represent weather
    - Moving 15 day average of daily temperature  I,e from reported -14  to reported date -1: mavg_15_temp
    - Moving 15 day average of daily humdity I,e from reported -14 to reported date -1: mavg_15_humidity

### Data Scope:

The project scope is limited to the data for following two citites.
1.	New York City
2.	Sao Paulo City

These cities were selected based common understanding about :
-	Similiar population 
-	no of covid cases 
-	Social distancing and lockdown measures and citizens compliance to those measure
-	but with some variation in weather

## Data Definition (Source and Target)

### Source data defintion

1. Covid metrcis:
    -   Covid19 rate: Total number of Covid cases by 100k inhabitants reported in selected cities per capital population ((New daily case / City Population) *100000) 
2.  Weather metrics: A combination of variables like daily Average Temperature,Average Humidity.
    -   Average daily temparture in celsius: daily_humidity
    -   Average daily humidity: daily_temp 
3. Final Combine Data dictionary

### Target data defintion

![data dict](Images/Data_Dict.png)

## ETL: 

After data discovery phase, we identifed the data sources, transformation logic and target data output required for model and co-relation analysis.The details of the ETL can be found in [Jupyter Notebook to perform full refresh for target file Final_Combine_Data](01_ETL_FullRefresh.ipynb)

## Methodology

To analyse the impact of weather on Covid19 rate of new cases, we shall be doing hypothesis testing and try to find out whether factors like temperature, humidity and their averages have any relationship with the rate of Covid19 infections.

1.	H0: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have no effect on the rate of new Covid19 cases in 2 cities.

2.	H1: Weather conditions such as average daily temperature, humidity, Moving 15 day average of daily temperature, Moving 15 day average of daily humdity have effect on the rate of new Covid19 cases in 2 cities.

To test our hypothesis, we shall be utilizing one or more of the following models: 
-  Correlation
-  Linear Regression Model


We are following the considerations below to complete the analysis:

- 15 days average temperature and humidity up to the day before as this is usually the virus incubation period
- New cases per 100K to compare same size of population
- Moving 7 days average of new cases per 100K to smooth out any reporting anomalies 
- Corelation using different methods . 
- We ran different regressions using 3 data sets: one for each city and one combined. For the combined, we added “is_New York flag” (1= NY, 0=SP)

**Assumptions:** For our modelling purpose we are taking into consideration following assumptions:
-   There are no extreme deviations in daily average weather parameters
-   Covid testing was available with similar opportunities to the residents of both cities
-   All or none Covid19 precautions were followed by residents of both of the cities 

## Data Analysis

### Data Selection Phase 1

- Started with 4 data sets 
1.  [Kaggle Weather Data]( https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities)
2.  [Major Cities Covid Data]( https://saludata.saludcapital.gov.co/osb/index.php/datos-de-salud/enfermedades-trasmisibles/covid19/)
3.  [New York Covid data](https://github.com/nychealth/coronavirus-data)
4.  [Sao Paulo daily covid data](https://github.com/wcota/covid19br/blob/master/DESCRIPTION.en.md)  

**Weather Data:**

-	Kaggle weather data only had temperature and missing data. So we decided to get the weather data from openweathermap.org. Due to historical data needed, we decided to do a one time bulk history pull rather than done api call per city per day.
- 	Weather data was transformed average temperature, average humidity, 1-7 day average, 8-14 day average, percentage change for temperature and humidity variables

**Covid Data:**


- Decided to use Majore Citites Covid Data with the assumption it has cumulative total covid cases per day. so we can demterin the new cases by comparing yestarday numbers with todays.
- For percent postivie cases ,we couldn't find a source with daily metrics available for both citis. so we decided not to use this variable as measure for covid spread.
- Using Major cities covid data source, we performed ETL to get the final variables for city data  like combining two city data set with variables total confirmed cases,cases per million 
- After calculating new cases, some outlier and simple plot we identified this data source has a dip in June which menas we couldn't use the data prior to June. 
- In addition the Major cities covid data source has issues with total cases data format since Mar 2021. The data start showing decimal "." as thousand separatore.
- Due to above mentioned issues we decided not to use the Major cities data and instead use New York CityHealth and SEADE data.

**Below are the screenshots from data issues found in the Major Cities Covid data:**

- Below is New York Citydaily total cases using Major Cities Covid data source 
![NYC_TotalCases](Images/newyork_totalconfirmdataset.png)

- Sao Paulo city's daily total cases using Major cities Covid data source
![SP_TotalCases](Images/SP_totalconfirmdataset.png)

- New York city's daily new cases (calcualted) outlier using Major cities Covid data source
![SP_newcases_outliers](Images/NY_Ave_7day_count.png)

- Sao Paulo city's daily new cases (calcualted) outlier using Major cities Covid data source
![SP_newcases_outliers](Images/SP_Ave_7day_count.png)

**CONLCUSION:**

We decided not to use Majori Cities Covid data and Kaggle weather data. Instead we found covid data from New York CityHealth and Seade Foundation for Sao Paulo.

### Data Selection and preliminary analysis

- We found following data sources reliable source of covid data and weather data.

1.  [Weather Data]( https://history.openweathermap.org/storage/fa037ddb81b7f7f0a0d1a0ebd131858e.csv)
2.  [New York Covid data](https://github.com/nychealth/coronavirus-data/blob/master/trends/data-by-day.csv)
3.  [Sao Paulo daily covid data](https://raw.githubusercontent.com/seade-R/dados-covid-sp/master/data/dados_covid_sp.csv)

- A quick analysis is done in Excel to evalutate qualtify of data and initial data analysis: [Excel Analysis](00_data_discovery_phase.xlsx) 

- Below charts show that using moving 7 day average for new cases is a better choice as it will remove any reported anamolies found in reported new cases for two cities.

**New York City daily new cases vs 7 days moving averages of new cases:**

![New York Daily new cases vs new cases 7 day moving average](Images/NYC_7day_Avg.png)

**Sao Paulo City daily new cases vs 7 days moving averages of new cases:**

![Sao Paulo Daily new cases vs new cases 7 day moving average](Images/SP_7day_Avg.png)

- To further smoothen the city data 7 day moving average per 100k population was pciked for modeling.

**Compare New York city and Sao Paulo city using 7 days moving averages of new cases:**

![7_AVG_100k](Images/7-day_avg_100k_newcases.png)

**New York City and Sao Paulo City weather data:**

- The new weather data includes variables like average and 15 average for temperature and humidity as incubation period is 15 days 

![15_Ave_temp](Images/15day_avg_temp.png)

![15_Ave_humidity](Images/15day_avg_humidity.png)

**Compare New York City 7 days moving averages of new cases per 100K population vs New York daily average temperature:**

- New York Citydaily new cases per 100K vs daily average temperature
![NYC_daily_covid_vs_temp](Images/NY_7Day_Avg_NewCases_per_100k_and_Avg_15Day_Temp.png)

**Compare Sao Paulo City 7 days moving averages of new cases per 100K population vs New York daily average temperature:**
-	SPC daily new cases per 100K vs daily average temperature
![SPC_daily_covid_vs_temp](Images/SP_7Day_Avg_NewCases_per_100k_and_Avg_15Day_Temp.png)

#### Concludsion from preliminary data analysis

1.	New York city new cases and daily average temperature followed simliar trend.
2.	Sao Paulo City 2020 data for new caes and temperature have similar trend but 2021 covid cases doesn't follow the daily temperature trend closely.
3.	New York City weather temperature variaes a lot throughout the year, while Sao Paulo temperature swings between seasons staing within 10-25 degree celsius. 
4.	Both cities humidity level throughouu the year stays above 40% .


## Models and correlation 

**Link to jupyter notebooks**
- Correlation analysis: [Correlation](03_Model_Analysis_Correlation.ipynb)
- [3 Datasets Regression using all 14.5 month data and using both temp and humidity](04_Model_Analysis_Regression_AllData_TempAndHumidity.ipynb)
- [3 Datasets Regression using all 14.5 month data and using only temp or only humidity](05_Model_Analysis_Regression_AllData_TempOnly.ipynb)
- [3 Datasets regression using 13.5 months data for train and 1 month for test](06_Regression_train_test.ipynb)

### Correlation

For correlations, we used spearman correlation as it works better with non linear realtionship.

- New York Correlation 

![NYC_C](Images/NYC_MNew_Correlation.png)

- Sau Paulo Correlation

![SP_C](Images/SP_MNew_Correlation.png)

- All viarbales correlation between the new transformed data 

![New_Variables](Images/Correlation_finaldataset.png)


- Pairplot to see relationship on the various columns in 2 cities i.e between Moving Average New Cases per 100k with Moving Avg 15 days Tempreture and Humidity

![PP](Images/pairplot.png)

### Regression Model

#### Using all data for training


During this phase of model run, we used all 14.5 months data for training on 3 different data sets (one for each city and one combined cities data)

**Using both temeprature and humidity for weather:**

-	**New York regression model using full 14.5 months data for training:**
![NYC_Regression](Images/NYC_MNew_Regression.png)

-	**Sao Pulo regression model using full 14.5 months data for training:**
![SP_Regression](Images/SP_MNew_Regression.png)

-	**Combined New York and Sao Pulo regression model using full 14.5 months data for training:**
![SP_NYC_Regression](Images/SP_NYC_MNew_Regression.png)


**Using temeprature ONLY for weather:**

-	**New York regression model using full 14.5 months data for training:**
![NYC_temponly_Regression](Images/NYC_MNew_tempOnly_Regression.PNG)

-	**Sao Pulo regression model using full 14.5 months data for training:**
![SP_temponly_Regression](Images/SP_MNew_tempOnly_Regression.PNG)

-	**Combined New York and Sao Pulo regression model using full 14.5 months data for training:**
![SP_NYC_temponly_Regression](Images/SP_NYC_MNew_tempOnly_Regression.PNG)

#### Conclusion using all 14.5 months data

1.	Temperature only model had lower accuracy compared to temperature and humidity both to define weather. 
2.  While New York only model gives a much higher accuracy then combined or Sao Paulo only, but model will not give better prediction for Sao Paulo
3.  Combined cities data has accuracy dropped by 1/2 compared to New York only accuracy. But it can predict both cities.
4. 	Eventhough the accuracy rate is high with no test data, the accuracy rate is lowe and with no test data it is overfitting. 

### Using 1 month for testing and 13.5 months for training

During this phase of model, we train model using 13.5 months of data (from Feb 29,200 to Apr 15, 2021) on 3 different data sets. we used both temperature and humditiy from weather data.

-	**New York regression model using full 13.5 months data for training:**
![NYC_traintest_Regression](Images/NYC_MNew_train_test_Regression.PNG)

-	**Sao Pulo regression model using full 13.5 months data for training:**
![SP_traintest_Regression](Images/SP_MNew_train_test_Regression.PNG)

-	**Combined New York and Sao Pulo regression model using full 13.5 months data for training:**
![SP_NYC_traintest_Regression](Images/SP_NYC_MNew_train_test_Regression.PNG)

-	** p-values from OLS method using combined data and 13.5 months of data used for training:**
![SP_NYC_OLS_MODEL_P_Value](Images/p_value_using_combined_test_train_OLS_model.PNG)

#### Conclusion from model using 13.5 monnths data for training

1.	The negative R-squared values from individual cities models are going to results in wrong model.
2.	In addition we conclude that while model trained on 13.5 months data for combined cities has 37% accuracy, but we should use this as final model as it follows best practices.
3.	Based on p values from different models and final model, we failed null hypthoesise. 
4.	Low accruacy means that our final model is not good enough to predict impact of change in temperature or humdity on new covid cases.
### Future analysis recomendation

We concluded that there are certain other factors that are impacting the covid spread which were out of scope of this project. In order to further improve our model, we've following recomendations:

1.	Remove impact of other variables if can be measured.
	
	-	vaccination rate
	-	Positive cases related to Brazilian mutant, which spread faster than the original.
	-	Active cases in the city
	-	Complaince to lockdown restrictions

2.	Run the analysis using additional city data with similar cities.

	-	Add more cities with diverse conditions to understand the behavior of Covid cases compare to different temperatures

3.	Use time series methodologies on the new cases variable before running the regression


## Analysis of Project using Google sheets:
-	[**Presentation Google link**](https://drive.google.com/file/d/17RzsmALKxAVrjdY_FZRhpZPeYnp8apSj/view?usp=sharing)
-	[**Presentation Git hub link**](Group_5_Final_Presentation_v3.ppt)

## Tools:
1.  **Data Analysis:** Python
2.  **Data Storage (Database):** PostgreSQL but later we did not use database as the data set size was small
3.  **Visualization:** Google Sheets

## Communication Protocols:
- **Slack group** created for coordination and exchange of ideas/information
- **Weekdays daily calls** to syncup progress and define next steps
- **Weekend calls** to refine outputs and prepare submission for the week
