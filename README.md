# Equity Factor Analysis

## Overview

This project analyzes historical U.S. equity returns using single-factor and multifactor regression models.

The goal is to examine how individual stocks respond to broader market movements, test whether those relationships remain stable over time, and determine whether additional systematic factors improve explanatory power.

The analysis covers six large U.S. equities:

- AAPL — Apple
- MSFT — Microsoft
- NVDA — NVIDIA
- JPM — JPMorgan Chase
- XOM — Exxon Mobil
- JNJ — Johnson & Johnson

SPY is used as a proxy for the broader U.S. equity market.

## Methods

The project includes:

- Daily return calculation
- Exploratory return analysis
- Correlation analysis
- Annualized and rolling volatility
- Single-factor market regression
- Beta estimation
- Rolling beta analysis
- Out-of-sample model testing
- Fama-French three-factor regression
- Single-factor vs. multifactor model comparison

Historical equity data is obtained using `yfinance`, while Fama-French factor data is retrieved through `pandas_datareader`.

## Key Findings

### Market sensitivity differs substantially across stocks

The single-factor regressions showed large differences in estimated market beta.

- NVDA had the highest full-sample beta at approximately 1.80.
- AAPL and MSFT had betas slightly above 1.
- JPM had a beta close to 1.
- XOM and JNJ had substantially lower market betas.

### Beta is not constant over time

NVDA's 126-day rolling beta varied substantially during the sample period, ranging from roughly 1.3 to above 3.0.

This demonstrates that a single historical beta can conceal substantial changes in market exposure over time.

### Out-of-sample performance varies considerably

Models were trained using 2020–2024 data and evaluated using 2025–2026 data.

Approximate out-of-sample R² values included:

- NVDA: 0.50
- JPM: 0.40
- AAPL: 0.38
- MSFT: 0.24

XOM and JNJ produced negative out-of-sample R² values, indicating that the single market factor generalized poorly for those equities.

### Additional factors improve explanatory power

The Fama-French three-factor model added the SMB and HML factors to the market factor.

Adjusted R² improved for all six equities, with the largest improvements occurring for XOM and JPM.

These results suggest that size and value exposures provide meaningful information beyond broad market exposure for some stocks.

## Main Takeaway

Simple factor models provide interpretable measures of equity risk and market exposure, but their usefulness varies substantially across companies and over time.

The analysis highlights the importance of:

- Testing model stability
- Evaluating models on unseen data
- Avoiding reliance on a single historical beta
- Considering multiple systematic sources of risk

## Setup

Create and activate the Conda environment:

```bash
conda create -n equity-factor python=3.12
conda activate equity-factor
```

Install the required packages:

```bash
python -m pip install -r requirements.txt
```

## Model Assumptions and Limitations

The analysis relies on several simplifying assumptions and has important limitations:

- Factor-return relationships are modeled as approximately linear.
- Historical relationships may not remain stable in the future.
- The analysis includes only six large U.S. equities.
- SPY is only a proxy for the broader equity market.
- Factor models describe statistical relationships rather than causation.
- The Fama-French three-factor model does not capture every source of systematic risk.
- Strong in-sample performance does not guarantee strong future performance.
- The analysis does not incorporate transaction costs, portfolio construction, or trading implementation.

## Future Work

Potential extensions include:

- Adding momentum, profitability, and investment factors
- Testing a larger universe of equities
- Comparing factor exposures across sectors
- Examining different market regimes
- Constructing factor-based portfolios
- Comparing traditional factor models with machine-learning approaches
