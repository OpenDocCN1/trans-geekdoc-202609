The first two features with non-zero weights in the Lasso path are temperature ("temp") and the time trend ("days_since_2011").

Now, let us select 5 features:

| Feature | Weight |
|---|---|
| seasonSPRING | -389.99 |
| seasonSUMMER | 0.00 |
| seasonFALL | 0.00 |
| seasonWINTER | 0.00 |
| holidayHOLIDAY | 0.00 |
| workingdayWORKING DAY | 0.00 |
| weathersitMISTY | 0.00 |
| weathersitRAIN/SNOW/STORM | -862.27 |
| temp | 85.58 |
| hum | -3.04 |
| windspeed | 0.00 |
| days_since_2011 | 3.82 |

Note that the weights for "temp" and "days_since_2011" differ from the model with two features. The reason for this is that by decreasing lambda even features that are already "in" the model are penalized less and may get a larger absolute weight. The interpretation of the Lasso weights corresponds to the interpretation of the weights in the linear regression model. You only need to pay attention to whether the features are standardized or not, because this affects the weights. In this example, the features were standardized by the software, but the weights were automatically transformed back for us to match the original feature scales.

# Other methods for sparsity in linear models

A wide spectrum of methods can be used to reduce the number of features in a linear model.

Pre-processing methods:

+   • Manually selected features: You can always use expert knowledge to select or discard some features. The big drawback is that it cannot be automated and you need to have access to someone who understands the data.

+   • Univariate selection: An example is the correlation coefficient. You only consider features that exceed a certain threshold of correlation between the feature and the target. The disadvantage is that it only considers the features individually. Some features might not show a correlation until the linear model has accounted for some other features. Those ones you will miss with univariate selection methods.

Step-wise methods:

+   • Forward selection: Fit the linear model with one feature. Do this with each feature. Select the model that works best (e.g. highest R-squared). Now again, for the remaining features, fit different versions of your model by adding each feature to your current best model. Select the one that performs best. Continue until some criterion is reached, such as the maximum number of features in the model.

+   • Backward selection: Similar to forward selection. But instead of adding features, start with the model that contains all features and try out which feature you have to remove to get the highest performance increase. Repeat this until some stopping criterion is reached.

I recommend using Lasso, because it can be automated, considers all features simultaneously, and can be controlled via lambda. It also works for the logistic regression model for classification.