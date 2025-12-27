# StatsForecast

[![CI](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml/badge.svg?branch=main)](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml)
[![Python](https://img.shields.io/pypi/pyversions/statsforecast)](https://pypi.org/project/statsforecast/)
[![PyPi](https://img.shields.io/pypi/v/statsforecast?color=blue)](https://pypi.org/project/statsforecast/)
[![conda-forge](https://img.shields.io/conda/vn/conda-forge/statsforecast?color=seagreen&label=conda)](https://anaconda.org/conda-forge/statsforecast)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://github.com/Nixtla/statsforecast/blob/main/LICENSE)
[![Docs](https://img.shields.io/website-up-down-green-red/http/nixtla.github.io/statsforecast.svg?label=docs)](https://nixtla.github.io/statsforecast/)
[![Downloads](https://pepy.tech/badge/statsforecast)](https://pepy.tech/project/statsforecast)

**StatsForecast** is a lightning-fast forecasting library designed for rigorous statistical and econometric modeling. It offers a comprehensive suite of univariate time series models—including `AutoARIMA`, `ETS`, `CES`, and `Theta`—optimized with `numba` for high-performance computation on large datasets.

## Key Features

*   **Performance:** Built with `numba` compilation for speed, avoiding common bottlenecks found in Python frameworks.
*   **Scalability:** Capable of fitting millions of time series efficiently.
*   **Comprehensive Models:** Includes standard statistical models (ARIMA, ETS) and benchmarking tools.
*   **Compatibility:** Easily integrates with standard data science stacks (Pandas, Polars).

## Installation

Install the latest stable release via pip:

bash
pip install statsforecast


Alternatively, install via conda:

bash
conda install -c conda-forge statsforecast


## Quick Start

The library is designed for simplicity and efficiency. Here is a minimal example to forecast using `AutoARIMA`:

python
import pandas as pd
from statsforecast import StatsForecast
from statsforecast.models import AutoARIMA

# 1. Prepare your dataframe (unique_id, ds, y)
df = pd.DataFrame({
    'unique_id': ['A'] * 24,
    'ds': pd.date_range(start='2020-01-01', periods=24, freq='M'),
    'y': [i + (i % 5) for i in range(24)]
})

# 2. Initialize the StatsForecast object
sf = StatsForecast(
    models=[AutoARIMA(season_length=12)],
    freq='M'
)

# 3. Fit and Predict
sf.fit(df)
forecast_df = sf.predict(h=12, level=[95])

print(forecast_df)


## Documentation

For detailed examples and API references, visit our [Documentation Page](https://nixtla.github.io/statsforecast/).

## Why StatsForecast?

Unlike other libraries that rely on heavy dependencies or slow execution, StatsForecast focuses on raw speed and minimal memory usage. It is the industry standard for applying statistical models to large-scale forecasting problems.