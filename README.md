# Formula One Lap Time Predictor
A machine learning project predicting F1 lap times for the 2019 Australian Grand Prix from 'Formula 1 World Championship (1950 - 2024)' a Kaggle dataset by Rohan Rao.

## Methodology & Pipeline
1. **Dataset:** Filtered `raceId = 1010` (2019 Australian Grand Prix) and selected 8 finishing drivers to ensure constant weather and track conditions.
2. **Data Cleaning:** Removed 16 pit-related laps (pit-in and pit-out) and slow outliers (>1.5× driver median lap time) out of 462 total laps.
3. **Feature Engineering:** Calculated `tire_age` (laps elapsed since last pit stop, resetting to 0) to capture tire degradation.
4. **Stint-Based Split:** Used each driver's final stint as test data and earlier stints as training data to avoid temporal data leakage.
5. **Model Evaluation:**
   - **Linear Regression:** Baseline (RMSE: 2.744, MAE: 2.278) vs. Enhanced (RMSE: 1.870, MAE: 1.433)
   - **Random Forest:** Baseline (RMSE: 1.398, MAE: 1.250) vs. Enhanced (RMSE: 1.578, MAE: 1.338)

## Key Findings
Including `tire_age` significantly improved Linear Regression performance (MAE dropped from 2.278s to 1.433s), confirming tire wear as a major linear predictor of lap degradation.
