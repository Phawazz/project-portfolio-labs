## Bike Sharing Demand: 0.437 RMSLE with Random Forest

### Project Overview
Following a deep-dive EDA, this phase of the project focuses on the machine learning pipeline for the Kaggle Bike Sharing Demand competition. By implementing a Random Forest Regressor and strategically transforming the target variable, I achieved an **RMSLE of 0.43762** on the global leaderboard.

### Technical Stack
- **Environment**: VS Code (Jupyter Notebook).
- **Libraries**: `Pandas` & `NumPy` (Data Manipulation) & `Scikit-learn` (Modeling).

### The Strategy
While following baseline frameworks, I made several critical adjustments to improve model generalization:
- **Temporal Feature Engineering:** Extracted **hour**, **month**, **year**, and **dayofweek** from raw datetime strings to capture the "commuter pulse" identified during EDA.
- **Log-Transformation (np.log1p)**: This was the main stuff in this little project. By predicting the log of the count rather than the raw value, I aligned the model with the competition’s RMSLE evaluation metric, effectively smoothing out high-demand outliers.
- **Validation Strategy**: Implemented a 20% hold-out validation set to act as a "local leaderboard," allowing me to verify my RMSLE score before final submission.

### Final Results
- **Model**: Random Forest Regressor
- **Validation RMSLE:** 0.3037
- **RMSLE on Kaggle:** 0.43762