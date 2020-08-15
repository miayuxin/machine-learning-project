# customer-transaction-prediction

## Goal 
Use logistic regression to predict a consumer’s propensity to purchase products.

## Grid Search
To increase the accuracy score, I used the Grid Search with 5 folds cross validations to identify the best hyperparameters for running logistic regression model.  
After applying it, the average accuracy score has increased from 90% to 92%.

## Feature Importances
![image](https://github.com/miayuxin/machine-learning-project/blob/master/Customer%20transaction%20prediction/Image/feature%20importances.png)

## Confusion Matrix and AUC score

However, Since I am dealing with imbalanced dataset, the accuracy is not the best metric to use.

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Customer%20transaction%20prediction/Image/imbalanced%20dataset.png)

Thus, I also looked at the confusin matrix and AUC score. 

#### Confusion matrix 
![image](https://github.com/miayuxin/machine-learning-project/blob/master/Customer%20transaction%20prediction/Image/confusion%20matrix.png)

#### AUC Score
![image](https://github.com/miayuxin/machine-learning-project/blob/master/Customer%20transaction%20prediction/Image/ROC.png)