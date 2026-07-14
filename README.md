# OLA Driver Attrition Prediction using Ensemble Learning

## Project Overview

Driver retention is one of the biggest operational challenges faced by ride-hailing companies such as Ola. High driver attrition increases recruitment costs, reduces operational efficiency, and negatively impacts customer experience. Predicting which drivers are likely to leave enables the company to take proactive retention measures.

This project develops a machine learning pipeline to predict driver attrition using demographic information, employment history, performance metrics, and income data. The solution applies feature engineering, missing value imputation, class imbalance handling, and ensemble learning algorithms to build a robust predictive model.

---

## Business Problem

Recruiting new drivers is significantly more expensive than retaining existing ones. Drivers frequently switch platforms or leave due to income fluctuations, poor performance ratings, or limited career growth.

The objective of this project is to build a binary classification model that predicts whether a driver is likely to leave the company.

---

## Objectives

* Perform comprehensive Exploratory Data Analysis (EDA)
* Handle missing values using KNN Imputation
* Aggregate monthly records into driver-level observations
* Engineer meaningful features
* Handle class imbalance
* Train ensemble learning models
* Evaluate models using appropriate classification metrics
* Generate business recommendations to improve driver retention

---

## Dataset Information

Each row represents a driver's monthly performance during 2019–2020.

### Features

| Feature              | Description                |
| -------------------- | -------------------------- |
| MMMM-YY              | Reporting Month            |
| Driver_ID            | Unique Driver Identifier   |
| Age                  | Driver Age                 |
| Gender               | Male (0), Female (1)       |
| City                 | Driver City Code           |
| Education_Level      | Education Level            |
| Income               | Monthly Income             |
| Date Of Joining      | Joining Date               |
| LastWorkingDate      | Last Working Date          |
| Joining Designation  | Initial Designation        |
| Grade                | Current Grade              |
| Total Business Value | Monthly Business Generated |
| Quarterly Rating     | Performance Rating (1–5)   |

---

# Project Workflow

## 1. Exploratory Data Analysis

Performed detailed EDA including:

* Dataset dimensions
* Data types
* Missing value analysis
* Duplicate record detection
* Statistical summaries
* Distribution analysis
* Outlier detection
* Correlation analysis
* Univariate and bivariate visualizations

Key visualizations include:

* Histograms
* Boxplots
* Countplots
* Correlation Heatmap
* Pairplots
* Target distribution

---

## 2. Data Preprocessing

### Date Conversion

Converted:

* Reporting Month
* Date Of Joining
* Last Working Date

to datetime format.

### Missing Value Treatment

Applied **KNN Imputer** on numerical variables to preserve relationships among observations.

### Driver-Level Aggregation

Since each driver appears multiple times (monthly observations), the data was aggregated into one record per driver using:

* Latest Grade
* Latest City
* Latest Income
* Latest Quarterly Rating
* Total Business Value statistics
* First Joining Date
* Last Working Date

---

## 3. Feature Engineering

Created several new features including:

### Target Variable

**Target = 1**

Driver has left the company

**Target = 0**

Driver is still active

(Target created from LastWorkingDate)

---

### Income Increase

Binary feature indicating whether monthly income increased during the driver's tenure.

---

### Quarterly Rating Improvement

Binary feature indicating whether the driver's quarterly rating improved over time.

---

### Additional Features

Examples include:

* Driver tenure
* Promotion indicator
* Grade improvement
* Business performance trends
* Average business generated
* Maximum business generated

---

## 4. Encoding

Categorical variables encoded using:

* One-Hot Encoding

---

## 5. Feature Scaling

Applied **StandardScaler** on numerical variables before model training.

---

## 6. Handling Class Imbalance

Since attrition datasets are naturally imbalanced, class imbalance was addressed using techniques such as:

* SMOTE (Synthetic Minority Oversampling Technique)

or

* Class Weight Balancing

depending on the model.

---

# Machine Learning Models

## Bagging Model

* Random Forest Classifier

Hyperparameters tuned using GridSearchCV / RandomizedSearchCV.

---

## Boosting Models

Implemented and compared:

* AdaBoost
* Gradient Boosting
* XGBoost
* LightGBM (optional)
* CatBoost (optional)

Hyperparameter tuning performed to maximize predictive performance.

---

# Model Evaluation

Performance evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC Score
* Confusion Matrix
* ROC Curve

Models were compared to identify the best-performing ensemble method.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Plotly
* Scikit-learn
* Imbalanced-learn
* XGBoost
* LightGBM
* CatBoost

---

# Project Structure

```
OLA-Driver-Attrition-Prediction/
│
├── data/
│   └── ola_driver.csv
│
├── notebooks/
│   └── OLA_Driver_Attrition.ipynb
│
├── images/
│   ├── correlation_heatmap.png
│   ├── roc_curve.png
│   └── feature_importance.png
│
├── README.md
└── requirements.txt
```

---

# Business Insights

* Drivers with declining quarterly ratings exhibit a higher probability of attrition.
* Income stagnation is strongly associated with driver churn.
* Drivers generating consistently low business value are more likely to leave.
* Longer-tenured drivers generally demonstrate greater retention.
* Promotions and grade improvements positively influence retention.
* Certain cities experience higher attrition rates, indicating regional operational differences.

---

# Recommendations

* Implement early-warning systems for drivers showing declining ratings or reduced business performance.
* Review compensation structures for drivers with stagnant income.
* Introduce incentive programs and performance-based rewards for high-performing drivers.
* Provide mentoring and support for newly onboarded drivers during their initial months.
* Conduct city-specific retention analyses to identify localized causes of attrition.
* Monitor driver engagement through periodic feedback and satisfaction surveys.

---

# Future Improvements

* Incorporate time-series models to capture performance trends more effectively.
* Use explainable AI techniques such as SHAP or LIME for model interpretability.
* Deploy the trained model as a REST API or interactive dashboard.
* Integrate real-time driver activity data for continuous attrition monitoring.

---

# Conclusion

This project demonstrates an end-to-end machine learning workflow for predicting driver attrition using ensemble learning techniques. Through comprehensive data preprocessing, feature engineering, imbalance handling, and model evaluation, the solution identifies drivers at risk of leaving, enabling proactive retention strategies and supporting data-driven decision-making.
