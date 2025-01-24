# Forecasting Prosumer Energy Behaviors with XGBoost

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
[![Notebooks](https://img.shields.io/badge/notebooks-Model.ipynb-blue)](Model.ipynb)

## Table of Contents
1. [Overview](#overview)  
2. [Methodology](#methodology)  
3. [Running the Model](#running-the-model)  
4. [Results](#results)  
5. [Summary](#summary)  

---

## Overview
Energy imbalance—caused by discrepancies between expected and actual energy usage—is a growing concern. Prosumers (consumers who also produce energy, such as via solar panels) can introduce unpredictability into the grid. This project leverages **XGBoost** to forecast prosumer energy behaviors, aiming to mitigate imbalance costs and enhance grid stability.

[View the Kaggle Competition](https://www.kaggle.com/competitions/predict-energy-behavior-of-prosumers)

**Key Objectives**  
- Develop an XGBoost-based prediction model incorporating prosumer behavior, weather data, and price signals.  
- Predict energy production and consumption for Estonian prosumers with solar panels.  
- Evaluate the effects of feature engineering and hyperparameter tuning on model performance.

---

## Methodology
1. **Data Acquisition**  
   - Sourced from a Kaggle competition provided by Enefit.  
   - Includes hourly consumption/production, daily gas prices, hourly electricity prices, weather data, and demographic information.

2. **Feature Engineering**  
   - **Temporal Features:** Hour of day, day of week, and day of year using cyclical transformations.  
   - **Lagged Energy Features:** Past consumption/production (2–7 days).  
   - **Weather Data:** Aggregated by hour and county.  
   - **Log Transformation:** Applied to skewed features.  
   - **Feature Selection:** Based on XGBoost’s feature importance.

3. **Model Training**  
   - Deployed an XGBoost regressor.  
   - Compared baseline vs. engineered features.  
   - Hyperparameter tuning (Grid Search) to reduce MAE.  
   - Evaluated performance with Mean Absolute Error (MAE).

4. **Validation**  
   - Measured error on a holdout set.  
   - Compared:
     - Raw features vs. engineered features.  
     - Default vs. tuned hyperparameters.  
   - Kaggle submission results via Enefit’s time-series API.

---

## Running the Model
1. Open the Jupyter Notebook (`Model.ipynb`).  
2. Run cells sequentially to load data, engineer features, train, and evaluate.  
3. Review outputs (MAE and plots) for performance insights.

---

## Results
- **Feature Engineering Improvements:** Temporal and lagged features significantly boost accuracy.  
- **Hyperparameter Tuning:** Reduces MAE and improves generalization.  
- **Top Features:** Day of year, consumption points (Eic), day of week, solar radiation forecasts, and installed capacity (Cap).

---

## Summary
With engineered features and optimized hyperparameters, the XGBoost model yielded a substantial performance improvement, achieving an MAE of **60.26** on the validation set and a Kaggle score of **102.1**.