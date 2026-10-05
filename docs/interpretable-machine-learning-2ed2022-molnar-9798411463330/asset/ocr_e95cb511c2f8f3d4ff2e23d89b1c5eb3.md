# 4.1 LINEAR REGRESSION

| Weight | SE | |t| |
| (Intercept) | 2399.4 | 238.3 | 10.1 |
| seasonSPRING | 899.3 | 122.3 | 7.4 |
| seasonSUMMER | 138.2 | 161.7 | 0.9 |
| seasonFALL | 425.6 | 110.8 | 3.8 |
| holidayHOLIDAY | -686.1 | 203.3 | 3.4 |
| workingDAYWORKING DAY | 124.9 | 73.3 | 1.7 |
| weathersitMISTY | -379.4 | 87.6 | 4.3 |
| weathersitRAIN/SNOW/STORM | -1901.5 | 223.6 | 8.5 |
| temp | 110.7 | 75.0 | 1.7 |
| hum | -17.4 | 3.2 | 5.5 |
| windspeed | -42.5 | 6.9 | 6.2 |
| days_since_2011 | 4.9 | 0.2 | 28.5 |

> $$\hat{eta}_j = \frac{\hat{eta}_j}{SE(\hat{eta}_j)}$$

Let us examine what this formula tells us: The importance of a feature increases with increasing weight. This makes sense. The more variance the estimated weight has (= less certain we are about the correct value), the less important the feature is. This also makes sense.

# 4.1.2 Example

In this example, we use the linear regression model to predict the number of rented bikes on a particular day, given weather and calendar information. For the interpretation, we examine the estimated regression weights. The features consist of numerical and categorical features. For each feature, the table shows the estimated weight, the standard error of the estimate (SE), and the absolute value of the t-statistic (|t|).

Interpretation of a numerical feature (temperature): An increase of the temperature by 1 degree Celsius increases the predicted number of bicycles by 110.7, while all other features remain fixed.

Interpretation of a categorical feature (“weathersit”): The estimated number of bicycles is -1901.5 when it is raining, snowing or stormy, compared to good weather - assuming that all other features do not change. When the weather is misty, the predicted number of bicycles is -379.4 lower than good weather, given all other features remain the same.

All the interpretations come with the footnote “all other features remain the same”. This is because of the nature of linear regression models. The predicted target is a linear combination of the weighted features. The estimated linear equation is a hyperplane in