# Machine Learning Project: Price Prediction and Churn Classification

Portfolio-ready machine learning project with two predictive tasks:

1. **Regression:** predict the target variable `__price`.
2. **Classification:** estimate churn probability using the target variable `__churn`.

The project includes feature engineering, baseline linear models, nonlinear models, model comparison, and feature selection.

---

## Project pipeline

### 1. Feature Engineering

Notebook: `notebooks/01_feature_engineering.ipynb`

Main steps:

- loaded the original dataset;
- split data by `dtype` into train and test parts;
- cleaned numeric features;
- encoded categorical features;
- generated new `f_` features;
- checked that generated features do not contain missing values;
- saved the enriched dataset for the next modeling stages.

Key result:

- original dataset: **30,471 rows**;
- train part: **20,483 rows**;
- test part: **9,988 rows**;
- final engineered dataset: **399 columns**;
- generated `f_` features: **337**;
- generated feature groups: missing indicators, clipped numeric features, robust-scaled features, logarithmic features, frequency encoding, one-hot encoding, semantic features, and interaction features.

---

### 2. Linear Models

Notebook: `notebooks/02_linear_models.ipynb`

Models tested:

- Linear Regression;
- Lasso;
- Ridge;
- Logistic Regression with different regularization settings.

Metrics:

- `metric_for_price`: negative Mean Squared Log Error, where higher value is better;
- `metric_for_churn`: ROC-AUC, where higher value is better.

Best results from the linear stage:

| Task | Best model | Validation score |
|---|---:|---:|
| Price prediction | Lasso | -0.147 |
| Churn classification | Logistic Regression with L1 regularization | 0.971 |

Additional holdout metrics:

| Task | Metric | Value |
|---|---:|---:|
| Regression | RMSE | 2.870 |
| Regression | R² | 0.560 |
| Classification | ROC-AUC | 0.965 |
| Classification | Accuracy | 0.926 |
| Classification | Precision | 0.778 |
| Classification | Recall | 0.742 |

---

### 3. Nonlinear Models

Notebook: `notebooks/03_nonlinear_models.ipynb`

Models tested:

- Decision Tree;
- Random Forest;
- Hist Gradient Boosting;
- LightGBM;
- XGBoost;
- CatBoost.

The strongest nonlinear models were based on gradient boosting, especially **LightGBM**.

Best nonlinear results from the notebook:

| Task | Best model | Validation score |
|---|---:|---:|
| Price prediction | LightGBM | -0.245 |
| Churn classification | LightGBM | 0.989 |

---

### 4. Feature Selection

Notebook: `notebooks/04_feature_selection.ipynb`

Feature selection methods tested:

- feature importance;
- permutation importance;
- L1 regularization;
- random variable method;
- recursive feature elimination.

Final selected solution:

| Task | Selection method | Number of features | Validation score |
|---|---:|---:|---:|
| Price prediction | Permutation importance | 160 | -0.146 |
| Churn classification | Permutation importance | 120 | 0.962 |

Final prediction file:

`outputs/final_submission.csv`

It contains:

- `__price_predict`;
- `__price_num_features`;
- `__churn_prob`;
- `__churn_num_features`;
- `__priority`.

---

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md
├── docs/
│   └── project_summary.md
├── notebooks/
│   ├── 01_feature_engineering.ipynb
│   ├── 02_linear_models.ipynb
│   ├── 03_nonlinear_models.ipynb
│   └── 04_feature_selection.ipynb
└── outputs/
    └── final_submission.csv
```

---

## How to run

Install dependencies:

```bash
pip install -r requirements.txt
```

Run notebooks in this order:

1. `notebooks/01_feature_engineering.ipynb`
2. `notebooks/02_linear_models.ipynb`
3. `notebooks/03_nonlinear_models.ipynb`
4. `notebooks/04_feature_selection.ipynb`

For Google Colab, upload the required input CSV files to the Colab runtime and adjust file paths if needed.

---

## Notes

Large intermediate datasets are not included in this repository.  
They are ignored by `.gitignore` to keep the repository lightweight and safe for public portfolio use.

Do not upload confidential data, API keys, passwords, or private business datasets to a public GitHub repository.
