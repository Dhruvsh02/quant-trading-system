Quantitative Trading System with Regime Detection & ML Enhancement

Porject Overview :-

This project implements a systematic quantitative trading framework for NIFTY index data using multi-asset features (Spot, Futures, Options).
The system combines:

- Feature engineering (EMA, IV, Greeks, volatility, PCR)
- Market regime detection using Hidden Markov Models (HMM)
- A rule-based baseline trading strategy
- Machine Learning enhancements using XGBoost and LSTM
- Backtesting and performance evaluation
- High-performance trade (outlier) analysis
- The goal is to study how market regimes and ML filters affect strategy profitability and risk.

Installation Instrcutions :-

1. Clone the repositary

- git clone https://github.com/Dhruvsh02/quant-trading-system
- cd quant_trading_system

2. Create Virtual Environment

- python -m venv venv
- source venv/bin/activate  # for macOS

3. Install Dependencies

- pip install -r requirements.txt
- (this project is tested on python 3.10/3.11 and macOS users should use tenserflow-macos)

How to Run the Project :- 

Run Notebooks
1. Open jupyter:

- jupyter notebook

2. Run the Notebooks in the Order:

- 01 - 01_data_acquisition.ipynb
- 02 - 02_data_cleaning.ipynb
- 03 - 03_data_merging.ipynb
- 04 - 04_features_engineering.ipynb
- 05 - 05_regime_detection.ipynb
- 06 - 06_strategy_logic.ipynb
- 07 - 07_ml_enhancement.ipynb
- 08 - 08_outlier_analysis

Output is automattically saving into:-
- data/
- results/
- plots/
- models/


Project Structure Explanation

QUANT_TRADING_SYSTEM/
│
├── data/
│   ├── data_cleaning_report.txt
│   ├── nifty_spot_raw.csv
│   ├── nifty_spot_clean.csv
│   ├── nifty_futures_5min.csv
│   ├── nifty_futures_clean.csv
│   ├── nifty_options_5min.csv
│   ├── nifty_options_clean.csv
│   ├── nifty_merged_5min.csv
│   ├── nifty_features_5min.csv
│   ├── nifty_regime_5min.csv
│   ├── nifty_strategy_signals.csv
│   ├── nifty_backtest_test_results.csv
│   └── nifty_backtest_metrics.csv
│
├── notebooks/
│   ├── 01_data_acquisition.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_data_merging.ipynb
│   ├── 04_features_engineering.ipynb
│   ├── 05_regime_detection.ipynb
│   ├── 06_strategy_logic.ipynb
│   ├── 07_ml_enhancement.ipynb
│   └── 08_outlier_analysis.ipynb
│
├── src/
│   ├── data_utils.py
│   ├── features.py
│   ├── greeks.py
│   ├── regime.py
│   ├── strategy.py
│   ├── backtest.py
│   └── ml_models.py
│
├── models/
│   ├── xgb_trade_filter.pkl
│   ├── lstm_trade_filter/
│   │   ├── saved_model.pb
│   │   └── variables/
│   └── model_info.txt
│
├── plots/
│   ├── equity_curve.png
│   ├── regime_overlay.png
│   └── outlier_by_hour.png
│
├── results/
│   ├── nifty_backtest_test_results.csv
│   ├── nifty_backtest_metrics.csv
│   ├── ml_return_comparison.csv
│   └── outlier_summary.csv
│
├── requirements.txt
├── README.md
├── .gitignore
└── venv/   (ignored in Git)


Key Results Summary

Baseline Strategy(regime + EMA)
- Total Return : -54.76%
- Sharpe Ratio : -3.30%
- Max Drawdown : -64.13%
- Win Rate : 34.87%
- Total Trades : 826

ML-Enhanced Strategy

Strategy              Return
- Baseline            -5.86%
- XGBoost Filtered    -4.85% (imporved)
- LSTM Filtered       0.0% (no trades dow to low confidence)

High-Performance Trade Insights 
- Outliers identified using PnL Z-Score > 3
- Outlier trades:
    - Occur mostly during early market hours
    - Have distinct IV, volatility, and gamma exposure
- Strong relationship between:
    - IV spread
    - Rolling volatility
    - Gamma exposure

These insights can be used to design better trade filters and risk controls.



Author

**Dhruv Sharma**

Quantitative Trading System 