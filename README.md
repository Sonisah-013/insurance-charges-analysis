# Insurance Charges Analysis

Exploratory data analysis and machine learning models predicting health insurance charges based on customer attributes such as age, BMI, and smoking status.

## Dataset

[Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance) — 1,338 records with the following columns:

| Column | Type | Description |
|---|---|---|
| age | Numeric | Age of the policyholder |
| sex | Categorical | Male / female |
| bmi | Numeric | Body Mass Index |
| children | Numeric | Number of dependents |
| smoker | Categorical | Smoking status (yes/no) |
| region | Categorical | Residential area (NE, NW, SE, SW) |
| charges | Numeric (target) | Medical costs billed, in USD |

## Key Findings

- **Smoking status** is the strongest driver of charges — smokers pay ~3.8x more on average ($32,050 vs $8,434)
- **Age** has a moderate positive correlation with charges (r = 0.30)
- **BMI** mainly raises charges for smokers — an interaction effect (obese smokers average $41,558 vs $21,363 for non-obese smokers)
- **Region** and **number of children** have minimal effect on charges

## Models & Results

| Model | R² Score | MAE |
|---|---|---|
| Linear Regression | 0.784 | $4,181 |
| **Random Forest** | **0.864** | **$2,564** |

Random Forest performed best, explaining ~86% of the variation in charges.

## Project Structure
