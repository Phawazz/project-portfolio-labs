# Student Performance Prediction

## Project Overview
This project specifically focuses on how hours spent on studying is correlated to the final exam scores of students.  Using a dataset containing information for 150 students, I built a **Simple Linear Regression model** to make these predictions.

## Tech Stack
* **Python** (Pandas, NumPy)
* **Machine Learning** (Scikit-Learn)
* **Visualization** (Seaborn, Matplotlib)

## Key Findings (EDA)
* **Correlation:** `hours_studied` showed the strongest positive correlation with `final_exam_score`.
* **Attendance Percentage:** `attendance_percentage` showed the least impact on the final score in this dataset based on the correlation heatmap.

## Model Evaluation
* **Model Type:** Simple Linear Regression
* **MAE (Mean Absolute Error):** 6.62
* **MSE (Mean Squared Error):** 85.45
* **R² Score:** 0.51
    * **Interpretation:** The model explains approximately 51% of the variance in student scores.