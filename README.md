
---

## Features & Methodology

### 1. Data Cleaning
- Date parsing  
- Handling missing values  
- Label encoding (Yes/No → 1/0)  
- Combining inpatient, outpatient, and beneficiary information  

### 2. Feature Engineering (Provider Level)
Engineered attributes include:
- Number of unique patients  
- Total and average payments  
- Outpatient and inpatient claim counts  
- Length-of-stay statistics  
- Maximum payment amounts  
- Claim duration metrics  

Final dataset: **22 provider-level features**

---

## Modeling Approach

### Models Trained
- **Logistic Regression**
- **Random Forest**
- **Gradient Boosting**

### Handling Class Imbalance
- **SMOTE applied only to the training set**
- Validation evaluated on original imbalanced distribution

### Metrics Used
- Accuracy  
- Precision  
- Recall  
- F1-Score  
- ROC-AUC  
- **Precision–Recall AUC (most important)**  

---

## Results Summary

| Model | ROC-AUC | PR-AUC | Recall | Precision |
|-------|---------|--------|--------|-----------|
| Logistic Regression | 0.947 | 0.775 | 0.88 | 0.53 |
| **Random Forest** | **0.967** | **0.785** | 0.77 | 0.63 |
| Gradient Boosting | 0.968 | 0.754 | 0.66 | **0.80** |

### **Final Model: Random Forest**
Selected for its **best PR-AUC**, strong ROC-AUC, and balanced performance metrics.

---

## Feature Importance (Random Forest)
Top predictors of fraud:
1. **max_length_of_stay**
2. total_inpatient_payment  
3. max_inpatient_payment  
4. num_outpatient_claims  
5. total_outpatient_payment  

Fraudulent providers tend to:
- Exhibit unusually long patient stays  
- Submit high-value claims  
- Have large numbers of outpatient/inpatient claims  
- Serve many different patients  

---

## Error Analysis
- **False Positives:** 46  
  - Non-fraud providers incorrectly flagged  
  - Impact: extra auditing (acceptable)

- **False Negatives:** 23  
  - Fraud providers missed  
  - Most risky error type

---

## Installation

### 1. Create virtual environment
```bash
python -m venv .venv
.venv\Scripts\activate
