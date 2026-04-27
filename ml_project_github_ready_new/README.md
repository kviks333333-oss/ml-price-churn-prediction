# ML Price & Churn Prediction Project

End-to-end machine learning project for two predictive tasks:

- **Regression:** predict price (`__price_predict`)
- **Classification:** predict churn probability (`__churn_prob`)
- **Prioritization:** calculate or submit priority score (`__priority`)

The project demonstrates a full ML workflow: feature engineering, linear models, nonlinear models, model comparison, feature selection and final submission preparation.

## Repository structure

```text
.
├── notebooks/
│   ├── 01_feature_engineering.ipynb
│   ├── 02_linear_models.ipynb
│   ├── 03_nonlinear_models.ipynb
│   └── 04_feature_selection.ipynb
├── outputs/
│   ├── h2_submission.csv
│   ├── h3_submission.csv
│   └── final_submission_h4.csv
├── data/
│   ├── sample_or_baseline_data_0_Kirill_Viksman.csv
│   └── README.md
├── docs/
│   └── project_summary.md
├── requirements.txt
├── .gitignore
└── README.md
```

## Main steps

### 1. Feature engineering
Data preparation, cleaning, encoding of categorical variables, creation of additional features and preparation of matrices for modeling.

### 2. Linear models
Training and evaluation of baseline linear models, including regularized approaches such as Ridge/Lasso for regression and logistic regression for classification.

### 3. Nonlinear models
Training stronger nonlinear models: tree-based models, boosting models and ensemble approaches. The goal is to improve predictive quality for both price and churn tasks.

### 4. Feature selection
Reducing the number of input features while preserving model quality. The project uses feature importance, permutation importance, L1-based selection, random variable method and recursive feature elimination logic.

### 5. Final output
The final submission contains:

```text
__price_predict,__price_num_features,__churn_prob,__churn_num_features,__priority
```

## How to run

1. Clone the repository.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open notebooks in order from `01_` to `04_`.
4. Run cells step by step.
5. Check final predictions in `outputs/final_submission_h4.csv`.


