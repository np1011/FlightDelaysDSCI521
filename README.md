## Prediction of Airline Delays for US Airports in 2019
## _DSCI521: Group 7, Winter 2023_

## Project Overview

Our project focuses on using an existing dataset that combines historical flight and weather data in order to attempt to predict flight delays. 

Flight delays, for our purposes, are defined as departure delays of over 15 minutes. The [dataset used](https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations?select=train_sets_documentation.txt) covers US flights in 2019 and gathers its data from the Bureau of Transportation Statistics (BTS) and the National Centers for Environmental Information (NOAA).

When scoping our project we hoped to use flight and weather information to predict weather events and flight delays in order to better understand the relationship between weather and flight delays. We anticipated that we would see the effect of severe weather events on flights. We thought there would be variation in weather and delays by airport, because of different weather conditions in different regions. We predicted that the project would allow us to use weather prediction in order to predict flight delays.

As it turned out, the relationship between weather and flight delays was not as strong as we expected. Rather, a variety of non-weather related factors combine with weather to predict flight delays. In line with our expectations, weather had varying impacts dependent on airport location. When this finding became apparent we focused our project on getting accurate flight delay predictions using all the data available to us in our chosen dataset, rather then focusing primarily on weather and/or weather prediction.

### **Code Files**
***GitHub***
- Exploratory_Data_Analysis.ipynb : exploration of data available in the dataset
- Classification_AllUSFlights.ipynb : 5 sklearn models attempt to classify flight delay based on weather data alone & weather plus other flight data for all US airports in 2019
- Classification-Douglas.ipynb : 5 sklearn models to classify flight delay based on weather data alone & weather plus other flight data for Douglas Municipal airport in 2019
- Classification-LaGuardia.ipynb : 5 sklearn models to classify flight delay based on weather data alone & weather plus other flight data for LaGuardia airport in 2019
- Flight_data_NaiveBayes.ipynb : Naive Bayes model to classify flight delay based on weather and other flight data for all US airports in 2019 

## Team Members
!!EDIT ME!!

## Data Used
Original dataset obtained from Kaggle : https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations?select=train_sets_documentation.txt </br>
Modified dataset uploaded to Kaggle : !!EDIT ME!! Add link to Kaggle

Dataset contains information on flights occurring in 2019, with statistics on flight delay, carrier and airport information and weather data.

##### Available Data

The creator of the dataset retrieved from Kaggle removed a number of available data points before generating the final data file. After doing an intial run of the models with the provided data, we went back in and added additional weather data points to improve our results.

##### Original Columns

- **MONTH** - Month
- **DAY_OF_WEEK** - Day of Week
- **DEP_DEL15** - TARGET Binary of a departure delay over 15 minutes (1 is yes, 0 is no)
- **DISTANCE_GROUP** - Distance group to be flown by departing aircraft
- **DEP_BLOCK** - Departure block
- **SEGMENT_NUMBER** - The segment that this tail number is on for the day
- **CONCURRENT_FLIGHTS** - Concurrent flights leaving from the airport in the same departure block
- **NUMBER_OF_SEATS** - Number of seats on the aircraft
- **CARRIER_NAME** - Carrier (airline name)
- **AIRPORT_FLIGHTS_MONTH** - Avg Airport Flights per Month
- **AIRLINE_FLIGHTS_MONTH** - Avg Airline Flights per Month
- **AIRLINE_AIRPORT_FLIGHTS_MONTH** - Avg Flights per month for Airline AND Airport
- **AVG_MONTHLY_PASS_AIRPORT** - Avg Passengers for the departing airport for the month
- **AVG_MONTHLY_PASS_AIRLINE** - Avg Passengers for airline for month
- **FLT_ATTENDANTS_PER_PASS** - Flight attendants per passenger for airline
- **GROUND_SERV_PER_PASS** - Ground service employees (service desk) per passenger for airline
- **PLANE_AGE** - Age of departing aircraft
- **DEPARTING_AIRPORT** - Departing Airport
- **LATITUDE** - Latitude of departing airport
- **LONGITUDE** - Longitude of departing airport
- **PREVIOUS_AIRPORT** - Previous airport that aircraft departed from
- **PRCP** - Inches of precipitation for day
- **SNOW** - Inches of snowfall for day
- **SNWD** - Inches of snow on ground for day
- **TMAX** - Max temperature for day
- **AWND** - Max wind speed for day

##### Added Columns

Weather stat breakdown

- **TMAX** - max temp
- **TAVG** - average temp
- **TMIN** - min temp

WT category - these are true/false so 1 indicates this weather event was present with 0 meaning not present

- **WT01** - fog
- **WT02** - heavy or heavy freezing fog
- **WT03** - thunder
- **WT05** - hail
- **WT07** - blowing dust, sand or other obstruction
- **WT08** - smoke or haze
- **WT09** - blowing or drifting snow
- **WT10** - tornado, waterspout or funnel cloud
- **WT11** - high or damaging winds

## Stakeholders, Use and Intentions

!!EDIT ME!! Analysis would be interesting both to the aviation industry itself, in order to understand factors influencing delay as well as those effected by flight delays (travelers, travel industry stakeholders). We intended to help reveal how weather predicts flight delays, but ultimately found non-weather events are very important for flight delays. We cannot control the weather but we might be able to control some of these other factors. For example, plane age has a very high correlation with flight delay. Could mechanical issues with old planes be causing delays? How can this be avoided?

## Analytic Approach

First, reviewed correlations between existing Kaggle dataset weather data and flight delays. Found that we were missing many potentially important weather data points. Added those weather data points back into dataset before proceeding further. 

Once the dataset was updated we took a variety of approaches to predicting flight delays with the updated dataset. We attempted both a self-written Naive Bayes model as well as a variety of models from sklearn (Logistic Regression, Decision Tree, Gradient Boosting, Random Forest, Random Forest and Extra Trees Classifiers). We selected our models to test based on researching other projects that had attempted both weather and flight prediction.

### **REQUIREMENTS**

**Pre-requisites**<br> 
import os<br>
import pandas as pd<br> 
import numpy as np<br> 
import matplotlib<br> 
import matplotlib.pyplot as plt<br> 
import seaborn as sns<br> 

**Store the classifier models to save time**<br> 
import joblib<br> 

**Sklearn**<br> 
from sklearn.preprocessing import LabelEncoder<br> 
from sklearn.model_selection import train_test_split<br> 
from sklearn.preprocessing import MinMaxScaler<br> 
from sklearn.linear_model import LogisticRegression<br> 
from sklearn.tree import DecisionTreeClassifier<br> 
from sklearn.ensemble import GradientBoostingClassifier<br> 
from sklearn.ensemble import RandomForestClassifier<br> 
from sklearn.ensemble import ExtraTreesClassifier<br> 

**Performance metrics**<br> 
from sklearn.metrics import accuracy_score<br> 
from sklearn.metrics import f1_score<br> 
from sklearn.metrics import precision_score<br> 
from sklearn.metrics import recall_score<br> 
from sklearn.metrics import classification_report<br> 
from sklearn.metrics import confusion_matrix<br> 
from sklearn.metrics import plot_confusion_matrix<br> 
from sklearn.metrics import roc_curve<br> 
from sklearn.metrics import roc_auc_score<br> 
from scipy.stats import pointbiserialr<br> 

### **EXPLORATORY DATA ANALYSIS**
First explores all data points in the dataset then looks for major patterns (most delayed carriers, most delayed airports). Then, drills down into data for the two airports we choose to focus on - LaGuardia and Douglas Municipal - to understand how they contribute to overall system delays and how weather in each location differs.

See full detail in Exploratory_Data_Analysis.ipynb

### **FEATURE SELECTION** 
Feature selection was performed for each grouping of data (All US Flights, LaGuardia and Douglas Municipal). In order to understand and select our features we did the following. Details can be found in Classification_AllUSFlights.ipynb, Classification-LaGuardia.ipynb and Classification-Douglas.ipynb.

1. Observe percentage of delayed vs. non-delayed flights for DEP_DEL15. Delays of over 15 minutes are represented by 1, no delay or delay of under 15 minutes is represented by 0.
2. Observe correlations between continuous and categorical data and DEP_DEL15 using Point Biserial Correlation and Spearman Coefficient, respectively. Weather data was classified as continuous and other flight data (i.e. carrier name, airport, departure time block) are categorical. 
3. Run Feature Importance Ranking using Random Forest Classifier and remove insignificant features from analysis. This aligns with features that have low correlations with DEP_DEL15. Different features were removed for each varition of our modeling attempts.

### **CLASSIFICATION ATTEMPTS**

### ***I. SKLEARN CLASSIFICATIONS***
We decided to use Sklearn for these classifications so that we could easily attempt multiple classification models on the same data in a timely manner. Based on our research of other projects, we decided to use Logistic Regression, Decision Tree, Gradient Boosting, Random Forest and Extra Trees. After running all the classifiers we used ROC AUC analysis to analyze performance of different classifiers. For each grouping of data (All Us, LaGuardia, Douglas) we compared using weather data only to using all available data points (weather and historical flight data) to better understand the significance of weather data for prediction.

The same process, with the same code base, was repeated for All US flights, LaGuardia and Douglas Municipal in order to compare and contrast classification results.

Source documentation and additional detail can be found in Classification_AllUSFlights.ipynb, Classification-LaGuardia.ipynb and Classification-Douglas.ipynb.

### ***II. NAIVE BAYES***
!! EDIT ME !!

## Findings/Results
!!EDIT ME!!
- Weather data was not successful at predicting flight delays. Non-weather factors had the highest correlation with delays. See BTS data given in Classification_AllUSFlights - extreme weather events are not a cause of most delays. Most delays are a mix of weather and the handling of that weather by airports, carriers etc.
- Different airports experienced different weather impacts (LaGuardia vs Douglas).
- Predicting at the airport level was more successful than all US
- Tree-based models performed the best. Could improvements be made in the handling of categorical vs continuous data in order to make other models work? Would additional data pre-processing help?
- 

## Challenges and Limitations
!!EDIT ME!!
- Variable nature of delays made it challenging to predict delays at a national level. We did not seek to add additional features to our dataset, it is possible we could better predict national delays with more data points (such as whether the incoming flight was delayed or whether or not there was an incoming flight).
- We are loooking at only 1 year of data. In a given year weather may be more or less extreme. Maybe we are missing that in some years weather is a more important factor.
- Not all flights originate in the US. Likely there are relationships with factors being ignored in our US-only data.
- Other projects had very high accuracy by using incoming flight delay as a feature. Is this a useful data point in making long term predictions? We only know that the prior flight is delayed shortly before the flight in question is set to take off. How can we use other data points to improve accuracy?
- We did not attempt all potential methods of data-preprocessing or model adjustment. There are many ways to improve upon model accuracy. Future use of he dataset could explore additional modifications. Would those improve results? For example, adding additional trees to our models had a slight positive effect on the accuracy, but it caused the All US model to be overly burdensome to run and difficult to repeat. What methods could be used to improve upon that?

