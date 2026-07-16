Temperature-Sensitive German Load Forecasting
What This Study Asks

This project tests whether Berlin temperature improves weekly German electricity-demand forecasts, or whether the previous year’s demand pattern remains more reliable.

The analysis uses German hourly load data from January 2015 to September 2020. After removing incomplete weeks, 299 weekly observations are retained. The final 104 weeks are used as the test period.

How the Forecasting Was Done

The workflow:

Cleans and aggregates hourly electricity data
Adds Berlin temperature and German holiday information
Creates heating and cooling degree-day features
Checks trend, seasonality and stationarity
Uses chronological training and testing
Compares load-only and weather-aware forecasts
Evaluates all models over the same two-year period
Models Tested

Simple forecasts:

Mean
Naive
Seasonal Naive
Drift

Advanced forecasts:

SARIMA
SARIMAX with temperature
SARIMAX with degree days
SARIMAX with weather and holidays
Gradient Boosting
Hourly LSTM

The SARIMA stage evaluates the required combinations of p, d and q. Gradient Boosting and LSTM models are selected using chronological validation.

Forecast Assessment

The models are compared using:

MAE
RMSE
MASE
sMAPE
Forecast bias
Prediction-interval coverage

Forecasts using actual future temperature are treated as conditional forecasts because those temperatures would not be known at the original forecast date.

Main Result

Seasonal Naive produced the lowest weekly RMSE of 2.988 GW.

Weather engineering improved both SARIMAX and Gradient Boosting. Degree days and holiday variables were more useful than raw temperature alone. However, the weather-aware models still did not outperform Seasonal Naive.

The LSTM learned repeated hourly patterns but produced a higher weekly error than the simpler forecasting methods.

Running the Notebook
Open the notebook in Google Colab or Jupyter Notebook.
Install the required libraries.
Run the cells in order.
Allow the SARIMA search and LSTM training to finish.
Review the generated forecasts, diagnostics and final metrics table.
Python Libraries
pandas
NumPy
Matplotlib
SciPy
statsmodels
scikit-learn
TensorFlow
requests
Final Recommendation

Seasonal Naive is recommended for operational weekly forecasting because it is accurate, transparent and does not depend on unknown future weather.

Weather-engineered Gradient Boosting is useful as a conditional comparison model when reliable temperature forecasts are available.
