# Time-Series Validation (Notebook)

Use information about previous time points to predict a subsequent time point—**correctly**.  
This notebook demonstrates:
- Feature engineering for prices (e.g., `percent_change`)
- Stationarity vs non-stationarity setups (and why it matters)
- Proper **time-aware validation** with `TimeSeriesSplit`
- Baselines: **LinearRegression** and **Ridge**
- Metrics: `r2_score`, `cross_val_score`
- **Bootstrap confidence intervals** for validation scores
- Helpful plots: coefficient bars & predictions vs. actual

---

## Contents
- **Data loading**: CSVs like  
  `chap4_X.csv`, `chap4_y.csv`, `chap4_X_stationarity.csv`, `chap4_y_stationarity.csv`,  
  `non_stationarity_X.csv`, `non_stationarity_y.csv`,  
  `prices_of_four.csv`, `prices_aapl_yhoo_nvda.csv`, `test_y.csv`
- **Utilities**:
  - `percent_change(series)` — simple return-like feature
  - `visualize_coefficients(model, feature_names)`
  - `visualize_predictions(y_true, y_pred)`
  - `my_pearsonr(x, y)` — custom correlation
  - `bootstrap_interval(values, n_boot=1000, ci=0.95)` — metric CI
- **Validation**:
  - `TimeSeriesSplit` (expanding/rolling windows)
  - No shuffling; preserves temporal order
- **Models**:
  - `sklearn.linear_model.LinearRegression`
  - `sklearn.linear_model.Ridge`

---

## Getting Started
```bash
# 1) Create/activate a virtual environment
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# 2) Install dependencies
pip install -r requirements.txt

# 3) Launch Jupyter
jupyter lab   # or: jupyter notebook

# 4) Git Clone
git clone https://github.com/Joe-Naz01/time_series_valid.git
cd time_series_valid
