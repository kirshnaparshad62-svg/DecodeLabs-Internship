# Fraud Detection in E-Commerce Transactions Using Machine Learning

## Project Overview

This project develops an end-to-end machine learning pipeline to detect fraudulent e-commerce transactions. Since the original dataset does not contain predefined fraud labels, a rule-based approach is used to engineer the target variable (`Is_Fraud`). The project follows a leak-free machine learning workflow by integrating preprocessing, feature scaling, SMOTE oversampling, and model training within cross-validation pipelines to ensure reliable model evaluation.

---

## Objectives

The main objectives of this project are to:

- Build a fraud detection model using supervised machine learning.
- Engineer fraud labels from transaction behavior.
- Prevent data leakage using pipeline-based preprocessing.
- Handle class imbalance using SMOTE.
- Compare multiple machine learning models.
- Optimize model performance using cross-validation and hyperparameter tuning.

---

## Dataset Information

**Dataset:** E-Commerce Transactions Dataset

### Dataset Summary

- Rows: 1,200
- Columns: 14

### Features

- OrderID
- Date
- CustomerID
- Product
- Quantity
- UnitPrice
- ShippingAddress
- PaymentMethod
- OrderStatus
- TrackingNumber
- ItemsInCart
- CouponCode
- ReferralSource
- TotalPrice

---

## Exploratory Data Analysis

The dataset was analyzed to understand its structure and quality before model development.

### Missing Values

The dataset was mostly complete.

Only one feature contained missing values:

- CouponCode → 309 missing values

---

## Fraud Label Engineering

Since no fraud labels were available, a new target variable (`Is_Fraud`) was created using business rules.

A transaction was labeled as fraudulent if:

- The transaction amount was greater than or equal to the 95th percentile of `TotalPrice`.
- The order status was **Cancelled** or **Returned**.

### Class Distribution

| Class | Percentage |
|-------|-----------:|
| Non-Fraud | 55.75% |
| Fraud | 44.25% |

---

## Data Preprocessing

The preprocessing pipeline was designed using Scikit-Learn's `ColumnTransformer`.

### Numerical Features

- Quantity
- UnitPrice
- ItemsInCart
- Month
- Weekday

### Categorical Features

- Product
- PaymentMethod
- CouponCode
- ReferralSource

### Preprocessing Steps

- Missing value imputation using Median strategy for numerical features.
- Missing value imputation using Most Frequent strategy for categorical features.
- One-Hot Encoding for categorical variables.
- Feature scaling using `StandardScaler(with_mean=False)`.

---

## Handling Class Imbalance

To improve model performance on the minority class, **SMOTE (Synthetic Minority Over-sampling Technique)** was applied.

SMOTE was integrated within the machine learning pipeline to prevent data leakage during cross-validation.

---

## Machine Learning Models

### Logistic Regression

Pipeline includes:

- Data Preprocessing
- Feature Scaling
- SMOTE
- Logistic Regression

Hyperparameter tuning was performed using **GridSearchCV**.

Optimized parameters include:

- Regularization parameter (`C`)
- SMOTE `k_neighbors`

### Random Forest

A Random Forest classifier was developed and evaluated using the same preprocessing workflow for performance comparison.

---

## Model Evaluation

Models were evaluated using the following metrics:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score
- Confusion Matrix
- Classification Report

A Stratified Train-Test Split and Stratified Cross-Validation were used to preserve class distribution during model evaluation.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- Imbalanced-Learn (SMOTE)
- Jupyter Notebook

---

## Project Structure

```text
Fraud-Detection-ML/
│
├── Fraud_Detection.ipynb
├── dataset.csv
├── README.md
├── requirements.txt
└── outputs/
```

---

## Key Features

- End-to-End Machine Learning Pipeline
- Rule-Based Fraud Label Engineering
- Leak-Free Data Preprocessing
- SMOTE for Class Imbalance
- One-Hot Encoding
- Feature Scaling
- Hyperparameter Tuning using GridSearchCV
- Logistic Regression and Random Forest Model Comparison

---

## Future Improvements

- Train advanced ensemble models such as XGBoost and LightGBM.
- Deploy the model using Streamlit or Flask.
- Integrate real-time fraud detection APIs.
- Improve fraud label generation using anomaly detection techniques.

---

## Author

**Kirshna Parshad**

This project was completed as part of a Data Science Internship to demonstrate practical skills in data preprocessing, feature engineering, handling imbalanced datasets, and building leak-free machine learning pipelines for fraud detection.