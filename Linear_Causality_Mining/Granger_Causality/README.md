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

