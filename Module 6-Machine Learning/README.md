# Module 6: Machine Learning

[Back to main syllabus](../README.md)

Machine learning has become a core empirical tool in AccFin research: tree ensembles and other flexible models now routinely outperform traditional linear benchmarks at prediction tasks such as forecasting earnings, detecting misstatements, and assessing credit risk. This module builds up from classical statistical inference to modern gradient-boosted trees, replicating recent AccFin papers along the way — a linear-regression specification, a classification task, a regression/forecasting task, and an explainability exercise that opens up what the model actually learned.

**Prerequisite reading**

- Chen, X., Cho, Y. H. (T.), Dou, Y., & Lev, B. (2022). Predicting future earnings changes using machine learning and detailed financial data. *Journal of Accounting Research* 60(2): 467-515. ([link](https://doi.org/10.1111/1475-679X.12429))
- Parker, C. (A.) Z., Jiang, L., Cho, S., & Vasarhelyi, M. A. (2025). Predicting material misstatements using machine learning. *The Accounting Review* 100(6): 225-262. ([link](https://doi.org/10.2308/TAR-2024-0035))

## 6.1. Statistical Testing and Regression

A refresher on classical statistical inference — the toolkit that empirical AccFin research rests on, and the benchmark against which the machine-learning methods in the rest of the module are judged. Section 1 works through the three *t*-tests you will use most with `scipy.stats`; Section 2 builds one complete specification of Kim, Li, Lu and Yu (2016), using the option volatility smirk panel constructed in the Module 3 exercise, estimating it with `pyfixest`.

**Prerequisite reading**

- Kim, J. B., Li, L., Lu, L. Y., & Yu, Y. (2016). Financial statement comparability and expected crash risk. *Journal of Accounting and Economics* 61(2-3): 294-312. ([link](https://doi.org/10.1016/j.jacceco.2015.12.003))

**Learning Outcomes**

By the end of this session, you will be able to:

- Run and interpret one-sample, independent-samples, and paired *t*-tests using `scipy.stats`.
- Aggregate a very large daily database into firm-year variables efficiently, by computing sufficient statistics on the WRDS server rather than downloading raw rows.
- Assemble an estimation sample the way a published paper does — sample filters, winsorizing continuous variables.
- Specify and estimate a linear regression with `pyfixest` using R-style formula syntax.
- Explain why standard errors in a firm-year panel must be clustered, and estimate two-way (firm and year) clustered standard errors.
- Absorb high-dimensional fixed effects, and explain via the Frisch-Waugh-Lovell theorem why this is equivalent to (and better than) adding a dummy per firm.
- Assemble a publication-style regression table with `pf.etable()`.

Our class is based on [6-1-Statistical_Testing_and_Regression-Final.ipynb](6-1-Statistical_Testing_and_Regression-Final.ipynb). Section 2 continues the Module 3 exercise [3-1e-Option_Volatility_Smirk-Final.ipynb](<../Module 3-Data Collection/3-1e-Option_Volatility_Smirk-Final.ipynb>).

## 6.2. Classification with XGBoost: Predicting the Direction of Earnings Changes

Following Chen et al. (2022), this session frames the direction of next-year earnings changes as a binary classification problem, engineers a wide set of Compustat-based predictors, and benchmarks a logistic regression against `xgboost.XGBClassifier`.

**Learning Outcomes**

By the end of this session, you will be able to:

- Frame a prediction problem (direction of earnings changes) as a binary classification task, using a drift-adjusted label.
- Engineer a wide set of financial-statement predictors (current value, lagged value, percentage change) by auto-detecting columns rather than hand-picking a subset.
- Explain why panel data needs a **chronological** train/validation/test split rather than a random one.
- Fit and evaluate a `LogisticRegression` benchmark (with imputation and scaling) and an `xgboost.XGBClassifier` (NaNs and all), and compare them with ROC-AUC and ROC curves.
- Tune an XGBoost model with a validation set and `early_stopping_rounds`.
- Read a gain-based feature-importance plot, and understand its limitations.

Our class is based on [6-2-Classification-Final.ipynb](6-2-Classification-Final.ipynb).

## 6.3. Forecasting Continuous Earnings with XGBoost

This session reuses 6.2's data and feature pipeline but predicts next-year *continuous* EPS — a regression task — following Chattopadhyay, Fang, and Mohanram (2025). It benchmarks a naive random-walk forecast and a regularized (Ridge) regression against an `xgboost.XGBRegressor` fit with a Huber loss.

**Prerequisite reading**

- Chattopadhyay, A., Fang, B., & Mohanram, P. (2025). Machine learning for earnings forecasting — US and international evidence. Working paper. ([link](https://dx.doi.org/10.2139/ssrn.5941658))

**Learning Outcomes**

By the end of this session, you will be able to:

- Frame a forecasting problem as a regression task, and implement a one-line random-walk benchmark.
- Explain why regression targets built from raw accounting data need outlier treatment (winsorizing using training-period bounds only) before a linear model can be trusted, and why tree ensembles are more forgiving.
- Fit `xgboost.XGBRegressor` with a Huber loss objective, and tune it with early stopping.
- Evaluate forecasts with price-scaled MAFE, RMSE, and MDAFE.
- Read an XGBoost regression feature-importance plot.

Our class is based on [6-3_Earnings_Forecasting-Final.ipynb](6-3_Earnings_Forecasting-Final.ipynb).

## 6.4o. Explainable AI: Using SHAP to Understand an XGBoost Model (Optional)

Following Parker et al. (2025), this optional session picks up the classification model from 6.2 and applies SHAP (SHapley Additive exPlanations) to understand which predictors drive it and how — going beyond a single gain-based importance score to directional, per-observation explanations.

**Learning Outcomes**

- Explain what a SHAP value is and how it differs from a gain-based feature-importance score.
- Use `shap.TreeExplainer` to compute exact SHAP values for an XGBoost model.
- Read SHAP bar, beeswarm, dependence (scatter), and waterfall plots to understand which features drive predictions, in which direction, and why for an individual firm-year.
- Critically interpret machine-learning output as an attention-directing tool rather than evidence of causation.

Our class is based on [6-4o-Explainable_AI.ipynb](6-4o-Explainable_AI.ipynb).

[Back to main syllabus](../README.md)
