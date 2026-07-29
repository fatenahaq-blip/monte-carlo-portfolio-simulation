# Monte Carlo Portfolio Simulation

# Monte Carlo Portfolio Simulation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/fatenahaq-blip/monte-carlo-portfolio-simulation/blob/main/notebooks/monte_carlo_portfolio_simulation.ipynb)



## Overview

This project uses Monte Carlo simulation to estimate possible future outcomes and risks for a diversified investment portfolio.

The model combines:

- long-term portfolio simulations;
- short-horizon Value at Risk;
- Expected Shortfall;
- drawdown analysis;
- stress testing;
- fat-tail simulations;
- portfolio-allocation comparisons.

The portfolio starts with an initial value of **$100,000** and contains US equities, technology equities, US bonds, and gold.

## Research Questions

This project investigates:

1. What range of portfolio values could occur over ten years?
2. What is the probability of ending below the initial investment?
3. What is the probability of reaching a selected investment target?
4. How severe could temporary portfolio drawdowns become?
5. What are the portfolio's 1-day, 10-day, and 1-month risk levels?
6. How does Expected Shortfall compare with Value at Risk?
7. How do normal and fat-tail simulations differ?
8. How does a stressed market scenario affect outcomes?
9. How do conservative, balanced, and growth allocations compare?

## Portfolio Allocation

| Asset | Ticker | Weight |
|---|---|---:|
| US equities | SPY | 40% |
| Technology equities | QQQ | 25% |
| US bonds | BND | 25% |
| Gold | GLD | 10% |

## Methodology

The project follows these steps:

1. Download adjusted historical prices.
2. Calculate daily asset returns.
3. Estimate portfolio return, volatility, and correlations.
4. Simulate 10,000 possible ten-year portfolio paths.
5. Calculate ending-value percentiles.
6. Estimate the probability of loss.
7. Estimate the probability of reaching a target value.
8. Calculate maximum simulated drawdowns.
9. Calculate short-horizon Value at Risk.
10. Calculate short-horizon Expected Shortfall.
11. Compare normal and fat-tail return distributions.
12. Conduct a stressed-market simulation.
13. Compare alternative portfolio allocations.

## Simulation Assumptions

- Initial portfolio value: **$100,000**
- Investment horizon: **10 years**
- Long-term simulations: **10,000**
- Trading days per year: **252**
- Short-horizon risk scenarios: **200,000**
- Target portfolio value: **$200,000**
- Historical data period: **2015 to 2025**
- Portfolio rebalancing is simplified
- Taxes, inflation, fees, and withdrawals are excluded

## Long-Term Simulation Results

| Metric | Result |
|---|---:|
| Starting portfolio value | $100,000.00 |
| Expected annual return assumption | 12.30% |
| Annual volatility assumption | 12.83% |
| Median 10-year ending value | $314,188.58 |
| 5th-percentile ending value | $161,911.22 |
| 95th-percentile ending value | $622,496.98 |
| Probability of ending with a loss | 0.21% |
| Probability of reaching $200,000 | 87.14% |
| Median maximum drawdown | -20.27% |
| Probability of at least a 20% drawdown | 51.99% |

## Interpretation of Long-Term Results

The median simulated ending value was approximately **$314,189**, meaning that half of the simulations finished above this value and half finished below it.

The 5th-percentile ending value was approximately **$161,911**. Under the model assumptions, only around 5% of the simulations finished below this amount.

The probability of ending below the original $100,000 investment was only **0.21%**, while the probability of reaching the $200,000 target was **87.14%**.

However, the portfolio was still exposed to significant temporary declines. The median maximum drawdown was approximately **20.27%**, and **51.99%** of simulations experienced a drawdown of at least 20%.

## Short-Horizon Risk Analysis

The project calculates Value at Risk and Expected Shortfall over:

- 1 trading day;
- 10 trading days;
- 21 trading days, approximately one month.

Risk is calculated at both:

- 95% confidence;
- 99% confidence.

### Risk Results

Replace the values below after running the updated notebook:

| Horizon | Confidence | Value at Risk | Expected Shortfall |
|---|---:|---:|---:|
| 1 day | 95% | $[insert result] | $[insert result] |
| 1 day | 99% | $[insert result] | $[insert result] |
| 10 days | 95% | $[insert result] | $[insert result] |
| 10 days | 99% | $[insert result] | $[insert result] |
| 1 month | 95% | $[insert result] | $[insert result] |
| 1 month | 99% | $[insert result] | $[insert result] |

## Value at Risk

Value at Risk estimates a loss threshold for a selected confidence level.

For example, a 95% one-day VaR estimates a loss amount that was exceeded in approximately 5% of the simulated one-day scenarios.

VaR does not explain how large losses may become after the threshold is exceeded.

## Expected Shortfall

Expected Shortfall estimates the average loss in the worst outcomes beyond the Value at Risk threshold.

Expected Shortfall is useful because it provides information about the severity of tail losses rather than only identifying a cutoff point.

## Why the Original Ten-Year VaR Was Removed

The earlier version calculated Value at Risk using ten-year ending portfolio values.

That calculation produced:

- 95% VaR: **$0.00**
- 95% Expected Shortfall: **$0.00**

This occurred because even the 5th-percentile ten-year ending value remained above the original $100,000 investment.

Although mathematically consistent with that definition, it was not a useful measure of short-term portfolio risk.

The revised notebook therefore calculates VaR and Expected Shortfall over one-day, ten-day, and one-month horizons, which are more practical for portfolio risk analysis.

## Maximum Drawdown Analysis

Maximum drawdown measures the largest decline from a previous portfolio peak.

A portfolio may finish above its initial value while still experiencing a large temporary decline along the way.

The simulation produced:

- Median maximum drawdown: **-20.27%**
- Probability of at least a 20% drawdown: **51.99%**

This highlights the difference between:

- long-term ending-value risk;
- short-term path risk.

## Fat-Tail Simulation

The base simulation uses normally distributed returns.

A second model uses a Student's t-distribution to allow more extreme outcomes.

This provides a simple way to test whether the portfolio results are sensitive to larger market shocks and heavier distribution tails.

## Stress Scenario

The stressed simulation assumes:

- expected annual return is 3 percentage points lower;
- annual volatility is 25% higher.

The stressed results are compared with the base-case simulation to show how portfolio outcomes may change under less favorable market conditions.

## Allocation Comparison

The project compares three sample allocations.

### Conservative Portfolio

| Asset | Weight |
|---|---:|
| SPY | 20% |
| QQQ | 10% |
| BND | 60% |
| GLD | 10% |

### Balanced Portfolio

| Asset | Weight |
|---|---:|
| SPY | 40% |
| QQQ | 25% |
| BND | 25% |
| GLD | 10% |

### Growth Portfolio

| Asset | Weight |
|---|---:|
| SPY | 50% |
| QQQ | 35% |
| BND | 5% |
| GLD | 10% |

The comparison illustrates the relationship between expected return and investment risk.

## Charts Included

The notebook includes:

- historical normalized asset-price chart;
- portfolio-allocation chart;
- simulated ten-year portfolio paths;
- ending-value distribution;
- maximum-drawdown distribution;
- one-month profit-and-loss distribution;
- Value at Risk threshold;
- Expected Shortfall threshold.

## Tools and Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- yfinance
- Google Colab
- GitHub

## Repository Structure

```text
monte-carlo-portfolio-simulation/
│
├── notebooks/
│   └── monte_carlo_portfolio_simulation.ipynb
│
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

## Limitations

1. Historical return and volatility estimates may not represent future conditions.
2. Expected returns and volatility are assumed to remain stable.
3. Normally distributed simulations may underestimate extreme events.
4. The fat-tail model is still a simplified representation of market risk.
5. Asset correlations may change during financial crises.
6. Taxes, inflation, transaction costs, management fees, and withdrawals are excluded.
7. The model does not include volatility clustering.
8. The portfolio contains only four ETFs.
9. VaR depends on the chosen confidence level, horizon, and distribution assumptions.
10. Monte Carlo simulations generate possible scenarios rather than exact predictions.

## Future Improvements

- Add historical VaR.
- Add parametric VaR.
- Add bootstrap simulations.
- Use GARCH volatility models.
- Add regime-switching simulations.
- Model changing correlations.
- Include annual portfolio rebalancing.
- Add periodic contributions and withdrawals.
- Include inflation-adjusted outcomes.
- Add transaction costs and management fees.
- Compare additional portfolios.
- Build an interactive Streamlit dashboard.
- Add downloadable risk reports.

## Disclaimer

This repository is for educational and research purposes only.

The results are based on historical data and model assumptions. They do not predict future investment performance and do not constitute investment advice.

## Author

Faten Abdelhaq
fatenahaq-blip

