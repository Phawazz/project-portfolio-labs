# Project Portfolio Labs

Documenting the applied data science and machine learning projects completed as part of my **ALX Data Science & Machine Learning specialization**. This repository tracks my progression through core algorithmic implementations, focusing on statistical rigor, clean code, and practical problem-solving.

Open to collaborations and opportunities in machine learning.

---

## Continuous Learning

I keep a detailed log of the fundamentals, technical hurdles, and core concepts (such as tree-splitting criteria and hyperparameter optimization) encountered during these implementations.

* [View my Learning Log](./LEARNING_LOG.md)

---

## Project Showcases

### Classification Models

* **Heart Disease Prediction (k-Nearest Neighbors)**
    * **Focus:** Clinical validity and diagnostic sensitivity. Prioritized high recall (~89.1%) for risk identification. Pipeline includes target-stratified imputation and feature scaling.
    * [View Project](./k-Nearest%20Neighbors/)

* **Wisconsin Breast Cancer Prediction (Logistic Regression)**
    * **Focus:** Predictive oncology diagnostics. Built a clean classification pipeline achieving 99% model accuracy on the test set.
    * [View Project](./Logistic%20Regression/) 

* **Titanic Survival Prediction (Random Forest)**
    * **Focus:** Automated missing data handling and feature engineering by building custom Scikit-Learn transformer classes (BaseEstimator, TransformerMixin). Designed a strict training pipeline with stratified splitting and GridSearch tuning, resulting in a ~78.5% accurate Random Forest model.
    * [View Project](./Random%20Forest%20Reg%20&%20Classifiers/Titanic%20Survival%20Prediction/)

* **Bank Loan Risk Classification (Decision Trees)**
    * **Focus:** Financial risk assessment. Leveraged synthetic data to explore decision node visualization (`plot_tree`), rule extraction, and the handling of categorical risk tiers (Low, Medium, High).
    * [View Project](./Decision%20Trees/Bank%20Loan%20Risk%20Classification/)

* **Salary Prediction (Decision Trees)**
    * **Focus:** Binary salary bracket classification (<=100k and >100k). Applied `LabelEncoder` to process categorical text features and configured a Decision Tree Classifier using Entropy for node splitting, achieving 80% test accuracy.
    * [View Project](./Decision%20Trees/Salary%20Prediction/)

### Regression Models

* **Bike Sharing Demand (Random Forest Regressor)**
    * **Focus:** Predicted continuous rental demand using a Random Forest Regressor. Implemented temporal feature engineering and a log-transformation (np.log1p) on the target variable to optimize for the competition's evaluation metric, achieving a 0.437 RMSLE on Kaggle. (Includes a dedicated [EDA pipeline](./Exploratory%20Data%20Analysis%20[EDA]/)). 
    * [View Project](./Random%20Forest%20Reg%20&%20Classifiers/Bike%20Sharing%20Demand/)

* **House Prices (Multiple Linear Regression)**
    * **Focus:** Predicted house prices across 12 distinct features using Multiple Linear Regression. Evaluated model stability and addressed moderate base-model overfitting by comparing standard Ordinary Least Squares (OLS) against Regularized techniques (Ridge and Lasso).
    * [View Project](./Multiple%20Linear%20Regression/)

* **Student Performance (Simple Linear Regression)**
    * **Focus:** Predicted student performance scores based on study hours. Conducted exploratory data analysis to isolate `hours_studied` as the primary driver, then trained a Simple Linear Regression model yielding an R² of 0.51 and an MAE of 6.62.
    * [View Project](./Simple%20Linear%20Regression/)

---

*Built with Python, Scikit-Learn, Pandas, and NumPy.*