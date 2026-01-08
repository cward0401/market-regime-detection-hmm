# Market Regime Detection & Volatility Modeling

## Overview
Financial markets are non-stationary systems that transition between latent regimes with distinct risk and return characteristics. this project applies a Gaussian Hidden Markov Model (HMM) to identify and characterize market regimes using historical financial time series data, with an emphasis on understaning regime-dependent risk behavior rather than predicting prices.

The analysisi focuses on how volatility, drawdowns, and tail risk vary across regimes, and how regime transitions contribute to periods of market stress.

---

## Problem Statement
Traditional market analysis often relies on unconditional statistics that obscure structural changes in risk. The objective of this project is to identify latent market regimes and quantify how shifts between regimes alter the statistical properties of returns and downside risk.

---

## Data Sources
The analysis uses daily data spanning multiple market cycles from the following sources:

- **S&P 500 ETF (SPY)** - equity markey proxy
- **VIX Index** - market-implied volatility
- **10-year U.S. Treasury Yield (DGS10)** - macro risk-free indicator

These instruments jointly capture equity performance, market uncertainty, and macroeconomic risk conditions.

---

## Methodology
The project follows a structured analytical workflow:

- Transform price series ino log returns and rolling volatility measures
- Engineer features capturing volatility dynamics, drawdowns, and risk sensitivity
- Standardize features and fit a Gaussian Hidden Markov Model with three latent regimes
- Infer regime assignments and analyze regime-specific risk characteristics
- Examine regime persistence and transition probablities

The focus is on interpretability, stability, and risk framing rather than model optimization.

---

## Key Findings
- Identified regimes exhibit materially different volatility and drawdown profiles
- High-volatility regimes are associated with deeper drawdowns and heavier tails
- Regime transitions cluster around periods of elevated market stress
- Average returns alone fail to capture meaningful differences in risk across regimes

---

## Risk Interpretation
Regime analysis provides a structural lens for understanding market risk that is not visible through unconditional metrics. The results hughlight how volatility clustering and regime persistence amplify downside risk during stress periods, reinforcing the importance of regime-aware risk assessment in financial decision-making.

---

## Limitations
- Regime identification is sensitive to feature selection and model specification
- Gaussian HMMs assume conditional normality within regimes
- Regime boundaries are probabalistic rather than deterministic
- Results are descriptive and not intended for price prediction

---

## Future Work
- Evaluate model stability across different numbers of regimes
- incorporate additional macroeconomic indicators
- compare regime-aware an unconditional risk metrics
- Extend analysis to other asset classes and international markets