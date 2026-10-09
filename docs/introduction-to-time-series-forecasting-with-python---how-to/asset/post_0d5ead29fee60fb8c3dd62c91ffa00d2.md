
## A.3. *Monthly Sunspots Dataset*

dataset is credited to Andrews & Herzberg (1985). The code below loads the Monthly Sunspot dataset, prints the first 5 rows of data and graphs the data as a line plot.

```python
# load the sunspots dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('sunspots.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(series.head())
series.plot()
pyplot.show()
```

Listing A.5: Create a line plot of the Monthly Sunspot dataset.

Below is a sample of the first 5 rows of the loaded dataset.

| Month | Value |
|---|---|
| 1949-01-01 | 58.0 |
| 1949-02-01 | 62.6 |
| 1949-03-01 | 70.0 |
| 1949-04-01 | 55.7 |
| 1949-05-01 | 85.0 |

Listing A.6: Example output of printing the first 5 rows of the Monthly Sunspot dataset.

Below is a line plot of the entire dataset.

![](img/da419ed7447ef051ee9d00167b7274cf_357_0.png)

Figure A.3: Line plot of the Monthly Sunspot dataset.

## A.4 Daily Female Births Dataset

This dataset describes the number of daily female births in California in 1959. The units are a count and there are 365 observations. The source of the dataset is credited to Newton (1988). The code below loads the Daily Female Births dataset, prints the first 5 rows of data and graphs the data as a line plot.

```python
# load the female births dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True,
                  squeeze=True)
print(series.head())
series.plot()
pyplot.show()
```

Listing A.7: Create a line plot of the Daily Female Births dataset.

Below is a sample of the first 5 rows of the loaded dataset.

```
Date
1959-01-01  35
1959-01-02  32
1959-01-03  30
1959-01-04  31
1959-01-05  44
```

Listing A.8: Example output of printing the first 5 rows of the Daily Female Births dataset.

Below is a line plot of the entire dataset.

![](img/da419ed7447ef051ee9d00167b7274cf_359_0.png)

## A.5 Airline Passengers Dataset

This dataset describes the total number of airline passengers over time. The units are a count of the number of airline passengers in thousands. There are 144 monthly observations from 1949 to 1960. The code below loads the Airline Passengers dataset, prints the first 5 rows of data and graphs the data as a line plot.

```python
# load the airline passengers dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True,
                   squeeze=True)
print(type(series))
print(series.head())
series.plot()
pyplot.show()
```

Listing A.9: Create a line plot of the Airline Passengers dataset.

Below is a sample of the first 5 rows of the loaded dataset.

```
Month
1949-01-01 112
1949-02-01  118
1949-03-01  132
1949-04-01  129
1949-05-01  121
```

Listing A.10: Example output of printing the first 5 rows of the Airline Passengers dataset.

Below is a line plot of the entire dataset.

![](img/da419ed7447ef051ee9d00167b7274cf_360_0.png)

Figure A.5: Line plot of the Airline Passengers dataset.

## Appendix B

### Workaround for Saving ARIMA Models

The Autoregressive Integrated Moving Average Model, or ARIMA, is a popular linear model for time series analysis and forecasting. The Statsmodels library provides an implementation of ARIMA for use in Python. ARIMA models can be saved to file for later use in making predictions on new data. There is a bug in the current version of the Statsmodels library that prevents saved models from being loaded. In this tutorial, you will discover how to diagnose and work around this issue. Let's get started.

#### B.1 Daily Female Births Dataset

In this lesson, we will use the Daily Female Births Dataset as an example. This dataset describes the number of daily female births in California in 1959. You can learn more about the dataset in Appendix A.4. Place the dataset in your current working directory with the filename *daily-total-female-births.csv*.

#### B.2 Python Environment

Confirm you are using the latest version of the Statsmodels library. You can do that by running the script below:

```python
# check the version of statsmodels
import statsmodels
print('statsmodels: %s' % statsmodels.__version__)
```

Listing B.1: Check Statsmodels version.

Running the script should produce a result showing Statsmodels 0.6.1 or 0.8.0.

```
statsmodels: 0.8.0
```

Listing B.2: Example output of checking the Statsmodels version.

You can use either Python 2 or 3.

#### B.3 ARIMA Model Save Bug

We can easily train an ARIMA model on the Daily Female Births dataset. The code snippet below trains an ARIMA(1,1,1) on the dataset. The model.fit() function returns an ARIMAResults object on which we can call save() to save the model to file and load() to later load it.

```python
# save and load an ARIMA model that causes an error
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults
# load data
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
# fit model
model = ARIMA(X, order=(1,1,1))
model_fit = model.fit()
# save model
model_fit.save('model.pkl')
# load model
loaded = ARIMAResults.load('model.pkl')
```

Listing B.3: Save and load an ARIMA model that causes an error.

Running this example will train the model and save it to file without problem. An error will be reported when you try to load the model from file.

```
Traceback (most recent call last):
  File "...", line 16, in <module>
    loaded = ARIMAResults.load('model.pkl')
  File ".../site-packages/statsmodels/base/model.py", line 1529, in load
    return load_pickle(fname)
  File ".../site-packages/statsmodels/iolib/smpickle.py", line 41, in load_pickle
    return cPickle.load(fin)
TypeError: __new__() takes at least 3 arguments (1 given)
```

Listing B.4: Example error message from loading the ARIMA model.

Specifically, note the line:

```
TypeError: __new__() takes at least 3 arguments (1 given)
```

Listing B.5: Specific error from loading the ARIMA model.

Alternately, if you are running a more recent version of Statsmodels, such as 0.8.0 you may get an error message such as:

```
AttributeError: 'ARIMA' object has no attribute 'dates'
```

Listing B.6: Alternate error from loading the ARIMA model.

So far so good, so how do we fix it?

#### B.4 ARIMA Model Save Bug Workaround

Zae Myung Kim discovered this bug in September 2016 and reported the fault. You can read all about it here:

- BUG: Implemented `__getnewargs__()` method for unpickling.  
  https://github.com/statsmodels/statsmodels/pull/3217

The bug occurs because a function required by pickle (the library used to serialize Python objects) has not been defined in Statsmodels. A function `__getnewargs__`[^1] must be defined in the ARIMA model prior to saving that defines the arguments needed to construct the object. We can work around this issue. The fix involves two things:

1. Defining an implementation of the `__getnewargs__()` function suitable for the ARIMA object.
2. Adding the new function to ARIMA.

Thankfully, Zae Myung Kim provided an example of the function in his bug report so we can just use that directly:

```python
def __getnewargs__(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))
```

Listing B.7: Example of defining the missing pickle function.

Python allows us to monkey patch an object, even one from a library like Statsmodels. We can define a new function on an existing object using assignment. We can do this for the `__getnewargs__()` function on the ARIMA object as follows:

```python
ARIMA.__getnewargs__ = __getnewargs__
```

Listing B.8: Example of adding the missing function to the ARIMA class.

The complete example of training, saving, and loading an ARIMA model in Python with the monkey patch is listed below:

```python
# save and load an ARIMA model with a workaround
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults

# monkey patch around bug in ARIMA class
def __getnewargs__(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))
ARIMA.__getnewargs__ = __getnewargs__

# load data
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True,
                  squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
```

[^1]: https://docs.python.org/2/library/pickle.html#object.__getnewargs__
