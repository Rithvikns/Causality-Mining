📈 Granger Causality in Causality Mining
What is Granger Causality?
Granger Causality is a statistical hypothesis test for determining whether one time series can predict another. It's based on the premise that a variable X Granger-causes Y if past values of X contain information that helps predict Y beyond what is possible using only past values of Y.

Important: Granger Causality does not imply true causality—only a predictive relationship.

🔍 How It Works
Given two time series, 
𝑋
𝑡
X 
t
​
  and 
𝑌
𝑡
Y 
t
,
.
.
.
,
𝑋
𝑡
−
𝑝
)
Var(Y 
t
​
 ∣Y 
t−1
​
 ,...,Y 
t−p
​
 )>Var(Y 
t
​
 ∣Y 
t−1
​
 ,...,Y 
t−p
​
 ,X 
t−1
​
 ,...,X 
t−p
​
 )
If including past values of 
𝑋
X improves the prediction of 
𝑌
Y, then 
𝑋
X is said to Granger-cause 
𝑌
Y.

🧪 Implementation Steps
Prepare the data: Ensure stationarity using techniques like differencing.

Select lag length: Use AIC/BIC to choose optimal lag.

Fit VAR model (Vector Autoregression).

Perform Granger Causality Test: Use F-tests or chi-square to assess significance.

In Python, using statsmodels:

python
Copy
Edit
from statsmodels.tsa.stattools import grangercausalitytests

# Perform Granger Causality test
results = grangercausalitytests(data[['Y', 'X']], maxlag=4, verbose=True)
💡 Use in Causality Mining
Granger Causality is used in causality mining pipelines for:

Time Series Causal Discovery: Identifying directional dependencies.

Event Log Analysis: Understanding sequences in logs (e.g., business processes).

Root Cause Analysis: Pinpointing drivers behind anomalies or events.

📌 Limitations
Assumes linearity.

Sensitive to non-stationarity.

Cannot detect instantaneous causality.

Only applicable to time series data.

🔧 Tools/Libraries
statsmodels: Built-in Granger Causality testing.

causal-learn: For more general causal discovery.

Tigramite: Advanced time-series causality analysis using PCMCI and other techniques.

📚 References
Granger, C. W. J. (1969). “Investigating Causal Relations by Econometric Models and Cross-spectral Methods”.

Statsmodels Documentation

Tigramite Causal Discovery Library

