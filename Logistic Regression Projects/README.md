# Breast Cancer Prediction with Logistic Regression

## Project Overview & Data Acquisition
This project implements a binary classification model using **Logistic Regression** to predict whether a breast mass is malignant or benign. The model is trained on the **Wisconsin Breast Cancer Dataset**, which consists of morphological features derived from digitized images of fine-needle aspirates (FNA).

**Clinical Goal:** To provide a high-accuracy diagnostic support tool, prioritizing the identification of malignant cases to ensure patient safety.

## Exploratory Data Analysis (EDA)
* **Data Integrity:** Verified completeness via heatmap; dropped redundant `id` and empty `Unnamed: 32` columns.
* **Class Balance:** Analyzed the distribution of Benign (0) vs. Malignant (1) cases to assess potential bias.
* **Correlation Analysis:** Generated a feature correlation matrix to identify multicollinearity among measurements such as radius, area, and perimeter.

## Data Preprocessing & Feature Engineering
* **Label Encoding:** Converted categorical diagnosis (M/B) to binary format (1/0).
* **Data Partitioning:** Split the dataset into Training (75%) and Testing (25%) sets.
* **Feature Standardization:** Applied `StandardScaler` to normalize the 30 morphological features, ensuring that variables with different units (e.g., area vs. smoothness) contribute equally to the model's decision boundary.

## Model Development & Evaluation
* **Algorithm:** Logistic Regression.
* **Accuracy:** 99%
* **Confusion Matrix:**
    * True Negatives (Benign): 89
    * True Positives (Malignant): 52
    * False Negatives: 2
    * False Positives: 0

## Model Interpretability & Clinical Insights
### **Key Predictors of Malignancy**
The model identified the following features as the strongest indicators of a malignant diagnosis:
1.  **Texture (Worst)**
2.  **Radius (Worst)**
3.  **Area (Worst)**

These findings align with clinical cytopathology, where nuclear pleomorphism (referring to significant variation in the size, shape, and texture of cell nuclei) is a primary marker for cancerous cells.

### **Clinical Conclusion**
Achieving a **Recall of 96%** for malignant cases is a strong result for a screening tool. However, the presence of 2 False Negatives highlights the importance of utilizing this model as a **decision-support system** alongside professional pathological review to minimize the risk of missed diagnoses.