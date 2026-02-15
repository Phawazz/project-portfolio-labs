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

### 01-02-2026: Model Persistence with Joblib
#### Key Concepts
`Joblib` is an alternative to `pickle` that can also be used for storing and restoring models. Because `Joblib` is generally faster and more efficient than `pickle`, it is preferred for objects with **large NumPy arrays** while Pickle is primarily used for serialisation of general-purpose Python objects.

#### New Python Libraries/Modules used today:
* Functions: Just like in `pickle`, `joblib.dump(model, 'filename.pkl')` to save, and `joblib.load('filename.pkl')` to restore.
* File extensions: `.pkl` or `.joblib` can be used.

#### Notes:
* **Syntax Convenience:** Unlike `pickle` which usually requires a file object (created via `with open(...)`) for safety purposes, joblib can accept the filename string directly, making the code cleaner.

* **Security:** Remains critical. One should never load files that come from untrusted sources as they may contain malicious code.

### 02-02-2026: Introduction to Decision Trees
#### Key Concepts
Decision trees are basically hierarchical models or algorithms that split data based on features. These non-parametric models can predict the value of a target variable by learning decision rules inferred from the training data. Its **main components** include `Root Node`, which refers to the entire dataset, `Decision Nodes`, which are points where the data splits based on a specific feature such as being above or below certain thresholds, and `Leaf/Terminal Nodes`, which refer to the final endpoints where a prediction is made, and no further splits. Lastly, just like in lasso regression, decision trees carries out intrinsic/implicit feature selection as well.

* **Advantages:** Easy to interpret and straightforward for visualization
* **Disadvantages:** They are prone to overfitting, and hence `max_depth` is used to limit the model from learning everything about the training data.

### 03-02-2026: Training a Decision Tree [Regression Tree]
#### Key Concepts
**Recursive Binary Splitting:** Binary implies that the tree will always split into two branches while 'recursive' is a programming term that refers to applying the same logic iteratively to every subset that's being created. 

**The steps:**
* **Step 1:** Starting at the root node, consideration of all possible binary splits. Here, the model looks at every single feature and every possible threshold.
* **Step 2:** Among all possible splits, the tree **selects** the one that gives the lowest Mean Squared Error (MSE) in the child nodes. This ensures that the resulting groups are the most 'pure' (meaning the resulting group has target values similar to each other (low variance)) or 'organized'. 
* **Step 3:** The repeat. At this point following the creation of two branches at each split, the model keeps repeating steps 1 & 2 for the new subsets until a stopping criterion (like `max_depth`) is reached.

### 04-02-2026: Pruning a Decision Tree
#### Key Concepts
Pruning: Just like gardening involves trimming branches to help a plant thrive, pruning in ML involves removing "weak" sections of a decision tree that don't add predictive value. The strategy used here is **Post-Pruning**:

* **Step 1:** Allow the tree to grow to its maximum extent. This intentionally creates a model with **low bias but high variance** (essentially an overfitted model)
* **Step 2:** Systematically cut back the "weakest" branches, the ones that provide little predictive power. This increases the model's stability (lower variance)

##### The Role of Cross-Validation (K-Fold):
So how do we know the branches that are useless? We use cross-validation to test the tree.
* If we cut a branch and the MSE (Mean Squared Error) **increases**, that branch was critical. We keep it.
* If we cut a branch and the MSE **stays the same or improves**, that branch was just noise. We permanently cut it.

#### Notes:
* **The Bias-Variance Tradeoff:** Since an ideal model with low bias (captures patterns in training data effectively) and low variance (generalises perfectly to unseen data) is highly unlikely, **pruning** serves as a strategic exchange. We accept a tiny bit less accuracy on training data (bias) to get a model that works much better on new, unseen data (variance). 


### 10-02-2026: Understanding Key Decision Tree Terminologies
#### Key Concepts

Today, I decided to properly understand the confusing terms behind the decision tree algorithm. While I reviewed a couple of resources online, this [youtube video](https://youtu.be/-W0DnxQK1Eo?si=-7GVEc-tYTIJdWTp) and [article](https://towardsdatascience.com/decision-trees-explained-entropy-information-gain-gini-index-ccp-pruning-4d78070db36c/) proved very helpful, explaining directly from first principles while also directly applying the mathematical equations to a fictitious dataset.

The core concepts are **Gini Impurity**, **Entropy**, and **Information Gain**. These are the metrics the algorithm uses to decide "Where do I split?". The goal is always to create child nodes that are more pure or homogenous than the parent. 

* **Gini Impurity:** This is a metric that measures the probability of a random sample being misclassified. It calculates the purity of a node and its values range from 0 (**pure node**) to 0.5 (**maximum impurity/perfectly mixed**). The minimum gini impurity from all available conditions is used as the tree-splitting criteria. Lower values indicate better, more homogenous splits. In algorithms like the scikit-learn `DecisionTreeClassifier`, Gini Impurity is used as the default criterion to select the best split by choosing the feature that results in the lowest weighted Gini impurity. 

* **Entropy & Information Gain:** Entropy is a measure of randomness or disorder. In decision trees, it's a measure of **disorder** or **impurity** in a node. Hence, a **pure node** (entropy = 0) is one in which all samples belong to a single class, while a node with an entropy of 1.0 has the highest possible disorder. The goal at each decision node is that, of all possible splits, the node with the lowest entropy is selected. The reduction in entropy from a parent node to a child node is known as **information gain** and it's calculated by subtracting the weighted average of the children's entropy from the parent's entropy. The higher the information gain, the more "disorder" or "impurity" that has been removed, and the better the split.

#### In Summary:
The best split is selected based on:
* **Lowest Gini Impurity** (also called **Gini Index**) 
* **Lowest Entropy** 
* **Highest Information Gain.** 

### 15-02-2026: Wrapping Up Decision Trees
#### REFLECTION

I have spent over a week learning and working on decision trees with resources outside the scope of my ALX program. By consuming youtube videos and technical articles, I have not only gained a clear understanding of how decision trees work, but also their application in both classification and regression tasks, and their role as the foundation for more robust algorithms like Random Forest. 

To summarise, both classification and regression trees use **recursive binary splitting** to iteratively partition data from the **root node** (where the entire dataset is present) to the **terminal nodes** where the final prediction is made. The splitting criteria, however, differ for both tree types.

In classification trees, the metrics for splitting are Gini impurity, Entropy (and information gain) while in Regression trees, Mean Squared Error (which measures variance) is the main criterion for splitting. Hence, the goal in classification trees is to **maximise purity** at every split while regression aims to **minimize error(variance).**

Lastly, there are two main ways to visualise a decision tree:
1. **The Tree Structure:** A flowchart showing the nodes, branches, and splitting rules (using `plot_tree` from `sklearn.tree`). A pro tip I found here is the use of a semicolon (';') at the end of the line (or assigning the code to a dummy variable) in order to **supress** text output and render the clean plot **ONLY**.
2. **The Decision Surface (or Step Function):** A plot showing how the model partitions the feature space into distinct regions. For regression, this looks like a **step function** (staircase) because the prediction remains constant within each leaf node.