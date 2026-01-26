# House Prices Prediction (Multiple Linear Regression)

## Project Overview
In this project, I built a Multiple Linear Regression model to predict house prices based on 12 distinct predictor variables (features). The analysis also includes a comparison between standard Ordinary Least Squares (OLS) regression and Regularized regression techniques (Ridge and Lasso) to evaluate model stability and overfitting.

## Tech Stack
* **Python** (Pandas, NumPy)
* **Modeling** (Scikit-Learn, Statsmodels)
* **Regularization** (Ridge, Lasso)
* **Visualization** (Seaborn, Matplotlib)

## Key Findings
Based on the OLS Regression results:
* **Distance Impact:** `Distance_to_CityCenter` has a significant negative coefficient (-3.12), indicating that for every unit increase in distance, the house price drops by approximately 3.12 units.
* **Property Features:** `Bedrooms` (+8.31) and `Bathrooms` (+5.82) showed strong positive correlations with price.
* **External Factors:** Higher `Crime_Rate` negatively impacts price, while `Nearby_Schools` showed a positive relationship.

## Model Evaluation
I evaluated the models using R-squared and Mean Squared Error (MSE).

* **Standard Linear Regression (OLS):**
    * Train R²: 0.694
    * Test R²: 0.533
    * *Observation:* The drop in testing accuracy (0.69 vs 0.53) suggests moderate overfitting in the base model.

* **Regularization (Ridge vs. Lasso):**
    * Both Ridge and Lasso produced nearly identical results to the standard model in this dataset, with Ridge maintaining a slightly higher edge in stability.
    * **Ridge Test R²:** 0.5337
    * **Lasso Test R²:** 0.5335