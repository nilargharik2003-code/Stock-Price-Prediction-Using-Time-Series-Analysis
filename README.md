# Stock-Price-Prediction-Using-Time-Series-Analysis
# Stock Price Prediction Using Time Series Analysis

## 📌 Project Overview

This project focuses on analyzing and forecasting the daily closing price of **Tata Motors Limited** using **Time Series Analysis** and the **ARIMA (Autoregressive Integrated Moving Average)** framework.

The project uses historical Tata Motors stock-price data from the **National Stock Exchange (NSE)**. The analysis follows a systematic time-series workflow, beginning with exploratory analysis and visualization, followed by trend and seasonality analysis, stationarity testing, differencing, ACF/PACF analysis, ARIMA model fitting, and short-term forecasting.

The original analysis was performed in R and was implemented in Python using equivalent statistical and time-series libraries.

---

## 🎯 Objectives

The main objectives of this project are:

- Analyze the historical movement of Tata Motors stock prices.
- Identify the underlying trend in the stock-price series.
- Examine possible seasonal patterns using different periods.
- Test whether the time series is stationary.
- Transform the non-stationary series into a stationary series using differencing.
- Analyze autocorrelation and partial autocorrelation using ACF and PACF.
- Fit an ARIMA-based time-series model to the stock-price data.
- Compare observed and fitted values.
- Generate short-term forecasts with confidence intervals.

---

## 📊 Dataset

The dataset contains historical daily stock-price observations of Tata Motors.

### Dataset Information

- **Company:** Tata Motors Limited
- **Exchange:** National Stock Exchange (NSE)
- **Observation period:** 4 May 2023 – 12 June 2024
- **Number of observations:** 277
- **Primary variable used:** Closing Price
- **Time variable:** Date

Although the original dataset contains multiple market-related variables, the analysis primarily focuses on the **daily closing price**, which is treated as the time-series variable.

---

## 🛠️ Technologies and Libraries

The project was implemented using Python.

### Programming Language
- Python

### Libraries

- **Pandas** – Data loading, preprocessing, and manipulation
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Statsmodels** – ADF test, ACF/PACF analysis, and ARIMA/SARIMAX modelling

---

## 🔄 Project Workflow

The complete analysis follows these steps:

1. Data Loading and Preprocessing
2. Exploratory Time-Series Visualization
3. Moving Average Analysis
4. Seasonality Analysis
5. Augmented Dickey-Fuller (ADF) Test
6. First-Order Differencing
7. Trend Analysis
8. ADF Test after Differencing
9. Autocorrelation Function (ACF)
10. Partial Autocorrelation Function (PACF)
11. ARIMA Model Fitting
12. Observed vs Fitted Values
13. Short-Term Forecasting
14. Interpretation and Conclusion

---

# 1. Data Loading and Preprocessing

The dataset is loaded using Pandas. The `Date` column is converted into a date-time format and used as the time index.

The closing price is extracted as the primary time-series variable.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

tata_stock_data = pd.read_csv("TATA_Motors_277_Days_Data.csv")

tata_stock_data["Date"] = pd.to_datetime(
    tata_stock_data["Date"],
    format="mixed"
)

tata_stock_data = tata_stock_data.set_index("Date")

tata_ts_data = tata_stock_data["Price"].iloc[::-1]
