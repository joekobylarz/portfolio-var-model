# Portfolio Value-at-Risk & Stress Testing Model

A project comparing three methods of calculating Value-at-Risk (VaR): Historical Simulation, Parametric (Variance-Covariance), and Monte Carlo Simulation (with Geometric Brownian Motion)  across three equity portfolios with different risk profiles. The project includes stress testing against a historical crisis period and backtesting to validate model accuracy.

**Status:** In progress

## Motivation

Built to apply concepts from my Mathematical Finance module (stochastic calculus, Brownian motion) alongside statistical/quantitative skills, and to explore how different risk modelling assumptions hold up against real market behaviour, particularly during periods of market stress.

## Methodology

- **Historical Simulation** — empirical, no distributional assumptions
- **Parametric (Variance-Covariance)** — assumes normally distributed returns
- **Monte Carlo Simulation** — simulates future price paths using Geometric Brownian Motion, with correlated asset movements

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

See ['notebooks/var_model.ipynb'](notebooks/var_model.ipynb) for the full analysis