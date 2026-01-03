# Air Quality (Nairobi + Dar es Salaam) — MongoDB Time Series Forecasting

## Overview
This project connects to a MongoDB air-quality dataset and builds time-series models to analyze and forecast PM2.5 readings.
Key tasks include data wrangling, resampling, outlier removal, imputation, and AutoReg/ARMA modeling with evaluation via MAE.

## Data Source
- MongoDB Host: 192.44.82.2
- Port: 27017
- Database: air-quality
- Collections used: nairobi, dar-es-salaam

> Note: Connection details are configurable via environment variables.

## Methods (Assignment Highlights)
- Localize timestamps to `Africa/Dar_es_Salaam`
- Filter PM2.5 outliers > 100
- Hourly resampling (mean)
- Missing value imputation (forward-fill)
- Train/test split (90% / 10%)
- Baseline MAE
- Hyperparameter search for AutoReg lags (p = 1..30)
- Walk-forward validation (WFV) on test set

## Results (fill in your actual values)
- Best AutoReg lag (p): __
- Baseline MAE: __
- Test MAE (WFV): __

## How to Run
### 1) Create environment
```bash
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\activate on Windows
pip install -r requirements.txt
