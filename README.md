# 📊 Data, Policy and Market: A Time Series Perspective (2014–2025)

This project analyzes the BSE SENSEX (2014–2025) using time series forecasting techniques to understand how major political and economic events influenced market behavior. 
The goal is to evaluate whether traditional statistical models and deep learning models can capture both long-term market trends and sudden real-world volatility caused by policy changes and global shocks.

### 🎯 Objectives
- Forecast Sensex movements using time series modeling
- Identify long-term trends and structural market shifts
- Understand the impact of major events such as:
```
2014 & 2019 Elections
Demonetization (2016)
GST Implementation (2017)
COVID-19 Crash (2020)
Post-COVID Recovery (2021–2023)
2024 Election volatility phase
```
- Compare performance of:
```
ARIMA/SARIMA/SARIMAX
```
- LSTM (Deep Learning)

### 📅 Event-Based Market Timeline Analysis

- A historical trend chart was created to visually map key events with market reactions.
This timeline clearly shows:
```
Stable upward growth post-2014 election
Policy-driven uncertainty during demonetization and GST
Sharp structural crash in 2020 due to COVID
Strong recovery rally (2021 onwards)
Higher unpredictability during 2024–2025
This step helped establish that Sensex is a trend-driven series with sudden event-based shocks.
```
### 📈 Trend Smoothing (Moving Average & Exponential Smoothing)
```
To reduce short-term noise and highlight market direction:
 200-Day Moving Average (200 DMA) was used as a long-term trend indicator.
It acted as a strong support/resistance marker during major phases like COVID crash and post-COVID rally.
```
#### Key Insight:

- Sensex consistently returned above its long-term average after shocks, proving strong long-term bullish structure.

### 🌦️ Seasonal Decomposition (STL)

- STL decomposition was applied to break the series into:
```
Trend component
Seasonal component
Residual component
```
- Key Insight:
```
 Trend was strongly upward (especially post-2020).
- Seasonal effects were moderate.
- Residual spikes reflected major domestic/global shocks.
- This validated that market behavior is a mix of structured movement + unpredictable volatility.
```
### 🧪 Stationarity & Correlation Testing
```
Since ARIMA-type models require stationarity, the series was tested using:
KPSS Test → confirmed non-stationarity (trend exists)
ADF Test → confirmed stationarity after differencing
Ljung-Box Test → confirmed serial correlation in raw series
```
##### Key Outcome:

- The data required differencing (d=1) to become stationary, confirming it follows a random-walk style structure common in stock indices.

###📌 ARIMA & SARIMA-Based Modeling
```
⚙️ Auto ARIMA Model Selection
AutoARIMA was used to identify the best model using AIC-based optimization.
 Selected model: ARIMA(0,1,0)
 Interpretation: Random Walk with Drift
```
### Insight:

- ARIMA captured the long-term upward direction but failed to model sharp real-world fluctuations after 2022, proving that linear models struggle with market volatility.


## Why SARIMAX?

- SARIMAX is an extended version of ARIMA that supports:
seasonality modeling
better diagnostics
stronger forecasting structure for real-world time series
It is particularly useful for financial series because it provides deeper residual testing and statistical interpretability.

- Selected SARIMAX Model
```
Final model chosen:
✅ SARIMAX(0,1,0)
This confirms Sensex behaves as a random walk process where the best predictor of today is yesterday’s value, plus noise and drift.
```
```
Interpretation of SARIMAX Output
1. Drift / Intercept Term
Intercept ≈ 17.47
p-value ≈ 0.055 (marginally significant)
Sensex has a persistent upward drift, indicating long-term growth expectation in the Indian market.

2. High Residual Variance (Sigma²)
Sigma² ≈ 1.73e+05
Even after modeling trend/differencing, large unexplained fluctuations remain, proving the market has strong volatility.

✅ Ljung-Box Test (p=0.65)
No significant autocorrelation left.
The model successfully captured the time-based dependence structure, leaving behind mostly random residuals.
Residuals are not normally distributed.

❌ Heteroskedasticity (p=0.03)
Residual variance is not constant.
Volatility clustering exists (high volatility follows high volatility), which is a signature characteristic of financial markets.
```
#### SARIMAX Final Conclusion

- SARIMAX effectively modeled the overall market structure, but its diagnostics revealed the most important real-world truth:
- Sensex is predictable in long-run trend but unpredictable in volatility.

## 🤖 Deep Learning Forecasting (LSTM)
### Why LSTM Was Used

- LSTM is capable of learning:
```
non-linear patterns
long-term memory dependencies
complex sequential market behavior
This makes it suitable for stock market forecasting where movement is not purely linear.
```
- LSTM Model Architecture (High-Level)
```
The LSTM model was designed with:
LSTM layers (50–100 units)
Dropout regularization (0.2–0.3)
Dense output layer for predicting next-day close
Adam optimizer with MSE loss
Training was performed with appropriate epochs and batch size, ensuring convergence without overfitting.
```
- LSTM Training Behavior (Validation Results)
```
Key Observations:
Training and validation loss converged rapidly
Both curves stayed close (minimal generalization gap)
No major overfitting signals were observed
The model generalized well on unseen data, which is a major achievement in financial prediction.
```
- LSTM Forecasting Insights
```
From prediction vs actual plots:
✅ Strengths
LSTM closely tracked both upward and downward movements
Captured short-term fluctuations far better than ARIMA/SARIMAX
Successfully adapted to non-linear market structure

⚠️ Limitation
During extreme spikes or sudden drops, the model slightly lagged and smoothed the movement

Conclusion:
Even deep learning struggles to perfectly predict rare shocks because those events are news-driven and discontinuous.
```
- Model Evaluation Summary
```
Residual plots and evaluation metrics showed:
stable error spread
no strong residual autocorrelation
highly accurate prediction alignment with actual values
```
#### 📌 Final takeaway:
- LSTM clearly outperformed ARIMA/SARIMAX for predictive performance and short-term movement learning.

## 📌 Final Insights & Conclusion

- Sensex follows a strong long-term upward trend driven by macroeconomic growth.
- Major policy and global events create sharp structural shocks.
- SARIMAX is strong for interpretability and diagnostics, proving the presence of:
fat tails
volatility clustering
market randomness in short-term
- LSTM provides superior predictive performance, especially for short-term forecasting and non-linear patterns.
##### This project provides a clear time-series-based understanding of how policy decisions and macro events influence investor sentiment, enabling:
- Improved risk interpretation
- Volatility awareness
- Event-driven market forecasting perspective
- Better decision-making for investors and analysts.
- LSTM provides superior predictive performance, especially for short-term forecasting and non-linear patterns.
- Both models struggle during extreme volatility, proving markets remain partially unpredictable.
