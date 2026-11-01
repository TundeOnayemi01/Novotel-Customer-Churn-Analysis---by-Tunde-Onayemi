# NovoTel Customer Churn Analysis

Capstone project, Post Diploma in Data Analytics, College of the North Atlantic (2026)

## Business question
Which customers are likely to leave NovoTel, and what drives churn?

## Data
- 7,043 customer records, 21 columns
- Source: [IBM Telco Customer Churn dataset (Kaggle)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- Key fields: tenure, contract type, monthly and total charges, internet service, add-on services (online security, tech support), payment method and demographics
- Target: Churn (Yes/No). 26.5% of customers churned.

## Tools
Python (pandas, NumPy, Matplotlib, Seaborn, scikit-learn), Jupyter Notebook

## Approach
1. Data cleaning: Converted TotalCharges to numeric. Removed 11 rows with blank TotalCharges (new customers with 0 months tenure) and 22 rows identical on every field except customer ID. Dropped customerID. Final dataset: 7,010 rows, 20 columns.
2. Exploratory analysis: Compared churn rates across customer, account and service features using stacked bar charts, KDE plots, correlation heatmaps and box plots.
3. Predictive modelling: Compared Logistic Regression, Decision Tree, Random Forest and Gradient Boosting using stratified 10-fold cross-validation on an 80/20 train-test split. Logistic Regression had the highest recall. It was tuned with GridSearchCV (C=0.01, balanced class weights), and the decision threshold was lowered to 0.40.
4. Evaluation: Recall was the main metric, since missing a churner costs more than a false alarm. On the unseen test set (1,402 customers): recall 0.86, precision 0.47, F1 0.61, accuracy 0.71. The model caught 320 of 371 churners.

## Key findings
- Month-to-month customers churned at 42.6%, compared with 11.3% for one-year and 2.8% for two-year contracts.
- Fiber optic customers churned at 41.8%, more than double the DSL rate (18.9%).
- Electronic check users churned at 45.1%, compared with 15 to 17% for automatic payments.
- Customers without tech support (41.5%) or online security (41.6%) churned at nearly three times the rate of those with these add-ons.
- Churners were concentrated in their first few months of service and at monthly charges of about $80 to $90.
- Tenure and two-year contracts were the strongest predictors (permutation importance).
- Gender and phone service had no meaningful effect on churn.

## Recommendations
- Target new customers with onboarding support or discounts in their first months.
- Offer incentives to move month-to-month customers onto one- or two-year contracts.
- Bundle or offer free trials of online security and tech support.
- Encourage auto-pay over electronic checks.
- Keep retention offers low-cost, since about half of flagged customers (precision 0.47) would have stayed anyway.
