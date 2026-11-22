---

## 5. Limitations & Future Improvements
* **Synthetic Data Constraints:** This project uses a synthetic procurement dataset created for learning and experimentation purposes. The delivery delay label (`Is_Delayed`) was generated using predefined rules based on selected procurement and logistics attributes.
* **Experimental Scope:** Consequently, the model results demonstrate the end-to-end application of foundational machine learning workflows rather than validated predictive performance on real-world enterprise procurement data.
* **Next Steps:** As an early-career applied science project, this analysis is designed to strengthen practical skills in data preparation, feature engineering, baseline model training, and evaluation. Future iterations would involve validating the pipeline on real historical ERP datasets, refining anomaly detection thresholds, and exploring more robust cross-validation and hyperparameter tuning techniques.

---

## 6. Repository Structure
* `Procurement_Data_Validation_and_Delay_Prediction.ipynb`: Complete Jupyter Notebook containing data simulation, validation rules, SQL queries, visualizations, and ML experiments.
* `raw_procurement_data.csv`: Raw synthetic procurement dataset with injected data quality issues.
