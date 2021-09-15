# Krakow Air Quality Prediction Project: Project Overview
* Created a tool that estimates air pollution quality in Krakow (RMSE PM 1.0) to help Krakowians aviod areas with harmful particles as a result of bad air quality
* Engineered features combining data from 55 low cost censors throughout the region of Krakow into one dataset
* Uses Linear Regression and Random Forest Regressors to create the models

## Code and Resources Used
* **Python Version:** 3.8.3
* **Packages:** pandas, numpy, sklearn, matplotlib, seaborns
* **Dataset:** https://www.kaggle.com/datascienceairly/air-quality-data-from-extensive-network-of-sensors

## Data Cleaning
I needed to clean the data so that it is usable for our model. I made the following changes and created the following variables:
* Combined 12 different months of dataframes into 1 big dataframe
* Removed columns with more than 10% of the data missing
* Combined data from 55 different sensors into one
* Created latitude and longitude columns using location dataframe
* Filled in the remainning data with the average from each months 
* Removed humidity columns since the number do not make sense

With over 230,000 rows, we have the follwing columns after data cleaning:
* UTC time
* temperature (celcius)
* pressure (hPa)
* pm1
* pm25
* pm10
* latitude
* longitude

## EDA
I looked at the distribution of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables.

![alt text](https://github.com/Panasak/Krakow_Air_Project/blob/main/data_sets/pm1_bar_month.png)
![alt text](https://github.com/Panasak/Krakow_Air_Project/blob/main/data_sets/pm1_distplot.png)
![alt text](https://github.com/Panasak/Krakow_Air_Project/blob/main/data_sets/heatmap.png)

## Model Building
First I transformed the categorical data into dummy variables (latitudes and longitudes). I also split the data into train and test sets with a test size of 30%

I tried two different models and evaulated them using Root Mean Squared Error. I choose RMSE because it is relatively easy to interpret and outliers aren't paticularly bad for this type of model.

I tried two different models:

* **Multiple Linear Regression** - Basedline for the model
* **Random Forest** - Based on the sparse data from the many categorical variables. I thought a random forest would be effective

## Model Performance
The Random Forest model far outperformed the other approach on the test and validation sets

* **Multiple Linear Regression:** RMSE = 2.82
* **Random Forest:** RMSE = 1.58

## 
