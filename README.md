# Telco Customer Churn Analysis

## 1. Business Problem

Telecommunication companies lose revenue when customers stop using their services. This project analyzes customer churn patterns and builds a predictive model to identify customers who are likely to leave.

The goal is to help a telecom company understand the main drivers of churn and recommend actions to improve customer retention.

## 2. Project Objectives

- Understand the characteristics of customers who churn.
- Identify important churn drivers such as contract type, tenure, payment method, and monthly charges.
- Build a machine learning model to predict customer churn.
- Evaluate the model using business-relevant metrics.
- Recommend retention strategies based on the findings.


## 3. Dataset

The project uses the IBM Telco Customer Churn dataset containing **7,043 customer records** and **21 features** describing customer demographics, subscribed services, billing information, and churn status.

The target variable is:

- **Churn** (Yes/No)

Key features include:

- Contract
- Tenure
- MonthlyCharges
- TotalCharges
- PaymentMethod
- InternetService
- OnlineSecurity
- TechSupport

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- SQL
- Git
- GitHub
- Jupyter Notebook

## 5. Key Business Questions

1. What percentage of customers churned?
2. Which contract types have the highest churn?
3. Does customer tenure affect churn?
4. Do customers with higher monthly charges churn more?
5. Which payment methods are associated with higher churn?
6. Can we predict whether a customer will churn?

## 6. Expected Outcome

The final output will include:

- SQL analysis
- Exploratory data analysis
- Churn prediction model
- Model evaluation
- Business recommendations

## Key Findings

### 1. Overall churn rate

The dataset contains 7,043 customers, with an overall churn rate of approximately 26.54%.

### 2. Contract type is a major churn driver

Customers on month-to-month contracts have the highest churn rate at approximately 42.71%, compared to 11.27% for one-year contracts and 2.83% for two-year contracts.

![Churn by Contract](reports/figures/churn_rate_by_contract.png)

### 3. New customers are most at risk

Customers with 0–12 months tenure have the highest churn rate at approximately 47.44%. Churn decreases as tenure increases.

![Churn by Tenure](reports/figures/churn_rate_by_tenure_group.png)

### 4. Payment method matters

Customers using electronic check have the highest churn rate among payment methods at approximately 45.29%.

### 5. Highest-risk segment

The highest-risk customer profile is:

- Month-to-month contract
- 0–12 months tenure
- Electronic check payment method
- High monthly charges

This segment has a churn rate of approximately 70.24% and contributes an estimated 413 churned customers.

![Top Risk Segment](reports/figures/top_segments_expected_churn.png)

## Modeling Summary

A Logistic Regression model was trained as the baseline model.

At the default threshold of 0.50:

- Accuracy: approximately 80%
- Churn precision: 65%
- Churn recall: 52%
- Churn F1-score: 58%

After lowering the threshold to 0.40:

- Accuracy: approximately 78%
- Churn precision: 58%
- Churn recall: 66%
- Churn F1-score: 62%

Lowering the threshold improved the model’s ability to identify churners, which may be useful if retention actions are low-cost.

![Detailed Risk Segments](reports/figures/top_full_risk_segments_expected_churn.png)



## Stakeholder Recommendations & Business Action Plan

### Executive Summary
Based on the data analysis of 7,043 telecom customers, the overall churn rate is **26.54%** (1,869 churned customers). Churn is heavily concentrated among **new customers**, **month-to-month contract holders**, and **electronic check payment users**.

---

### High-Risk Segment Identification
1. **Contract Type**: Month-to-month contract holders have a **42.71%** churn rate, compared to **11.27%** for 1-year and **2.83%** for 2-year contracts.
2. **Tenure Window**: Customers in their first year (0–12 months) experience a **47.44%** churn rate, whereas tenure > 48 months drops to **9.51%**.
3. **Payment Method**: Electronic check users churn at **45.29%**, with **78.22%** of them sitting on month-to-month plans.
4. **Primary High-Risk Cohort**: Customers with **Month-to-Month + 0–12 Months Tenure + Electronic Check** hit a **63.10%** churn rate (954 customers, representing ~602 expected churns).

---

### Strategic Action Plan

#### 1. Onboarding & Early Lifecycle Retention (Months 0–12)
- **Implement a 90-Day VIP Onboarding Sequence**: Trigger automated check-ins at Day 30, 60, and 90 to identify service issues early.
- **First-Year Renewal Incentives**: Offer loyalty perks or service add-on discounts at Month 6 to encourage tenure extension.

#### 2. Contract Transition Strategy
- **Annual Plan Upgrade Campaign**: Target month-to-month users with targeted pop-ups or email offers highlighting annual savings.
- **Flexible Contract Options**: Test 6-month or hybrid contract options to bridge the gap between month-to-month and multi-year commitments.

#### 3. Payment Method Migration
- **Autopay Adoption Incentive**: Provide a one-time bill credit ($10–$15) to transition electronic check users to Automatic Bank Transfer or Credit Card billing.
- **Billing Friction Audit**: Investigate potential UX/technical issues associated with electronic check processing that may cause dissatisfaction.

---

### Prioritized Target Matrix
| Priority Level | Segment Description | Churn Rate | Primary Action |
| :--- | :--- | :--- | :--- |
| **Tier 1 (Critical)** | Month-to-Month + Tenure 0–12 mo + Electronic Check | **63.10%** | Immediate onboarding intervention & Autopay incentive |
| **Tier 2 (High)** | Month-to-Month + Tenure 0–12 mo (All Payments) | **51.35%** | First-year contract conversion campaign |
| **Tier 3 (Medium)** | Electronic Check (All Contracts) | **45.29%** | Payment method migration push |