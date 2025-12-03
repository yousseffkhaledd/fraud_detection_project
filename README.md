# Healthcare Provider Fraud Detection

## Project Overview

Machine learning system to flag potentially fraudulent healthcare providers using provider-level patterns from Medicare claims. The goal is to help auditors focus on high-risk providers, reduce losses, and keep false alarms reasonable.

## Team Members

- Dareen: Notebook 1
- Sara Ezzat: Notebook 2
- Youssef Khaled: Notebook 3
- Omar Belal: Report and Powerpoint

## Summary of Results

- Final model: Random Forest (tuned)
- Performance (fraud class): PR-AUC 0.785, ROC-AUC 0.967, Recall 0.74, Precision 0.63
- Financial impact (test period):
	- Fraud detected (TP): $32,370,000
	- Audit overhead (FP): $270,000
	- Missed fraud (FN): $11,368,000
	- Net savings: $20,702,000 (≈10,800% ROI)
- Top fraud indicators: max_length_of_stay, total/max inpatient payment, num_outpatient_claims, total_outpatient_payment

## Reproduction Instructions


### Prerequisites
- Python 3.8+
- Jupyter Notebook or Google Colab


### Setup
```bash
git clone https://github.com/yousseffkhaledd/fraud_detection_project.git
cd fraud_detection_project
python -m venv .venv
.venv\\Scripts\\activate
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn joblib
```

### Run Notebooks (in order)
```bash
jupyter notebook notebooks/01_data_exploration_and_feature_engineering.ipynb
jupyter notebook notebooks/02_modeling.ipynb
jupyter notebook notebooks/03_evaluation.ipynb
```

Notes:
- Notebook 1 produces `data/processed_data_ready_for_modeling.csv`.
- Notebook 2 trains and saves the tuned Random Forest and test set artifacts.
- Notebook 3 reports metrics, plots, and the financial impact figures above.
