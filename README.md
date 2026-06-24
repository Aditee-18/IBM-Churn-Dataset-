# 📉 Customer segmentation and Churn prediction

**Name:** Aditee Srivastava 
---

## 📖 Overview

I recently started a 6-week internship at **Coding Blocks School of Technology**, where I am learning **Data Science, Machine Learning, and AI** concepts in depth. This repository contains my **first major project**, focused on deep exploratory analysis, data visualisation, and business-driven customer retention strategies.

### About the Dataset

The dataset used is the **IBM Telco Customer Churn Dataset**, which represents a fictional telecommunications company.

It contains:

- Customer demographics
- Account information (Tenure, Monthly Charges, Total Charges)
- Services subscribed to
- Contract details
- Payment methods
- Churn status

The objective of this project is to:

- Predict whether a customer will churn or stay.
- Understand the major factors behind customer churn.
- Develop actionable business strategies to improve customer retention.

---

## 🎯 Business Problem

Customer acquisition is significantly more expensive than customer retention.

By accurately predicting customers who are at high risk of churning, companies can:

- Launch targeted retention campaigns
- Offer discounts and personalized plans
- Improve customer satisfaction
- Reduce revenue loss
- Increase long-term customer value

---

## 🛠️ Libraries & Tools Used

- **Python**
- **Pandas** – Data manipulation
- **NumPy** – Numerical computations
- **Scikit-Learn**
  - Random Forest
  - K-Means Clustering
  - Grid Search CV
  - Cross Validation
  - Evaluation Metrics
- **Imbalanced-Learn**
  - SMOTE
- **Matplotlib**
- **Seaborn**

---

## 🧠 What I Learned Through This Project

During this project, I gained practical experience with:

- Data cleaning and preprocessing techniques.
- Exploratory Data Analysis (EDA) and data visualization.
- Feature encoding and feature selection.
- Random Forest classification.
- Hyperparameter tuning using Grid Search.
- Model evaluation using Accuracy, Precision, Recall, F1-Score, ROC-AUC, and Cross Validation.
- Handling imbalanced datasets using SMOTE.
- Threshold tuning and understanding business-oriented model optimization.
- Customer segmentation using K-Means Clustering.
- Translating machine learning results into business recommendations.
---

# 🧠 Project Workflow

---

## 1️⃣ Data Preprocessing & Exploratory Data Analysis

### Data Cleaning

- Handled missing values.
- Standardized data formats.
- Processed company-specific keywords.
- Ensured consistency across all columns.

### Exploratory Data Analysis (EDA)

Performed deep analysis to uncover relationships between:

- Customer demographics
- Billing structure
- Contract type
- Service subscriptions
- Customer churn

### Data Visualization

Created comprehensive visualizations using **Seaborn** and **Matplotlib** to identify:

- Which customers churn the most
- Impact of tenure on churn
- Influence of monthly charges
- Effect of contract types on retention

### Encoding

Converted categorical features into numerical representations suitable for machine learning models.

---

## 2️⃣ Predictive Modeling – Random Forest

### Train-Test Split

Split the dataset into training and testing sets to evaluate performance on unseen data.

### Baseline Model

Trained a **Random Forest Classifier** using:

```python
class_weight='balanced'
```

to account for class imbalance.

### Hyperparameter Tuning

Used **Grid Search CV** to find the best parameters.

### Key Observation

- Deep trees caused overfitting.
- A shallower tree:

```python
max_depth = 5
```

forced the model to generalize better and improved performance on unseen data.

### Feature Importance

Extracted:

```python
feature_importances_
```

to identify the most influential features.

Removed noisy and irrelevant columns to build:

- Faster model
- Simpler model
- More robust model

---

## 3️⃣ Advanced Techniques for High Recall

In a business setting:

> Missing a churner (**False Negative**) is much more expensive than incorrectly flagging a loyal customer (**False Positive**).

Therefore, maximizing **Recall** became the primary goal.

---

### ✅ Method A: Threshold Tuning 

Instead of using the default threshold:

```python
0.50
```

I lowered the classification threshold to:

```python
0.30
```

This instructed the model to flag customers even with moderate churn risk.

### Results

| Metric | Score |
|-------|------:|
| Recall | **95%** |
| Precision | 42% |
| F1 Score | 58% |

---

### Method B: SMOTE (Synthetic Minority Over-Sampling)

Generated synthetic churn samples to perfectly balance the dataset before training.

### Results

| Metric | Score |
|-------|------:|
| Recall | 72% |
| Precision | 58% |
| F1 Score | 64% |

### Why SMOTE Didn't Work Better

Many customers who churned shared the same characteristics as customers who stayed.

Examples:

- Similar Monthly Charges
- Similar Tenure
- Similar Service Plans

SMOTE generated synthetic churners directly within these overlapping regions.

As a result:

- Added noise to the dataset
- Increased ambiguity
- Confused the model
- Reduced recall compared to threshold tuning

---

## 4️⃣ Model Evaluation

### Cross Validation

Performed **5-Fold Cross Validation** on the optimized Random Forest model.

### Results

| Metric | Score |
|-------|------:|
| Average Recall | **82%** |
| Average Accuracy | **75%** |

The model remained stable across different train-test splits, indicating good generalization.

---

### ROC-AUC Score

Achieved:

```text
ROC-AUC = 0.845
```

This means:

> The model has an **84.5% probability** of ranking a randomly chosen churner as higher risk than a randomly chosen non-churner.

---

# 💼 Business Application & Insights

## Customer Segmentation using K-Means Clustering

Predicting churn is useful, but making those predictions actionable is even more important.

To help the marketing team:

- Extracted churn probabilities from the Random Forest model.
- Combined them with:
  - Monthly Charges
  - Tenure
- Applied **K-Means Clustering** to segment customers.

---

### Finding the Optimal Number of Clusters

Calculated:

- WCSS (Within Cluster Sum of Squares)

Applied:

- Elbow Method

This suggested:

```text
Optimal K = 3
```

---

# 📊 Customer Segments

---

## 🔴 1. High Risk New Customers (Primary Target)

**Characteristics**

- Short tenure (~11 months)
- High monthly charges (~$70/month)
- Average churn probability: **67%**

### Business Strategy

✅ Allocate most of the retention budget here.

Actions:

- Personalized discounts
- Immediate customer calls
- Contract upgrades
- Loyalty rewards

---

## 🟢 2. Loyal Premium Customers

**Characteristics**

- Long tenure (~58 months)
- Highest monthly charges (~$90/month)
- Average churn probability: **31%**

### Business Strategy

✅ Stable revenue base.

Actions:

- Upselling premium plans
- Cross-selling additional services
- Exclusive loyalty benefits

---

## 🔵 3. Budget Loyal Customers

**Characteristics**

- Medium tenure
- Low monthly charges (~$29/month)
- Average churn probability: **17%**

### Business Strategy

✅ Lowest churn risk.

Actions:

- Automated marketing campaigns
- Periodic engagement emails
- Minimal retention spending

---

# 🚀 Conclusion

This project helped me connect machine learning concepts with a real business use case.

Rather than focusing only on building a predictive model, I learned how to:

- Analyze customer behavior through data.
- Evaluate models using multiple metrics.
- Handle class imbalance problems.
- Make business-driven decisions when choosing model strategies.
- Convert predictions into actionable retention plans.

A key takeaway from this project was that machine learning is not just about achieving high accuracy—it is about solving the right business problem and providing insights that can lead to meaningful decisions.

This project marks the beginning of my journey into applied Data Science and Machine Learning, and it gave me valuable hands-on experience with the complete machine learning workflow from raw data to business recommendations.

---