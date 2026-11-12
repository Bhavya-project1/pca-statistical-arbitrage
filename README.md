# PCA-Based Statistical Arbitrage: Cross-Sector Residual Mean Reversion

A baseline statistical-arbitrage research notebook that uses **Principal Component Analysis (PCA)** to estimate common return factors across a multi-sector equity universe, then studies the residual component for mean-reversion opportunities.

The notebook's stated workflow is:

**Multi-sector stocks → PCA residuals → mean-reversion z-score → cross-sectional statistical arbitrage → out-of-sample backtest.**

## Universe and Research Design

- Historical sample: 2010-01-01 to 2021-01-01 (end date exclusive).
- Universe: up to 44 equities across 11 sectors.
- Chronological split: 90% training / 10% testing.
- PCA factor count: 8.
- Rolling z-score window: 60 observations.
- Residual stationarity screen: Augmented Dickey–Fuller p-value threshold of 0.10.
- Half-life screen: 2 to 120 observations.
- Maximum tradable residual series: 20.
- Entry z-score: 1.0.
- Long/short selection: 3 names on each side.
- Backtest transaction-cost assumption: 5 basis points.
- Initial capital assumption: 100,000 (currency units are not specified in the notebook).

The sector universe is defined directly in the notebook and includes Technology, Financials, Healthcare, Consumer Staples, Consumer Discretionary, Industrials, Energy, Communication Services, Utilities, Materials, and Real Estate.

## Methodology

1. Download adjusted historical prices and create daily returns.
2. Split the return panel chronologically.
3. Fit the scaler and PCA model on the training sample.
4. Reconstruct common-factor returns and calculate residual returns.
5. Screen candidate residuals using training-period ADF p-values and estimated half-life.
6. Form rolling residual z-scores and cross-sectional long/short positions.
7. Backtest the strategy using lagged holdings for P&L and an explicit turnover-based transaction-cost deduction.
8. Evaluate the held-out period.

## Implementation Details

PCA is fitted on the training data only, then applied to the combined return sample using the fitted transformation. The backtest shifts holdings by one period before applying daily returns, which is intended to avoid using same-day signals for same-day P&L.

## Repository Contents

- BASELINE_PCA_STAT_ARB.ipynb — main implementation.

## Technology

Python · NumPy · pandas · yfinance · scikit-learn · statsmodels · Matplotlib

## Run

~~~bash
pip install -r requirements.txt
jupyter notebook
~~~

Open the notebook and run the cells in order. The notebook retrieves historical data at runtime.

## Research Limitations

The notebook's fixed historical ticker universe may introduce survivorship and look-ahead issues because it does not demonstrate point-in-time index membership or delisted-stock handling. The use of current ticker symbols across the full historical sample also needs survivorship-bias review. The backtest should be extended with walk-forward PCA refitting, liquidity constraints, borrow costs and short availability, corporate-action checks, turnover analysis, and multiple untouched test periods.

No numerical performance claim is made here: the notebook's outputs are not retained as a stable, independently verified result set. Re-run the notebook and preserve dated metrics before reporting performance.

## Disclaimer

Research and educational use only. The baseline is not evidence of a persistent arbitrage opportunity and is not investment advice.
