
## 30.7  Operational Model

In this section, we assume that we have not fooled or lied to ourselves. This section includes the following steps:

- **Finalize Model**: Train and save the final model.
- **Make Prediction**: Load the finalized model and make a prediction.
- **Validate Model**: Load and validate the final model.

### 30.7.1  Finalize Model

Finalizing the model involves fitting an ARIMA model on the entire dataset, in this case, on a transformed version of the entire dataset. Once fit, the model can be saved to file for later use. Because a Box-Cox transform is also performed on the data, we need to know the chosen `lambda` so that any predictions from the model can be converted back to the original, untransformed scale. The example below fits an ARIMA(0,1,2) model on the Box-Cox transform dataset and saves the whole fit object and the `lambda` value to file.

There is a bug in the current version of the statsmodels library that results in an error when you try to load a saved ARIMA model from file. Learn more about this bug and the workaround in Appendix B. The example below saves the fit model to file in the correct state so that it can be loaded successfully later.

```python
# finalize model and save to file with workaround
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from scipy.stats import boxcox
import numpy

# monkey patch around bug in ARIMA class
def __getnewargs___(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))

ARIMA.__getnewargs__ = __getnewargs__

# load data
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
# transform data
transformed, lam = boxcox(X)
# fit model
model = ARIMA(transformed, order=(0,1,2))
model_fit = model.fit(disp=0)
# save model
model_fit.save('model.pkl')
numpy.save('model_lambda.npy', [lam])
```

Listing 30.28: Save the finalized ARIMA model with workaround.

Running the example creates two local files:

- `model.pkl`: This is the ARIMAresult object from the call to `ARIMA.fit()`. This includes the coefficients and all other internal data returned when fitting the model.
- `model_lambda.npy`: This is the lambda value stored as a one-row, one-column NumPy array.

This is probably overkill and all that is really needed for operational use are the AR and MA coefficients from the model, the d parameter for the number of differences, perhaps the lag observations and model residuals, and the lambda value for the transform.

### 30.7.2  Make Prediction

A natural case may be to load the model and make a single forecast. This is relatively straightforward and involves restoring the saved model and the lambda and calling the forecast() function. The example below loads the model, makes a prediction for the next time step, inverts the Box-Cox transform, and prints the prediction.

```python
# load the finalized model and make a prediction
from statsmodels.tsa.arima_model import ARIMAResults
from math import exp
from math import log
import numpy

# invert box-cox transform
def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)

model_fit = ARIMAResults.load('model.pkl')
lam = numpy.load('model_lambda.npy')
yhat = model_fit.forecast()[0]
yhat = boxcox_inverse(yhat, lam)
print('Predicted: %.3f' % yhat)
```

Listing 30.29: Load finalized ARIMA model and make a prediction.

Running the example prints the prediction of about 452. If we peek inside validation.csv, we can see that the value on the first row for the next time period is 452. The model got it 100% correct, which is very impressive (or lucky).

```
Predicted: 452.043
```

Listing 30.30: Example output when loading the finalized ARIMA and making one prediction.

### 30.7.3  Validate Model

We can load the model and use it in a pretend operational manner. In the test harness section, we saved the final 12 months of the original dataset in a separate file to validate the final model. We can load this validation.csv file now and use it to see how well our model really is on unseen data. There are two ways we might proceed:

- Load the model and use it to forecast the next 12 months. The forecast beyond the first one or two months will quickly start to degrade in skill.
- Load the model and use it in a rolling-forecast manner, updating the transform and model for each time step. This is the preferred method as it is how one would use this model in practice, as it would achieve the best performance.

As with model evaluation in previous sections, we will make predictions in a rolling-forecast manner. This means that we will step over lead times in the validation dataset and take the observations as an update to the history.

```python
# evaluate the finalized model on the validation dataset
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults
from scipy.stats import boxcox
from sklearn.metrics import mean_squared_error
from math import sqrt
from math import exp
from math import log
import numpy

# invert box-cox transform
def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)

# load and prepare datasets
dataset = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
X = dataset.values.astype('float32')
history = [x for x in X]
validation = read_csv('validation.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
y = validation.values.astype('float32')
# load model
model_fit = ARIMAResults.load('model.pkl')
lam = numpy.load('model_lambda.npy')
# make first prediction
predictions = list()
yhat = model_fit.forecast()[0]
yhat = boxcox_inverse(yhat, lam)
predictions.append(yhat)
history.append(y[0])
print('>Predicted=%.3f, Expected=%.3f' % (yhat, y[0]))
# rolling forecasts
for i in range(1, len(y)):
    # transform
    transformed, lam = boxcox(history)
    if lam < -5:
        transformed, lam = history, 1
    # predict
    model = ARIMA(transformed, order=(0,1,2))
    model_fit = model.fit(disp=0)
    yhat = model_fit.forecast()[0]
    # invert transformed prediction
    yhat = boxcox_inverse(yhat, lam)
    predictions.append(yhat)
    # observation
    obs = y[i]
    history.append(obs)
    print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
# report performance
rmse = sqrt(mean_squared_error(y, predictions))
print('RMSE: %.3f' % rmse)
pyplot.plot(y)
pyplot.plot(predictions, color='red')
pyplot.show()
```

Listing 30.31: Load and validate the finalized model.

Running the example prints each prediction and expected value for the time steps in the validation dataset. The final RMSE for the validation period is predicted at 53 robberies. This is not too different to the expected error of 49, but I would expect that it is also not too different from a simple persistence model.

```
>Predicted=452.043, Expected=452
>Predicted=423.088, Expected=391
>Predicted=408.378, Expected=500
>Predicted=482.454, Expected=451
>Predicted=445.944, Expected=375
>Predicted=413.881, Expected=372
>Predicted=413.209, Expected=302
>Predicted=355.159, Expected=316
>Predicted=363.515, Expected=398
>Predicted=406.365, Expected=394
>Predicted=394.186, Expected=431
>Predicted=428.174, Expected=431
RMSE: 53.078
```

Listing 30.32: Example output from validating the finalized model.

A plot of the predictions compared to the validation dataset is also provided. The forecast does have the characteristic of a persistence forecast. This does suggest that although this time series does have an obvious trend, it is still a reasonably difficult problem.

![](img/da419ed7447ef051ee9d00167b7274cf_296_0.png)

Figure 30.8: Line plot of expected validation values (blue) compared to predicted validation values (red).

## 30.8  Extensions

This tutorial was not exhaustive; there may be more that you can do to improve the result. This section lists some ideas.

- **Statistical Significance Tests.** Use a statistical test to check if the difference in results between different models is statistically significant. The Student's t-test would be a good place to start.
- **Grid Search with Data Transforms.** Repeat the grid search in the ARIMA hyperparameters with the Box-Cox transform and see if a different and better set of parameters can be achieved.
- **Inspect Residuals.** Investigate the residual forecast errors on the final model with Box-Cox transforms to see if there is a further bias and/or autocorrelation that can be addressed.
- **Lean Model Saving.** Simplify model saving to only store the required coefficients rather than the entire `ARIMAResults` object.
