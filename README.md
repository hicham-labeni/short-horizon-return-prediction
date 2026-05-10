# Short-Horizon Return Prediction Research

Research-oriented exploratory study of weak predictability in short-horizon equity returns using lagged-return features and linear models.

The objective of this project is methodological rather than performance-driven.  
The study investigates whether minimal leakage-aware feature engineering pipelines can detect weak predictive structure in financial time-series under realistic validation constraints.

---

# Research Goals

Main objectives:

- test short-memory predictability hypotheses
- evaluate signal stability across regimes
- avoid look-ahead bias
- benchmark interpretable linear models
- study weak-signal behavior under chronological validation

The workflow follows conservative quantitative research practices commonly used in early-stage alpha research.

---

# Dataset

Daily OHLCV market data for Apple (AAPL) obtained from Yahoo Finance.

Period covered:

- January 2015 → April 2026

Variables include:

- Open
- High
- Low
- Close
- Volume

Returns are computed from closing prices to improve statistical stability and stationarity properties.

---

# Feature Engineering

Constructed predictors:

- lag1 return
- lag2 return
- lag3 return
- rolling 20-day volatility

Target:

- next-day return

All features are built using strictly forward-looking alignment to prevent look-ahead bias.

---

# Validation Methodology

Validation protocol:

- chronological train/test split
- expanding-window walk-forward validation
- yearly out-of-sample evaluation windows

Random shuffling was intentionally avoided due to temporal dependence and non-stationarity in financial data.

---

# Models Evaluated

The following baseline models were benchmarked:

- Ordinary Least Squares (OLS)
- Ridge Regression
- Lasso Regression

Evaluation metric:

- correlation(predictions, realized returns)

Correlation is preferred over MSE because directional structure is more relevant in weak-signal financial prediction settings.

---

# Main Findings

Key observations:

- predictive structure remains weak
- Ridge slightly stabilizes estimates relative to OLS
- Lasso removes most weak distributed signal
- volatility features provide limited incremental value
- predictive correlations vary substantially across market regimes

The results are consistent with the low signal-to-noise nature of short-horizon financial forecasting.

---

# Limitations

Current limitations include:

- single-asset dataset
- simple feature space
- linear modeling assumptions
- no hyperparameter optimization
- no nonlinear interaction modeling

---

# Potential Extensions

Future research directions:

- multi-asset cross-sectional analysis
- nonlinear models
- regime-aware architectures
- alternative volatility estimators
- multi-horizon prediction frameworks

---

# Repository Structure

```text
README.md
ols_ridge_lasso_walkforward.ipynb
requirements.txt
