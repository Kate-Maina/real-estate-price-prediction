![Dashboard Preview](Images/images.jpeg)
# Real Estate Price Prediction Using Machine Learning

## Executive Summary  
Accurate property valuation is essential for real estate stakeholders, from buyers and sellers to developers and investors. This project applies machine learning models to predict house prices based on a wide array of features such as size, location, and amenities. The end goal is to develop a robust and interpretable pricing model suitable for decision support or integration into digital platforms.


## Problem Statement  
In the dynamic real estate market, price estimation is often subjective or inconsistent. Buyers want fair prices, sellers seek profitability, and investors need reliable valuation to make informed decisions. This project aims to build predictive models that estimate residential property prices using historical data and machine learning techniques.

Dataset Source: [House Price Prediction - Kaggle](https://www.kaggle.com/datasets/shree1992/housedata)


## Objectives  
- Predict house prices using supervised machine learning.
- Identify the most influential features affecting house value.
- Compare and evaluate multiple regression models.
- Recommend the most accurate model for real-world use.
- Suggest ways to improve data quality and modeling performance.


## Dataset Overview  
- **Source**: [Kaggle House Data](https://www.kaggle.com/datasets/shree1992/housedata)  
- **Region**: King County, Washington (USA)  
- **Records**: ~21,000 residential properties  
- **Key Features**:  
  - Structural: bedrooms, bathrooms, square footage  
  - Location: city, zipcode  
  - Others: condition, view, year built, year renovated  


## Methodology  

### 1. Data Preprocessing  
- Dropped irrelevant columns (IDs, raw dates)
- Converted date fields to extract month/year features
- Handled missing values appropriately
- One-hot encoded categorical variables
- Capped outliers at the 99th percentile for price

### 2. Feature Engineering  
- Created `mean_price_per_sqft_city` to encode location-specific pricing
- Calculated `price_per_sqft` for internal exploration
- Extracted year/month from dates
- Optionally log-transformed target variable for better model fitting

### 3. Model Development  
- Trained and tuned the following models:
  - Linear Regression
  - OLS Regression
  - Decision Tree Regressor (with and without tuning)
  - Random Forest Regressor (with and without tuning)
  - Gradient Boosting Regressor (with and without tuning)

### 4. Evaluation Metrics  
- R² Score (Goodness of fit)
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)


## Model Performance Comparison

| Model                           | R² Score   | MAE             | RMSE             |
| ------------------------------- | ---------- | --------------- | ---------------- |
| **Linear Regression**           | 0.6763     | $101,303.79     | $146,338.28      |
| **Ridge Regression**            | 0.6760     | $101,376.31     | $146,403.24      |
| **Lasso Regression**            | 0.6760    | $101,320.66     | $146,347.25     |
| **Optimized Decision Tree**     | 0.5805     | $119,574.35     | $166,593.99      |
| **Random Forest Regressor**     | 0.6287     | $108,043.70     | $156,725.73      |
| **Optimized Random Forest**     | 0.6324     | $107,785.49     | $155,943.21      |
| **Gradient Boosting Regressor** | 0.6969     | $97,820.38      | $141,594.02      |
| **Optimized Gradient Boosting**| **0.6984** | **$97,485.83**   | **$141,243.55**  |


## Key Findings  

- `sqft_living`, `view`, and city-specific features like `mean_price_per_sqft_city` were consistently the most predictive features.
- Optimized Gradient Boosting delivered the **best performance** across all metrics (R² ≈ 0.698).
- Outlier filtering had minimal effect, indicating the model’s robustness.
- Multicollinearity was observed in linear models, making tree-based methods more reliable.


## Recommendations  

1. **Adopt Gradient Boosting for Deployment**  
   Use the optimized Gradient Boosting Regressor as the production model due to its superior performance and balance of accuracy and generalization.

2. **Enrich the Dataset**  
   - Add external features such as school proximity, crime rates, and walkability.
   - Incorporate macroeconomic variables like interest rates or local market trends.

3. **Improve Feature Quality**  
   - Recode `yr_renovated` as a boolean or age-since-renovation.
   - Investigate and clean zero values in fields like `sqft_basement`.

4. **Build an Interactive Tool**  
   Develop a dashboard (e.g., with Tableau) that allows users to input property features and receive an instant price estimate.

5. **Explore Advanced Models**  
   Experiment with deep learning or geospatial models if more granular location data becomes available.


## Limitations  
- Model is based only on King County data—may not generalize to other markets.
- Market fluctuations and economic shifts are not captured in the current dataset.
- Some important qualitative features (e.g., interior finish, curb appeal) are not available.

## Future Work  
- Incorporate external economic indicators (interest rates, inflation).  
- Explore deep learning approaches (e.g., neural networks).  
- Integrate geospatial analysis using maps for better location-based insights.  
- Develop a full-stack web application for deployment.


## Author  
**Catherine Maina**  
Moringa School Data Science Program 
