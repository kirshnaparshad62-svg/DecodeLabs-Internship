#  Advanced EDA & Feature Engineering on Product Sales Dataset

##  Project Overview

This project demonstrates a complete data preprocessing pipeline on a regional product sales dataset. The objective is to transform raw transactional data into a clean, structured, and machine learning-ready dataset through data cleaning, outlier treatment, feature engineering, categorical encoding, and feature scaling.

---

##  Objective

The primary objectives of this project are to:

* Clean and preprocess raw sales data.
* Handle missing values.
* Detect and remove outliers.
* Engineer meaningful business features.
* Encode categorical variables.
* Standardize numerical features.
* Prepare the dataset for machine learning applications.

---

##  Dataset Information

**Dataset:** `Product-Sales-Region.xlsx`

### Dataset Summary

* **Rows:** 1,500
* **Columns:** 19

### Features

* Date
* Region
* Product
* Quantity
* UnitPrice
* StoreLocation
* CustomerType
* Discount
* Salesperson
* TotalPrice
* PaymentMethod
* Promotion
* Returned
* OrderID
* CustomerName
* ShippingCost
* OrderDate
* DeliveryDate
* RegionManager

---

#  Project Workflow

## 1. Data Cleaning

* Inspected the dataset for missing values.
* Identified **370 missing values** in the **Promotion** column.
* Filled missing values using **Mode Imputation**.
* Successfully produced a dataset with **no missing values**.

---

## 2. Outlier Detection

Outliers were detected using two statistical methods.

### IQR Method

* Applied the Interquartile Range (IQR) technique.
* Removed **17 outlier records** from the **TotalPrice** feature.

### Z-Score Validation

* Verified remaining observations using the Z-Score method.
* No additional outliers were detected.

---

## 3. Feature Engineering

Created the following business-oriented features:

### DeliveryDays

Calculated the delivery duration.

```text
DeliveryDate - OrderDate
```

### RevenueAfterDiscount

Calculated revenue after applying discounts.

```text
Quantity × UnitPrice × (1 − Discount)
```

### EstimatedProfit

Estimated profit after deducting shipping costs.

```text
RevenueAfterDiscount − ShippingCost
```

### SalesCategory

Categorized sales into four groups:

* Low
* Medium
* High
* Premium

---

## 4. Categorical Encoding

Applied **One-Hot Encoding** to convert categorical variables into numerical format using:

* Region
* Product
* StoreLocation
* CustomerType
* PaymentMethod
* Promotion
* Salesperson
* RegionManager

The `drop_first=True` parameter was used to avoid the dummy variable trap.

---

## 5. Feature Scaling

Standardized all numerical features using **StandardScaler**.

After scaling:

* Mean ≈ 0
* Standard Deviation ≈ 1

This makes the dataset suitable for many machine learning algorithms.

---

#  Technologies Used

* Python
* Pandas
* NumPy
* SciPy
* Scikit-Learn
* Jupyter Notebook

---

#  Project Structure

```text
Project 1/
│
├── Ds_Project1_Advanced_EDA_Feature_Engineering.ipynb
└── Readme.md
```

---

#  Output

The final processed dataset was exported as:

```text
Cleaned_Product_Sales.csv
```

The dataset is:

* Cleaned
* Free from missing values
* Outlier treated
* Feature engineered
* One-Hot Encoded
* Standardized
* Ready for machine learning

---

#  Key Highlights

* Data Cleaning
* Missing Value Imputation
* Outlier Detection (IQR & Z-Score)
* Feature Engineering
* One-Hot Encoding
* Feature Scaling
* Machine Learning Ready Dataset

---

#  Future Improvements

* Build predictive machine learning models.
* Perform feature selection.
* Apply dimensionality reduction techniques (PCA).
* Develop interactive dashboards using Tableau or Power BI.
* Deploy the preprocessing pipeline as a web application using Streamlit.

---

##  Author

**Kirshna Parshad**

This project was completed as part of a Data Science Internship to strengthen practical skills in data preprocessing, feature engineering, and preparing real-world datasets for machine learning workflows.
