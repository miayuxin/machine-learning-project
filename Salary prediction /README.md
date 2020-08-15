# salary-prediction

## Goal 
This project is aim to learn the regularization method, I tried to use Ridge and Lasso Regression to predict salaries for a baseball player.

## Ridge Regression
![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/Ridge%20regression%20.png)

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/alpha_ridge.png)

## Lasso Regression
![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/lasso.png)

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/alpha_lasso.png)


We can see below 9 variables regression coefficients have been shrunk to zero in Lasso model.

That is because the weight (coefficient) of those variables have non correlation with our prediction (salary).

In other words, we can say Lasso shrinks the less important feature’s coefficient to zero thus, removing some feature altogether.

So, this works well for feature (variable) selection in case we have a huge number of features.

- League_N
- NewLeague_A
- cumulative_home_runs

- cumulative_at_bats

- years_experience

- RBI

- Assists

- Division_W

- NewLeague_N

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/coefficient.png)

The specific reasons is below.

![image](https://github.com/miayuxin/machine-learning-project/blob/master/Salary%20prediction%20/image/Lasso%26Ridge.png)

For a 2 dimensional feature space, the diagram with the diamond and cyan colour is Lasso. The diagram with the circle and green colour is Ridge regression. And the elliptical contours around β ̂ are the cost function of linear regression (Residual Sum of Squares - RSS).

As the ellipse expands, the corresponding RSS increases. The estimated value of lasso and ridge is the first point of contact with the restricted area during the continuous expansion of the ellipse under a certain restricted area.

Thus, if there is a certain parameter estimated to be zero, then where should this contact point be? It must be on a certain axis. The diamond (Lasso) has corners on the axes, thus whenever the elliptical region (RSS) hits such point, one of the features completely vanishes.

On the other side, since the restricted area of the Ridge is circular, the real contact point cannot fall on the coordinate axis, and may be infinitely close, but it can never be reached. This is the mathematical interpretation that is not available. So Ridge cannot shrink the parameter to zero, but Lasso can.

## Conclusion

#### Difference between Ridge Regression and Lasso
The important difference between them is how they tackle the issue of multicollinearity between the features.

In Ridge Regression, the coefficients of correlated variables tend be similar, while in Lasso one of them is usually zeroed and the other is assigned the entire impact. Because of this, Ridge regression is expected to work better if there are many large parameters of about the same value, i.e. when most predictors truly impact the response.

Lasso, on the other hand, is expected to come on top when there are a small number of significant parameters and the others are close to zero (e.g., when only a few predictors actually influence the response.)