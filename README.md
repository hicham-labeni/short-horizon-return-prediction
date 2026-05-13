# Baseline Study of Short-Horizon Equity Return Forecasting

Exploratory quantitative study of short-horizon equity return dynamics using lagged-return features and linear baseline models.

The objective of this project is methodological rather than performance-driven.  
The analysis focuses on evaluating whether simple lag-based features contain weak but persistent statistical structure under chronological validation settings.

---

# Project Goals

Main objectives:

- explore short-term return forecasting signals
- evaluate the stability of weak signals over time
- avoid look-ahead bias in feature construction and validation
- compare interpretable linear baseline models
- study signal stability under walk-forward evaluation

The workflow emphasizes chronological validation and basic leakage prevention techniques commonly used in financial time-series analysis.

---

# Dataset

Daily OHLCV market data for Apple (AAPL) downloaded from Yahoo Finance.

Period covered:

- January 2015 → April 2026

Variables include:

- Open
- High
- Low
- Close
- Volume

Daily returns are computed from closing prices to obtain a more stationary series for modeling.

---

# Exploratory Data Analysis (EDA)

The notebook includes several exploratory analyses to better understand the structure of the financial time series:

- closing price evolution over time
- daily return time series visualization
- return distribution analysis
- rolling mean and rolling volatility analysis
- lagged-return feature inspection
- walk-forward performance visualization

The exploratory analysis highlights several common financial time-series properties:

- noisy short-term returns
- volatility clustering
- heavy-tailed return distributions
- unstable statistical relationships across market periods

---

# Feature Engineering

Constructed features:

- lag1 return
- lag2 return
- lag3 return
- rolling 20-day return volatility

Prediction target:

- next-day return

Lagged variables and rolling statistics are constructed using only past information in order to avoid look-ahead bias.

---

# Validation Methodology

Validation approach:

- chronological train/test split
- expanding-window walk-forward evaluation
- yearly out-of-sample testing windows

Random shuffling was intentionally avoided because financial time-series exhibit temporal dependence and non-stationarity.

---

# Models Evaluated

The following linear baseline models were tested:

- Ordinary Least Squares (OLS)
- Ridge Regression
- Lasso Regression

Evaluation metric:

- correlation between predicted and realized returns

Correlation between predicted and realized returns was used as a simple proxy for directional alignment and signal consistency across periods, rather than minimizing prediction error magnitude.

---

# Main Findings

Main observations from the experiments:

- statistical relationships remain weak overall
- Ridge regression produced slightly more stable results than OLS in some periods
- under the selected regularization strength, Lasso frequently collapsed toward near-zero predictions, suggesting that the weak signal was too diffuse to survive sparse regularization
- adding rolling volatility did not materially improve forecasting performance
- walk-forward results varied significantly across market periods

Overall, the results are consistent with the low signal-to-noise nature of short-horizon equity return forecasting.

---

# Limitations

This project has several important limitations:

- single-asset analysis
- relatively small feature space
- linear modeling assumptions
- no hyperparameter optimization
- no transaction cost modeling
- no portfolio construction or trading strategy layer
- no explicit regime detection framework

As a result, the study should be viewed as an exploratory baseline analysis rather than a production-ready forecasting system.

---

# Potential Extensions

Possible future improvements include:

- multi-asset analysis
- nonlinear machine learning models
- rolling retraining procedures
- regime-aware modeling approaches
- alternative volatility estimators
- statistical significance and robustness testing

---

# Repository Structure

```text
README.md
ols_ridge_lasso_walkforward.ipynb
requirements.txt
