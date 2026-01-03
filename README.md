````md
# Predicting Air Quality in Dar es Salaam (PM2.5) — Time Series Forecasting

This project builds an end-to-end time-series workflow to extract, clean, analyze, and forecast **hourly PM2.5** readings for **Dar es Salaam** using a MongoDB air-quality dataset and an **AutoRegressive (AutoReg)** model with **walk-forward validation (WFV)**.

---

## Demo / Evidence
- **Project PDF (full notebook export):** `Predicting Air Quality in Dar es Salam.pdf`
- **Repository:** this GitHub repository

> The PDF contains the complete workflow, outputs, and plots (time series, rolling average, ACF/PACF, residual diagnostics, and walk-forward validation predictions).

---

## Problem Statement
Air quality (PM2.5) changes over time and often exhibits autocorrelation and seasonal patterns. The objective is to:

1. Build a clean hourly PM2.5 time series from raw sensor measurements stored in MongoDB.
2. Train and tune an AutoReg model to forecast PM2.5 values.
3. Evaluate performance using Mean Absolute Error (MAE) and walk-forward validation.

---

## Data Source
- **Database:** `air-quality` (MongoDB)
- **Collection:** `dar-es-salaam`
- The project queries PM2.5 readings from the **site with the most total sensor readings** in the Dar es Salaam collection.

---

## Methodology

### 1) Data Wrangling (PM2.5)
A `wrangle()` pipeline is used to prepare the time series:

- Localize timestamps to **Africa/Dar_es_Salaam**
- Filter PM2.5 readings and remove outliers **(PM2.5 > 100)**
- Resample to **hourly mean** PM2.5
- Impute missing values using **forward-fill**
- Output: a single hourly time series `y`

### 2) Exploratory Analysis & Diagnostics
The project includes standard time-series diagnostics:
- PM2.5 time-series plot
- **7-day rolling average** (window = 168 hours)
- **ACF** and **PACF** plots

### 3) Modeling
- Train/test split: **90% train / 10% test**
- Baseline model: mean predictor (MAE baseline)
- Hyperparameter tuning: AutoReg lag `p` tested for **p = 1..30**
- Final model trained with the best-performing `p`
- Residual diagnostics (histogram + ACF of residuals)
- Evaluation: **walk-forward validation (WFV)** over the entire test set

---

## Results (from this run)
- **Baseline MAE:** 4.0531  
- **Best lag (p):** 26  
- **Test MAE (WFV):** 3.97  

> Results can vary slightly depending on the dataset snapshot and runtime environment.

---

## Repository Contents
Typical contents for this repo:
- `Predicting Air Quality in Dar es Salam.pdf` — full exported notebook (recommended artifact for reviewers)
- `*.ipynb` — notebook(s) used to build and evaluate the model (if included)
- `README.md` — this file

---

## How to Reproduce (Optional)
If the notebook(s) are included in this repository, you can reproduce the work locally.

1) **Create and activate a Python environment**
```bash
python -m venv .venv

# Windows:
.venv\Scripts\activate

# macOS/Linux:
source .venv/bin/activate
````

2. **Install dependencies**

```bash
pip install pandas numpy pymongo statsmodels matplotlib plotly scikit-learn
```

3. **Run the notebook**

```bash
jupyter lab
```

Then open the assignment notebook and run cells top-to-bottom.

> **Note:** MongoDB connectivity requires access to the server and the correct host/port settings.

---

## Key Skills Demonstrated

* Data wrangling with MongoDB (NoSQL) using PyMongo
* Time-series preprocessing (resampling, outlier handling, imputation)
* Autoregressive modeling with statsmodels
* Model selection via MAE-based hyperparameter tuning
* Robust evaluation using walk-forward validation
* Clear visualization and statistical diagnostics (ACF/PACF, residual checks)

---

## Author

Nouhan Doumbouya

```
::contentReference[oaicite:0]{index=0}
```
