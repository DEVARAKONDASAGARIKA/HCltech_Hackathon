# Climate Time-Series Forecasting and Regression Analysis (Delhi Weather 2013–2024)

This project is developed for the HCLTech Hackathon under the Data Science track. It focuses on end-to-end data processing, exploratory data analysis (EDA), feature engineering, and regression modeling using climate data from Delhi (2020–2024).

---------------------------------------------------------
1. Problem Statement
---------------------------------------------------------

The objective is to build a complete data science pipeline that prepares weather data for time-series forecasting and regression tasks. The project aims to analyze climate trends, engineer useful features, clean the dataset, and build predictive models to estimate maximum temperature.

---------------------------------------------------------
2. Dataset Description
---------------------------------------------------------

Dataset: Daily weather observations for Delhi from 2013 to 2024 (filtered to 2020–2024).

Main variables:
- Temperature: temp, tempmax, tempmin, feelslike, heat_index  
- Humidity: humidity  
- Wind: windspeed  
- Pressure: sealevelpressure  
- Precipitation: precip, precipprob, precipcover  
- Date information: DATE column used to derive additional time-based features  

---------------------------------------------------------
3. Project Pipeline
---------------------------------------------------------

Step 1: Data Ingestion
- Loaded CSV file into Pandas
- Saved dataset into SQLite database (climate.db)
- Retrieved data using SQL queries

Step 2: Data Preprocessing
1. Missing Values:
   - Numeric columns: linear interpolation  
   - Categorical fields: forward/backward fill  

2. Outlier Treatment:
   - Applied percentile clipping (1st–99th percentile)

3. Stationarity Check:
   - Performed Augmented Dickey-Fuller (ADF) test  
   - Applied differencing for non-stationary features  

4. Scaling:
   - Used MinMaxScaler on numeric columns  

---------------------------------------------------------
4. Feature Engineering
---------------------------------------------------------

1. Time-based features:
   - year, month, day, weekday, dayofyear, weekofyear

2. Season classification:
   - Winter, Summer, Monsoon, Autumn

3. Holiday indicator:
   - Marked major holidays from 2020–2024

4. Interaction features:
   - temp_range = tempmax - tempmin  
   - humidity_temp_interaction  
   - wind_temp_interaction  

5. Derived features:
   - heat_index using custom formula

6. Feature Selection:
   - Used correlation matrix to identify top predictors

---------------------------------------------------------
5. Exploratory Data Analysis (EDA)
---------------------------------------------------------

Performed detailed EDA to understand data distribution, patterns, and relationships.

Analyses include:
- Distribution plots (histograms and KDE plots)
- Boxplots for outlier visualization
- Correlation heatmap
- Temperature trend plots (2020–2024)
- Seasonal temperature analysis
- Scatter plots (temperature vs humidity)

Key observations:
- Temperature values follow stable, near-normal distribution  
- Humidity varies significantly across seasons  
- Pressure is tightly grouped  
- Strong correlations among temperature-based features  
- Negative correlation between temperature and humidity  

---------------------------------------------------------
6. Regression Modeling
---------------------------------------------------------

Objective: Predict maximum temperature (tempmax)

Models used:
- Linear Regression  
- RandomForest Regressor  

Data split:
- 80% training  
- 20% testing  

Metrics computed:
- RMSE  
- MAE  
- MAPE  
- Weighted MAPE  
- R² Score  

Random Forest outperformed Linear Regression.

Hyperparameter tuning was done using GridSearchCV with:
- n_estimators: [100, 200, 300]
- max_depth: [5, 10, 20, None]
- min_samples_split: [2, 5, 10]

Best model: Tuned RandomForest.

---------------------------------------------------------
7. Tech Stack
---------------------------------------------------------

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- SQLite3  
- Scikit-Learn  
- Statsmodels  
- Google Colab  

---------------------------------------------------------
8. Folder Structure
---------------------------------------------------------

climate.db  
notebook.ipynb  
README.md  
dataset.csv  

---------------------------------------------------------
9. Future Enhancements
---------------------------------------------------------

- Implement SARIMA, Prophet, or LSTM for time-series forecasting  
- Build visualization dashboard using Streamlit  
- Deploy model using Flask or FastAPI  
- Build automated retraining pipeline  



