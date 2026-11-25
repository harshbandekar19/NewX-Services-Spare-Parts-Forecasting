# Project Summary – NewX Services Spare Parts Inventory Forecasting

## 1. Project Overview

The NewX Services project involved analyzing historical service invoice records to understand operational activity patterns and forecast future weekly invoice-record volume.

The project applied statistical time-series forecasting techniques to historical data, with a focus on exploratory data analysis, stationarity, model evaluation, validation, and forecast uncertainty.

**Project Type:** Time-Series Forecasting & Data Analytics  
**Domain:** Automotive Service Operations  
**Primary Model:** ARIMA(2,1,0)

---

## 2. Business Objective

The primary objective was to investigate historical service activity and estimate future weekly invoice-record volume.

The analysis aimed to:

- Understand the historical data and its quality.
- Identify trends and patterns in service activity.
- Convert transaction-level data into a weekly time series.
- Investigate stationarity and autocorrelation.
- Develop statistical forecasting models.
- Compare models using appropriate metrics.
- Evaluate forecast reliability using time-series cross-validation.
- Interpret forecasts in an operational context.

---

## 3. Methodology

### Data Analysis

Performed data inspection, missing-value analysis, duplicate analysis, date validation, and exploratory analysis of invoice-line descriptions and transaction patterns.

### Time-Series Preparation

Aggregated invoice records into weekly observations and examined historical trends, fluctuations, stationarity, and autocorrelation.

### Forecasting

Evaluated baseline forecasting techniques and developed ARIMA and SARIMA candidates.

### Model Validation

Used a chronological train-test split, expanding-window time-series cross-validation, forecasting metrics, and residual diagnostics.

### Final Forecast

Generated four future weekly forecasts with 95% prediction intervals.

---

## 4. Model Performance

### Selected Model: ARIMA(2,1,0)

| Metric | Value |
|---|---:|
| Test MAE | 73.57 |
| Test RMSE | 104.16 |
| Test MAPE | 16.74% |
| Average CV MAE | 66.34 |
| Average CV RMSE | 81.99 |

The model showed modest average improvement over the Naive baseline during rolling-origin cross-validation. However, performance was not consistently superior across all folds.

---

## 5. Forecast Summary

The model predicted approximately 443–463 weekly invoice records over the four-week forecast horizon.

| Week | Forecast |
|---|---:|
| 2019-01-13 | 463 |
| 2019-01-20 | 443 |
| 2019-01-27 | 446 |
| 2019-02-03 | 450 |

The forecasts suggest relatively stable short-term operational activity, while the wide prediction intervals indicate substantial uncertainty.

---

## 6. Key Insights

- Historical weekly activity showed a significant increasing trend.
- The original weekly series was non-stationary.
- First differencing helped achieve stationarity.
- ARIMA(2,1,0) was competitive with baseline methods and modestly better on average in cross-validation.
- Seasonal models did not provide sufficient consistent improvement.
- Short-term forecasts were more informative than longer-horizon forecasts.
- Prediction intervals highlighted uncertainty that point predictions alone would not reveal.

---

## 7. Business Relevance

Weekly invoice-record forecasting may provide an approximate indication of future service activity and help with operational workload planning.

However, the current analysis does not directly forecast spare-part consumption or inventory quantities. Actual inventory planning would require part-level usage, stock levels, procurement history, supplier lead times, and stock-out information.

---

## 8. Limitations

- Forecast target is weekly invoice-record volume rather than actual spare-part demand.
- Approximately 84 weekly observations were available.
- Wide prediction intervals indicate substantial uncertainty.
- Model performance varied across cross-validation folds.
- Seasonal patterns could not be reliably established.
- Actual stock movement, inventory quantities, and supplier information were unavailable.

---

## 9. Future Improvements

- Standardize and categorize invoice-line descriptions.
- Develop individual spare-part demand series.
- Incorporate stock and procurement data.
- Investigate intermittent-demand forecasting approaches for parts with sparse demand.
- Add supplier lead-time and stock-out information.
- Develop inventory decision-support dashboards.

---

## 10. Conclusion

The project demonstrates a structured approach to time-series forecasting, from data quality assessment and exploratory analysis to statistical model development, validation, diagnostics, and forecast interpretation.

ARIMA(2,1,0) was selected as the primary forecasting model because of its competitive test performance, modest average improvement over the Naive baseline in cross-validation, and satisfactory residual diagnostics.

The work provides a foundation for further operational analytics and can be extended into a more comprehensive spare-parts demand forecasting system when actual inventory and consumption data become available.