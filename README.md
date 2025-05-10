# ⏳ Time Series Forecasting of Electricity Demand in Germany

A comprehensive machine learning project analyzing and forecasting electricity consumption in Germany from 2006 to 2018. The project compares various statistical and machine learning models.

---

## 📌 Research Question

> *Can we forecast electricity demand using time series models?*

---

<img src="[https://github.com/user-attachments/assets/ad82f7c9-d288-4307-9bb6-26dae963e4f6](https://github.com/user-attachments/assets/bc3a4961-e9ce-4fd3-9063-5012f5d10aa0)" alt="Student_squirrel" width="400"/>

---

## 📊 Dataset
* **Main Data:** German electricity consumption (2006–2017)
* **Source:** [Kaggle Dataset](https://www.kaggle.com/datasets/mvianna10/germany-electricity-power-for-20062017)
* **Units:** Gigawatt-hours (GWh)
* **Exogenous Variable:** Historical temperature data from [Open-Meteo](https://open-meteo.com/en/docs/historical-weather-api)

---

## 🧠 Methods and Models

The project implements and evaluates:

1. **Baseline (Naive Seasonal Model)**
2. **SARIMA**
3. **Prophet**
4. **Holt-Winters Exponential Smoothing**
5. **XGBoost Regression**

Each model is tested with:

* Weekly and daily time series
* With and without external temperature input

---

## 🔬 Change Point Detection

* **Shewhart Control Charts** and **CUSUM** were used to detect structural shifts in the time series.
* Notable change detected in early 2009, likely caused by:

  * The global financial crisis
  * The Russia–Ukraine gas conflict
  * Energy policy shifts in Europe

---

## 🌡️ Temperature Analysis

* Strong **negative correlation** between summer temperatures and electricity demand (up to -0.37)
* Heat reduces electricity usage in Germany due to low use of cooling appliances
* Used as an **exogenous regressor** in SARIMA, Prophet, and XGBoost models

---

## 📈 Key Results

| Model            | Weekly RMSE | Weekly+Temp RMSE | Daily RMSE | Daily+Temp RMSE |
| ---------------- | ----------- | ---------------- | ---------- | --------------- |
| **Baseline**     | 61.78       | —                | 149.65     | —               |
| **SARIMA**       | 47.27       | 44.71            | —          | —               |
| **Prophet**      | **41.12**   | 42.28            | 61.34      | 60.73           |
| **Holt-Winters** | 50.39       | —                | 150.71     | —               |
| **XGBoost**      | 45.03       | **39.79**        | **56.18**  | **59.46**       |

---

## 🧾 Conclusions

* **SARIMA**  improved with temperature, didn't handled the daily data.
* **Prophet** outperformed others on **Weekly data with temperature**.
* **XGBoost** outperformed others RMSE in all other tests.
* Adding temperature data had **mild impact** on most models.
* No single model was best for all cases.

## 🔍 Summary
Electricity consumption in Germany from 2006 to 2018 (excluding 2018) shows a time series with structural changes and a partial return to earlier trends. Despite this complexity, the models successfully forecasted future demand — capturing both overall trends and seasonal (weekly and yearly) patterns. No single model emerged as fully optimal, but the best-performing candidates were Prophet and XGBoost. Including temperature as an external regressor slightly improved forecasting accuracy in some models.

Future research could explore whether these models remain effective in contexts with more volatile or irregular consumption patterns, where prediction is more challenging.

Thanks for reading, hope this project offers valuable insights into forecasting and data-driven energy planning.

