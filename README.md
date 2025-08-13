# Fraud Detection ML Project

A machine learning project for proactive detection of fraudulent financial transactions, using advanced feature engineering and model comparison.

---

## **Project Overview**

This project aims to **detect fraudulent transactions** for a financial institution using a large, real-world dataset. The goal is to build a model that flags suspicious transactions, provides actionable insights, and recommends infrastructure updates to reduce fraud losses.

---

## **Dataset**

- **Source:** Acquired from Accredian case study.
- **Size:** ~6.3 million rows, 10–11 columns.
- **Features:** Transaction step, type, amount, origin/destination accounts, balances before/after, fraud flag, etc.
- **Class Imbalance:** Fraud cases are extremely rare (~0.13%).

---

## **Project Steps**

### **1. Data Cleaning & Preparation**
- **Missing Values:** None found; all data was complete.
- **Outliers:** No extreme outliers detected; log-transformed transaction amount to reduce skew.
- **Multicollinearity:** Removed redundant/engineered features (e.g., balance deltas, multiple time features) to avoid multicollinearity.

### **2. Exploratory Data Analysis (EDA)**
- **Filtered** transaction types to keep only TRANSFER and CASH_OUT (the only types where fraud occurs).
- **Visualized** transaction patterns, fraud rates, and class distribution.
- **Identified** key fraud indicators: accounts emptied via transfers, moderate-sized transactions.

### **3. Feature Engineering**
- **Created** domain-driven features (e.g., `is_account_emptied`, log-transformed amount, transaction type flags).
- **Encoded** categorical variables.
- **Finalized** feature set: transaction amount, log amount, balances, transaction type, and account activity flags.

### **4. Model Development**
- **Models:** Logistic Regression, Random Forest, XGBoost.
- **Imbalance Handling:** Used class weights and sampling techniques.
- **Split:** 70% training, 30% test (stratified).

### **5. Model Evaluation**
- **Logistic Regression:** High recall, many false positives.
- **Random Forest:** High precision, misses some frauds.
- **XGBoost:** Best overall balance—catches almost all frauds with a manageable number of false alarms.
- **Metrics:** Classification reports, ROC-AUC, feature importance tables.

### **6. Findings**
- **Top Fraud Predictors:** Emptying accounts via transfers, transaction type, balances, and amount.
- **Real-World Relevance:** Features align with intuitive financial fraud scenarios.

### **7. Recommendations**
- **Real-time monitoring** of suspicious transactions (emptying accounts, transfers).
- **Rule-based alerts** combined with ML predictions.
- **Human review** for flagged cases to reduce false positives.
- **Continuous model updates** and behavioral analytics.

### **8. Validation**
- **Track metrics:** Fraud detection rate, false positive rate, time to detection.
- **A/B test** new vs. old systems.
- **Regular audits** and feedback loops for improvement.

---

## **How to Use This Repository**

1. **Clone the repository:**
git clone [your-repo-url]

text
2. **Navigate to the project directory.**
3. **Install dependencies** (if any, e.g., requirements.txt).
4. **Open and run the Jupyter Notebook** (`fraud_detection.ipynb` or similar) to reproduce the analysis.
5. **Review the report and model outputs** for detailed explanations.

---

## **Results & Insights**

- **XGBoost achieved the best overall performance**—nearly perfect recall with reasonable precision.
- **Random Forest** minimized false positives but missed more frauds.
- **Logistic Regression** had high recall but many false alarms.
- **Top features:** `is_account_emptied`, `type_TRANSFER`, `balance` changes, `amount`.
- **All results are realistic** and align with financial fraud patterns—no artificial “perfect” scores due to thorough feature engineering and leakage checks.

---

## **Author**

[Aditya Kumar Pandey]  
Contact: [aditya.240201001@iiitbh.ac.in]

---

## **Acknowledgments**

- **Dataset** provided by Accredian.


---

## **License**

This project is licensed under the MIT License - see the LICENSE file for details.****
