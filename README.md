# CA03
# Decision Tree Income Classification Project
#This project was completed with the assistance of AI tools, which were used to help brainstorm approaches, optimize code, and clarify technical concepts. All implementation, testing, and final decisions were performed and validated by the author to ensure accuracy and understanding.

## Overview

This project builds and evaluates a Decision Tree classification model to predict whether an individual earns more than $50K per year using demographic and socioeconomic variables. The dataset is derived from U.S. Census data and contains binned categorical features representing characteristics such as occupation level, education, capital gains, and age group.

The goal of this project is to apply machine learning techniques to a real-world dataset, evaluate model performance, tune hyperparameters, and interpret the resulting decision tree.

---

## Dataset Description

The dataset contains:

* **48,842 observations**
* **Categorical predictor variables only (pre-binned)**
* **Binary target variable**

  * `0 = <=50K`
  * `1 = >50K`
* A column indicating whether each row belongs to the training or testing set

All numerical features were discretized into grouped categories before modeling. This improves interpretability and helps decision trees generalize better by reducing sensitivity to small numeric variations.

---

## Data Quality Analysis

A full data quality assessment was performed prior to modeling:

* No missing values detected
* No invalid categories
* No corrupted records
* No true duplicate entries (identical rows represent valid repeated demographic profiles)

The dataset was therefore considered clean and suitable for modeling without modification.

---

## Modeling Approach

### Feature Preparation

* Training and testing sets were created using the dataset’s built-in split column
* Categorical variables were converted using **one-hot encoding**
* Feature matrices were aligned to ensure identical column structures

---

### Baseline Model

A Decision Tree classifier with default parameters was first trained to establish baseline performance.

---

### Hyperparameter Tuning

Four hyperparameters were tuned sequentially:

* Split criterion (`gini` vs `entropy`)
* Minimum samples per leaf
* Maximum features
* Maximum tree depth

At each stage, the best value was selected based on **test accuracy**, as required.

---

### Best Model Parameters

The best-performing decision tree used:

```
criterion = gini
min_samples_leaf = 20
max_features = None
max_depth = 10
```

These settings reduced overfitting while maintaining predictive accuracy.

---

## Final Model Performance

| Metric    | Score |
| --------- | ----- |
| Accuracy  | 0.846 |
| Precision | 0.718 |
| Recall    | 0.572 |
| F1 Score  | 0.637 |

The tuned model improved performance across all evaluation metrics compared to the baseline model, indicating successful hyperparameter optimization.

---

## Feature Importance Insights

The most influential predictors were:

1. MSR category (strongest predictor)
2. Occupation category
3. Capital gain status
4. Education level
5. Age group

This indicates that socioeconomic indicators play a dominant role in predicting income class.

---

## Decision Tree Interpretation

The root node split on MSR category, demonstrating that it is the most informative feature. Early splits focused on occupation and capital gains, showing that the model learned meaningful real-world relationships rather than arbitrary patterns.

Because the tree depth was limited and minimum leaf size constrained, the model is unlikely to overfit.

---

## Prediction Example

A new individual with the following characteristics:

* Age: 58
* Hours worked: 48
* Occupation: Mid-Low
* MSR: High
* Capital gain: Yes
* Education: High
* Workclass: Income

was predicted to belong to the:

**>50K income class**

with probability:

**0.711 (≈71%) confidence**

---

## Key Takeaways

* Decision Trees can effectively model categorical socioeconomic data.
* Hyperparameter tuning significantly improves performance.
* Limiting tree complexity improves generalization.
* Feature importance analysis provides interpretable insights.
* The model captures meaningful socioeconomic patterns rather than random noise.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Graphviz

---

## Conclusion

This project demonstrates the full machine learning workflow:

data understanding → preprocessing → modeling → tuning → evaluation → interpretation → prediction.

The resulting model is accurate, interpretable, and computationally efficient, making it suitable for real-world classification tasks involving structured demographic data.

---
