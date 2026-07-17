# 📈 Tata Motors Stock Price Forecasting - T Vardhini

---

## 🔹 Introduction About the Project

**The goal of this project** is to forecast the daily closing price of Tata Motors stock using classical time series techniques such as **ARIMA** and **SARIMA**.

This is a **time series forecasting problem**, where historical stock price data is used to predict future trends.

---

## 🎯 Objective

* Forecast future stock prices using historical data
* Compare ARIMA and SARIMA model performance
* Evaluate prediction accuracy using **MAPE (Mean Absolute Percentage Error)**

---

## 📊 Dataset Information

**The dataset** consists of historical daily stock price data of Tata Motors.

### Features in the dataset:

* `Date` : Trading date
* `Open` : Opening stock price
* `High` : Highest price of the day
* `Low` : Lowest price of the day
* `Close` : Closing stock price
* `Adjusted Close` : Adjusted closing price
* `Volume` : Number of shares traded

👉 **Target variable:**

* `Close` (used for forecasting)

---

## ⚙️ Approach for the Project

### 1. Data Preprocessing

* Converted `Date` column to datetime format
* Sorted data chronologically
* Removed duplicate timestamps
* Set `Date` as index
* Ensured continuous time series
* Handled missing values using forward fill

---

### 2. Stationarity Check

* Applied **ADF (Augmented Dickey-Fuller test)**
* Observed non-stationarity in original series
* Applied **first-order differencing** to make data stationary

---

### 3. Parameter Selection

* Used **PACF → p (AutoRegressive term)**
* Used **ACF → q (Moving Average term)**
* Used differencing → d

👉 Final ARIMA parameters:

```
(p, d, q) = (4, 1, 2)
```

---

### 4. ARIMA Model

* Built baseline ARIMA model
* Evaluated residuals
* Observed remaining patterns → indicated missing seasonality

---

### 5. Seasonality Detection

* Performed time series decomposition
* Identified repeating seasonal patterns
* Concluded need for seasonal modeling

---

### 6. SARIMA Model

Extended ARIMA to capture seasonality:

```
SARIMA(p,d,q)(P,D,Q,s) = (4,1,2)(4,1,2,12)
```

---

### 7. Model Evaluation

* Used time-based train-test split
* Evaluation metric: **MAPE**

---

## 📈 Results

### Model Performance:

* ARIMA → Lower performance
* SARIMA → Better performance

👉 **Final MAPE: 2.86%**

✔ SARIMA successfully captured both trend and seasonality

---

## 📌 Key Insights

* Proper preprocessing is critical for time series models
* Stationarity is essential for ARIMA-based models
* ACF & PACF help in parameter tuning
* Seasonal patterns significantly improve accuracy
* SARIMA outperformed ARIMA

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib / Plotly
* Statsmodels
* Scikit-learn

---

## 🚀 How to Run the Project

```bash
pip install pandas numpy matplotlib statsmodels scikit-learn
```

Run the notebook:

```bash
jupyter notebook
```

---

## 📉 Evaluation Metric

**MAPE (Mean Absolute Percentage Error)**

* Measures average percentage deviation between predicted and actual values
* Achieved: **2.86% (Strong performance)**

---

## ⚠️ Limitations

* Stock prices are highly volatile
* Model uses only historical price data
* External factors (news, macro trends) are not included
* Assumes consistent seasonal behavior

---

## 🔮 Future Improvements

* Incorporate external variables (news, economic indicators)
* Use advanced models (LSTM, Prophet)
* Perform hyperparameter tuning
* Use larger historical datasets
* Deploy using Streamlit / API

---

## 🎤 Project Summary

Developed a time series forecasting model using **ARIMA and SARIMA**.
After preprocessing and ensuring stationarity, parameters were selected using ACF/PACF.
SARIMA effectively captured seasonal patterns and achieved a **MAPE of 2.86%**, demonstrating strong predictive capability.

---
