# Week-1
The goal is to predict the power output (kW or MW) of a single wind turbine for the short-term (e.g., the next hour) using its current and historical data.
# ⚡ Wind Turbine Power Forecasting using Machine Learning

## 🎯 Project Overview

This project implements a **Short-Term Wind Power Prediction** model using Supervisory Control and Data Acquisition (**SCADA**) data. The primary goal is to predict the electrical power output ($\text{kW}$) of a single turbine, which is critical for reliable grid management and energy trading.

The project demonstrates proficiency in:
* Handling **time-series data** and engineering temporal features.
* Cleaning highly non-linear, real-world data based on the **Wind Turbine Power Curve** physics.
* Applying ensemble methods (Random Forest/XGBoost) for regression on complex environmental data.

---

## 💾 Data and Preparation

### Data Source
* **Dataset:** [Insert the exact name and source here, e.g., Wind Turbine SCADA Dataset (T1.csv) from Kaggle]
* **Target Variable:** `LV ActivePower (kW)` (The generated power output).
* **Key Input Variables:** `Wind Speed (m/s)`, `Theoretical_Power_Curve (KWh)`, and `Time Features`.

### Data Cleaning: Power Curve Filtering
A critical step involved removing abnormal operating conditions (faults or maintenance) where wind speed was high but power output was zero.
* **Filter Applied:** Dropped records where $\text{Wind Speed} > 2 \text{ m/s}$ AND $\text{Power Output} = 0$.

### Feature Engineering
* **Lagged Variables:** Created 1-hour and 2-hour lagged features for $\text{Wind Speed}$ and $\text{Power Output}$ to capture time dependency.
* **Cyclical Encoding:** Used sine and cosine transformations on `Hour of Day` and `Wind Direction` to represent circular features accurately.

---

## 🛠️ Model Implementation and Evaluation

The dataset was split chronologically (80% Train, 20% Test) to maintain the integrity of the time-series forecasting task.

### Models Tested

| Model | Rationale |
| :--- | :--- |
| **Baseline: Linear Regression** | Establishes a benchmark for basic predictive capability on the data. |
| **Primary: Random Forest Regressor** | Excellent for modeling the non-linear, step-like segments of the **Power Curve**. |
| **Advanced: XGBoost Regressor** | A robust gradient boosting method expected to yield the highest predictive accuracy. |

### Performance Metrics (On Test Set)

| **Metric** | **Random Forest** **(RF)** | 

| **R^2** | 0.8272 |
| **Mean Absolute Error (MAE)** | 0.0737 | 

### Visualization of Results

* **Time-Series Plot:** Visual comparison of actual vs. predicted power output over a 48-hour period, demonstrating prediction accuracy under fluctuating conditions. 
* **Power Curve Plot:** A scatter plot of predicted power vs. wind speed, validating that the model successfully mapped the turbine's operational physics. 

---


