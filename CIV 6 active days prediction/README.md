# Civilization VI Game Active Days Prediction

## Purpose 
Implement multiple regression model and checked for linear regression assumption to predict Civilization VI's active days. 

## Dataset 
The dataset is from 2K Games with 500k data volumn. 

## Feature Engineering
To improve the performance of linear regression model, I constructed the feature engineering to extract features from raw data, and generated 1,244 features.
- Created additional binary columns to encode the presence of a NaT value in the expansion packs and DLC columns.  
(include 2 values: 1 if the variable is NaT, 0 if the variable has a non-Null value.)
- Break apart the date columns and get the year, month, day.
- Number of DLCs or expansion packs owned.
- Created a feature: to find the days from most recent DLC install.

## Check for Linear Assumption
From part 4, we can clearly see that a linear regression model on this CIV6 dataset violates a number of assumptions that cause significant problems, with the interpretation of the model itself.

## Feature Importances
#### Which of your IVs are significant and why?
Please refer to part 6's section "independent variables that are significant (p value < 0.05)".
We see there are 736 predictors(IV) p-values lower than 0.05, which are statistically significant.
On the other hand, there are 508 predictors(IV) that p-values are greater than the usual significance level of 0.05, which are not statistically significant.
Keeping variables that are not statistically significant can reduce the model’s precision.
The reason why p-values lower than 0.05 are significant is because that the p-value for each term tests the null hypothesis that the coefficient is equal to zero (no effect).
A low p-value (< 0.05) indicates that I can reject the null hypothesis.
Conversely, a larger (insignificant) p-value suggests that changes in the predictor are not associated with changes in the response.
In other words, the predictors that have low p-values are likely to be a meaningful addition to my linear regression model, because changes in the predictor's value are related to changes in the response variable.

#### Feature importances of Ridge Regression 
![image](https://github.com/miayuxin/machine-learning-project/blob/master/CIV%206%20active%20days%20prediction/image/feature%20importance.png)


## Conclusion
The R squared value on testing dataset is 0.41, which means 41% of the variability in y (activedays) can be explained by using X (the remaining 1244 independent variables).
The mean square error is 1461.81, which is big as well.
Thus, this R square value is bad, as a low R-squared is most problematic when you want to produce predictions that are reasonably precise (have a small enough prediction interval).
We should use nonlinear regression because linear models are unable to fit the specific curve that these data follow.
