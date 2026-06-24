# Wine Quality Prediction using Machine Learning

## Overview

This project focuses on predicting wine quality using machine learning while following a complete end-to-end workflow.

Instead of directly training a model, the main focus was on understanding the data, performing exploratory analysis, building baseline models, engineering useful features, and improving the model through iterative experimentation.

The goal was to understand how data characteristics affect model performance and how thoughtful feature engineering can improve results.

---

## Dataset

The dataset contains physicochemical properties of wine samples such as:

* Fixed Acidity
* Volatile Acidity
* Citric Acid
* Residual Sugar
* Chlorides
* Free Sulfur Dioxide
* Total Sulfur Dioxide
* Density
* pH
* Sulphates
* Alcohol

### Target Variable

The original target variable was wine quality with values ranging from **3 to 8**.

Initially, a multi-class classification approach was used, but due to class imbalance, the target was later converted into binary classes:

* 0 → Quality ≤ 5
* 1 → Quality > 5

---

## Exploratory Data Analysis

EDA was performed in multiple stages.

### Univariate Analysis

Each feature was analyzed for:

* Distribution patterns
* Skewness
* Outliers
* Real-world validity of extreme values

### Bivariate Analysis

Relationships between features and the target were studied using pairplots and boxplots.

Main observations:

**Strong features**

* Volatile Acidity
* Citric Acid
* Alcohol

**Relatively weak features**

* Residual Sugar
* Density
* Chlorides

---

## Baseline Model

A Random Forest Classifier was used as the baseline model.

The initial multi-class approach performed poorly because minority classes were heavily underrepresented.

This highlighted an important lesson:

> Sometimes the problem lies in target formulation rather than preprocessing.

After converting the target to binary classification, model performance improved significantly.

---

## Feature Engineering

New features were created based on relationships between existing variables.

Created features:

* Sulfur Ratio
  (Free Sulfur Dioxide / Total Sulfur Dioxide)

* Total Acidity
  (Fixed Acidity + Volatile Acidity + Citric Acid)

* Sugar-Alcohol Ratio
  (Residual Sugar / Alcohol)

* Sulphate-Alcohol Interaction
  (Sulphates × Alcohol)

---

## Feature Selection

Feature importance was checked after training.

Low-importance features were removed, and the model was retrained.

The final model achieved similar performance with fewer features, making it simpler and more efficient.

---

## Model Performance

### Baseline Model

* Accuracy: **80.6%**

### After Feature Engineering

* Accuracy: **81.8%**

### Final Model (After Feature Selection)

* Accuracy: **82.5%**

Final Classification Performance:

* Precision: **0.81 – 0.84**
* Recall: **0.81 – 0.84**
* F1 Score: **0.81 – 0.84**

Confusion Matrix:

```text
[[121 28]
 [28 143]]
```

---

## Key Learnings

This project helped reinforce several important machine learning concepts:

* EDA is about understanding data, not just plotting graphs
* Outliers should not always be removed
* Accuracy alone can be misleading
* Class imbalance can significantly affect model behavior
* Feature engineering should be based on reasoning, not random experimentation
* Simpler models with fewer features can perform just as well

---

## Tools Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn

---

## Conclusion

This project was a complete machine learning workflow starting from raw data analysis to model improvement.

The biggest takeaway was understanding that building a good model is not just about preprocessing or tuning algorithms, but about understanding data, making informed decisions, and iterating systematically.
