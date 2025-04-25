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
Y, then 
𝑋
X is said to Granger-cause 

Only applicable to time series data.

🔧 Tools/Libraries
statsmodels: Built-in Granger Causality testing.

causal-learn: For more general causal discovery.

Tigramite: Advanced time-series causality analysis using PCMCI and other techniques.

📚 References
Granger, C. W. J. (1969). “Investigating Causal Relations by Econometric Models and Cross-spectral Methods”.

Statsmodels Documentation

Tigramite Causal Discovery Library

