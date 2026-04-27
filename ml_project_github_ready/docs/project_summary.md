# Project Summary

## Short description

This project solves two machine learning tasks on one dataset:

1. predicting `__price` as a regression task;
2. predicting `__churn` as a binary classification task.

The work is organized as a full ML pipeline:

- data inspection;
- feature engineering;
- linear baseline models;
- nonlinear models;
- feature selection;
- final prediction file generation.

## What was done

### Data and feature engineering

The initial dataset contained 30,471 rows. The training part contained 20,483 rows, and the test part contained 9,988 rows.

A large number of additional features was created. The feature engineering block included:

- missing-value indicators;
- clipped numeric variables;
- robust-scaled variables;
- logarithmic transformations;
- frequency encoding for categorical variables;
- one-hot encoding;
- domain-inspired semantic features;
- interaction features.

The final engineered dataset contained 399 columns.

### Modeling

For regression, the project compared linear models and nonlinear models.  
For classification, the project compared logistic regression and tree-based/boosting models.

The quality of regression models was evaluated using negative MSLE.  
The quality of classification models was evaluated using ROC-AUC.

### Feature selection

The final stage tested five feature selection approaches:

- feature importance;
- permutation importance;
- L1 regularization;
- random variable method;
- recursive feature elimination.

The final selected setup used:

- 160 features for price prediction;
- 120 features for churn prediction.

## Business interpretation

The project can be interpreted as a prioritization model.  
The regression model estimates expected value through `__price_predict`, while the classification model estimates churn risk through `__churn_prob`.

Together, these predictions can help rank objects or customers by priority and focus attention on the most valuable or risky cases.
