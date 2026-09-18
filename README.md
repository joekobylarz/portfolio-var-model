# Portfolio Value-at-Risk & Stress Testing Model

A project comparing three methods of calculating Value-at-Risk (VaR): Historical Simulation, Parametric (Variance-Covariance), and Monte Carlo Simulation (with Geometric Brownian Motion)  across three equity portfolios with different risk profiles. The project includes stress testing against a historical crisis period and backtesting to validate model accuracy.

**Status:** Complete

## Motivation

Built to apply concepts from my Mathematical Finance module (stochastic calculus, Brownian motion) alongside statistical/quantitative skills, and to explore how different risk modelling assumptions hold up against real market behaviour, particularly during periods of market stress.

## Methodology

- **Historical Simulation** — empirical, no distributional assumptions
- **Parametric (Variance-Covariance)** — assumes normally distributed returns
- **Monte Carlo Simulation** — simulates future price paths using Geometric Brownian Motion, with correlated asset movements via Cholesky decomposition

Applied across three portfolios (Sector-Diversified Core, High-Beta & Financials Heavy, Defensive & Inflation-Hedged), then stress-tested and backtested for validation.

For Portfolio 3, energy was capped at 25% to preserve the portfolio's defensive character while still testing the inflation-hedge hypothesis

## Tools

Python — pandas, numpy, matplotlib, seaborn, scipy, yfinance

## Project Structure
├── data/             # historical price data

├── notebooks/        # main analysis notebook

├── .gitignore

├── README.md

## Notebook

See [notebooks/var_model.ipynb](notebooks/var_model.ipynb) for the full analysis

## Findings

- **Portfolio 3 (Defensive/Inflation-Hedged) was the lowest risk portfolio across all three methods of calculating VaR** - this goes against the initial hypothesis that its ~25% energy allocation would put its risk somewhere between Portfolio 1 and Portfolio 2. The diversification from its consumer staples and healthcare core outweighed the increased volatility from energy exposure.

- **Parametric VaR exceeded Historical VaR at the 95% confidence level but fell below it at 99% across all three portfolios** - an example of "fat tails" (high kurtosis) in real financial returns. Normal distributions exaggerate risk at moderate confidence levels but underestimate it in extreme tail scenarios, which is particularly important as 99% VaR is meant to capture exactly those scenarios.

- **Monte Carlo VaR followed the Parametric VaR closely, rather than Historical VaR** - despite explicitly modelling asset correlations via Cholesky decomposition. This shows the underlying distribution behind the shocks (Gaussian in both cases) drives the outcome more than the correlation structure does.

- **Full sample backtesting showed reasonably calibrated models, but breach rates spiked to 30-58% during the COVID-19 stress window** - demonstrating a well-known limitation of static VaR models. They perform reasonably under normal conditions but break down during the volatile, correlated crises where risk management is most important.

- **Scope and limitations** - this analysis uses static VaR (calculated from the full sample), rather than a rolling window, tests a single historical crisis period, and models Monte Carlo shocks using standard Gaussian assumptions. Natural progressions could be rolling-window VaR, fatter tailed distributions, and Expected Shortfall (CVaR).