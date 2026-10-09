dataset back into the original form. To do this, we must keep track of the last actual observation. This is so that the predicted differenced value can be added to it.

```
```python
# fit an AR model and save the whole model to file
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
model = AR(X)
model_fit = model.fit(maxlag=6, disp=False)
# save model to file
model_fit.save('ar_model.pkl')
# save the differenced dataset
numpy.save('ar_data.npy', X)
# save the last ob
numpy.save('ar_obs.npy', [series.values[-1]])
```
```

Listing 27.3: Save the AR model for the Daily Female Births dataset.

This code will create a file **ar_model.pkl** that you can load later and use to make predictions. The entire differenced training dataset is saved as **ar_data.npy** and the last observation is saved in the file **ar_obs.npy** as an array with one item.

The NumPy save() function<sup>2</sup> is used to save the differenced training data and the observation. The load() function<sup>3</sup> can be used to load these arrays later. The snippet below will load the model, differenced data, and last observation.

```
```python
# load the AR model from file
from statsmodels.tsa.ar_model import ARResults
import numpy
loaded = ARResults.load('ar_model.pkl')
print(loaded.params)
data = numpy.load('ar_data.npy')
last_ob = numpy.load('ar_obs.npy')
print(last_ob)
```
```

Listing 27.4: Load the AR model for the Daily Female Births dataset.

Running the example prints the coefficients and the last observation.

```
```python
[ 0.12129822 -0.75275857 -0.612367 -0.51097172 -0.4176669 -0.32116469
-0.23412997]
```
```

²https://docs.scipy.org/doc/numpy/reference/generated/numpy.save.html
³https://docs.scipy.org/doc/numpy/reference/generated/numpy.load.html