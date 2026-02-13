# Salary Prediction with Decision Trees 

## Project Overview
This project builds a Machine Learning model to predict whether an employee earns more than **$100,000/year** based on their educational and professional background. It serves as a practical application of the **Decision Tree Classifier** algorithm and explores concepts like **Gini Impurity** and **Entropy**.

## Objective
To classify employees into two salary brackets (`<=100k` and `>100k`) based on three categorical features:
- **Company:** Google, Facebook, ABC Pharma
- **Job Role:** Sales Executive, Business Manager, Computer Programmer
- **Degree:** Bachelors, Masters

## Technologies Used
- **Python** (Logic & Scripting)
- **Pandas** (Data Manipulation & Cleaning)
- **Scikit-Learn** (Model Building & Evaluation)
- **Matplotlib** (Decision Tree Visualization)

## Workflow
1.  **Data Loading:** Imported dataset using Pandas.
2.  **Preprocessing:** Used `LabelEncoder` to convert categorical text data into numerical format.
3.  **Model Training:** Trained a Decision Tree Classifier on the processed data.
4.  **Evaluation:** Achieved **80% accuracy** on the test set.
5.  **Visualization:** Plotted the actual Decision Tree logic using Matplotlib to trace the decision path (Root -> Leaf).

## Limitations
- **Small Dataset:** The model was trained on a small, fictitious dataset for learning purposes.
- **Limited Features:** Real-world salary prediction requires more complex features (Years of Experience, Location, Performance).