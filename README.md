# Used-car-price-prediction

The goal of this analysis is to predict the price of a used car depending on its specification. 

### Data preprocessing: 
Starting from cleaning, exploring the descriptive statistics of the variables and dealing with missing values.
It's very useful to see the probability distribution of each feature. And for the optimal results I’ll be looking for normal distributions, rather than exponential. 
Looking at the description it is visible that there are a few outliers so the easiest way to deal with that is to remove some of the observations.
### Checking the OLS assumptions:
As the distribution of the dependent variable ‘price’ is not normally distributed and its relationship with other features is not linear. Therefore, log-transformation is the best way to deal with this issue.
As one would suspect, year and mileage can be correlated and the best way to check for multicollinearity is to use statsmodels VIF.
### Linear regression model:
In fact, this is a log linear regression as the dependent variable is the logarithm of "price".
Looking at the regression graph, it can be seen that the points are roughly situated along the 45 ° line.
The residuals appear to be a normal distributed with a mean of 0 and the distribution is fairly symmetrical. Perhaps a slightly longer tail can be observed located in the lower half-space, suggesting that these predictions may overestimate the target.
R-squared result is around 0.86 therefore the model is explaining 86% variability of the data.
Standardised weights are comparable and the bigger the weight the bigger the impact. Positive weight shows that as the value of the feature increases so do the log-price and the price respectively, for example the bigger horsepower number the higher the price. Negative weights behave exactly opposite. 
Interpreting the dummy variable is slightly different. They are qualitative factors and dropped values are the benchmark used for comparison. 
### Testing:
The model performed quite well with the min difference% - 0.000324, however the max difference% -  281.851452 is not that ideal. The percentiles show that for most of the predictions it came relatively close.

Final conclusions:
Revising the dataset it can be told which types of observation make good predictions and which are far off from the observed values. At the bottom of the data set there are a few predictions which are extremely low. The features used in the model scored on average quite well at predicting the price, apart from these last samples. The residuals for all these outliers are negative therefore their predictions are higher than the targets.

Data reference:
autoscout24-germany-dataset from [Kaggle](https://www.kaggle.com/ander289386/cars-germany)
