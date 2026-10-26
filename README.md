
# AML Behavioral Feature Engineering Pipeline

## 1. Project Overview & Business Problem
This project aims to solve one of the major problems financial institutions and transaction consultants face in day-to-day work: flagging suspicious movements that could be involved in money laundering operations.

## 2. Dataset & Transaction Representation
The Kaggle dataset `HI-Small-Trans` has been downloaded to boil down 5 million transactions across 500,000 bank accounts. First, traditional magnitude features were computed, such as the maximum amount within a 24-hour window or the total amount within a 7-day window. The dataset was then represented as a graph network using the NetworkX library, where basic graph metrics were extracted. A dataframe integrating all the  magnitude features and network metrics has been created. A Machine Learning MOdel has been deployed (XGBoost) to detect launderer accounts and fine-tuing thresholds has been practiced to  achieve a meaningful recall
## 3. Engineered Behavioral Features
Behavioral features are key to detecting fraudulent accounts, capturing patterns such as circular loops, scatterer accounts, and source accounts. Feature engineering defines metrics to quantify these movements:

- **Structural Fan Ratios (`fan_in`, `fan_out`):** Count of unique senders delivering funds (`IN`). Identifies  collection behavior, and count of unique receivers collecting funds (`OUT`) 
- **Dwell Times (`min_dwell_time`, `avg_dwell_time`):** Tracks the velocity at which funds pass through an account (`IN` immediately followed by `OUT`), identifying automated layering.
- **Rolling 1-Hour Burst (`max_hourly_burst`):** Captures rapid surges in transaction frequency within sliding 1-hour windows.

## 4. Architecture & Technical Trade-offs

## 5. Tech Stack & Execution
* **Data Processing & Feature Engineering:** DuckDB (High-performance out-of-core SQL execution)
* **Graph Topology:** NetworkX (Directed graph metrics, centrality, and community structures)
* **Machine Learning:** XGBoost (Imbalance-aware gradient boosting with `scale_pos_weight`)
* **Evaluation & Governance:** Precision-Recall AUC & compliance-driven decision threshold tunin

## 6. Next Steps / Model Integration
To push the PR-AUC past to 0.18-0.25 isntitutional threshold , and transition from ma research notebook to a production-ready model , following optimizations are planned : 
- **Louvain Community Detection:** Integrate graph community clustering to explicitly capture multi-hop mule rings and closed-loop laundering structures.
- **Micro-Burst Velocity Windows:** Expand SQL feature extraction to sub-hourly rolling windows to catch rapid-fire structuring.
- **Enterprise Rule Translation:** Export trained XGBoost decision paths and DuckDB feature queries into production-ready SQL/SAS scoring rules for real-time transaction monitoring systems.
