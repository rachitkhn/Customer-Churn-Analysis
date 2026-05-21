# 📉 Customer Churn Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-green?style=flat-square&logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

> An end-to-end machine learning project predicting customer churn using client behavioural data and pricing history — structured across dedicated notebooks for EDA, feature engineering, and modelling to reflect real-world data science workflows.

---

## 📌 Project Overview

Customer churn — the loss of clients to competitors or cancellation — is one of the most costly challenges businesses face. Retaining an existing customer is significantly cheaper than acquiring a new one, making churn prediction a high-value analytical capability.

This project builds a complete churn prediction pipeline using two datasets: **client profile data** and **price history data**. By combining behavioural, contractual, and pricing signals, the model identifies customers at high risk of churning, enabling targeted retention strategies before it's too late.

The project is structured across three dedicated notebooks, mirroring a professional data science workflow — from raw data exploration through to model deployment-readiness.

---

## 🎯 Objectives

- Explore and understand the drivers of customer churn through rigorous EDA
- Engineer meaningful features from client and pricing data to improve predictive power
- Build, evaluate, and compare classification models for churn prediction
- Deliver actionable insights and a retention-ready churn scoring model

---

## 📂 Repository Structure

```
Customer-Churn-Analysis/
│
├── EDA.ipynb                          # Exploratory Data Analysis — distributions, patterns, churn drivers
├── Feature-ChurnAnalysis.ipynb        # Feature engineering, selection, and transformation
├── Modelling and Evaluation.ipynb     # Model training, hyperparameter tuning, and evaluation
│
├── client_data.csv                    # Customer profile and behavioural attributes
├── price_data.csv                     # Historical pricing data per customer
│
├── README.md
└── LICENSE
```

---

## 📊 Datasets

### `client_data.csv` — Customer Profile Data
Contains customer-level attributes capturing demographic information, contract details, and consumption behaviour:

| Feature | Description |
|---|---|
| `id` | Unique customer identifier |
| `channel_sales` | Sales channel through which the customer was acquired |
| `cons_12m` | Electricity consumption over the last 12 months |
| `cons_gas_12m` | Gas consumption over the last 12 months |
| `cons_last_month` | Consumption in the most recent month |
| `date_activ` | Date the customer's contract was activated |
| `date_end` | Contract end date |
| `date_modif_prod` | Date the product was last modified |
| `date_renewal` | Upcoming contract renewal date |
| `forecast_cons_12m` | Forecasted consumption for next 12 months |
| `has_gas` | Whether the customer has a gas contract |
| `imp_cons` | Current electricity consumption |
| `margin_gross_pow_ele` | Gross margin on power electricity |
| `margin_net_pow_ele` | Net margin on power electricity |
| `nb_prod_act` | Number of active products |
| `net_margin` | Net margin for the customer |
| `num_years_antig` | Customer tenure in years |
| `origin_up` | Origin of the customer's electricity campaign |
| `pow_max` | Maximum power subscribed |
| `churn` | **Target variable** — 1 = Churned, 0 = Retained |

### `price_data.csv` — Historical Pricing Data
Contains time-series pricing records per customer, enabling price sensitivity analysis:

| Feature | Description |
|---|---|
| `id` | Customer identifier (links to client_data) |
| `price_date` | Date of the price record |
| `price_off_peak_var` | Variable price during off-peak period |
| `price_peak_var` | Variable price during peak period |
| `price_mid_peak_var` | Variable price during mid-peak period |
| `price_off_peak_fix` | Fixed price during off-peak period |
| `price_peak_fix` | Fixed price during peak period |
| `price_mid_peak_fix` | Fixed price during mid-peak period |

---

## 🔬 Methodology

### Notebook 1 — Exploratory Data Analysis (`EDA.ipynb`)
- Assessed data quality: missing values, data types, and distributions
- Analysed churn rate across customer segments (tenure, sales channel, consumption level)
- Investigated correlations between pricing behaviour and churn likelihood
- Visualised consumption patterns, contract timelines, and margin distributions
- Identified class imbalance in the churn target variable

### Notebook 2 — Feature Engineering (`Feature-ChurnAnalysis.ipynb`)
- Merged `client_data` and `price_data` on customer ID for a unified feature space
- Engineered time-based features from contract dates (days to renewal, contract duration, months since activation)
- Created price sensitivity features: average price changes, peak-to-off-peak price ratios, price volatility
- Derived consumption trend features from 12-month vs. last-month consumption
- Applied encoding for categorical variables and scaling for continuous features
- Used feature importance techniques (Random Forest, correlation analysis) to select the most predictive attributes

### Notebook 3 — Modelling & Evaluation (`Modelling and Evaluation.ipynb`)

**Models trained:**

| Model | Characteristic |
|---|---|
| Logistic Regression | Interpretable linear baseline |
| Random Forest | Robust ensemble; handles non-linearity well |
| Gradient Boosting | High-performance boosted trees |
| XGBoost | Optimised gradient boosting with regularisation |

**Techniques applied:**
- Train/test split with stratification to preserve churn class balance
- Cross-validation (k=5) for reliable generalisation estimates
- SMOTE or class weighting to address class imbalance
- Hyperparameter tuning via Grid Search / Random Search
- Threshold optimisation to balance precision and recall for business use

**Evaluation metrics:**

| Metric | Business Relevance |
|---|---|
| Accuracy | Overall correctness |
| Precision | Avoid wasting retention budget on non-churners |
| Recall | Ensure at-risk customers are captured |
| F1 Score | Balance between precision and recall |
| AUC-ROC | Overall discriminative ability of the model |
| Confusion Matrix | Detailed breakdown of predictions |

---

## 📈 Key Insights

- **Price sensitivity is a primary churn driver** — customers exposed to high peak-to-off-peak price differentials showed significantly elevated churn rates
- **Contract renewal proximity matters** — churn risk spikes sharply in the 3 months leading up to contract expiry
- **Tenure is protective** — long-standing customers (5+ years) churn at a substantially lower rate than newer customers
- **Consumption decline signals disengagement** — customers whose monthly consumption dropped below their 12-month average were disproportionately likely to churn
- **Sales channel influences loyalty** — certain acquisition channels produced materially higher-risk customer cohorts

---

## 🛠️ Technologies Used

- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, XGBoost, imbalanced-learn
- **Environment:** Jupyter Notebook

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/rachitkhn/Customer-Churn-Analysis.git
cd Customer-Churn-Analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn jupyter

# Run notebooks in order
jupyter notebook EDA.ipynb
jupyter notebook "Feature-ChurnAnalysis (1).ipynb"
jupyter notebook "Modelling and Evaluation.ipynb"
```

---

## 💡 Business Applications

- **Proactive Retention:** Identify high-risk customers weeks before contract expiry and trigger targeted retention offers
- **Pricing Strategy:** Use price sensitivity insights to design competitive tariffs that reduce churn without sacrificing margin
- **Customer Segmentation:** Cluster customers by churn risk profile to personalise engagement and communication strategies
- **Revenue Protection:** Quantify the revenue at risk from predicted churners and prioritise intervention accordingly

---

## 👤 Author

**Rachit Khandelwal**
[GitHub](https://github.com/rachitkhn) · [LinkedIn](https://linkedin.com/in/rachitkhn)

---

*This project was developed as part of a data science portfolio, demonstrating end-to-end ML workflow design, feature engineering depth, and business-focused analytical thinking.*
