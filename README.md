# PMD-temp-prediction-2025-
# Temperature Prediction Using Prophet

This repository contains a Python implementation for temperature prediction using Facebook's Prophet library. The project demonstrates how to build, tune, and evaluate a time series forecasting model to predict temperature based on historical data.

---

## Table of Contents
1. [Overview](#overview)
2. [Features](#features)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Dataset](#dataset)
6. [Model Tuning](#model-tuning)
7. [Evaluation Metrics](#evaluation-metrics)
8. [Cross-Validation](#cross-validation)
9. [Contributing](#contributing)
10. [License](#license)

---

## Overview

Time series forecasting is a critical task in many domains, including weather prediction, finance, and resource planning. This project uses **Prophet**, an open-source forecasting tool developed by Facebook, to predict future temperatures based on historical data. Prophet is designed to handle seasonality, trends, and holidays, making it a powerful tool for time series forecasting.

---

## Features

- **Data Preprocessing**: Clean and prepare time series data for modeling.
- **Prophet Model**: Build and tune a Prophet model for temperature prediction.
- **Custom Seasonality**: Add custom seasonality components (e.g., monthly, weekly).
- **Cross-Validation**: Evaluate model performance using time series cross-validation.
- **Evaluation Metrics**: Calculate MAE, MSE, and RMSE to assess model accuracy.

---

## Installation

To run this project, you need to install the required Python libraries. Follow the steps below:

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/temp-prediction.git
   cd temp-prediction
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

   Alternatively, you can install the libraries manually:
   ```bash
   pip install pandas numpy scikit-learn prophet
   ```

---

## Usage

1. **Prepare Your Data**:
   - Ensure your dataset is in CSV format with two columns:
     - `ds`: The date or timestamp (in `YYYY-MM-DD` or `YYYY-MM-DD HH:MM:SS` format).
     - `y`: The temperature value to be predicted.

2. **Run the Script**:
   - Update the file paths in the script to point to your dataset.
   - Run the Python script:
     ```bash
     python temp_prediction.py
     ```

3. **View Results**:
   - The script will output the following:
     - Forecasted temperatures for the specified future period.
     - Evaluation metrics (MAE, MSE, RMSE).
     - Cross-validation performance metrics.

---

## Dataset

The dataset used in this project should contain historical temperature data with the following columns:
- `ds`: The date or timestamp.
- `y`: The temperature value.

Example dataset format:
| ds         | y    |
|------------|------|
| 2023-01-01 | 12.5 |
| 2023-01-02 | 13.0 |
| 2023-01-03 | 14.2 |

You can use your own dataset or download publicly available weather data from sources like [NOAA](https://www.ncdc.noaa.gov/) or [Kaggle](https://www.kaggle.com/).

---

## Model Tuning

The Prophet model can be tuned to improve its performance. Key parameters include:
- `changepoint_prior_scale`: Controls the flexibility of the trend.
- `seasonality_prior_scale`: Controls the strength of seasonality.
- `holidays_prior_scale`: Controls the influence of holidays (if applicable).

Example:
```python
m = Prophet(
    changepoint_prior_scale=0.05,
    seasonality_prior_scale=10.0,
    holidays_prior_scale=10.0,
    weekly_seasonality=True,
    yearly_seasonality=True,
    daily_seasonality=False
)
```

You can also add custom seasonality:
```python
m.add_seasonality(name='monthly', period=30.5, fourier_order=5)
```

---

## Evaluation Metrics

The model's performance is evaluated using the following metrics:
- **MAE (Mean Absolute Error)**: The average absolute difference between predicted and actual values.
- **MSE (Mean Squared Error)**: The average squared difference between predicted and actual values.
- **RMSE (Root Mean Squared Error)**: The square root of MSE, providing a measure of the model's error in the same units as the target variable.

Example output:
```
MAE: 1.23
MSE: 2.34
RMSE: 1.53
```

---

## Cross-Validation

Prophet provides built-in cross-validation functionality to evaluate the model's performance over different time horizons. The `cross_validation` function splits the data into training and testing sets, allowing you to assess how well the model generalizes to unseen data.

Example:
```python
df_cv = cross_validation(m, initial='730 days', period='180 days', horizon='365 days')
df_p = performance_metrics(df_cv)
print(df_p)
```

---

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these steps:
1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Commit your changes.
4. Submit a pull request.

Please ensure your code follows the project's style and includes appropriate documentation.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [Facebook Prophet](https://facebook.github.io/prophet/) for the open-source forecasting tool.
- [scikit-learn](https://scikit-learn.org/) for evaluation metrics.
- [pandas](https://pandas.pydata.org/) for data manipulation.

---

For questions or feedback, please open an issue or contact the repository owner.

---

**Happy Forecasting!** 🌡️📈
