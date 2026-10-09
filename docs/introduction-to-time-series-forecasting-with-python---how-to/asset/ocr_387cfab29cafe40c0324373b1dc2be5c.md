[50]

# Listing 27.5: Example output of loading the AR model for the Daily Female Births dataset.

I think this is good for most cases, but is also pretty heavy. You are subject to changes to the Statsmodels API. My preference is to work with the coefficients of the model directly, as in the case above, evaluating the model using a rolling forecast. In this case, you could simply store the model coefficients and later load them and make predictions. The example below saves just the coefficients from the model, as well as the minimum differenced lag values required to make the next prediction and the last observation needed to transform the next prediction made.

```
# fit an AR model and manually save coefficients to file
from pandas import read_csv
from statsmodels.tsa.ar_model import AR
import numpy

# create a difference transform of the dataset
def difference(dataset):
    diff = list()
    for i in range(1, len(dataset)):
        value = dataset[i] - dataset[i - 1]
        diff.append(value)
    return numpy.array(diff)

# load dataset
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
X = difference(series.values)
# fit model
window_size = 6
model = AR(X)
model_fit = model.fit(maxlag=window_size, disp=False)
# save coefficients
coef = model_fit.params
numpy.save('man_model.npy', coef)
# save lag
lag = X[:window_size:]
numpy.save('man_data.npy', lag)
# save the last ob
numpy.save('man_obs.npy', [series.values[-1]])
```

# Listing 27.6: Save the AR model coefficients for the Daily Female Births dataset.

The coefficients are saved in the local file man_model.npy, the lag history is saved in the file man_data.npy, and the last observation is saved in the file man_obs.npy. These values can then be loaded again as follows:

```
# load the manually saved model from file
import numpy
coef = numpy.load('man_model.npy')
print(coef)
lag = numpy.load('man_data.npy')
print(lag)
last_ob = numpy.load('man_obs.npy')
print(last_ob)
```