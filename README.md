## Prediction of Airline Delays due to local weather
## _DSCI521: Group 7, Winter 2023_

## Project Overview

Our project focuses on using an existing dataset that combines historical flight and weather data in order to attempt to predict flight delays. 

Flight delays, for our purposes, are defined as departure delays of over 15 minutes. The [dataset used](https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations?select=train_sets_documentation.txt) covers US flights in 2019 and gathers its data from the Bureau of Transportation Statistics (BTS) and the National Centers for Environmental Information (NOAA).

When scoping our project we hoped to use flight and weather information to predict weather events and flight delays in order to better understand the relationship between weather and flight delays. We anticipated that we would see the effect of severe weather events on flights. We thought there would be variation in weather and delays by airport, because of different weather conditions in different regions. We predicted that the project would allow us to use weather prediction in order to predict flight delays.

As it turned out, the relationship between weather and flight delays was not as strong as we expected. Rather, a variety of non-weather related factors combine with weather to predict flight delays. In line with our expectations, weather had varying impacts dependent on airport location. When this finding became apparent we focused our project on getting accurate flight delay predictions using all the data available to us in our chosen dataset, rather then focusing primarily on weather and/or weather prediction.

## Team Members


## Data Used
Dataset obtained from Kaggle : https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations?select=train_sets_documentation.txt

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

## Analytic Approach
#### **Phase 1**
Reviewed correlations between existing Kaggle dataset weather data and flight delays. Found that we were missing many potentially important weather data points. Added those weather data points back into dataset before proceeding further. 

### **Phase 2**
Take a variety of approaches to predicting flight delays with the updated dataset. We attempted both a self-written Naive Bayes model as well as a variety of models from sklearn (Logistic Regression, Decision Tree, Gradient Boosting, Random Forest, Random Forest and Extra Trees Classifiers). We selected our models to test based on researching other projects that had attempted both weather and flight prediction.

### SKLEARN Classifiers

#### Set up Environment

**Pre-requisites**<br> 
import pandas as pd<br> 
import numpy as np<br> 
import matplotlib<br> 
import matplotlib.pyplot as plt<br> 
import seaborn as sns<br> 

**Store the classifier models to save time**<br> 
import joblib<br> 

**Sklearn**
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


## Findings/Results

## Challenges and Limitations

