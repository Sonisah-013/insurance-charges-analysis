# 🏥 Insurance Charges Analysis

Exploratory data analysis and machine learning models that predict health insurance charges from customer attributes such as age, BMI, and smoking status.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![pandas](https://img.shields.io/badge/pandas-data%20analysis-150458.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Key Findings](#key-findings)
- [Visualizations](#visualizations)
- [Models & Results](#models--results)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [How to Run](#how-to-run)
- [Future Work](#future-work)
- [Author](#author)

## Overview

Health insurance charges vary widely between people, and it isn't always clear which factors drive the difference. This project analyzes **1,338 customer records** to answer three questions:

1. What patterns exist in the data?
2. Which factors most affect charges?
3. Can charges be predicted accurately from customer attributes?

The workflow covers data cleaning, exploratory data analysis (EDA), feature encoding, model training, and evaluation — a complete, practical data science pipeline.

## Dataset

**Source:** [Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance) (Kaggle)

| Column | Type | Description |
|---|---|---|
| `age` | Numeric | Age of the primary policyholder (18–64) |
| `sex` | Categorical | Gender (male / female) |
| `bmi` | Numeric | Body Mass Index |
| `children` | Numeric | Number of dependents covered |
| `smoker` | Categorical | Smoking status (yes / no) |
| `region` | Categorical | Residential area (NE, NW, SE, SW) |
| `charges` | Numeric (target) | Medical costs billed, in USD |

- 1,338 rows, **no missing values**
- Class imbalance: ~80% non-smokers, ~20% smokers

## Key Findings

| Factor | Effect on Charges |
|---|---|
| 🚬 Smoking status | **Strong** — dominant driver |
| 🎂 Age | Moderate — steady increase |
| ⚖️ BMI | Weak alone, **strong when combined with smoking** |
| 🗺️ Region | Minimal |
| 👨‍👩‍👧 Children | Minimal |

- Smokers pay **$32,050** on average vs. **$8,434** for non-smokers (**~3.8x more**)
- Age correlates with charges at **r = 0.30**; BMI at **r = 0.20**
- **Interaction effect:** obese smokers (BMI ≥ 30) average **$41,558**, vs. **$21,363** for non-obese smokers — obesity alone barely changes non-smoker charges
- Charges are **right-skewed**, with ~10% of customers as high-cost outliers

## Visualizations

| | |
|---|---|
| ![Distribution](imag<img width="1065" height="722" alt="image" src="https://github.com/user-attachments/assets/a2858671-a310-4a2b-9cbe-6d63209dc5a7" />
es/charges_distribution.png) | ![Smoker Boxplot](images/charges_by_smoker.png) |
| ![Age vs Charges](images/age_vs_charges.png) | ![BMI Interaction](images/bmi_smoker_interaction.png) |
| ![Correlation Heatmap](images/correlation_heatmap.png) | ![Pairplot](images/pairplot.png) |

*(Update these paths once your chart images are in the `images/` folder.)*

## Models & Results

Two models were trained on an 80/20 train-test split (`random_state=42`), using one-hot encoded categorical features:

| Model | R² Score | MAE |
|---|---|---|
| Linear Regression | 0.784 | $4,181 |
| **Random Forest (200 trees)** | **0.864** | **$2,564** |

**Random Forest** was the best performer, explaining ~86% of the variance in charges — likely because it captures the BMI × smoking interaction that a linear model cannot.

## Project Structure

```
insurance-charges-analysis/
├── data/
│   └── insurance.csv
├── notebooks/
│   └── analysis.ipynb
├── images/
│   └── (EDA charts and plots)
├── report/
│   └── Insurance_Analysis_Report.docx
├── README.md
└── requirements.txt
```

## Tech Stack

`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scikit-learn` · `Jupyter Notebook`

## How to Run

```bash
# Clone the repo
git clone https://github.com/Sonisah-013/insurance-charges-analysis.git
cd insurance-charges-analysis

# Set up a virtual environment
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # macOS/Linux

# Install dependencies
pip install -r requirements.txt

# Run the notebook
jupyter notebook notebooks/analysis.ipynb
```

## Future Work

- Hyperparameter tuning (GridSearchCV / RandomizedSearchCV)
- Try gradient boosting (XGBoost, LightGBM)
- Explicitly model the BMI × smoker interaction term
- Deploy as a simple web app (Streamlit/Flask) for live charge predictions
- Validate findings against additional real-world insurance datasets

## Author

**Soni Kumari Sah**
BSc CSIT · Aspiring ML/AI Engineer
GitHub: [@Sonisah-013](https://github.com/Sonisah-013)

---

⭐ If you found this project useful, consider giving it a star!
