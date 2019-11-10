# Telecom Churn prediction
"Predict behavior to retain customers. You can analyze all relevant customer data and develop focused customer retention programs." [IBM Sample Data Sets]

### Data
Dataset is available [here](https://www.kaggle.com/blastchar/telco-customer-churn).

### Context
Each row represents a customer, each column contains customer’s attributes described on the column Metadata.

The data set includes information about:
- Customers who left within the last month – the column is called Churn
- Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
- Demographic info about customers – gender, age range, and if they have partners and dependents

### Approach
First, I analyzed the data using plots and basic data manipulation with pandas to find trends and dependencies between features. Then created some new features and validated them using correlation and cross-validation. Finally trained different models and tuned hyperparameters using GridSearch.

### Evaluation Metric
Dataset was imbalanced so [ROC-AUC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) seems to be a good choice. [Accuracy](https://en.wikipedia.org/wiki/Accuracy_and_precision) metric might give a good score but it will be biased towards the majority class.


### Results
RandomForest with ROC-AUC of 0.890303.

### Conclusion
Here we are predicting whether the customer will churn or not. I case of wrong results we expect false positives should be more as compared to false negatives because in real-case scenarios let's say the model predicts that the customer will churn even if he/she won't then we can take certain measures to prevent and ensure that the customer stays. But if our model predicts that the customer will not churn and he/she will churn in the future then it's bad for business. So here RandomForest and CatBoostClassifier win.

**Scores**
- LogisticRegression: 0.861236
- RandomForest: 0.890303
- LightGBM: 0.882556
- CatBoost: 0.855759

Overall **RandomForest** gave the best scores with less false negatives and high recall value.