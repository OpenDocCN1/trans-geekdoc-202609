# 4.3 GLM, GAM AND MORE

temperature feature to predict the number of rented bikes. The following figure shows the estimated slope: with the standard linear model, a linear model with transformed temperature (logarithm), a linear model with temperature treated as categorical feature and using regression splines (GAM).

![](bbox=[0.238, 0.212, 0.843, 0.532])

Figure 4.13: Predicting the number of rented bikes using only the temperature feature. A linear model (top left) does not fit the data well. One solution is to transform the feature with e.g. the logarithm (top right), categorize it (bottom left), which is usually a bad decision, or use Generalized Additive Models that can automatically fit a smooth curve for temperature (bottom right).

# Feature transformation

Often the logarithm of the feature is used as a transformation. Using the logarithm indicates that every 10-fold temperature increase has the same linear effect on the number of bikes, by changing from 1 degree to 10 degrees Celsius has the same effect as changing from 0.1 to 1 (sounds wrong). Other examples for feature transformations are the square root, the square function and the exponential function. Using a feature transformation means that you replace the column of this feature in the data with a function of the feature, such as the logarithm, and fit the linear model as usual. Some statistical programs also allow you to specify transformations in the call of the linear model. You can be creative when you transform the feature. The interpretation of the feature changes according to the selected transformation. If you use a log transformation, the interpretation in a linear model becomes: "If the logarithm of the feature is increased by one, the prediction is increased by the corresponding weight." When you use a GLM with a link function that is not the identity function, then the interpretation gets more complicated, because you have to incorporate both transformations