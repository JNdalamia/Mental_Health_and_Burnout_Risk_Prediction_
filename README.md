# Mental Health & Burnout Risk Prediction

> **Can machine learning identify patterns associated with burnout
> risk?**

This project uses a synthetic mental-health and burnout dataset to
explore burnout-risk patterns and build a multiclass machine-learning
model.

The project was developed in **Python/Kaggle** and follows a practical
workflow from data cleaning and EDA to statistical testing, model
comparison, tuning, and final evaluation.

**Dataset:** [Mental Health & Burnout Prediction Dataset on
Kaggle](https://www.kaggle.com/datasets/mobeenfatimah/mental-health-and-burnout-prediction-dataset)

------------------------------------------------------------------------

## 🎯 Objective

Predict `Burnout_Risk` as:

-   **Low**
-   **Moderate**
-   **High**

while understanding which factors are associated with different
burnout-risk groups.

> **Note:** The dataset is synthetic. The findings demonstrate a
> data-science workflow and should not be interpreted as clinical or
> causal evidence.

------------------------------------------------------------------------

## 📊 Dataset

-   **50,000 rows**
-   **40 original columns**
-   Numerical and categorical features
-   Target distribution:
    -   Low: **50.74%**
    -   Moderate: **29.56%**
    -   High: **19.70%**

The data was checked for missing values, duplicates, and invalid values.
Missing numerical values were median-imputed, while missing
`Therapy_Attendance` values were recorded as `Unknown`. After cleaning,
no missing values remained.

### Preventing data leakage

The following columns were excluded before modelling:

``` text
Person_ID
Burnout_Score
Mental_Health_Status
AI_Wellness_Recommendation
```

This was important because some of these variables are identifiers or
are derived from information closely related to the target.

------------------------------------------------------------------------

## 🔎 Key EDA Findings

Several interesting patterns emerged:

-   Higher burnout-risk groups tended to report **longer working hours
    and fewer hours of sleep**.
-   **Anxiety and depression scores increased** across higher
    burnout-risk groups, while **mood scores decreased**.
-   `Chronic_Stress` showed an exceptionally strong descriptive
    relationship with burnout risk:
    -   High risk among Chronic Stress = **91.79%**
    -   High risk without Chronic Stress = **8.47%**
-   Some wellbeing variables were highly correlated:
    -   Anxiety ↔ Depression: **0.91**
    -   Anxiety ↔ Mood: **-0.94**
    -   Mood ↔ Productivity: **0.97**

These relationships indicate association and information overlap, not
causation.

------------------------------------------------------------------------

## 🧪 Hypothesis Testing

Using **α = 0.05**:

### Significant associations

  Feature               Test            p-value
  --------------------- ------------ ----------
  Sleep Hours           ANOVA          \< 0.001
  Work Hours per Week   ANOVA          \< 0.001
  Stress Level          Chi-square     \< 0.001
  Chronic Stress        Chi-square     \< 0.001

### Not significant in the tests performed

  Feature                p-value
  -------------------- ---------
  Job Satisfaction         0.820
  Work-Life Balance        0.559
  Support System           0.551
  Therapy Attendance       0.752

Statistical significance was considered alongside EDA and model
performance rather than treated as proof of predictive importance or
causation.

------------------------------------------------------------------------

## 🤖 Model Comparison

A majority-class baseline achieved **50.74% accuracy**.

Five models were then compared using stratified 5-fold cross-validation:

  Model                   CV Accuracy   CV Macro F1
  --------------------- ------------- -------------
  Logistic Regression          81.42%    **0.7948**
  Gradient Boosting            81.20%        0.7943
  Random Forest                81.22%        0.7941
  KNN                          76.71%        0.7420
  Decision Tree                74.98%        0.7237

The strongest models were Logistic Regression, Gradient Boosting, and
Random Forest.

------------------------------------------------------------------------

## ⚙️ Hyperparameter Tuning

The two leading models were tuned with `GridSearchCV`.

### Logistic Regression

``` text
C = 10
solver = lbfgs
```

### Gradient Boosting

``` text
learning_rate = 0.05
max_depth = 3
n_estimators = 100
```

------------------------------------------------------------------------

## 🏆 Final Model

**Tuned Gradient Boosting** was selected based primarily on Macro F1,
which is useful for this three-class, imbalanced target.

  Metric                  Result
  ----------------- ------------
  Accuracy            **81.80%**
  Macro Precision     **80.51%**
  Macro Recall        **79.84%**
  Macro F1            **0.8011**

Logistic Regression had marginally higher accuracy (**81.87%**) but a
slightly lower Macro F1 (**0.7997**).

### Final confusion matrix

  Actual / Predicted           Low    Moderate        High
  -------------------- ----------- ----------- -----------
  **Low**                **4,478**         596           0
  **Moderate**                 490   **2,164**         302
  **High**                       0         432   **1,538**

The main challenge was distinguishing **Moderate** burnout risk from Low
and High. The model did not directly confuse Low and High in the final
test results.

------------------------------------------------------------------------

## 💡 What I Learned

This project reinforced several practical lessons:

-   Always check for **target leakage** before modelling.
-   Accuracy alone can hide class-level weaknesses.
-   EDA, statistical testing, and machine learning answer different
    questions and should complement each other.
-   Strong correlations can indicate overlapping information between
    features.
-   Confusion matrices can reveal problems that a single performance
    score cannot.
-   A slightly lower accuracy model can still have better **balanced
    class performance**.

------------------------------------------------------------------------

## 🚀 Next Steps

With more time, I would:

1.  Improve classification of the **Moderate** class through feature
    engineering, class weighting, and threshold analysis.
2.  Add model interpretation using feature importance and explainability
    techniques.
3.  Compare additional models such as XGBoost.
4.  Refactor preprocessing into an `sklearn Pipeline` so imputation,
    scaling, and encoding are fitted independently within each
    cross-validation fold.
5.  Reserve the test set strictly for one final evaluation after all
    model-selection decisions.

------------------------------------------------------------------------

## 🛠️ Tools

Python · pandas · NumPy · SciPy · scikit-learn · Matplotlib · Seaborn ·
Jupyter/Kaggle

------------------------------------------------------------------------

## 📁 Project Structure

``` text
Mental-Health-and-Burnout-Risk-Prediction/
│
├── data/
├── notebooks/
│   └── mental-wellness.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

------------------------------------------------------------------------

## 👤 Author

**Jason Ndalamia**

IT & Data Systems Specialist \| Clinical Data Management & QA \| Data
Analytics \| Developing Data Science & Machine Learning Skills
