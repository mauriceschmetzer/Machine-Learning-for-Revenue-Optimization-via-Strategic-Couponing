# Machine Learning for Revenue Optimization via Strategic Couponing

## Executive summary
This project builds a predictive model that decides whether to send a €5 voucher after a customer’s first order. The aim is to maximize incremental revenue by targeting only those customers who would otherwise churn while avoiding unnecessary discounts to customers who would buy again without an incentive.

## Business context
- Customers are labeled with `target90`, indicating whether they place another order within 90 days of their first purchase.
- Sending a voucher to a true churner yields an expected uplift of €1.25 (25% redemption on a €10 order minus the €5 voucher value).
- Sending a voucher to someone who would reorder anyway costs €5.
- Not sending a voucher leaves revenue unchanged.

The expected revenue objective for a set of predictions is captured as:
$$R = 1.25 \cdot TP_{\text{churn}} - 5 \cdot FP_{\text{voucher}}$$
where $TP_{\text{churn}}$ counts customers correctly identified as churners (and thus voucher-worthy) and $FP_{\text{voucher}}$ counts customers who would have re-ordered but received a voucher.

## Data
- Labeled dataset of first-order customers with order- and customer-level attributes (see notebook for the full schema).
- Target: `target90` (1 = reorder within 90 days, 0 = churn).
- Decision rule: send a €5 voucher to customers predicted to churn.

## Approach
The accompanying notebook walks through the following steps:
- Exploratory data analysis to understand distributions, leakage risks, and class balance.
- Feature preparation (type casting, handling missing values, encoding/normalization as needed).
- Train/validation splits for offline evaluation.
- Model training for tree-based learners and boosting methods.
- Business-centric evaluation using the expected revenue objective alongside standard classification metrics (confusion matrix, precision/recall/AUC) to sanity-check behavior.

## Models trained
- Random Forest
- AdaBoost
- XGBoost

## Results and interpretation
- The notebook compares the above models on the expected revenue objective and common classification metrics.
- Visual diagnostics (e.g., performance curves and feature importance plots) help explain why the best-performing model makes its decisions.
- Use the notebook’s final evaluation section to choose the operating threshold that maximizes expected revenue for your business constraints.

## Repository layout
- README.md: Project overview and instructions.
- Machine_Learning_Revenue_Optimization_via_Strategic_Couponing.ipynb: End-to-end analysis, modeling, and evaluation.

## Getting started
1) Create an environment (Python 3.10+ recommended):
```
python -m venv .venv
.venv\Scripts\activate
```
2) Install core dependencies:
```
pip install -U pip
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
```
3) Launch Jupyter and open the notebook:
```
jupyter notebook Machine_Learning_Revenue_Optimization_via_Strategic_Couponing.ipynb
```

## Reproducing the analysis
- Run the notebook top-to-bottom to recreate data preparation, training, and evaluation steps.
- Adjust the decision threshold in the evaluation section to see how expected revenue responds.
- If you bring new data, ensure columns match the training schema or update the feature preprocessing cells accordingly.
