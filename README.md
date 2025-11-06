# Volatility Forecasting for Risk Management
ARCH / GARCH / EGARCH / GJR-GARCH / EWMA (with Walk-Forward Evaluation)

## Project Overview

This project analyzes and forecasts daily volatility of the S&P 500 Index, one of the most widely followed benchmarks for the U.S. equity market.
The goal is to predict next-day volatility using different time-series models that capture how market risk evolves over time.

Understanding and forecasting volatility is crucial for:

* Risk management – setting trading limits and capital buffers
* Trading strategies – adjusting positions based on expected market swings
* Portfolio management – estimating Value-at-Risk (VaR) and downside exposure

## Models Used

I compared five volatility models to see how each captures S&P 500 market movements:

| Model                                                    | What it does                                                  | Key Feature                                                   |
| -------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| **EWMA (Exponentially Weighted Moving Average)**         | Assigns more weight to recent returns.                        | Fast-reacting baseline, ideal for short-term risk monitoring. |
| **ARCH (Autoregressive Conditional Heteroskedasticity)** | Models volatility based only on past squared returns.         | Captures volatility clustering.                               |
| **GARCH (Generalized ARCH)**                             | Adds previous volatility into the mix.                        | Produces smoother, persistent forecasts.                      |
| **EGARCH (Exponential GARCH)**                           | Works with log-volatility and captures asymmetry.             | Reacts stronger to negative market shocks.                    |
| **GJR-GARCH**                                            | Similar to GARCH but distinguishes between up and down moves. | Handles downside risk more effectively.                       |

## Results Summary

| Model         | Predicted Volatility | Realized (Actual) Volatility | Observation                                        |
| ------------- | -------------------- | ---------------------------- | -------------------------------------------------- |
| **ARCH**      | 1.1229               | 1.0852                       | Slightly overestimates volatility.                 |
| **GARCH**     | 1.4420               | 1.0852                       | Smooth but tends to overpredict.                   |
| **EGARCH**    | 1.4156               | 1.0852                       | Captures asymmetry; still somewhat high.           |
| **GJR-GARCH** | 1.3041               | 1.0852                       | Closest to realized volatility.                    |

All results are based on S&P 500 daily returns from the analyzed period.

## EWMA Forecast vs. Realized Volatility
The chart below shows how the EWMA model predicted volatility (orange line) tracks the actual realized volatility (blue line) of the S&P 500:
<img width="1118" height="611" alt="EWMA Model" src="https://github.com/user-attachments/assets/6a472d31-1151-4b98-9be8-13ab451b93b2" />

## Key Takeaways

* Volatility in S&P 500 is persistent - high volatility days often follow other high volatility days.
* EWMA adapts fastest to sudden market moves - useful during sharp rallies or sell-offs.
* GARCH-family models give smoother, more stable forecasts - good for longer-term risk control.
* Each model has its trade-offs between reactiveness (EWMA) and stability (GARCH).

## How It Works

1. Pulled S&P 500 daily price data (closing prices).
2. Calculated daily log returns.
3. Computed realized volatility as the benchmark.
4. Trained and forecasted with each model (ARCH, GARCH, EGARCH, GJR-GARCH, EWMA).
5. Generated 1-day-ahead volatility forecasts.
6. Compared each model’s prediction to actual S&P 500 volatility.

## Conclusion

This project applies multiple volatility forecasting models on S&P 500 daily data to analyze and predict market risk. The EWMA model reacts quickly to sudden changes, while the GARCH-family models provide smoother and more consistent forecasts. Together, they show how different models balance short-term sensitivity and long-term stability. Overall, the project demonstrates practical skills in financial modeling, data analysis, and risk forecasting.
