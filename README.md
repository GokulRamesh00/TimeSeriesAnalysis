## Project Title: Time Series Analysis & Forecasting of Airline Passengers  
**Dataset:** international-airline-passengers.csv  
**Objective:** To forecast airline passenger count using different time series models and determine the best approach based on statistical evaluation metrics.

---

## 1. Steps in the Analysis

### 1.1 Data Preprocessing
- Converted data into time series format.
- Checked for missing values and performed statistical analysis.

### 1.2 Exploratory Data Analysis
- **Time Series Plots**: Visualized trends, seasonality, and patterns.
- **Density Plots**: Checked data distribution.
- **Seasonal Decomposition**: Identified components (trend, seasonal, residual).

### 1.3 Stationarity Testing
- **Dickey-Fuller test**: Conducted to check stationarity.
- **Transformations Applied**: Log transformation and differencing to stabilize variance.

### 1.4 Model Selection
- **ARIMA Model**: Evaluated based on RMSE.
- **SARIMA Model**: Included seasonality and outperformed ARIMA.
- **Auto ARIMA**: Automated parameter selection for best configuration.
- **Prophet Model**: Used for trend and seasonality-based forecasting.

### 1.5 Evaluation Metrics
- **Root Mean Square Error (RMSE)**
- **Mean Squared Error (MSE)**
- **R-squared Score**
- **Akaike Information Criterion (AIC)** (for model selection)

---

## 2. Model Comparison

The table below summarizes the performance of each model based on key evaluation metrics:

| **Model**                 | **Order/Configuration**      | **AIC**  | **RMSE**  | **MSE**  | **R² Score** |
|---------------------------|-----------------------------|---------|---------|---------|------------|
| **ARIMA** (1,1,1)        | (1,1,1)                     | 987.28  | 109.90  | 12077.74| 0.427      |
| **Auto ARIMA**           | (2,1,2)                     | 936.76  | 3891.50 | Large Error (Issue with transformation) | 0.335 |
| **SARIMA** (Best Model)  | (3,1,3)(1,1,1,12)           | 682.47  | **23.82** | **567.57** | **0.907** |
| **Tuned SARIMA**         | (0,1,1)(1,1,1,6)            | 682.47  | 27.96   | 781.21  | 0.872      |
| **Prophet Model**        | Automatic trend & seasonality | N/A     | 29.91   | 893.65  | 0.812      |

---

## 3. Best Model Selection

- **SARIMA(3,1,3)(1,1,1,12) was the best-performing model** due to:
  - **Lowest RMSE (23.82)** indicating better forecast accuracy.
  - **Lowest AIC (682.47)** showing optimal model fit.
  - **Highest R² Score (0.907)** proving strong explanatory power.
  - Successfully captured **seasonality and trend components**, which ARIMA alone could not.

- **Auto ARIMA produced incorrect results due to a transformation issue**, leading to unusually high RMSE values.
- **Prophet performed reasonably well but did not outperform SARIMA.**

---

## 4. Requirements
- **Python 3.12+**
- **Libraries Used:**
  - `numpy`, `pandas`, `matplotlib`, `seaborn`
  - `statsmodels`, `pmdarima`, `prophet`
  - `sklearn.metrics`

---

## 5. Usage
1. Run `TSA.ipynb` step by step.
2. Modify the **train-test split** if needed.
3. Use `evaluate_forecast(y_true, y_pred)` for model evaluation.

---

## 6. Conclusion
- **SARIMA model is the recommended model** for forecasting airline passengers due to:
  - **Lowest error metrics and best model fit.**
  - **Handling of seasonality and trend better than ARIMA.**
  - **Higher accuracy than Auto ARIMA and Prophet.**

