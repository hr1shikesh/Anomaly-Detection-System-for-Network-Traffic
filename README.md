# 🔐 Intrusion Detection with Machine Learning (NSL-KDD Dataset)

This repository contains a full pipeline to detect and classify network intrusions using machine learning models on the NSL-KDD dataset. The workflow includes data preprocessing, attack-type labeling, model training, hyperparameter optimization, and explainability using SHAP.

---

## 📊 Dataset

We use the improved version of the KDD Cup 1999 dataset—**NSL-KDD**, which provides a better-balanced distribution and removes duplicate records.

- Train: `KDDTrain+.arff`
- Test: `KDDTest+.arff`

These are converted to `.csv` files for easier processing.

---

## 🧪 Models Compared

We evaluated several classic ML models:

| Model          | Accuracy | Precision | Recall | F1-Score | Computation Time (s) |
|----------------|----------|-----------|--------|----------|-----------------------|
| Decision Tree  | 0.9984   | 0.9984    | 0.9984 | 0.9984   | 2.13                  |
| Random Forest  | 0.9987   | 0.9987    | 0.9987 | 0.9987   | 15.01                 |
| SVM            | 0.9918   | 0.9918    | 0.9918 | 0.9918   | 90.42                 |
| KNN            | 0.9957   | 0.9957    | 0.9957 | 0.9957   | 38.99                 |
| XGBoost        | **0.9991** | **0.9991** | **0.9991** | **0.9991** | 5.95              |
| AdaBoost       | 0.9882   | 0.9882    | 0.9882 | 0.9882   | 14.83                 |

> 🚀 **XGBoost** performed best overall and was further fine-tuned.

---

## 🔧 Key Features

### ✅ Data Preprocessing
- One-hot encoding of categorical variables
- Standardization of numerical features
- Label encoding of the target class

### 🏷️ Attack Type Classification
A custom rule-based function maps anomalies to specific attack types (e.g., Smurf, Neptune, Probe, R2L, U2R).

### 📈 Model Tuning with XGBoost
- Hyperparameter tuning with `GridSearchCV`
- Stratified 3-fold cross-validation
- Imbalanced data handling with `scale_pos_weight`

### 🧠 Model Explainability
- SHAP visualizations:
  - Force plots
  - Waterfall plots
- Per-instance feature importance
- Top features grouped by attack type

---

## 📂 Project Structure

├── data/ │ ├── KDDTrain+.arff │ ├── KDDTest+.arff │ └── *.csv ├── models/ │ └── best_xgboost_model.json ├── shap_analysis/ │ └── top_features_by_attack_type.csv ├── intrusion_detection.ipynb ├── README.md └── requirements.txt


💡 Future Enhancements
Deep learning model comparison (e.g., LSTM, CNN)

Real-time anomaly detection pipeline

Deployment via Flask or FastAPI



