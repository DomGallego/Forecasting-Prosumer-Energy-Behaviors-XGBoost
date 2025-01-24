# Forecasting Prosumer Energy Behaviors with XGBoost: A Machine Learning Approach to Mitigate Energy Imbalance

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)  [![Notebooks](https://img.shields.io/badge/notebooks-Model.ipynb-blue)](Model.ipynb)

This repository contains the code and resources for a project focused on forecasting energy consumption and production behaviors of **prosumers** (consumers who also produce energy, e.g., with solar panels).  The project utilizes **XGBoost**, a powerful gradient boosting machine learning algorithm, to address the challenge of energy imbalance in modern grids caused by the increasing adoption of decentralized renewable energy sources.

## Project Overview

Energy imbalance, the discrepancy between expected and actual energy usage, is a growing concern for energy companies. Prosumers, while contributing to renewable energy adoption, introduce unpredictability into the grid due to the variable nature of their energy production and consumption patterns. This unpredictability leads to:

* **Financial Burdens:** Increased operational costs and imbalance penalties for energy providers.
* **Grid Instability:** Potential disruptions in energy supply and demand balance.
* **Inefficient Resource Utilization:** Suboptimal use of energy resources and infrastructure.

This project aims to develop a robust and accurate forecasting model using XGBoost to predict prosumer energy behaviors. By improving forecast accuracy, energy companies can better integrate prosumers into the grid, minimize imbalance costs, and ensure a more stable and efficient energy system.

**Key Objectives:**

* **Develop an XGBoost-based energy prediction model:**  Account for prosumer behavior, weather conditions, electricity and gas prices, and temporal patterns.
* **Predict energy production and consumption for Estonian prosumers:** Specifically targeting customers with installed solar panels, using data provided by Enefit, a Baltic energy company.
* **Evaluate the effectiveness of feature engineering and hyperparameter tuning:** Optimize model performance for accurate energy forecasting.

## Methodology

The project follows a structured machine learning workflow:

1. **Data Acquisition:** Utilizing an open-source dataset from a Kaggle competition ("Predict Energy Behavior of Prosumers") hosted by Enefit. The dataset includes:
    * Hourly energy consumption and production data.
    * Daily gas prices and hourly electricity prices.
    * Historical and forecasted weather data (temperature, dew point, cloud cover, wind, solar radiation, snowfall, air pressure).
    * Client information (installed solar panel capacity, business/residential indicator, county).
    * County demographic data (population, area size).

2. **Feature Engineering:**  Creating relevant features to improve model accuracy. This includes:
    * **Temporal Features:** Extracting hour of day, day of week, and day of year using sine and cosine transformations to capture cyclical patterns.
    * **Lagged Energy Features:** Incorporating past energy consumption/production data (lags of 2-7 days, mean, standard deviation, variance) as predictors of future behavior.
    * **Weather Feature Aggregation:**  Averaging weather variables across hours and counties to match the data granularity.
    * **Log Transformation:** Applying logarithmic transformation to skewed numerical features (energy, weather, prices) to reduce skewness and stabilize variance.
    * **Feature Selection:**  Iterative pruning of less important features based on XGBoost's feature importance scores to improve model generalization and reduce overfitting.

3. **Model Training:** Implementing an XGBoost regression model for energy forecasting.
    * **Baseline Model:** Training with raw features and default XGBoost hyperparameters.
    * **Feature Engineering Models:** Training with engineered features and default hyperparameters to assess the impact of feature engineering.
    * **Hyperparameter Tuning:**  Utilizing Grid Search to optimize key XGBoost hyperparameters (e.g., `max_depth`, `min_child_weight`, `subsample`, `colsample_bytree`, `learning_rate`) to minimize Mean Absolute Error (MAE).
    * **Evaluation Metric:**  Using Mean Absolute Error (MAE) to evaluate model performance, as it provides a robust measure of prediction accuracy and is less sensitive to outliers compared to Mean Squared Error (MSE).

4. **Results and Validation:** Evaluating model performance on a validation set and comparing different model versions:
    * **Raw Features vs. Engineered Features:** Demonstrating the improvement achieved through feature engineering.
    * **Default Hyperparameters vs. Tuned Hyperparameters:** Showing the impact of hyperparameter optimization on model accuracy.
    * **Kaggle Submission:** Submitting predictions to the Kaggle competition platform via Enefit's provided time-series API to assess performance in a realistic forecasting scenario.

## Repository Structure

├── Model.ipynb <- Jupyter Notebook containing data exploration, feature engineering, model training, and evaluation.
├── README.md <- This README file.
└── requirements.txt <- List of Python dependencies for the project.