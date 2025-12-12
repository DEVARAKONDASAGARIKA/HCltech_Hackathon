HCL Tech Stock Time Series Forecasting — README

This repository contains a complete workflow for time-series forecasting of HCL Technologies Ltd. stock data, implemented using Python in a Jupyter Notebook.
The notebook includes data ingestion, preprocessing, EDA, stationarity checks, model building, forecasting, and evaluation.

HCL_Tech.ipynb                                      # Main notebook
README.md                                           # Documentation
kaggle_weather_2013_to_2024.csv                     # CSV file
Design_timeseriesforecast.md                        # Design (pipeline)

1. Introduction
This project performs end-to-end time series analysis on HCL Tech stock prices.
The goal is to build a forecasting model using techniques like:
ARIMA / SARIMA
Prophet
LSTM (if used)
Moving averages
Exponential smoothing
The notebook demonstrates how stock prices evolve over time and generates future predictions.

Data Ingestion Layer
Source:
The dataset is loaded from the local environment and optionally inserted into an SQL database through the implemented data ingestion layer.
Steps included:
Loading CSV
Creating SQLite DB
Pushing cleaned data into DB table
Fetching back from DB
Schema validation
Checking nulls
Data types
Column names
Missing values
Outliers

Exploratory Data Analysis (EDA)
Visualizations included:
Line plot of closing price
Volume trends
Moving averages
Seasonal decomposition (trend, seasonality, residuals)

Stationarity Checks
Methods used:
Augmented Dickey-Fuller (ADF) test
Rolling statistics
Differencing
ADF Hypothesis
H₀: Series is non-stationary
H₁: Series is stationary

Model Building
Depending on your notebook content, models may include:
ARIMA / SARIMA
p, d, q parameter selection
AIC comparison

Forecasting Results
Predictions generated for:
Next 30 days period

Model Evaluation
Metrics used:
Naive Forecast(BaseLine)
RMSE         0.346
MAE          0.277
MAPE         20%

ARIMA:
RMSE         5.90
MAE          4.61
MAPE         20.72%

SARIMA:
RMSE         5.370
MAE          4.256
MAPE         19%

HOLT WINTER:
RMSE         7.483
MAE          6.298
MAPE         27.59%

ETS:
RMSE         7.479
MAE          6.30
MAPE         27.6%

Conclusion:
Summaries may include:
The model that performed best
Observations from trends and patterns
Forecasting reliability
Limitations
Example:
The SARIMA(1,1,1)(1,0,1)[12] model provided the lowest RMSE and captures seasonal trends effectively.

How to Run:
jupyter notebook HCL_Tech.ipynb
