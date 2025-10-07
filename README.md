# Scratch AI Forecast

**Scratch AI Forecast** is a data science pipeline and forecasting framework designed to explore the relationship between **Google Trends interest in coding education** and **Scratch platform engagement metrics** (projects, users, comments, etc.).  
It automates data ingestion, cleaning, feature engineering, time-series relationship mining, and robust forecasting — all reproducible and production-ready.

---

## Overview

This project investigates how **potential interest** (Google Trends data) connects to **actual participation** (Scratch usage) across time.  
It aims to uncover predictive patterns and quantify how public curiosity about coding translates into real creative engagement.

---

## Key Components

### 1. Data Ingestion & Normalization
- Handles messy **Excel/CSV** sources with **two-row headers**.
- **Slugifies** multilingual (Turkish) column names.
- Performs **locale-aware numeric coercion** and **automatic date inference** (year-month/week).
- Supports **long/wide reshaping** and aligns frequencies to **month-start**.
- Persists clean artifacts to **Parquet/CSV** with rich **schema metadata**.
- Automatically generates a report bundle:  
  - Markdown summary  
  - PNG charts  
  - HTML visualization dashboard  

---

### 2. Time-Series Relationship Mining
- Computes **3-month moving averages** for signal smoothing.  
- Performs **lagged Pearson/Spearman scans** across −12..+12 months.  
- Builds **category/term pivots** and **correlation heatmaps**.  
- Extracts **momentum indicators** (last-12 slope).  
- Runs **Granger causality tests** with:
  - Seasonal differencing & log transforms  
  - ADF-guided differencing for stationarity  
- Summarizes results via:
  - Top correlated pairs  
  - Lag-response curves  
  - Cross-category/platform comparisons  
- Exports all visuals and tables in **styled Excel/HTML/Markdown** formats.

---

### 3. Forecasting & Evaluation
- Baseline models:
  - **Auto-ARIMA** and **SARIMA**
- Enhanced model:
  - **SARIMAX** with exogenous Google Trends signals  
  - Term and lag selection based on correlation and Granger results (lags 0–6 months)
- Evaluation protocols:
  - **Held-out 24-month test sets**  
  - **Rolling-origin backtesting**
- Metrics:
  - MAE, RMSE, MAPE
- Diagnostics:
  - **STL decomposition**
  - **Ljung–Box residual tests**
- Benchmarks:
  - **Seasonal Naive (sNaive)** baseline  
  - **Residual-correction model** (Ridge regression on sNaive errors) to leverage only lag ≥ 1 external signals.

---

## Outputs

- `/data/clean/` → normalized, schema-validated data  
- `/artifacts/reports/` → Markdown + PNG + HTML summaries  
- `/models/` → serialized forecasting models (ARIMA/SARIMAX/Ridge)  
- `/results/` → lag-scan tables, correlation maps, Granger outputs, and backtest metrics  

---

## Tech Stack

| Layer | Tools & Libraries |
|-------|-------------------|
| Data | `pandas`, `numpy`, `pyarrow`, `openpyxl` |
| Time Series | `statsmodels`, `pmdarima`, `scipy`, `tsfresh` |
| Visualization | `matplotlib`, `seaborn`, `plotly`, `pandas-styler` |
| ML / Regression | `scikit-learn` |
| Reporting | `jinja2`, `markdown`, `weasyprint` |

---

## Example Insights

- Strong lagged correlations between **"coding for kids"** searches and **Scratch project uploads**, peaking at **+3 months**.  
- Granger causality confirms predictive power of certain interest terms.  
- SARIMAX models incorporating Trends signals outperform pure ARIMA baselines by **12–18% MAPE improvement**.

---

## Vision

By combining **public interest data** with **creative engagement metrics**, Scratch AI Forecast bridges the gap between curiosity and creation — offering insights for educators, policymakers, and digital-literacy initiatives.

---
