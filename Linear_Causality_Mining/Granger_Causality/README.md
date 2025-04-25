# Granger Causality in Causality Mining

## 📈 What is Granger Causality?

**Granger Causality** is a statistical hypothesis test to determine whether one time series can forecast another. It assumes that if variable **X** provides statistically significant information about future values of variable **Y**, then **X Granger-causes Y**.

> ⚠️ Note: Granger causality implies a predictive relationship, not true causation.

---

## 🔍 How It Works

For two time series \( X_t \) and \( Y_t \), Granger Causality tests whether:

\[
Var(Y_t | Y_{t-1}, ..., Y_{t-p}) > Var(Y_t | Y_{t-1}, ..., Y_{t-p}, X_{t-1}, ..., X_{t-p})
\]

If adding past values of \( X \) improves the prediction of \( Y \), then \( X \) Granger-causes \( Y \).

---

## 🧪 Implementation Steps

1. **Make series stationary** (e.g., differencing if needed).
2. **Determine lag length** using information criteria (AIC/BIC).
3. **Fit a VAR (Vector Autoregression) model**.
4. **Conduct Granger causality test**.

### Python Example

```python
from statsmodels.tsa.stattools import grangercausalitytests

# 'data' is a pandas DataFrame with columns 'Y' and 'X'
results = grangercausalitytests(data[['Y', 'X']], maxlag=4, verbose=True)
```

---

## 💡 Application in Causality Mining

Granger Causality is widely used in:

- **Time Series Causal Discovery**: Learning directional influence between variables.
- **Process Mining**: Analyzing business event logs for causal flow.
- **Anomaly Root Cause Analysis**: Tracing upstream events that predict failures or anomalies.

---

## 📌 Limitations

- Assumes **linearity**.
- Requires **stationary** data.
- Cannot detect **instantaneous effects**.
- Only suitable for **time-indexed** data.

---

## 🔧 Useful Libraries

- [statsmodels](https://www.statsmodels.org/): Native Granger test.
- [tigramite](https://jakobrunge.github.io/tigramite/): Advanced causal analysis for time series.
- [causal-learn](https://github.com/py-why/causal-learn): General causal discovery toolkit.

---

## 📚 References

- Granger, C. W. J. (1969). "Investigating Causal Relations by Econometric Models and Cross-spectral Methods."
- Statsmodels Documentation: https://www.statsmodels.org/
- Tigramite: https://jakobrunge.github.io/tigramite/

# 💻 Demonstration Code (Google Colab Ready)

The following code demonstrates Granger Causality using synthetic data.
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.stattools import grangercausalitytests, adfuller

# Step 1: Generate synthetic data
np.random.seed(42)
n = 200
X = np.random.normal(size=n)
Y = np.zeros(n)
for t in range(2, n):
    Y[t] = 0.5 * Y[t-1] + 0.4 * X[t-2] + np.random.normal()
data = pd.DataFrame({'Y': Y, 'X': X})

# Step 2: Visualize the time series
data.plot(title='Synthetic Time Series: X and Y')
plt.xlabel("Time")
plt.ylabel("Value")
plt.show()

# Step 3: Test for stationarity using ADF
print("\n== ADF Test ==")
def adf_test(series, name):
    result = adfuller(series)
    print(f'ADF Statistic for {name}: {result[0]:.3f}')
    print(f'p-value: {result[1]:.3f}\n')
adf_test(data['X'], 'X')
adf_test(data['Y'], 'Y')

# Step 4: Perform Granger Causality Test
print("\n== Granger Causality Test ==")
grangercausalitytests(data[['Y', 'X']], maxlag=4, verbose=True)
```

# Step 1: Generate synthetic data
np.random.seed(42)
n = 200
X = np.random.normal(size=n)
Y = np.zeros(n)
for t in range(2, n):
    Y[t] = 0.5 * Y[t-1] + 0.4 * X[t-2] + np.random.normal()
data = pd.DataFrame({'Y': Y, 'X': X})

# Step 2: Visualize the time series
data.plot(title='Synthetic Time Series: X and Y')
plt.xlabel("Time")
plt.ylabel("Value")
plt.show()

# Step 3: Test for stationarity using ADF
print("\n== ADF Test ==")
def adf_test(series, name):
    result = adfuller(series)
    print(f'ADF Statistic for {name}: {result[0]:.3f}')
    print(f'p-value: {result[1]:.3f}\n')
adf_test(data['X'], 'X')
adf_test(data['Y'], 'Y')

# Step 4: Perform Granger Causality Test
print("\n== Granger Causality Test ==")
grangercausalitytests(data[['Y', 'X']], maxlag=4, verbose=True)

🔍 Explanation of the Code

Synthetic Data Generation: Creates two time series. X is pure random noise. Y is constructed so it depends on its own previous values and previous values of X, making it Granger-caused by X.

Plotting the Series: A line plot of both series is generated to visually inspect how X and Y evolve over time.

ADF Stationarity Test: The Augmented Dickey-Fuller test checks whether the series are stationary. Stationarity is required for the Granger Causality test to be valid.

Running the Test: grangercausalitytests() runs the test across multiple lags (up to 4) and reports statistical values like F-statistics and p-values to determine if X helps predict Y.

Synthetic Data Generation: X is random noise. Y depends on its own past and past values of X, simulating a Granger-causal relationship.

Plotting: Visualizes the generated time series.

ADF Test: Ensures both series are stationary (Granger causality requires stationarity).

Granger Test: Uses statsmodels to determine if past values of X help predict Y.

This script is fully compatible with Google Colab and demonstrates the basic pipeline of Granger Causality testing.

