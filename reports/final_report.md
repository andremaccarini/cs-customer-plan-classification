# Plan Recommendation Model — Final Report

## Objective

This project aims to develop a classification model that predicts the most suitable mobile plan (Smart or Ultra) for each customer based on behavioral data. The model supports business decisions by recommending more appropriate and cost-effective plans for current customers.

---

## Dataset

- Records: **3,211**
- Target variable: `is_ultra` (1 = Ultra plan, 0 = Smart plan)
- Features: `calls`, `minutes`, `messages`, `mb_used`, and new engineered features

---

## Data Cleaning & EDA

- No missing values were found.
- Class imbalance: ~30% Ultra vs. 70% Smart — justifies using **F1-score** and **ROC AUC** over accuracy.
- Customers who:
  - **Talk more (minutes)** and **use more data (mb_used)** are more likely to be Ultra.
  - There’s overlap between Smart and Ultra in many metrics, justifying the use of ML instead of simple thresholds.

---

## Feature Engineering

To enhance model performance and capture behavioral nuances, new features were created:

- `heavy_user`: Customers who talk more than 800 minutes and use over 10,000 MB
- Standard scaling applied to numerical features with high variance

---

##  Modeling & Evaluation

Three classification algorithms were tested:

- **Random Forest**
- **Logistic Regression**
- **Support Vector Classifier (SVC)**

Two main approaches were applied to handle class imbalance:

1. **Baseline** (default class weighting)
2. **Balanced** (using `class_weight='balanced'`)

An **undersampling strategy** was initially tested with Random Forest but discarded due to inferior performance.

### Best Performing Model

**Random Forest (Balanced Class Weight)**  
- **F1 Score:** `0.647`  
- **ROC AUC:** `0.816`  
- **Accuracy:** `0.803`  
- **Best Params:**  
  `{'n_estimators': 100, 'min_samples_split': 2, 'min_samples_leaf': 2, 'max_depth': 5, 'class_weight': 'balanced'}`
---

## Conclusion

- Class imbalance handling via class weights improved model performance.
- The model is suitable for deployment to assist marketing or CRM teams in upselling plans.
- Future improvements:
  - Try additional algorithms (e.g., Gradient Boosting, LightGBM)
  - Deploy the model in a production environment
  - Use time-based features like day of week or session-based usage

---

## Artifacts

- Trained model: `models/random_forest_balanced.pkl`
- Cleaned dataset: `data/interim/users_behavior_cleaned.csv`
- Feature-engineered dataset: `data/processed/df_ready.csv`

---

## Author

**André Maccarini**  
[LinkedIn](https://www.linkedin.com/in/amaccarini/) | [GitHub](https://github.com/andremaccarini) | [Medium](https://medium.com/@andremaccarini)
