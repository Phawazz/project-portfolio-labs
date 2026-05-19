# Heart Disease Prediction with K-Nearest Neighbors (KNN)

## Project Overview & Data Acquisition
In this project, I used a K-Nearest Neighbors (KNN) classifier to predict the presence of heart disease. Built using the **UCI Heart Disease Dataset**, I prioritised statistical rigor and clinical validity in my entire pipeline, ensuring features like *patient age* are preserved due to their impact on cardiovascular health.

**Clinical Goal:** To maximize diagnostic recall (sensitivity) for identifying heart disease risk, *minimizing* the potential clinical consequence of undetected cardiac pathologies.

## Exploratory Data Analysis (EDA)

* **Visualizing Category Distributions:** Created two grids of annotated count plots to:
    * (1) analyze risk factor frequencies across all categorical attributes, and
    * (2) also analyze the frequencies in both those with and without heart disease.
* **Correlation Matrix Analysis:** Evaluated feature collinearity using a customized correlation threshold of `0.25`. Rather than drops based purely on mathematical multi-collinearity, clinical domain knowledge was applied to retain **Age** as a vital non-negotiable covariate for cardiovascular risk modeling.

## Data Cleansing & Target-Stratified Imputation
* **Structural Outlier Removal:** Isolated and dropped an impossible physiological data entry error where `RestingBP == 0`.
* **Target-Stratified Missing Value Imputation:** Identified 172 missing serum cholesterol values masked as `0`. 
  * *Methodology:* Converted `0` entries to `NaN` so they'd be excluded from median calculations automatically. Applied `groupby('HeartDisease').trasnform()` with `fillna(median)` to impute group-specific medians, ensuring no manual masks or class leakage. 

## Data Preprocessing & Feature Engineering
* **Categorical Encoding:** Applied one-hot encoding to convert clinical indicators (e.g., `RestingECG`, `ST_Slope`) into model-ready numeric arrays.
* **Feature Scaling:** Implemented `MinMaxScaler` to normalize the feature spaces, ensuring distance calculations in the KNN algorithm are not distorted by differences in feature measurement units.

## Model Development & Hyperparameter Tuning
* **Algorithm:** K-Nearest Neighbors (KNN)
* **Optimization:** Executed a structured hyperparameter grid search (`GridSearchCV`) to evaluate neighborhood counts (k) and distance metrics.
* **Optimal Hyperparameters:** `{'metric': 'manhattan', 'n_neighbors': 9}`

## Model Evaluation & Clinical Insights
### **Performance Metrics**
* **Test Set Accuracy:** 83.15%
* **Diagnostic Recall (Sensitivity):** ~89.1%

### **Confusion Matrix Breakdown**
* **True Negatives (Healthy):** 55
* **True Positives (Diseased):** 98
* **False Positives:** 19 
* **False Negatives:** 12 

### **Conclusion**
By altering the standard pre-processing pipeline to mask missing values before calculation, the model avoids structural skew and anchors its geometric distance vectors on genuine clinical profiles. Achieving an **89.1% Recall** ensures that the model operates as a dependable diagnostic decision-support system to safeguard high-risk patients.

---
*Inspired by Dataquest's "Predict Heart Disease with KNN in Python" tutorial on YouTube, with custom modifications to the preprocessing and feature selection pipeline.*