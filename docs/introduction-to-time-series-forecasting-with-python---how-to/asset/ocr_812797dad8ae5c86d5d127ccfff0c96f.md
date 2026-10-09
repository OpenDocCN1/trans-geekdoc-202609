![](bbox=[0.2, 0.14, 0.82, 0.5])

Figure 22.4: Line plot of the persistence forecast (red) on the Minimum Daily Temperatures dataset (blue).

# 22.7 Autoregression Model

An autoregression model is a linear regression model that uses lagged variables as input variables. We could calculate the linear regression model manually using the LinearRegression class in scikit-learn and manually specify the lag input variables to use. Alternately, the Statsmodels library provides an autoregression model that automatically selects an appropriate lag value using statistical tests and trains a linear regression model. It is provided in the AR class$^{5}$. We can use this model by first creating the model AR() and then calling fit() to train it on our dataset. This returns an ARResult object$^{6}$. Once fit, we can use the model to make a prediction by calling the predict() function for a number of observations in the future. This creates a 17-day forecast, which is different from the persistence example above. The complete example is listed below.

```
```
# create and evaluate a static autoregressive model
from pandas import read_csv
from matplotlib import pyplot
```
```

+   5. http://statsmodels.sourceforge.net/develop/generated/statsmodels.tsa.ar_model.AR.html
6. http://statsmodels.sourceforge.net/develop/generated/statsmodels.tsa.ar_model.ARResults.html