# 🩺 Diabetes Risk Prediction

**Developed by** Maitan Yerassyl

---

## 📋 Project Overview

A multi-class classification study predicting diabetes risk category — **Low Risk**, **Prediabetes**, or **High Risk** — using clinical and demographic data from 6,000 patient records.


---

## 📁 Repository Structure

```
├── data/
│   └── diabetes_risk_dataset.csv        # Source dataset (6 000 patient records, 19 features)
├── notebooks/
│   ├── EDA_Preprocessing.ipynb    # EDA, visualisations, feature engineering
│   └── Modelling.ipynb            # Model training, evaluation, comparison
├── report/
│   └── Report.docx    # Full written report (PDF version)
├── .gitignore
└── README.md
```

---

## 📊 Dataset

**Source:** [Diabetes Risk Prediction Dataset](https://www.kaggle.com/datasets/vishardmehta) — Kaggle (Vishard Mehta)

- **Records:** 6,000 patient records
- **Features:** 19 columns (17 used after dropping leakage/ID columns)
- **Target:** `diabetes_risk_category` — 3 classes

| Class | Count | Share |
|-------|-------|-------|
| Low Risk | 2,602 | 43.4% |
| High Risk | 2,245 | 37.4% |
| Prediabetes | 1,153 | 19.2% |

> ⚠️ Note: `Patient_ID` and `diabetes_risk_score` were dropped before modelling — the latter is a direct numeric proxy of the target and would cause data leakage.

---

## 🔬 Methods

### Preprocessing
- Dropped leakage column (`diabetes_risk_score`) and ID column (`Patient_ID`)
- Ordinal encoding for categorical features (`gender`, `physical_activity_level`, `family_history_diabetes`)
- Feature engineering: `glucose_bmi_interaction = fasting_glucose_level × bmi`
- 80/20 stratified train/test split (`random_state=42`)
- `StandardScaler` fitted on training set only, applied to both sets

### Models
| Model | Key Hyperparameters |
|-------|---------------------|
| Logistic Regression (baseline) | `max_iter=1000` |
| Decision Tree | `max_depth=6`, `class_weight='balanced'` |
| K-Nearest Neighbours | `k=11`, scaled features |

---

## 📈 Results

| Model | Test Accuracy | Macro F1 | F1 — Prediabetes | CV Mean | CV Std |
|-------|:---:|:---:|:---:|:---:|:---:|
| Logistic Regression | **0.943** | **0.928** | **0.853** | 0.950 | 0.008 |
| Decision Tree | 0.898 | 0.880 | 0.771 | 0.890 | 0.004 |
| KNN (k=11) | 0.900 | 0.871 | 0.738 | 0.892 | 0.006 |

**Best model:** Logistic Regression — highest test accuracy (94.3%) and Macro F1 (0.928).

---

## 💡 Key Findings

1. **Fasting glucose and HbA1c** are the dominant predictors, aligning precisely with ADA clinical diagnostic thresholds (glucose: 100 / 126 mg/dL; HbA1c: 5.7% / 6.5%).
2. **Prediabetes** is consistently the hardest class to classify across all models — its clinical ambiguity in the 100–126 mg/dL glucose range directly maps to model uncertainty.
3. Initial hypothesis was largely confirmed: glucose is the dominant feature, BMI plays a secondary role, and age contributes but with significant class overlap.

---

## 🚀 Getting Started

### Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Run the notebooks

```bash
# Clone the repo
git clone https://github.com/<your-username>/diabetes-risk-prediction.git
cd diabetes-risk-prediction

# Launch Jupyter
jupyter notebook notebooks/
```

Open `EDA_Preprocessing.ipynb` first, then `Modelling.ipynb`.

---

## 📚 Dependencies

| Library | Version |
|---------|---------|
| Python | ≥ 3.9 |
| pandas | ≥ 1.5 |
| numpy | ≥ 1.23 |
| scikit-learn | ≥ 1.2 |
| matplotlib | ≥ 3.6 |
| seaborn | ≥ 0.12 |

