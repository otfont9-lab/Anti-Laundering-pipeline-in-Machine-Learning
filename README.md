
# AML Behavioral Feature Engineering Pipeline

## 1. Project Overview & Business Problem
This project aims to solve one of the major problems financial institutions and transaction consultants face in day-to-day work: flagging suspicious movements that could be involved in money laundering operations.

## 2. Dataset & Transaction Representation
The Kaggle dataset `HI-Small-Trans` has been downloaded to boil down 5 million transactions across 500,000 bank accounts. First, traditional magnitude features were computed, such as the maximum amount within a 24-hour window or the total amount within a 7-day window. The dataset was then represented as a graph network using the NetworkX library, where basic graph metrics were extracted. A dataframe integrating all the  magnitude features and network metrics has been created. A Machine Learning MOdel has been deployed (XGBoost) to detect launderer accounts and fine-tuing thresholds has been practiced to  achieve a meaningful recall

## 3. Engineered Behavioral Features
* **Structural Fan Ratios (`fan_in`, `fan_out`):**
* **Dwell Times (`min_dwell_time`, `avg_dwell_time`):**
* **Rolling 1-Hour Burst (`max_hourly_burst`):**

## 4. Architecture & Technical Trade-offs


## 5. Tech Stack & Execution


## 6. Next Steps / Model Integration
