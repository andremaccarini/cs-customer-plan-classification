# Megaline Plan Recommendation

## Project Overview

This project aims to predict which modern mobile plan — **Smart** or **Ultra** — should be recommended to each customer, based on their behavior. The dataset was provided by TripleTen and contains historical usage patterns of users who already migrated to newer plans.

The goal is to build a classification model with **at least 0.75 accuracy** and identify key behavioral indicators that influence plan choice.

---

## Project Structure

megaline-plan-recommendation/  
├── data/  
│   ├── raw/ → Original data  
│   ├── interim/ → Cleaned data  
│   └── processed/ → Feature-engineered, ready for modeling  
├── models/ → Saved ML model (.pkl)  
├── notebooks/ → Jupyter notebooks (EDA, feature engineering, modeling)  
├── reports/  
│   ├── figures/ → Visualizations  
│   └── final_report.md  
├── requirements.txt  
└── README.md

---

## Workflow Summary

1. **EDA**: Explored user activity and plan distribution. The `is_ultra` column was used as the binary target.
2. **Feature Engineering**:
   - New features like `TenureByAge`, `BalanceSalaryRatio`, and `IsHeavyUser`.
   - One-hot encoding of categorical variables.
   - Scaling of numerical features.
3. **Modeling**:
   - Tested **Random Forest**, **Logistic Regression**, and **SVC**.
   - Used both **baseline** and **class_weight='balanced'** strategies.
   - Evaluated models using:
     - F1 Score
     - ROC AUC
     - Accuracy
     - ROC Curves
4. **Model Selection**:
   - **Random Forest with balanced class weight** achieved the best results.

---

## Best Model

**Random Forest Classifier (balanced)**  
- F1 Score: **0.647**  
- ROC AUC: **0.816**  
- Accuracy: **0.803**

Saved in `models/random_forest_balanced.pkl`.

---

## Key Findings

- `Minutes`, `MB_used had the strongest influence on plan choice.
- Users with high usage patterns were more likely to be assigned the **Ultra** plan.
- Class imbalance was moderate but handled using `class_weight='balanced'`.

---

## Visual Insights

All major plots from the EDA and modeling stages — such as:
- Plan distribution,
- Feature importance,
- ROC comparison —

are saved in `/reports`.

---

## Next Steps

- Explore deployment with Streamlit.
- Try alternative techniques like SMOTE for class balancing.
- Add business rule filters before prediction (e.g., usage thresholds).

---

##  Author

**André Maccarini**
🔗 [LinkedIn](https://www.linkedin.com/in/amaccarini/) • [Medium](https://medium.com/@andremaccarini) • [Github](https://github.com/andremaccarini)

---

##  License

This project is licensed under the MIT License.
