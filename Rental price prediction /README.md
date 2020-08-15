# rental-price-prediction

## Goal

Conduct the regression analysis for predicting the rental prices in Australia, determine whether the square meters influences the rental price. 

## Dataset

The dataset from Australia's current rental pricing.

## Data Cleaning

Before building the models, I conducted below data cleaning:
- Collapse 'nsw', 'Nsw', 'New South Wales' to 'NSW'
- Collapse 'Qld', 'queensland', 'Queensland' to 'QLD'
- Remove the outliers of price

## Summary of findings through EDA

Overall, based on this dataset, Australia can cluster the neighborhood into 3 rent groups: 
1. The most expensive rent price were in Byron Shire Council area, across any property type variables. 
2.  Average rent prices in Australua were in Ballina Shire Council. 
3.  Low rent prices were in Tweed Shire Council.
In addition, high-end pricing in Byron Shire Council is substantially higher, and is the most popular neighborhood (with 2,447 frequency) as compared to other areas as well.

## Machine Learning Models Development

We can see that Lismore City Council and Richmond Valley Council do not have much dataset, and they are clearly do not have linear relationship between price and square meters. Thus. I will exclude these 2 areas when analyzing regression.

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Rental%20price%20prediction%20/Image/Distribution.png)

It's interesting that the rent price clusters the neighborhood into 3 distributions.

Both Tweed Shire Council and Ballina Shire Council are obviously not fit the regression line.

Thus, I will spliting into below 3 groups to build linear regression model, and see each model performance.

- Byron Shire Council
- Ballina Shire Council
- Tweed Shire Council

#### Linear Regression Model for Byron Shire Council

Since the relationship between square meters and price in Byron Shire Council is clearly a exponential distribution, I applied the log transformation to make the later linear regression model performs better.

After log transformation, we can see that the R squared value is 0.95.

(means 95% of the variability in y - price can be explained by using X - square meters), and below scatter plot shows a positive linear relationship between square meters and price in Byron Shire Council as well.

Thus, I consider this model performs well, and can be used to predict price.

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Rental%20price%20prediction%20/Image/Byron%20Shire%20Council.png)

#### Linear Regression Model for Ballina Shire Council

The R squared value is 0.90 (means 90% of the variability in y - price can be explained by using X - square meters), and below scatter plot shows a positive linear relationship between square meters and price in Ballina Shire Council as well.

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Rental%20price%20prediction%20/Image/Ballina%20Shire%20Council.png)

#### XGBoosting Model for Ballina Shire Council

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Rental%20price%20prediction%20/Image/gradient%20boosting.png)
