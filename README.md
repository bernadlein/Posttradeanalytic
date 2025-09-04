# BERNADUS BOLI
# Post-Trade Analytics Portfolio

A professional-grade portfolio project demonstrating **data pipelines, post-trade analytics, data quality checks, and user-facing reporting**. 
Built with Python, SQL (SQLite), and Streamlit—designed to mirror workflows at an investment manager (post-trade analytics & reporting).

> ✅ Ready to clone & run locally. Includes synthetic data if you don't want to fetch market data on day one.

## What this shows
- Ingestion (Yahoo Finance or CSV) → **ETL & validation** → **Signal & order generation** → **Execution simulation** → **Post-trade analytics**
- **Data quality gates**: schema & sanity checks
- **Excel report** generation (for business stakeholders)
- **Streamlit dashboard** for self-serve insights
- **Tests** + **CI** (GitHub Actions)

## Repo structure
```
data/
  raw/               # raw prices (CSV) - includes synthetic_prices.csv
  processed/         # parquet/csv outputs
notebooks/
  01_quickstart.ipynb
src/
  ingest/prices.py
  etl/validate.py
  etl/transform.py
  trades/strategy.py
  trades/execution.py
  analytics/performance.py
  reporting/excel_report.py
  reporting/dashboard_app.py
sql/
  schema.sql
tests/
  test_performance.py
.github/workflows/
  ci.yml
requirements.txt
Makefile
```

## Quickstart
```bash
# 1) Create & activate venv (optional)
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 2) Install
pip install -r requirements.txt

# 3) Run the demo (uses synthetic data by default)
python -m src.ingest.prices --use-synthetic
python -m src.trades.strategy
python -m src.trades.execution
python -m src.analytics.performance --save
python -m src.reporting.excel_report  # creates /data/processed/post_trade_report.xlsx

# 4) Dashboard
streamlit run src/reporting/dashboard_app.py
```

## Use real market data
Set environment variables or pass CLI args:
```bash
python -m src.ingest.prices --tickers AAPL,MSFT,SPY --start 2023-01-01 --end 2024-12-31
```

## Tests & CI
```bash
pytest -q
```
A simple GitHub Actions workflow runs lint/tests on push/PR.

## License
MIT
# Posttradeanalytic
