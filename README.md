# IC3-Time-Series | Stakeholder report | Forecasting weekly revenue for a dutch recruitment agency

By applying **time series forecasting** on weekly revenue data, we can anticipate demand cycles, identify low-activity periods in advance, and support better resource planning.  
This enables **proactive business decision-making** — such as scheduling staff, optimizing marketing activity, and stabilizing cash flow — rather than reacting after fluctuations occur.

In line with **SDG 8 (Decent Work & Economic Growth)** and **SDG 9 (Industry, Innovation & Infrastructure)**, this project contributes to more sustainable and data-driven business operations, strengthening the resilience and efficiency of small- to medium-sized enterprises.

**Impact:**  
Predicting seasonal dips and peaks helps recruitment agencies plan workload and budgets more effectively.  
Concretely, this means marketing and sales teams can anticipate slower months (e.g., January, August) and redistribute effort, reducing downtime and ensuring steady revenue performance year-round.

---

## **Dataset Index**
**Stakeholder report:**  
[Forecasting weekly revenue for a Dutch recruitment agency →](https://www.notion.so/Stakeholder-report-Forecasting-weekly-revenue-for-a-dutch-recruitment-agency-29c98c6768cd804cbf3cd2952092a261)

---

## **Summary**

This project forecasts **weekly revenue** for a Dutch recruitment agency using **ARIMA** and **SARIMA** time-series models.  
The goal is to recognize recurring seasonal patterns, anticipate future dips, and support proactive operational planning.  
By leveraging statistical modelling, the analysis provides evidence-based insights into business performance dynamics and expected volatility.

This aligns with **SDG 8 (Decent Work & Economic Growth)** by enabling sustainable planning and workforce stability, and **SDG 9 (Industry, Innovation & Infrastructure)** by promoting the adoption of advanced analytical methods in SMEs.

---

## **Hypothesis**

We assume that past revenue contains enough temporal information — including trend and seasonality — to predict future values accurately.  
If the model can reproduce historical cycles and forecast upcoming dips or surges, it can serve as a reliable decision-support tool for business planning.

---

## **Dataset Info**

- **Source:** Internal weekly revenue dataset (2021–2025)  
- **Content:** Aggregated weekly turnover in euros  
- **Target variable:** `Revenue (€)` (continuous numeric value)  
- **Frequency:** Weekly (`W-MON`)  
- **Granularity:** One value per week across ~250 weeks  

---

## **Notebook Index**

### 01. `IC3_Time-Series_Revenue-prediction.ipynb`

#### **1. Data Preparation & Exploration**
- Set weekly frequency and handle missing weeks  
- Visualize full revenue history  
- Examine recurring patterns and seasonal dips  
- Compute 4-week rolling averages for smoothing  

#### **2. Stationarity & Differencing**
- Conduct **Augmented Dickey-Fuller (ADF)** test  
- Apply first differencing to remove trend  
- Verify stationarity visually and statistically  

#### **3. ARIMA Grid Search**
- Compact grid search over `(p, d, q)` parameters  
- Select best model by **AIC** (Akaike Information Criterion)  
- Identify **ARIMA(0, 1, 2)** as best-performing baseline  

#### **4. Model Diagnostics**
- Plot residual **ACF** and **Q–Q** distributions  
- Confirm residuals behave like white noise (no autocorrelation)  
- Validate normal distribution assumption  

#### **5. SARIMA Forecasting**
- Extend model to include **seasonal parameters (P, D, Q, s)**  
- Forecast test period (hold-out year 2025)  
- Generate forward projection into 2026  
- Plot 4-week rolling average with **95% confidence intervals**  

#### **6. Model Comparison**

| Metric | ARIMA | SARIMA | SARIMAX | **Best** |
|---------|--------|---------|----------|----------|
| **MAE** | 5.782  | **3.479**  | 3.479  | SARIMA  |
| **RMSE**| 8.625  | **4.439**  | 4.439  | SARIMA  |
| **MAPE (%)**| 10.462  | **6.581**  | 6.581  | SARIMA  |

#### **7. Forecast Export**
- Export final SARIMA forecast (historical + projected) to Excel  
- File: `/outputs/forecast_weekly.xlsx`  

---

## **Final Results**

The **SARIMA model** delivered the most accurate and stable forecasts, outperforming both ARIMA and SARIMAX in all key metrics.  
Residual diagnostics confirmed no remaining autocorrelation and near-normal error distribution.  
Seasonal peaks and dips were successfully captured, showing predictable low-revenue periods around **January and August**.

We briefly experimented with **XARIMA** (extended ARIMA with exogenous features), but it did not improve accuracy for this dataset and was excluded from the final report for clarity.

---

## **Key Metrics (Hold-Out Evaluation)**

- **MAE = 3.48**  
- **RMSE = 4.44**  
- **MAPE = 6.58 %**  

The model effectively balances simplicity and predictive reliability, making it suitable for ongoing business forecasting applications.

---

## **Takeaway**

- ARIMA captured overall trend but missed seasonal rhythm.  
- SARIMA incorporated seasonality and significantly reduced forecasting error.  
- The final export provides a practical foundation for **budget forecasting**, **staffing**, and **campaign timing** decisions.  

By adopting time-series forecasting, the agency gains the ability to plan ahead, optimize operations, and sustain healthy growth patterns.

---

## **Limitations & Future Work**

- No exogenous variables (e.g., job postings, campaigns) included.  
- Forecast uncertainty increases beyond one-year horizon.  
- Future improvements could involve **SARIMAX**
---

## **Ethical & Business Reflection**

All data used is non-personal and aggregated at company level.  
The project promotes fair work planning, efficient resource use, and supports a culture of data-driven decision-making — contributing positively to sustainable business operations.

---

## **Repository Link**

Notebook: `IC3_Time-Series_Revenue-prediction.ipynb`  
Stakeholder Report: [View on Notion →](https://www.notion.so/Stakeholder-report-Forecasting-weekly-revenue-for-a-dutch-recruitment-agency-29c98c6768cd804cbf3cd2952092a261)

---

## **Environment Setup**

### Create virtual environment
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -U pip
pip install -r requirements.txt
