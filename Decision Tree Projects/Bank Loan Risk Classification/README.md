# Decision Tree Loan Risk Classifier 

### Background
In a banking environment, the "Explainability" of a model is just as important as its accuracy. This project simulates a bank's risk assessment process, where a Decision Tree is tasked with classifying loan applicants into three risk categories (`Low`, `Medium`, and `High`) based on synthetic features.

### Tech Stack
- **Python**
- **Pandas/NumPy**: Data simulation and vectorized logic.
- **Scikit-Learn**: DecisionTreeClassifier and Metrics.
- **Matplotlib**: Model visualization.

### Methodology
- **Synthetic Data Generation**: Created 600 samples with the following features: `Age`, `CreditScore`, `Income`, and `ExistingLoans`.
- **Labeling Logic**: Applied a strict conditional "Ground Truth" where:
  - **High Risk**: Credit Score < 550.
  - **Medium Risk**: Credit Score 550-699.
  - **Low Risk**: Credit Score ≥ 700 + Income ≥ $10,000.
- **Hyperparameter Tuning**: Identified an optimal `max_depth` to prevent overfitting while maintaining 1.0 accuracy (possible here due to the synthetic nature of the rules).

### Key Results
- **Optimal Depth**: The model successfully captured the full rule-set at a depth of 4.
- **Explainability**: Using `plot_tree`, I visualized how the model prioritizes `CreditScore` as the primary decision node, followed by `Income`, exactly as defined in the simulation logic.