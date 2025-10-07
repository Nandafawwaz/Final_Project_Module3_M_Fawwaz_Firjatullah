# Final Project Module 3 - Travel Insurance Claim Prediction

This project is part of **Purwadhika Capstone Module 3 (Machine Learning)** and focuses on predicting whether a travel insurance claim will be made by a customer.  
The goal is to help the insurance company reduce unnecessary claim investigations and operational costs by identifying high-risk customers efficiently.

## Project Overview

Insurance companies often face high investigation costs due to the need to manually check every claim.  
This project aims to build a **classification model** that predicts whether a customer will make a **claim** or not, enabling the company to prioritize only likely claimants.

---

## Dataset

The dataset containin information such as:

| Feature | Description |
|----------|--------------|
| Agency | Travel agency handling the booking |
| Agency Type | Type of agency (e.g., Air, Travel) |
| Distribution Channel | How the insurance was sold |
| Product Name | Type of insurance product |
| Duration | Duration of the trip |
| Destination | Travel destination |
| Net Sales | Total sales value |
| Commission | Commission earned |
| Gender | Customer gender |
| Age | Customer age |
| Claim | Target variable (1 = claimed, 0 = not claimed) |

---

## Data Preprocessing & Feature Engineering

Steps performed:
1. **Dropped uninformative columns:** `Agency Type`, `Distribution Channel`
2. **Handled categorical variables** using one-hot encoding and binary encoding
3. **Scaled numerical features** using `RobustScaler`
4. **Split the dataset** into train and test sets (80/20)
5. **Handled severe class imbalance** using class weighting and bagging

---

## Modeling

Several models were tested:
- Logistic Regression (baseline)
- KNN
- XGBoost
- Decision Tree
- Random Forest
- LightGBM
- Logreg + Random Forest + LightGBM Stacked
- **Bagging Logistic Regression (final model)**

The **Bagging Logistic Regression** model achieved the best trade-off between recall and cost efficiency.

## Cost Simulation

| Scenario                       | People Checked | Claims Captured | Total Cost | Savings vs. Baseline |
| ------------------------------ | -------------- | --------------- | ---------- | -------------------- |
| **Without Model**              | 8866 (100%)    | 135             | $44,330    | —                    |
| **With Model (Bagged LogReg)** | 1535 (17.31%)  | 85 (62.96%)     | $7,675     | **$36,655 Saved**    |

Interpretation:
Using the model allows the company to focus on high-risk customers and reduce manual checks by over 80%, saving substantial investigation costs while still identifying most legitimate claims.
