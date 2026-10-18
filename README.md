# MSCS_634_Lab_4 — Regression Analysis with Regularization Techniques

**Student:** Vineela Reddy Karnatakam  
**Course:** MSCS-634 — Advanced Big Data and Data Mining

## Purpose
This lab examines how simple linear regression, multiple linear regression, polynomial regression, Ridge (L2) regression, and Lasso (L1) regression predict the continuous disease-progression target in scikit-learn's Diabetes dataset (442 observations and 10 standardized features). Models are compared using MAE, MSE, RMSE, and R² on the same fixed 80/20 train/test split.

## Files
- `MSCS_634_Lab_4.ipynb` — completed, executed Jupyter Notebook with code, plots, metric tables, and analysis.
- `requirements.txt` — dependencies.

## How to run
1. Clone this repository and open its directory.
2. Install dependencies: `python -m pip install -r requirements.txt`.
3. Launch `jupyter notebook` (or open the notebook in JupyterLab / VS Code).
4. Open `MSCS_634_Lab_4.ipynb` and choose **Run All**.

The Diabetes data load directly through scikit-learn; no external data download is necessary.

## Key insights
- Using all 10 predictors offers a broader representation than predicting from BMI alone.
- Higher-degree polynomials can fit training data more closely but generalize worse; in this run degree 8 produced the largest training-vs-test R² gap among the tested BMI polynomials.
- Ridge uses an L2 penalty to shrink weights, whereas Lasso uses an L1 penalty and can set some weights to exactly zero.
- On the fixed seed-42 test split, **Lasso with alpha=1** had the lowest test RMSE across the evaluated models (**about 53.15**) and a test **R² of about 0.467**. This is a descriptive result from one split, not evidence it is always the best model.
- Increasing alpha changes model complexity and can cause underfitting if too large.

## Decisions and challenges
- Used an 80/20 split with `random_state=42` for reproducibility and fair test-row alignment.
- Verified missing data and explored target distribution, feature summaries, and correlations. No arbitrary removal of outliers or duplicate feature vectors was performed.
- Applied polynomial features to **BMI alone** to make polynomial degrees easy to visualize and compare; the separate multiple regression uses all 10 predictors.
- Standardization occurs within Ridge/Lasso pipelines to avoid data leakage.
- Compared a small predefined range of alphas. Test-set results were used for educational *comparison*, not parameter tuning. Real-world selection should use cross-validation on the training data and a final untouched test set.
- These are statistical predictions, not causal claims or medical guidance.

## Submission
Create a public GitHub repository named `MSCS_634_Lab_4`, upload the three files, and submit its URL in your course portal.
