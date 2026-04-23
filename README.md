# Telco Customer Churn Prediction 📉

A complete end-to-end machine learning project predicting customer churn 
for a telecommunications company. Built as a hands-on learning project 
by a non-technical product manager learning to code.

---

## 📌 Business Context

Customer churn — when a customer cancels their service and moves to a 
competitor — is one of the most costly problems in the telecom industry. 
Acquiring a new customer costs 5 to 25 times more than retaining an 
existing one. Even a 5% reduction in churn can increase profitability 
by 25 to 95%.

The goal of this project is to answer two business questions:
1. **Who is likely to churn?** — Build a model that flags at-risk customers
   before they cancel, so the retention team can intervene proactively.
2. **Why do they churn?** — Identify the key drivers of churn so the 
   product and commercial teams can address root causes.

---

## 📊 Dataset

**Source:** [IBM Telco Customer Churn Dataset via Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

**Size:** 7,032 customers × 20 features (after cleaning)

**Target variable:** `Churn` — whether a customer left within the last month

### Feature categories:

| Category | Features |
|---|---|
| Demographics | Gender, SeniorCitizen, Partner, Dependents |
| Services | PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies |
| Account info | Tenure, Contract, PaperlessBilling, PaymentMethod, MonthlyCharges, TotalCharges |

---

## 🔍 Key Findings

### Churn Drivers
Through exploratory data analysis and model feature importance, three 
factors emerged as dominant predictors of churn:

**1. Contract Type** — The single strongest predictor of churn.

| Contract | Churn Rate |
|---|---|
| Month-to-month | 42.7% |
| One year | 11.3% |
| Two year | 2.8% |

Month-to-month customers churn at **15x the rate** of two-year contract 
customers. This is the most actionable finding in the entire project.

**2. Internet Service Type** — Fiber optic customers churn at nearly 
double the rate of DSL customers (41.9% vs 19.0%), suggesting a potential 
gap between customer expectations and service delivery for the premium tier.

**3. Tenure** — Nearly half of customers (47.7%) churn within their first 
12 months. Churn drops dramatically with time — customers who reach 
5+ years churn at just 6.6%. The first year is the critical retention window.

### Business Recommendations
- **Annual contract incentive programme** — Offer month-to-month customers 
  a meaningful discount to switch to annual contracts. The 15x churn rate 
  difference justifies significant incentive spend.
- **New customer onboarding** — Build a structured 90-day onboarding 
  programme targeting the highest-risk window. Customers who feel 
  supported in year one are far more likely to stay.
- **Fiber optic investigation** — Conduct targeted NPS surveys and customer 
  interviews for Fiber optic customers to understand whether churn is 
  driven by price, quality, or competitor offers.
- **CRM integration** — Deploy the trained model in the CRM to 
  automatically flag high-risk customers for proactive retention calls 
  before they cancel.

---

## 🤖 Models & Results

Three models were trained and evaluated on a held-out test set of 1,407 
customers (20% of the data).

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.805 | 0.650 | 0.572 | 0.609 | 0.836 |
| Random Forest | 0.790 | 0.628 | 0.511 | 0.563 | 0.820 |
| **XGBoost** | **0.749** | **0.520** | **0.714** | **0.602** | **0.821** |

**Chosen model: XGBoost** — selected for its superior Recall (0.714), 
meaning it successfully identifies 71.4% of customers who actually churn. 
For a retention use case, missing a churner is more costly than a false 
alarm, making Recall the primary evaluation metric.

---

## 🗂️ Project Structure

```
churn-prediction/
│
├── churn_analysis.ipynb        # Main notebook: full analysis end-to-end
├── requirements.txt            # Python dependencies
├── xgboost_churn_model.pkl     # Trained XGBoost model
├── scaler.pkl                  # Fitted StandardScaler for new data
├── feature_columns.pkl         # Encoded feature names for alignment
└── .gitignore                  # Excludes data files and cache
```

> **Note:** The dataset CSV is not included in this repository as a best 
> practice for data privacy. Download it directly from the 
> [Kaggle page](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.13 | Core language |
| pandas | Data manipulation and cleaning |
| matplotlib + seaborn | Data visualisation |
| scikit-learn | Preprocessing, model evaluation |
| XGBoost | Primary prediction model |
| Jupyter Notebook | Interactive analysis environment |
| Git + GitHub | Version control |

---

## 🚀 How to Run This Project

1. Clone the repository
```bash
   git clone https://github.com/adamfaik/churn-prediction.git
   cd churn-prediction
```

2. Install dependencies
```bash
   pip install -r requirements.txt
```

3. Download the dataset from 
   [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) 
   and place `WA_Fn-UseC_-Telco-Customer-Churn.csv` in the project folder

4. Open the notebook
```bash
   jupyter notebook churn_analysis.ipynb
```

5. Run all cells from top to bottom

---

## 👤 Author

Built by **Adam Faik** as a hands-on learning project — using Claude.ai 
(Anthropic) as an AI tutor throughout the build.