# IC3-Time-Series | Stakeholder report | Forecasting weekly revenue for a dutch recruitment agency

By applying **time series forecasting** to weekly revenue data, we can uncover long-term trends, seasonality, and irregular patterns that influence business performance.

The dataset includes weekly revenue records from previous 4,5 years, capturing fluctuations caused by **market cycles, holidays, and hiring demand**.

The goal of this project is to **predict the expected revenue for 2026**, enabling proactive business planning and data-driven decision-making.

This project supports **SDG 8 (Decent Work and Economic Growth)** by promoting sustainable business growth through predictive analytics, and **SDG 9 (Industry, Innovation, and Infrastructure)** by showcasing how AI can enhance financial and operational foresight in recruitment.

This analysis compared several time series forecasting models to predict weekly revenue trends.
While the ARIMA model captured the overall trend, it failed to reflect seasonal fluctuations.
The SARIMA model, which accounts for seasonality, achieved the lowest error scores (MAE = 3.48, RMSE = 4.44, MAPE = 6.58%) and proved the most accurate and stable.
Alternative models such as SARIMAX and XARIMA did not add meaningful improvement.
The final SARIMA forecast was exported to Excel for future analysis and visualization.
