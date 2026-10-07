# Stock-Price-Prediction-Using-Time-Series-Analysis
# Stock Price Prediction Using Time Series Analysis 📈

This project focuses on analyzing and forecasting the daily closing price of **Tata Motors** using **Time Series Analysis** and the **ARIMA (Autoregressive Integrated Moving Average)** framework. The analysis examines trend, seasonality, stationarity, autocorrelation, and short-term forecasting performance using historical stock-price data.

## 💾 Data Description

The analysis uses historical daily stock-price data of **Tata Motors Limited** from the **National Stock Exchange (NSE)**.

### Dataset Information

* **Company:** Tata Motors Limited
* **Exchange:** National Stock Exchange (NSE)
* **Observation Period:** May 2023 – June 2024
* **Number of Observations:** 277
* **Primary Variable:** Daily Closing Price
* **Time Variable:** Date

The closing price was used as the primary time-series variable for the analysis.

***

## 🛠️ Methodology Summary

The time-series analysis involved the following stages:

### 1. Data Preprocessing

* The dataset was loaded using **Pandas**.
* The `Date` variable was converted into datetime format and used as the time-series index.
* The **closing price (`Price`)** was extracted as the primary variable for analysis.
* The observations were arranged chronologically before performing the time-series analysis.

### 2. Trend Analysis

* Moving averages were calculated using window sizes of **4, 9, 16, 18, 27, and 35 observations**.
* These moving averages were used to smooth short-term fluctuations and examine the underlying trend in Tata Motors' stock price.

### 3. Seasonality Analysis

* Seasonality was investigated using different periods:
  * 4
  * 9
  * 16
  * 18
  * 27
  * 35
* The resulting time-series plots were examined to identify possible recurring patterns.

### 4. Stationarity Testing

* The **Augmented Dickey-Fuller (ADF) test** was applied to the original closing-price series.
* The original series produced an ADF statistic of **-0.4513** with a p-value of **0.9012**.
* Since the p-value was greater than 0.05, the original series was considered **non-stationary**.
* First-order differencing was therefore applied.
* The ADF test was then repeated on the differenced series, producing an ADF statistic of **-17.4563** and a p-value of approximately **4.62 × 10⁻³⁰**.
* The differenced series was therefore considered **stationary**.

### 5. ACF and PACF Analysis

* The **Autocorrelation Function (ACF)** was examined to investigate possible moving-average behaviour.
* The **Partial Autocorrelation Function (PACF)** was examined to investigate possible autoregressive behaviour.
* Neither plot showed a clear low-order AR or MA structure that could unambiguously determine the model orders.

### 6. ARIMA Model Fitting

* The final model used in the project was:

**ARIMA(0,1,0)(0,0,1)[35] with drift**

* The model was implemented in Python using the **SARIMAX** implementation available in `statsmodels`.
* The model was fitted to the Tata Motors closing-price time series.

### 7. Model Evaluation and Forecasting

* Fitted values were obtained from the trained model and compared with the observed stock prices.
* The fitted values closely followed the historical price movements.
* A **10-step short-term forecast** was generated using the fitted model.
* Forecast confidence intervals were also calculated and visualized to represent uncertainty in the predictions.

***

## 📊 Results Summary

| Analysis | Result |
| :--- | :--- |
| **Original Series ADF Statistic** | -0.4513 |
| **Original Series p-value** | 0.9012 |
| **Original Series** | Non-Stationary |
| **Differencing Applied** | First-Order Differencing |
| **Differenced Series ADF Statistic** | -17.4563 |
| **Differenced Series p-value** | 4.62 × 10⁻³⁰ |
| **Differenced Series** | Stationary |
| **Final Model** | ARIMA(0,1,0)(0,0,1)[35] with Drift |
| **Forecast Horizon** | 10 Steps |
| **Forecast Confidence Interval** | Generated |

***

## 🔍 Observation

The analysis showed that the original Tata Motors closing-price series was **non-stationary**, as indicated by the high p-value of the ADF test. After applying first-order differencing, the series became stationary, confirming that differencing was required before fitting the ARIMA model.

The ACF and PACF plots did not provide a clear low-order AR or MA structure. The final ARIMA model was therefore fitted based on the model specification used in the original analysis.

The **observed vs fitted plot** showed that the fitted values closely followed the historical stock-price movements, indicating that the model captured the major patterns in the observed series.

Finally, the model was used to generate a **10-step short-term forecast** along with confidence intervals. The increasing width of the confidence interval reflects greater uncertainty as the forecast moves further into the future.

Overall, the analysis demonstrates how **ARIMA-based time-series modelling can be used to analyze and generate short-term forecasts for stock-price data**.

***

## 🧰 Tools & Libraries

* **Python**
* **Pandas** – Data preprocessing and time-series handling
* **NumPy** – Numerical computations
* **Matplotlib** – Data visualization
* **Statsmodels** – ADF test, ACF/PACF analysis, and SARIMAX modelling

***

## ⚠️ Disclaimer

This project is intended for **academic and educational purposes**. Stock-price forecasts are statistical estimates based on historical data and should not be interpreted as guaranteed predictions or financial advice.
