# NewX Services – Spare Parts Inventory Forecasting

## Project Overview

This project analyzes historical service invoice records from NewX Services to identify operational patterns and forecast future weekly invoice-record volume using statistical time-series forecasting techniques.

The project explores historical trends, data quality, time-series properties, and forecasting performance to estimate future service activity and support operational planning.

> **Note:** The forecasting target in this project is weekly invoice-record volume. It is used as a proxy for operational activity and does not represent actual spare-parts demand or inventory quantities.

---

## Business Problem

Service operations need to understand their historical workload patterns and anticipate future activity to support operational planning.

The objective of this project is to analyze historical service invoice records and develop a time-series model capable of forecasting future weekly invoice-record volume.

---

## Project Objectives

- Analyze historical service invoice records.
- Perform data quality assessment and exploratory data analysis.
- Identify trends and patterns in weekly operational activity.
- Examine stationarity and autocorrelation.
- Develop baseline forecasting models.
- Build and evaluate ARIMA and SARIMA models.
- Compare forecasting performance using multiple evaluation metrics.
- Apply time-series cross-validation.
- Analyze forecast residuals and uncertainty.
- Generate future forecasts with 95% prediction intervals.

---

## Dataset Information

The dataset contains service invoice-line records with information such as:

- Invoice Date
- Job Card Date
- Business Partner Name
- Vehicle Number
- Vehicle Model
- Current Kilometer Reading
- Invoice Line Description

The dataset covers approximately 2017–2019.

The data was aggregated into a weekly time series for forecasting analysis.

---

## Project Workflow

1. Data Loading and Inspection
2. Data Understanding
3. Data Quality Assessment
4. Exploratory Data Analysis (EDA)
5. Date-Based Analysis
6. Weekly Time-Series Aggregation
7. Trend Analysis
8. Stationarity Testing
9. ACF and PACF Analysis
10. Baseline Forecasting
11. ARIMA Model Development and Selection
12. SARIMA Model Comparison
13. Time-Series Cross-Validation
14. Residual Diagnostics
15. Forecast Error and Bias Analysis
16. Forecast Horizon Analysis
17. Final Model Comparison
18. Future Forecasting
19. Interpretation and Business Insights
20. Conclusion and Limitations

---

## Models Evaluated

- Naive Forecast
- Fixed 4-Week Moving Average
- Rolling 4-Week Moving Average
- Seasonal Naive Forecast
- ARIMA
- SARIMA
- Bias-Corrected ARIMA (experimental)

---

## Final Model

### ARIMA(2,1,0)

The ARIMA(2,1,0) model was selected as the primary forecasting model based on its test-set performance, rolling-origin cross-validation results, and residual diagnostics.

| Evaluation Metric | Test Result |
|---|---:|
| MAE | 73.57 |
| RMSE | 104.16 |
| MAPE | 16.74% |

### Cross-Validation Performance

| Model | Average CV MAE | Average CV RMSE |
|---|---:|---:|
| ARIMA(2,1,0) | 66.34 | 81.99 |
| Naive | 67.81 | 88.46 |

ARIMA showed modest average improvement over the Naive baseline, although performance varied across individual validation folds.

---

## Forecast Results

The model forecasts weekly invoice-record volume for the following four weeks:

| Forecast Week | Predicted Records |
|---|---:|
| 2019-01-13 | 463 |
| 2019-01-20 | 443 |
| 2019-01-27 | 446 |
| 2019-02-03 | 450 |

The predictions remain relatively stable around 450 records per week. However, the wide 95% prediction intervals indicate considerable uncertainty in future actual volumes.

---

## Key Findings

- Historical weekly invoice-record volume exhibited an increasing trend.
- The original weekly time series was non-stationary.
- First differencing helped achieve stationarity.
- ARIMA(2,1,0) performed modestly better than the Naive baseline on average during rolling-origin cross-validation.
- Seasonal models did not demonstrate sufficient consistent improvement.
- The final forecasts indicate relatively stable short-term operational activity.
- Forecast uncertainty increases with the prediction horizon.

---

## Visualizations

### Historical Weekly Invoice Record Volume

![Weekly Trend](images/weekly_trend.png)

### Actual vs Forecast

![Forecast Plot](images/forecast_plot.png)

### Model Comparison

![Model Comparison](images/model_comparison.png)

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Scikit-learn
- Google Colab
- Statistical Time-Series Analysis

---

## Limitations

- The forecast target represents invoice-record volume, not actual spare-part demand.
- Actual stock quantities and inventory movement data are unavailable.
- The time series contains approximately 84 weekly observations.
- The prediction intervals are wide, reflecting substantial forecast uncertainty.
- Model performance varies across cross-validation folds.
- Seasonality could not be established with sufficient confidence.
- Supplier lead times, procurement data, and stock-out information are unavailable.

Therefore, the current model cannot directly calculate part-level demand, reorder points, safety stock, or optimal purchase quantities.

---

## Future Scope

- Standardize invoice-line descriptions.
- Categorize service items and spare parts.
- Develop item-level demand forecasting models.
- Integrate inventory and stock movement data.
- Incorporate supplier lead times and procurement history.
- Develop reorder-point and safety-stock calculations.
- Build an interactive operational forecasting dashboard.

---

## Repository Structure

```text
NewX-Services-Spare-Parts-Forecasting/
│
├── README.md
├── NewX_Services_Spare_Parts_Forecasting_Final.ipynb
├── requirements.txt
│
├── data/
│   └── README.md
│
├── images/
│   ├── weekly_trend.png
│   ├── forecast_plot.png
│   └── model_comparison.png
│
└── reports/
    └── project_summary.md
```

---

## Conclusion

This project demonstrates the application of statistical time-series analysis to historical service operations data. Through exploratory analysis, stationarity testing, baseline comparisons, ARIMA/SARIMA modeling, cross-validation, and residual diagnostics, a forecasting approach was developed to estimate future weekly invoice-record volume.

The project also highlights the importance of forecast uncertainty, validation methodology, and understanding the limitations of available data when translating model results into business decisions.

---

**Project Category:** Data Analytics | Time-Series Forecasting | Machine Learning

**Author:** Harsh Bandekar