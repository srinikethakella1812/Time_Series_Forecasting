# U.S. Airline Passenger Demand Forecasting

Analysis of U.S. airline passenger demand using monthly data derived from the Bureau of Transportation Statistics (BTS) T100 dataset. It combines exploratory time-series analysis, feature engineering, and forecasting model comparisons in a Jupyter notebook.

## Project workflow

The [`Demand_Fcst.ipynb`](./Demand_Fcst.ipynb) notebook walks through:

- Downloading T100 data from the [BTS TranStats website](https://www.transtats.bts.gov/DL_SelectFields.aspx?gnoyr_VQ=FIL&QO_fu146_anzr=) for the configured years (currently 2022–2025), then combining the downloaded files.
- Cleaning and summarizing the data, aggregating passenger counts monthly, and exploring trends, seasonality, and categorical patterns.
- Assessing the time series with additive decomposition, autocorrelation plots, and the Augmented Dickey-Fuller test.
- Engineering time-series and categorical features.
- Comparing naive, moving-average, seasonal-naive, ARIMA, SARIMA, multivariate regression, and Random Forest forecasts over a seven-month holdout period.
- Evaluating forecasts with MAE, RMSE, MAPE, and MASE.

## Interactive Tableau dashboard

Explore the results in the [Demand_Fcst Tableau Public dashboard](https://public.tableau.com/app/profile/sriniketh.akella5434/viz/Demand_Fcst/EDA). It contains two views:

- **EDA** — interactive views of overall and year-by-year passenger trends, seasonal demand, and passenger demand across airline and other categorical dimensions.
- **Modeling** — actual-versus-forecast comparisons and model performance charts for MAE, RMSE, MAPE, and MASE. Use the dashboard controls to explore forecast series.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- Microsoft Edge (needed for the notebook's automated data-download step)

Install the notebook's Python dependencies:

```bash
python -m pip install pandas numpy matplotlib seaborn statsmodels scikit-learn selenium
```

Selenium Manager obtains a compatible Edge WebDriver automatically. No local WebDriver path needs to be configured.

## Run the notebook

1. Clone or download this repository.
2. Install the dependencies listed above.
3. Open `Demand_Fcst.ipynb` from the repository root.
4. Run the cells in order. The extraction cells use Selenium and Edge to download the data.

The notebook creates `data/t100/` automatically. If you cannot run browser automation, place the combined source CSV at `data/t100/data_t100.csv` and start with the data-loading/analysis section.

## Data and generated files

Downloaded BTS archives, the combined input dataset, and analysis exports are stored locally in `data/t100/`. The notebook writes:

- `data_t100.csv` — combined downloaded source data
- `EDA_data.csv` — prepared data used for exploratory analysis
- `Act_Fcst_data.csv` — actual passenger counts and model forecasts
- `Model_perf.csv` — forecast model performance metrics

The `data/` directory is excluded from Git, so downloaded source data and generated outputs are not included in this repository. Run the notebook to generate them locally.

## Data source

U.S. Department of Transportation, Bureau of Transportation Statistics (BTS), TranStats T100 data. Data availability and the latest published periods are determined by BTS.
