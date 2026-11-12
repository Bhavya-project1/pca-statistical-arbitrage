# PCA-Based Statistical Arbitrage: Baseline Model

A research notebook exploring **Principal Component Analysis (PCA)** as a tool for decomposing common-factor movements in financial return series and investigating a baseline statistical-arbitrage framework.

PCA transforms correlated variables into orthogonal components ordered by explained variance. In quantitative finance, this can help separate broad co-movement from residual movements that may be studied for potential relative-value relationships.

## Research Objectives

- Prepare a panel of asset returns.
- Use PCA to identify dominant common components.
- Examine variance explained by principal components.
- Study residual or idiosyncratic movements after factor decomposition.
- Establish a baseline for further statistical-arbitrage research.

## Repository Contents

- `BASELINE_PCA_STAT_ARB.ipynb` — main research notebook.

## Methodological Context

PCA is a dimensionality-reduction method, not by itself a trading signal. A statistical-arbitrage strategy requires additional design choices, such as residual construction, signal standardisation, entry and exit rules, position sizing, risk controls, and realistic execution assumptions.

Consult the notebook for the specific universe, sample period, PCA implementation, residual definition, and implemented strategy logic.

## Run

```bash
pip install numpy pandas scipy scikit-learn matplotlib seaborn statsmodels jupyter
jupyter notebook
```

Open `BASELINE_PCA_STAT_ARB.ipynb` and execute the notebook. Install any additional dependency used by the implementation if prompted.

## Validation Priorities

A credible test should guard against look-ahead bias, use chronological or walk-forward evaluation, account for turnover and transaction costs, test parameter stability, and compare against appropriate baselines. Statistical significance and economic profitability are separate questions.

## Project Status

Baseline research implementation. Results should not be interpreted as evidence of a live or profitable arbitrage opportunity without further out-of-sample validation.

## Disclaimer

For educational and research purposes only. Not investment advice.
