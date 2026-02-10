# Air_Quality_Forecasting_Using_Machine_Learning
Air quality forecasting project using regression, MLP, and LSTM models to predict hourly PM10 concentrations in Auckland from 2019–2023 using meteorological and pollution data

This project develops machine learning models to forecast hourly particulate matter concentrations (PM10) in Auckland, New Zealand, using five years (2019–2023) of data from the Environmental Auckland Data Portal. The dataset includes PM10 (target), PM2.5, lagged PM values, gaseous pollutants (NO, NO2), and meteorological variables such as air temperature, relative humidity, wind speed/direction, and solar radiation collected at a single monitoring station.
​

After extensive preprocessing (handling 50k+ missing values, fixing timestamps, removing negative readings, and replacing outliers based on realistic climate ranges), the analysis selects the five most informative predictors of PM10 using Pearson correlation: NO, relative humidity, NO2, air temperature, and wind speed. Exploratory plots show large day‑to‑day variability and frequent PM10 peaks between 2020 and 2023, with mean hourly concentrations around 15.7 µg/m³.
​

The modelling pipeline splits the data into 70% training and 30% testing, then fits baseline and tuned Multi‑Layer Perceptron (MLP) regressors and a Long Short‑Term Memory (LSTM) network. A single‑layer MLP with 25 neurons is optimized over learning rate, followed by a two‑layer MLP where the 25 neurons are redistributed across layers to minimize MSE. For the LSTM, the architecture is tuned over epochs, batch size, and hidden units using repeated runs (30 per setting) with Adam optimization to find the best combination (5 epochs, batch size 32, 120 neurons).
​

Final results show that both models track the overall PM10 trend but struggle with extreme spikes; the tuned two‑layer MLP achieves RMSE ≈ 2.66 and R² ≈ 0.59, while the LSTM achieves RMSE ≈ 2.59 and R² ≈ 0.69 on the test set, indicating better performance and stronger capture of temporal dependencies. This repository contains the preprocessing scripts, feature‑selection notebooks, MLP and LSTM training code, and plotting utilities to reproduce the experiments and extend them to other stations or pollutants.


Project overview
Brief context: PM2.5/PM10 and health.

Location and period: Auckland, 2019–2023.

Goal: predict hourly PM10 (and/or PM2.5) using regression, MLP, LSTM.


Data description
Source (Environmental Auckland Data Portal).

Station used (Penrose or Takapuna).

Main variables: PM10/PM2.5, lags, NO, NO2, AQI, temperature, humidity, wind speed/direction, solar radiation.

Time resolution and units.
