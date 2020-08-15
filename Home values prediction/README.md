# home-prices-prediction

## Goal

This is my first machine learning project. 
I use this project learning by doing the exploratory data analysis, and developing the machine learning model - Linear Regression. 

I will analyze what factors influence the home prices, and develop a Linear Regression model to predict the home prices. 

## Dataset
This dataset proves the factors that affecting housing price negotiations.

With 80 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa from 2006 to 2010.

Some noise has been added to the actual sales price, thus this price does not match the official records.

I will observe features include construction location, area, grade, quality, type, supporting facilities, construction time, and sale time etc.

## Exploratory Data Analysis

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Home%20values%20prediction/Image/heatmap.png)

Summarize the strong correlation factors with the sales price are:

- OverallQual: overall quality evaluation.
- YearBuilt: original construction date.
- ToatlBsmtSF: basement area.
- 1stFlrSF: first floor area.
- GrLiveArea: above grade (ground) living area square feet.
- FullBath: full bathrooms above grade.
- TotRmsAbvGrd: total rooms above grade (does not include bathrooms).
- GarageCars: size of garage in car capacity.
- GarageArea: size of garage in square feet.

On the other hand, I see 
- OverallQual and GrLivArea have a strong linear relationship with SalePrice.
- GarageCars and GarageArea are also strongly correlated with SalePrice. While we can see that actually GarageCars have a strong linear relationship with GarageArea with 0.88 matrix. Thus, we can just select one higher correlation variable: GarageCars.
- Similarly, TotalBsmtSF and 1stFlrSF have strong correlation, so I picked the TotalBsmtSF one. (TotalBsmtSF means the total square feet of basement area, 1stFlrSF means the first Floor square feet.)

## Data Normalization

After using the log transformation to normalize our target value - SalePrice, the distribution looks like below. 

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Home%20values%20prediction/Image/data%20cleaning.png)

## Linear Regression Model Performance

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Home%20values%20prediction/Image/result.png)