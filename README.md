# HCltech_Hackathon

#  **Daily Delhi Climate Time Series Forecasting Model*

##  1. Problem Statement
Accurate time series forecasting helps in climate research, agriculture planning, environmental monitoring, and energy management.  
This project builds an *end-to-end forecasting system* using Daily Delhi Climate Data to predict future temperature trends.

The pipeline includes:  
 Data ingestion  
 Preprocessing  
 Exploratory Data Analysis (EDA)  
 Feature engineering  
 Multiple forecasting models  
 Evaluation  
 Deployment via UI/API  



## 📊 2. Dataset Information
*Dataset:* Daily Climate Time Series Data (Delhi, India)  
*Source:* Kaggle  
*Rows:* ~1450 daily observations  
*Columns:*
- date
- meantemp
- humidity
- wind_speed
- meanpressure

*Target Variable:* meantemp  
*Frequency:* Daily  



##  3. System Architecture


 Raw Dataset → Ingestion (SQLite) → Preprocessing → EDA →
 Feature Engineering → Modeling → Evaluation → Deployment (UI/API)




##  4. Data Ingestion
- CSV loaded into a pandas DataFrame  
- Inserted into *SQLite* as climate.db  
- Table name: delhi_climate  
- Read back into DataFrame for processing  
- date column converted to datetime and set as index  



##  5. Preprocessing Steps
Performed essential cleaning:

# Step 1: Convert date to datetime & set as index  
# Step 2: Sort data chronologically  
# Step 3: Remove duplicate dates  
# Step 4: Handle missing values (ffill → bfill)  
# Step 5: Detect and correct outliers (Z-score method)  
# Step 6: Convert all data to numeric  
# Step 7: Optional scaling for ML/LSTM models  

Result: Clean, continuous, model-ready time series dataset.



# 6. Exploratory Data Analysis (EDA)
Conducted visual and statistical analysis:

- Line plot of mean temperature  
- Yearly and seasonal patterns  
- Seasonal decomposition (trend, seasonal, residual)  
- Distribution analysis of all features  
- Correlation heatmap  
- Outlier visualization  

Key insights:  
- Strong yearly temperature seasonality  
- Humidity and pressure influence temperature  
- Data trends show expected climate behavior  



# 7. Feature Engineering

To improve model performance, the following features were created:

# Lag Features
- lag_1, lag_7, lag_14, lag_30

# Rolling Window Features
- roll_mean_7, roll_mean_30  
- roll_std_7

# Date-time Features
- Day of week  
- Month  
- Year  
- Day of month  

These help ML and neural models learn temporal relationships.



# 8. Modeling Approaches

Multiple models were built and evaluated:

# Baseline Model
- Last value carried forward

# Statistical Models
- ARIMA  
- SARIMA  
- SARIMAX (with regressors)

# Prophet Model
- Captures yearly and weekly patterns

# Machine Learning Models
- Linear Regression  
- Random Forest  
- XGBoost Regression  

# Deep Learning Model (Optional)
- LSTM for sequence prediction  

Models were trained using 80% of data and tested on 20% (time-based split).



# 9. Evaluation Metrics

Models were evaluated using:

- *RMSE* – Root Mean Squared Error  
- *MAE* – Mean Absolute Error  
- *MAPE* – Mean Absolute Percentage Error  
- *R² Score* (for ML models)

Visual evaluation:
- Actual vs Predicted plot  
- Forecast future 30-day temperatures  
- Residual analysis  



# 10. Deployment

Two deployment options available:

# Streamlit Interface
- Upload CSV  
- View EDA charts  
- Generate forecast  
- Display future trend graph  

# FastAPI / Flask API
- /predict endpoint returns JSON forecast  
- Can integrate with dashboards/UI  



# 11. Project Folder Structure


.
├── data/
│   └── DailyDelhiClimateTrain.csv
├── database/
│   └── climate.db
├── notebooks/
│   ├── 01_preprocessing.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_modeling.ipynb
│   └── 05_forecasting.ipynb
├── src/
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── model_arima.py
│   ├── model_ml.py
│   ├── evaluate.py
│   └── utils.py
├── app/
│   └── streamlit_app.py
├── README.md
└── requirements.txt




# 12. How to Run the Project

# *1. Install dependencies*

pip install -r requirements.txt


# *2. Run preprocessing & EDA notebooks*
Use Jupyter or Google Colab.

# *3. Train models*
Run modeling notebooks.

# *4. Run Streamlit app*

streamlit run app/streamlit_app.py




# 13. Deliverables

- Cleaned dataset & SQLite DB  
- Preprocessing pipeline  
- EDA visualizations & insights  
- Feature engineering notebook  
- Models (ARIMA, Prophet, ML)  
- Evaluation metrics  
- Forecast visualization  
- Deployment UI/API  
- Final README + repository structure  



# 14. Conclusion

This project demonstrates a complete *time series forecasting pipeline* using real-world climate data.  
It is extendable to:

- Weather prediction systems  
- Agricultural planning  
- Energy demand forecasting  
- Environmental monitoring  

The modular code allows easy swapping of models and datasets for future scaling.


      
       
