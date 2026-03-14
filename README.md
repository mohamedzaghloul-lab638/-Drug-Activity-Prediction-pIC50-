🧬 Drug Activity Prediction (pIC50)

A machine learning pipeline for predicting the biological activity (pIC50) 
of drug-like molecules using molecular fingerprints and physicochemical descriptors.

📌 Overview
This project builds a predictive model for molecular bioactivity using data 
from ChEMBL database, transforming IC50 values to pIC50 and training an 
XGBoost regression model.

🔬 Workflow
1. **Data Collection** — Fetching bioactivity data from ChEMBL
2. **Data Preprocessing** — Cleaning, filtering, and converting IC50 → pIC50
3. **Feature Engineering** — Morgan Fingerprints (2048-bit) + RDKit Descriptors
4. **Model Training** — XGBoost Regressor with GridSearchCV optimization
5. **Prediction** — Predicting pIC50 & IC50 for new molecules

⚙️ Features
- Morgan Fingerprints (radius=2, 2048-bit)
- Physicochemical Descriptors: MolWt, LogP, TPSA, HBA, HBD, RotBonds
- Hyperparameter tuning via GridSearchCV

📊 Model Performance and Optimisation
| Model | R² Score | RMSE |
|-------|----------|------|
| Random Forest | 0.637 | 0.548 |
| XGBoost | 0.719 | 0.482 |
| XGBoost + GridSearch | 0.733 | 0.470 |

🛠️ Tech Stack
- Python, RDKit, Scikit-learn, XGBoost
- Pandas, NumPy, Joblib
- ChEMBL Database

📁 Project Structure
├── data/
│   ├── raw_data.csv
│   └── processed_data.csv
├── models/
│   └── pic50_model.pkl
├── notebooks/
│   └── drug_activity_prediction.ipynb
└── README.md

🚀 Usage
```python
import joblib
model = joblib.load('models/pic50_model.pkl')
predicted_pic50 = model.predict(features)
predicted_ic50_nM = 10 ** (-predicted_pic50) * 1e9
```

📦 Installation
```bash
pip install rdkit scikit-learn xgboost pandas numpy joblib
```
