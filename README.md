# Procurement Data Validation & Delivery Delay Prediction

## 1. Business Context & Objective
In large-scale Commercial & Industrial (C&I) solar EPC projects, procurement delays and inconsistent vendor quotation records directly impact project timelines and budget control. 

Inspired by real-world enterprise procurement workflows, this project simulates **3,050 purchase order (PO) records** with injected data anomalies and builds an automated pipeline to:
1. **Audit, clean, and validate** dirty enterprise procurement datasets.
2. **Query and identify** high-risk suppliers using SQL.
3. **Engineer domain-specific features** and train baseline Machine Learning models to predict supplier delivery delays (`Is_Delayed`).

---

## 2. Dataset & Data Quality Pipeline
* **Dataset (`raw_procurement_data.csv`):** Simulated procurement logs covering 20 vendors, 4 material categories (`Solar_Panel`, `Inverter`, `Mounting_Structure`, `Cables`), pricing benchmarks, logistics distances, and historical vendor reliability.
* **Data Cleaning & Validation Steps (`Pandas`):**
  * **Deduplication:** Identified and removed 50 duplicate `PO_ID` records.
  * **Anomaly Detection:** Flagged and filtered out invalid unit prices (`<= 0` or `> 3x` market benchmark price) caused by manual entry typos.
  * **Group-Based Imputation:** Handled missing values (`NaN`) in `Historical_OnTime_Rate` using vendor-specific median values to preserve supplier performance integrity.

---

## 3. Exploratory SQL Analysis & Feature Engineering
* **SQL Querying (`sqlite3`):** Aggregated clean procurement records by `Vendor_ID` (`HAVING Total_Orders >= 50`) to rank top high-risk suppliers based on delay rate percentages and average price variances.
* **Feature Engineering:**
  * `Price_Variance_Ratio`: Normalized percentage difference between quoted unit price and market benchmark price.
  * `Logistics_Risk_Score`: Interaction feature combining delivery distance (`Distance_km`) and historical delay rate (`1 - Historical_OnTime_Rate`).

---

## 4. Baseline Modeling & Reproducibility
* **Methodology:** Applied an 80/20 stratified train-test split with fixed random seeds (`random_state=42`) to ensure full experimental reproducibility.
* **Models Evaluated (`scikit-learn`):**
  * **Logistic Regression** (with `StandardScaler`) as an interpretable linear baseline.
  * **Random Forest Classifier** (100 estimators) validated via **5-Fold Cross-Validation** (`F1-score`).

---

## 5. Repository Structure
* `Procurement_Data_Validation_and_Delay_Prediction.ipynb`: Complete Jupyter Notebook containing data simulation, validation rules, SQL queries, visualizations, and ML experiments.
* `raw_procurement_data.csv`: Raw synthetic procurement dataset with injected data quality issues.
