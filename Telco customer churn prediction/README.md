# The key to driving telecom success: Customer Churn Prediction

## 1. Introduction 

### **Current problems in telco market**
Customer loyalty is the key to profitability in the telecom industry. Because telecom providers manage large fixed infrastructures that must be offset by revenue, customer churn is particularly problematic in this industry. Low switching costs for customers mean that customer loyalty is the only real tool that telecom companies must reduce their churn rates. Connected data, used to improve service quality, dynamically adjust pricing/promotions, and offer personalized content to consumers, enable telecom providers to influence customer loyalty and increase customer retention directly.

### **Purposes of my work**
Using machine learning techniques to develop a churn prediction model which assists telecom operators to predict customers who are most likely subject to churn.

### **Embed insights into the company**
Provide the best model that has achieved the highest AUC value for a company to predict the churn of customers.

## 2. Dataset

This IBM sample dataset has information about telco customers, and if they left the company within the last month (churn).  
The data set contains informations about Telco customers where each row represents a unique customers and the columns are informations regarding customers’services.
There are a total of 7,032 customers in the dataset among which 1,869 left within the last month.
With a churn rate that high, i.e 26.58%, Telco may run out of customers in the coming months if no action is taken.

### **This data set includes information about:**
- Customers who left within the last month – the column is "Churn".
- Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies.
- Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges.
- Demographic info about customers – gender, age range, and if they have partners and dependents.

## 3. Problem definition

- What are the factors influence the customer churn?
- How to predict the churn and customer life-time values?

## 4. Data preprocessing

- There are 11 missing values in “TotalCharges” columns, so I removed all rows with missing values.
- Converted all categorical variables into binary (dummy) variables. 
- Most of features have “yes” or “no” element. Some features have 3 elements and the third element is “No phone service”, which is same meaning as “no”. Therefore, I decided to delete those columns containing “no”, because the columns with “yes” have both 0 and 1.
- Normalized and scaled the total changes and monthly charges. 

  Specifically, it has been standardized to have a mean of 0 and a standard deviation of 1. It is rescaled using the z-score formula. The reason is that the feature of total charges and monthly charges have different scale with other binary variables. Both variables are quantitative (continuous) variables, while the remaining variables are all categorical (binary) variables, with Yes and No distinction. Thus, the data required to be scaled when building the machine learning models.

- Splitted the data into training (80%) and testing (20%) sets. 

## 5. Models development  

I built and compared the classification models for predicting the potential customer churn and applied GridSearch to tune hyperparameters with 5-folds cross validation, including: 

- Logistic Regression with Lasso (L1 regularization) and Ridge (L2 regularization) 
- Decision Tree
- KNN Classifier
- Random Forest

### **5.1 - Logistic Regression with Lasso Regularization**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/Logistic%20regression%20.png)

#### **Confusion matrix**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/cf_lasso.png)

Since the Lasso Regression model with Grid Search method is the best performance model, so we decided to analyze the confusion matrix. Noticed that there are 931 cases are true negative results and 211 are true positive results. However, there are 115 are false positive results (those customers are not leaving the telco company, but the model predicted that they are leaving. 150 of customers should be leaving, but the model thought that they are not. Telco comapny may need to decide which error (type I or type II error) they want to minimize depending on the company's strategy.

The cost for false positive is that the company is spending campaign fees for the customers who are not leaving the company. That is waste of money. The cost of false negative is that the company will lose customers. We can compare the cost of campaign and the cost of losing customers.

Since we don't know the campaign fees in this dataset, we are not going to analyze this part. However, we can do the prediction on customer life-time value to know what the customer value for the company for each customer based on their tenure and total monthly charges. We will focus on this part in the part 7.


### **5.2 - Decision Tree**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/decision%20tree.png)

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/roc_decision%20tree.png)

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/auc%20score_decision%20tree.png)


### **5.3 - KNN Classifier**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/knn.png)

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/knn_roc.png)

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/knn_auc.png)

### **5.4 - Random Forest**

#### **Top 10 important features of Random Forest:**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/rf_feature%20importance.png)

#### **Confusion matrix**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/rf_confusion%20matrix.png)

#### **ROC curve and AUC score**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/rf_auc.png)

#### **Partial dependence plot**

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/pdp.png)


## 6. Conclusion 

#### Customer churn
Random Forest performed best with the highest AUC score 86% among all models.
![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/AUC%20score.png)

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/auc_conclusion%20.png)

## 7. Additional analysis - customer life-time value prediction

To conduct the further analysis to predict the customer life-time value (predict the cost of false negative). The train data consists only customers who already left the telco company, since we can only know tenure value for customers who left the Telco. We added new column named 'life_time_value' ('Tenure' * 'MonthlyCharges'). Noticed that we deleted 'Churn_Yes' and 'tenure' to build the model. We were deleting 'Churn_Yes' column in the dataset, since we need to use this dataset to predict any data (Churn_Yes = 0 or Churn_Yes = 1); however if we only use the data that 'Churn_Yes' equals to 1, the model won't be able to predict life-time value if the dataset also includes that 'Churn_Yes' equals to 0. We were deleting 'tenure', because when we want to predict new data through the model, we don't know the tenure for those customers who are staying with the company. The tenure for those customers is the time length staying with the company up to now, because they are not leaving the company.

#### **Model development**

We were using 3 models to predict the life_time_value and we compared MSE (Mean Squared Error) to get the best performance model. The three models are:

- Random Forest
- Linear Regression (Ridge Regression & Lasso Regression)
- Decision Tree

The result shows that Mean Square Error for Ridge Regression is the lowest, which is 3,378. 
Thus, Ridge Regression is the best model to predict customer life-time value.

![Alt text](https://github.com/miayuxin/machine-learning-project/blob/master/Telco%20customer%20churn%20prediction/Image/MSE.png)

