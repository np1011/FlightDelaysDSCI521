## Prediction of Airline Delays due to local weather
## _DSCI521: Group 7, Winter 2023_

## Project Overview

Our project focuses on using an existing dataset that combines historical flight and weather data in order to attempt to predict flight delays. 

Flight delays, for our purposes, are defined as departure delays of over 15 minutes. The [dataset used](https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations?select=train_sets_documentation.txt) covers US flights in 2019 and gathers its data from the Bureau of Transportation Statistics (BTS) and the National Centers for Environmental Information (NOAA).


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

## Findings/Results

## Challenges and Limitations

