### 28-01-2026: Dummy Variable Encoding & Feature Selection

#### Key Concepts
* **Dummy Variable Encoding:** With a fundamental understanding that the variables used in building regression models have to be in numeric form, it then makes perfect sense to convert categorical variables such as gender (male vs female) into values like 0 and 1, representing each category of gender. The Pandas method used for this is `get_dummies`, which transforms the text found in columns containing categorical variables into numbers by creating a column for each new category (eg Gender_Male & Gender_Female).

* **Feature Selection:** Feature selection simply involves eliminating some input variables, potentially leading to a reduction in the computational cost of modeling and improvement in the performance of the model. Common approaches include correlation analysis, statistical significance (p-values) AND variance thresholds.

#### New Python Libraries/Modules used today:
*  `MinMaxScaler` from `sklearn.preprocessing` for normalising data: putting all features on the same scale before checking variance.
*  `VarianceThreshold` from `sklearn.feature_selection` to automatically drop features that don't change enough (low variance) to be useful.

#### Notes:
* **The "Dummy variable trap":** The creation of two columns such as `Gender_Male` and `Gender_Female` causes perfect correlation between both columns. This is solved by dropping one column using `drop_first=True`