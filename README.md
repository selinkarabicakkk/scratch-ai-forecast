##Scratch AI Forecast##

-Built a resilient data ingestion and normalization pipeline for messy Excel/CSV with two‑row headers: slugified multilingual column names (Turkish), robust numeric coercion (locale‑aware separators), automatic date inference (year–month/week), long/wide reshaping, frequency alignment to month‑start, and persisted clean artifacts to Parquet/CSV with schema metadata and an auto‑generated Markdown/PNG/HTML report bundle.

-Performed time‑series relationship mining between Google Trends categories/terms and Scratch KPIs using 3‑month moving averages: lagged Pearson/Spearman scans (−12..+12), category/term pivots, heatmaps, momentum (last‑12 slope), and Granger causality with seasonal differencing/log transforms and ADF‑guided differencing; summarized top pairs, lag curves, and platform comparisons with styled exports.

-Delivered forecasting with rigorous evaluation: auto‑ARIMA SARIMA baseline vs SARIMAX with exogenous Trends signals (term selection via lag scans/Granger, 0..6 month lags), held‑out 24‑month tests and rolling‑origin backtests using MAE/RMSE/MAPE, STL decomposition, Ljung–Box residual diagnostics, and a production‑friendly sNaive baseline plus a residual‑correction model (Ridge on sNaive errors) to exploit only lag≥1 external signals.
