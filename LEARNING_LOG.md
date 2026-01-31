### 28-01-2026: Dummy Variable Encoding & Feature Selection

#### Key Concepts
* **Dummy Variable Encoding:** With a fundamental understanding that the variables used in building regression models have to be in numeric form, it then makes perfect sense to convert categorical variables such as gender (male vs female) into values like 0 and 1, representing each category of gender. The Pandas method used for this is `get_dummies`, which transforms the text found in columns containing categorical variables into numbers by creating a column for each new category (eg Gender_Male & Gender_Female).

* **Feature Selection:** Feature selection simply involves eliminating some input variables, potentially leading to a reduction in the computational cost of modeling and improvement in the performance of the model. Common approaches include correlation analysis, statistical significance (p-values) AND variance thresholds.

#### New Python Libraries/Modules used today:
*  `MinMaxScaler` from `sklearn.preprocessing` for normalising data: putting all features on the same scale before checking variance.
*  `VarianceThreshold` from `sklearn.feature_selection` to automatically drop features that don't change enough (low variance) to be useful.

#### Notes:
* **The "Dummy variable trap":** The creation of two columns such as `Gender_Male` and `Gender_Female` causes perfect correlation between both columns. This is solved by dropping one column using `drop_first=True`

### 29-01-2026: Model Persistence

#### Key Concepts
* **Saving & Restoring Models:** Until now, I've always wondered how models are used in production. Do we re-run the entire code file of the model each time we need it for making predictions? Do we keep re-training the models each time we need it? In today's learning, I learnt the right way to do it. Saving a model involves storing its parameters and all information needed to make predictions. The python library used is `Pickle`. 

* **Object Serialisation:** This is the technical term for converting a Python object (whether a list, dictionary or as in this case, a machine learning model) into a file that can either be stored for later use or transmitted over a network. Deserialisation can be done as well, which involves retrieving or loading the file for use (again).

#### New Python Libraries/Modules used today:
*  `Pickle`: The `pickle.dump` function is used to 'dump' the model into a file created with the function `with open ('model_save_path.pkl', 'wb')` where `wb` means **write binary**. our model is serialised into a **byte stream** and hence when being loaded for use again with `pickle.load()`, `rb` meaning **read binary** is used.

#### Notes:
There are 2 key things to take note of.
* Security: Only unpickle files you created yourself or trust 100%. Never load a pickle file from an unknown email attachment as it can execute malicious code.
* Compatibility: Pickle is sensitive to versions. A model saved in one version of Python (or Scikit-Learn) may fail to load in a different version. It saves the structure, not the library code itself.

### 31-01-2026: Scaling & Regularisation
#### Key Concepts
* **Scaling data:** Quite often, our data contain variables with varying magnitudes (e.g., milligrams vs prices). Scaling involves putting all our variables on the same scale. There are two types: **normalisation** and **standardisation**. The former turns all data into values within the range of 0 and 1, while the latter re-scales data such that mean becomes 0 and standard deviation becomes 1. Both use modules `MinMaxScaler` & `StandardScaler` from `sklearn.preprocessing` respectively. Standardising data is also usually a necessary prerequisite for regularisation to ensure penalty terms treat all features equally.

* **Regularisation:** This is a technique for preventing overfitting, which occurs when the model gets very used to the training data, including its noise and outliers, thereby performing very good on training data and poorly on new data. The aim of regularisation is to improve a model's generalisation, its ability to make accurate predictions on new, unseen data. Regularisation is of 2 types: **Lasso (L1)** and **Ridge(L2)**. Both work by adding a penalty term (lambda/alpha) to the loss function based on the model's coefficients.
    * **L1:** LASSO stands for "Least Absolute Shrinkage and Selection Operator". It penalises the absolute values of coefficients, shrinking some to exactly zero, and thus implictly implementing feature selection.
    * **L2:** Ridge penalises the squared values of coefficients, shrinking them close to zero but never to exact zero.

#### New Python Libraries/Modules used today:
*  `Ridge & Lasso` from `sklearn.linear_model`
*  `GridSearchCV` from `sklearn.model_selection`: used for applying cross-validation on ridge regularisation.
*  `LassoCV` from `sklearn.linear_model`: Has a built-in cross-validation and also used for lasso regularisation

#### Notes:
* Pandas is remains critical to the entire workflow! The ability to efficiently inspect, drop and clean data is probably just as important as the modeling itself.