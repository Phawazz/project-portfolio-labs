# Bike Sharing Demand: From EDA to 0.43 RMSLE

## Project Overview
In this project, I worked on the bike sharing demand competition on kaggle, using the `RandomForestRegressor` model for predictions. In the Exploratory Data Analysis (EDA) of this dataset earlier shared under the EDA section of this repo, I carried out analysis and visualisations to track how weather, time of the day, and user type move the needle on urban cycling demand. What started as a tutorial-follow evolved into an optimized workflow where I improved the data processing and hit an **RMLSE of 0.43762** on the Kaggle Leaderboard.

## Technical Stack
- **Environment**: VS Code (Jupyter Notebook).
- **Stack**: `Pandas`, `NumPy`, `Seaborn`, `Matplotlib`, `Scikit-learn`.
- **Key Move**: Switched from raw count prediction to **Log-Transformation** (using `np.log1p`) to align with the competition's RMSLE metric.

## Results
- **Model**: Random Forest Regressor.
- **Final Score**: 0.43762 (Kaggle Public/Private)
