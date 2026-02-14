# Titanic Survival Prediction (Random Forest Pipeline) 

I honestly just wanted to build a simple Decision Tree to tick off a youtube tutorial I had just watched. However, after checking the data, discussion and the some submissions on Kaggle, I fell down a rabbit hole of production-grade Machine Learning and ended up building a full **Random Forest Pipeline** instead.

This is a complete engineering pipeline that processes raw data, handles missing values, and tunes itself to predict who survived the 1912 Titanic shipwreck.

## The "Why"
I got tired of manually cleaning data as soon as I came across a better way to do this with Python's object-oriented programming which allowed me to create classes and keep re-using them. Therefore, I learnt the advanced stuff: **Custom Transformers** and **Pipelines**. By *inheriting* from Scikit-Learn's `BaseEstimator` & `TransformerMixin`, I built a system that automates the boring parts. Now, the code handles the cleanup logic itself, leaving me to focus on the actual model performance.

## Key Techniques Used
* **Custom Transformers:** Based on a very helpful tutorial I came across, I wrote my own classes (`AgeImputer`, `FeatureEncoder`, and `FeatureDropper`) to clean data inside the pipeline.
* **Scikit-Learn Pipeline:** Raw data goes in, predictions come out.
* **Stratified Shuffling:** Used `StratifiedShuffleSplit` to ensure my training/test split was statistically identical to the real population (just like what's commonly referred to as matching in clinical trials I think).
* **Random Forest Classifier:** Why ask one 'decision tree' when you can ask 100 and choose what majority agree on?
* **GridSearchCV:** Ran an automated experiment to test different hyperparameters and find the "winning" model settings.

## Results
* **Model:** Random Forest (Tuned)
* **Accuracy:** ~78.5% (#2097 rank on kaggle leaderboard for the condition lol)
* **Stratification Check:** verified that the distribution of Survivors, Class, and Sex was identical across Train/Test sets.

## Lessons Learned 
1.  **Pipelines are King:** At first, the `BaseEstimator` and `TransformerMixin` syntax looked scary (I literally zoomed off onto something else other than working for over 30 mins). But once it clicked, I realized how powerful it is to bundle everything into one object.
2.  **Data Leakage is Real:** Learned the hard way that you can't just `fit_transform` on the Test Set. You have to use the "ruler" you built during training.
3.  **Stratification Matters:** Random splitting is dangerous. You need your test set to be a true mirror of reality. There must be same proportion of rich people, gender, and survival status in each set.

---