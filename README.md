# AlphaForge: Bitcoin Alpha Generation using Machine Learning

A quantitative finance project that predicts daily Bitcoin returns using blockchain on-chain metrics, macroeconomic indicators, and engineered technical features. The predicted returns are converted into long/short trading signals and evaluated against a buy-and-hold benchmark using both statistical and financial performance metrics.

## Problem Statement

The objective was to develop a machine learning pipeline capable of generating alpha for Bitcoin by combining multiple information sources:

- Blockchain on-chain metrics
- Macroeconomic indicators
- Historical price-derived technical features

The final model predicts daily Bitcoin log returns, generates trading signals, and evaluates whether the strategy outperforms passive Bitcoin investing.

## Dataset

- **Time Period:** September 2014 to 2026
- **Observations:** 4,292 daily samples
- **Target:** Daily Bitcoin log returns
- **Feature Sources:**
  - On-chain blockchain metrics
  - Macroeconomic indicators
  - Engineered technical indicators

## Project Workflow

### 1. Exploratory Data Analysis
- Distribution analysis of all features
- Correlation heatmap generation
- Augmented Dickey-Fuller (ADF) stationarity tests
- Identification of relationships between on-chain and macroeconomic variables

### 2. Feature Engineering
Additional predictive features were engineered, including:
- Lagged returns (1, 2, 3, 5, 7 and 14 days)
- Momentum indicators
- Rolling volatility measures

### 3. Data Preparation
- Forward-filled missing values
- Chronological train/validation/test split (70% / 15% / 15%)
- Feature scaling using `StandardScaler`
- Data leakage prevention by fitting preprocessing only on training data

### 4. Machine Learning Models
Implemented and compared:
- Random Forest Regressor
- XGBoost Regressor

XGBoost was selected as the primary model after hyperparameter tuning for improved predictive performance and feature utilisation.

### 5. Alpha Signal Generation
Predicted returns were converted into:
- Long position if predicted return > 0
- Short position otherwise

The strategy was backtested against a Buy-and-Hold Bitcoin benchmark.

### 6. Evaluation
The model was evaluated using:

**Statistical Metrics**
- MAE
- RMSE
- R² Score
- Directional Accuracy

**Financial Metrics**
- Annualised Sharpe Ratio
- Maximum Drawdown
- Cumulative Return

### 7. Model Interpretation
Feature importance was analysed using:
- XGBoost Gain Importance
- Split Frequency
- Permutation Importance

This provided insights into which on-chain, macroeconomic and technical indicators contributed most to prediction performance.

## Results

The generated trading strategy achieved:
- Higher Sharpe Ratio than Buy-and-Hold
- Significantly higher cumulative returns
- Competitive directional prediction accuracy (~66%)

The project demonstrates that combining blockchain fundamentals, macroeconomic signals, and engineered market features can produce informative alpha signals for systematic cryptocurrency trading.

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Statsmodels
