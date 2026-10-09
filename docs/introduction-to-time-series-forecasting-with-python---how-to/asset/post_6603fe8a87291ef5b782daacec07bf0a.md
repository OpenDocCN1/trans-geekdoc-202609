
## 22.5. Autocorrelation Plots

Running the example shows the swing in positive and negative correlation as the temperature values change across summer and winter seasons each previous year.

![](img/da419ed7447ef051ee9d00167b7274cf_203_0.png)

Figure 22.2: Autocorrelation plot of the Minimum Daily Temperatures dataset with pandas.

The Statsmodels library also provides a version of the plot in the plot_acf() function⁴ as a line plot.

```python
# autocorrelation plot of time series
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.graphics.tsaplots import plot_acf
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
plot_acf(series, lags=31)
pyplot.show()
```

Listing 22.5: Create an autocorrelation plot of the Minimum Daily Temperatures dataset with Statsmodels.

In this example, we limit the lag variables evaluated to 31 for readability.

⁴ http://statsmodels.sourceforge.net/devel/generated/statsmodels.graphics.tsaplots.plot_acf.html

![](img/da419ed7447ef051ee9d00167b7274cf_204_0.png)

Figure 22.3: Autocorrelation plot of the Minimum Daily Temperatures dataset with Statsmodels.

Now that we know how to review the autocorrelation in our time series, let’s look at modeling it with an autoregression. Before we do that, let’s establish a baseline performance.

## 22.6 Persistence Model

Let’s say that we want to develop a model to predict the last 7 days of minimum temperatures in the dataset given all prior observations. The simplest model that we could use to make predictions would be to persist the last observation. We can call this a persistence model and it provides a baseline of performance for the problem that we can use for comparison with an autoregression model.

We can develop a test harness for the problem by splitting the observations into training and test sets, with only the last 7 observations in the dataset assigned to the test set as *unseen* data we wish to predict. The predictions are made using a walk-forward validation model so that we can persist the most recent observations for the next day. This means that we are not making a 7-day forecast, but 7 1-day forecasts.

```python
# evaluate a persistence model
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
from matplotlib import pyplot
from sklearn.metrics import mean_squared_error
from math import sqrt

# load dataset
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0,
    parse_dates=True, squeeze=True)
# create lagged dataset
values = DataFrame(series.values)
dataframe = concat([values.shift(1), values], axis=1)
dataframe.columns = ['t', 't+1']
# split into train and test sets
X = dataframe.values
train, test = X[1:len(X)-7], X[len(X)-7:]
train_X, train_y = train[:,0], train[:,1]
test_X, test_y = test[:,0], test[:,1]
# persistence model
def model_persistence(x):
    return x
# walk-forward validation
predictions = list()
for x in test_X:
    yhat = model_persistence(x)
    predictions.append(yhat)
rmse = sqrt(mean_squared_error(test_y, predictions))
print('Test RMSE: %.3f' % rmse)
# plot predictions vs expected
pyplot.plot(test_y)
pyplot.plot(predictions, color='red')
pyplot.show()
```

Listing 22.6: Persistence model of the Minimum Daily Temperatures dataset.

Running the example prints the root mean squared error (RMSE). The value provides a baseline performance for the problem, in this case 1.850 degrees.

```
Test RMSE: 1.850
```

Listing 22.7: Example output of the persistence model on the Minimum Daily Temperatures dataset.

The expected values for the next 7 days are plotted compared to the predictions from the model.

![](img/da419ed7447ef051ee9d00167b7274cf_206_0.png)

Figure 22.4: Line plot of the persistence forecast (red) on the Minimum Daily Temperatures dataset (blue).

## 22.7 Autoregression Model

An autoregression model is a linear regression model that uses lagged variables as input variables. We could calculate the linear regression model manually using the LinearRegression class in scikit-learn and manually specify the lag input variables to use. Alternately, the Statsmodels library provides an autoregression model that automatically selects an appropriate lag value using statistical tests and trains a linear regression model. It is provided in the AR class$^{5}$. We can use this model by first creating the model AR() and then calling fit() to train it on our dataset. This returns an ARResult object$^{6}$. Once fit, we can use the model to make a prediction by calling the predict() function for a number of observations in the future. This creates a 17-day forecast, which is different from the persistence example above. The complete example is listed below.

```python
# create and evaluate a static autoregressive model
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.tsa.ar_model import AR
from sklearn.metrics import mean_squared_error
from math import sqrt
# load dataset
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# split dataset
X = series.values
train, test = X[1:len(X)-7], X[len(X)-7:]
# train autoregression
model = AR(train)
model_fit = model.fit()
print('Lag: %s' % model_fit.k_ar)
print('Coefficients: %s' % model_fit.params)
# make predictions
predictions = model_fit.predict(start=len(train), end=len(train)+len(test)-1, dynamic=False)
for i in range(len(predictions)): 
    print('predicted=%f, expected=%f' % (predictions[i], test[i]))
rmse = sqrt(mean_squared_error(test, predictions))
print('Test RMSE: %.3f' % rmse)
# plot results
pyplot.plot(test)
pyplot.plot(predictions, color='red')
pyplot.show()
```

Listing 22.8: Autoregression model of the Minimum Daily Temperatures dataset.

Running the example first prints the chosen optimal lag and the list of coefficients in the trained linear regression model. We can see that a 29-lag model was chosen and trained. This is interesting given how close this lag is to the average number of days in a month. The 7 day forecast is then printed and the root mean squared error of the forecast is summarized.

```
Lag: 29
Coefficients: [  5.57543506e-01  5.88595221e-01 -9.08257090e-02  4.82615092e-02
  4.00650265e-02  3.93020055e-02  2.59463738e-02  4.46675960e-02
  1.27681498e-02  3.74362239e-02 -8.11700276e-04  4.79081949e-03
  1.84731397e-02  2.68908418e-02  5.75906178e-04  2.48096415e-02
  7.40316579e-03  9.91622149e-03  3.41599123e-02 -9.11961877e-03
  2.42127561e-02  1.87870751e-02  1.21841870e-02 -1.85634575e-02
 -1.77162867e-03  1.67319894e-02  1.97615668e-02  9.83245087e-03
  6.22710723e-03 -1.37732255e-03]
predicted=11.871275, expected=12.900000
predicted=13.053794, expected=14.600000
predicted=13.532591, expected=14.000000
predicted=13.243126, expected=13.600000
predicted=13.091438, expected=13.500000
predicted=13.146989, expected=15.700000
predicted=13.176153, expected=13.000000
Test RMSE: 1.225
```

Listing 22.9: Example output of the Autoregression model on the Minimum Daily Temperatures dataset.

A plot of the expected vs the predicted values is made. The forecast does look pretty good (about 1 degree Celsius out each day), with big deviation on day 5.

![](img/da419ed7447ef051ee9d00167b7274cf_208_0.png)

Figure 22.5: Line plot of the AR model forecast (red) on the Minimum Daily Temperatures dataset (blue).

The Statsmodels API does not make it easy to update the model as new observations become available. One way would be to re-train the AR model each day as new observations become available, and that may be a valid approach, if not computationally expensive. An alternative would be to use the learned coefficients and manually make predictions. This requires that the history of 29 prior observations be kept and that the coefficients be retrieved from the model and used in the regression equation to come up with new forecasts.

The coefficients are provided in an array with the intercept term followed by the coefficients for each lag variable starting at **t** to **t-n**. We simply need to use them in the right order on the history of observations, as follows:

$\hat{y} = b0 + (b1 \times X1) + (b2 \times X2) \ldots (bn \times Xn)$ (22.3)

Below is the complete example.

```python
# create and evaluate an updated autoregressive model
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.tsa.ar_model import AR
from sklearn.metrics import mean_squared_error
from math import sqrt
# load dataset
```

5. http://statsmodels.sourceforge.net/develop/generated/statsmodels.tsa.ar_model.AR.html
6. http://statsmodels.sourceforge.net/develop/generated/statsmodels.tsa.ar_model.ARResults.html
