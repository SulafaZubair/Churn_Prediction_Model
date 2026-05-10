                                    CHURN PREDICTION PROJECT
PROBLEM STATEMENT:
The goal of this project is to predict whether a Foodpanda customer is likely to churn (i.e., stop using the service) based on their behavioral and transactional data. The project involves performing data preprocessing, feature engineering, and exploratory data analysis to extract key insights. Multiple supervised machine learning algorithms will be implemented and compared, and techniques will be applied to improve model performance if the predictive accuracy is below 80%. The target variable for prediction is churned.

Key Points in This Problem Statement:

Prediction Task – “predict whether a customer will churn” → Binary classification.

Target Variable – Clearly mentioned (churned).

Data Preparation – Preprocessing & feature engineering are included.

Exploratory Analysis – Visualizations with Matplotlib/Seaborn to extract insights.

Modeling – Multiple supervised algorithms and performance comparison.

Optimization – Improve accuracy if below threshold.

Business Motivation:

Predicting customer churn helps Foodpanda take proactive steps to retain customers, reduce revenue loss, and improve customer engagement.

# Customer Churn Prediction Project

## Overview
This project aims to **predict whether a customer will churn** (stop using the service) using transactional, demographic, and behavioral data.  
The target variable is `Churned` (0 = active, 1 = churned).

The dataset contains 27+ features including:

- Demographics: age, gender, city  
- Transactional: restaurant_name, category, quantity, price, order_frequency  
- Loyalty: loyalty_points, active_tenure_days, total_tenure_days  
- Other: days_since_last_order, delivery_status, rating  

---

## Data Preprocessing

1. **Encoding categorical features** using one-hot encoding:
   - gender, age, city, restaurant_name, category, delivery_status
2. **Feature engineering**:
   - `spend_per_item` = price / quantity  
   - `order_gap` = days_since_last_order / (order_frequency + 1)  
   - `loyalty_strength` = loyalty_points / (active_tenure_days + 1)  
   - `customer_satisfaction` (based on rating and loyalty points)
3. **Train-test split**:
   - 80% training, 20% testing, stratified on `Churned`
4. **Scaling**: Not required for tree-based models.

---

## Feature Importance

Top features identified by Random Forest:

| Feature | Importance |
|---------|------------|
| spend_per_item | 0.104 |
| price | 0.096 |
| loyalty_points | 0.096 |
| loyalty_strength | 0.095 |
| order_gap | 0.095 |
| days_since_last_order | 0.095 |
| active_tenure_days | 0.083 |
| order_frequency | 0.071 |

**Insight:**  
Behavioral features dominate the model, while demographic and categorical features contribute almost no predictive power.

---

## Modeling

- **Model used:** Random Forest Classifier  
- **Hyperparameters:** n_estimators=300, max_depth=10, min_samples_split=5, min_samples_leaf=2  
- **Evaluation metrics:**
  - Accuracy: 50.5%  
  - ROC-AUC: 0.52  

**Observation:** Model performance is only slightly better than random guessing due to weak signal in the dataset.

---



---

## Conclusion

- Current data is insufficient for high-accuracy churn prediction.  
- Top features driving churn are behavioral: spend_per_item, price, loyalty_points, order_gap, etc.  
- Model provides insights into feature importance but cannot reliably separate churners from non-churners.  
- Future data collection and temporal feature engineering are essential for meaningful predictions.

---

## Author
Sulafa Zubair
- Date: March 2026  

---

