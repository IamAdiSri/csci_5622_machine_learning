# Bicycle Count Prediction Contest

Submission by Aditya Srivastava (adsr4895@colorado.edu)

## Data Analysis and Feature Engineering

The following steps were performed:
1. The date has been split into three columns for day, month and year
2. The seasons have been converted to numbers
3. The Holiday and Functioning Day features have been binarized
4. The Dew Point Temp field has been dropped from the data due to high correlation with Temperature to avoid a multilcollinearity problem
5. The numerical features, `'Temperature(�C)', 'Humidity(%)', 'Wind speed (m/s)', 'Visibility (10m)', 'Dew point temperature(�C)', 'Solar Radiation (MJ/m2)', 'Rainfall(mm)', 'Snowfall (cm)'` have been scaled using sklearn's Robust scaler.
7. I noticed that the bicycle count is 0 for every row that has Functioning Day as 'No', so I remove those rows during training. Those rows are manually set to 0 during prediction. The model is not made to make predictions on those rows.

# Modeling

The best performing model was the CatBoost model, which performs gradient boosting on decision trees, for which the params were identified using a grid search. It uses the same preprocessing as given above.

I also tried other models including a neural network for which the only additional step was that the categorical features were one-hot encoded, but it performed significantly worse.

[image](leaderboard.png)