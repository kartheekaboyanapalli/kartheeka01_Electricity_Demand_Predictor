### Hourly Electricity Demand Batch Prediction Service
---
# Project Overview
---
This project presents an end-to-end, production-ready electricity demand forecasting system designed to optimize energy supply and reduce operational costs for Public energy company. Utilizing MLOps best practices. The solution is fully automated, integrating data collection, feature engineering, model training, inference, and continuous monitoring into a seamless ML pipeline. access the app here .

### Business Problem
---
Public Energy Company encounters several operational challenges in managing electricity supply across various NYC locations:

* Overproduction: Generating excess electricity, leading to increased costs and energy waste.
  
* Shortages: Underestimating peak demand, causing power outages and lowering customer satisfaction.

* Resource Misallocation: Inefficient distribution of electricity resources, impacting operational efficiency and increasing the carbon footprint.

* These issues lead to higher operational expenses, reduced profitability, and lower customer satisfaction.
  
### ML Problem
---
Accurately predict electricity demand for the next hour to align energy generation with forecasted demand. This ensures optimal resource allocation, enhances operational efficiency, and improves customer satisfaction.

### Data Sources
---
To ensure accurate predictions, we use multiple data sources:

     * Historical electricity Demand Data: Fetched from EIA API.
     
     * Weather Data: Historical weather information retrieved from Openmeteo Weather API.
     
     * Calendar Events: Public holidays extracted using pandas.tseries.holiday.

### Project methodalgy
Our methodalgy features three-stage ML pipelines, leveraging modern MLOps principles such as feature stores, model registries, and automated inference to ensure scalability and reliability.

### 1. Feature Pipeline
This pipeline fetches and preprocesses the required data, transforms it into a time-series format, and stores it in the Hopsworks Feature Store.

**Steps:**
1.Fetch historical electricity demand data from the EIA API.

2.Fetch historical weather data (temperature) from OpenWeatherMap API.

3.Merge data sources based on timestamps.

4.transform data into time series format

5.Store transformed data in the Hopsworks Feature Store.

### 2.Training Pipeline
This pipeline fetches data from the feature store, processes it into feature-target format, trains a machine learning model, and evaluates it before saving the trained model in the Hopsworks Model Registry.

**Steps:**
1.Load preprocessed time series data from the feature store.

2.Transform data into features and target:

***Prediction Target:** Hourly electricity demand for NY.

***Features:**
     Hourly temperature for NY
     Lag-based features
     
3.Train a LightGBM model with hyperparameter tuning using Optuna with 5-fold cross-validation.

4.Implement feature engineering:
    * Adding US Federal Holidays using pandas.tseries.holiday.
    * Incorporating time-series features (lags, rolling statistics).
    
5.Evaluate the model using Mean Absolute Error (MAE).

6.Store the trained model in the Hopsworks Model Registry.





