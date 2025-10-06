# 451 Financial Engineering: Programming Assignment 1

## Overview

This repository contains the code and analysis for Programming Assignment 1 of MSDS-451, focusing on predicting the direction of Bitcoin (BTC-USD) spot prices using machine learning classifiers. The project leverages tree-based ensemble boosting methods (XGBoost) and a variety of engineered features, including lagged prices, technical indicators (RSI), and volume-based metrics. The notebook also implements and evaluates several trading strategies based on model predictions.

## Repository Structure

```
.
├── 451_pa1_bitcoin.ipynb           # Main Jupyter notebook for the assignment
├── btc_historical_data.csv         # Raw historical Bitcoin price data
├── btc-with-computed-features.csv  # Feature-engineered dataset (generated)
├── README.md                       # This documentation file
...
```

## Requirements

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Required Python packages:
  - numpy
  - pandas
  - polars
  - matplotlib
  - seaborn
  - scikit-learn
  - xgboost
  - yfinance
  - pyarrow
  - scipy

You can install all dependencies using:

```sh
pip install numpy pandas polars matplotlib seaborn scikit-learn xgboost yfinance pyarrow scipy
```

## Instructions for Running the Program

1. **Download the repository and data:**
   - Clone this repository or download the files.
   - Ensure `btc_historical_data.csv` is present in the working directory. If not, the notebook will download it using yfinance.

2. **Open the Notebook:**
   - Launch Jupyter Notebook or JupyterLab.
   - Open `451_pa1_bitcoin.ipynb`.

3. **Run the Notebook:**
   - Execute each cell in order. The notebook will:
     - Download and preprocess Bitcoin price data.
     - Engineer features (lags, EMA, RSI, etc.).
     - Perform exploratory data analysis and feature selection.
     - Train and evaluate XGBoost classifiers using time series cross-validation.
     - Tune hyperparameters with randomized search.
     - Backtest and compare multiple trading strategies (buy-and-hold, systematic buy, and momentum-based).

4. **Results:**
   - The notebook prints out model performance metrics (AUC, accuracy, confusion matrix, classification report).
   - Trading strategy results are displayed, including final portfolio values for each approach.
   - Visualizations show buy/sell signals and price evolution.

## Instructions for Testing

- **Unit Testing:**  
  This notebook is designed for exploratory analysis and does not include separate unit tests. However, you can validate the results by:
  - Checking the printed outputs for model metrics and trading strategy returns.
  - Comparing the generated CSV files (`btc-with-computed-features.csv`) with your expectations.
  - Modifying parameters (e.g., initial capital, buy/sell thresholds) and rerunning cells to observe changes in outcomes.

- **Reproducibility:**  
  The notebook uses fixed random seeds where applicable (e.g., `random_state=2025` in XGBoost) to ensure reproducible results.

## Key Findings

- Including RSI and Volume features improved the AUC score from 0.86 to 0.87–0.89; increasing estimators to 500 further improved AUC to 0.91 (with some risk of overfitting).
- A naive buy-and-hold strategy would have yielded substantial returns due to Bitcoin's historical growth.
- A systematic buy strategy (investing $250 on each buy signal) outperformed simple buy-and-hold in this period.
- A momentum-based strategy (selling after consecutive dips, buying after momentum shifts) provided a more practical approach, balancing risk and return.

## References

- [yfinance GitHub](https://github.com/ranaroussi/yfinance)
- [Polars Online User Guide](https://docs.pola.rs/)
- [Scikit-learn TimeSeriesSplit](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.TimeSeriesSplit.html)
- [XGBoost documentation](https://xgboost.readthedocs.io/en/latest/index.html)
- See the notebook for a full list of references.

---

## Use of AI Assistants

AI assistants, including GitHub Copilot and ChatGPT, were used to:

- Generate and refine Python code for data preprocessing, feature engineering, and model evaluation.
- Suggest efficient ways to implement technical indicators (such as RSI) and cross-validation strategies.
- Draft and improve documentation, code comments, and Markdown explanations.
- Provide guidance on best practices for reproducibility and code organization.
- Enhance project report for incorporating insights for developing advanced trading strategies and next steps.

All code was reviewed, tested, and adapted to ensure correctness and alignment with assignment requirements.