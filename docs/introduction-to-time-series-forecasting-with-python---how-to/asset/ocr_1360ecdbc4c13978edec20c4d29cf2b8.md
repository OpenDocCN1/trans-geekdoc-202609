```
# update and save differenced observation
diffed = observation - last_ob[0]
data = numpy.append(data, [diffed], axis=0)
numpy.save('ar_data.npy', data)
# update and save real observation
last_ob[0] = observation
numpy.save('ar_obs.npy', last_ob)
```

Listing 27.13: Update the differenced data and last observation for the AR model.

We can make the same changes for the data files for the manual case. Specifically, we can update the man_data.npy and man_obs.npy respectively. The complete example is listed below.

```
# update the data for the manual model with a new obs
import numpy
# get real observation
observation = 48
# update and save differenced observation
lag = numpy.load('man_data.npy')
last_ob = numpy.load('man_obs.npy')
diffed = observation - last_ob[0]
lag = numpy.append(lag[1:], [diffed], axis=0)
numpy.save('man_data.npy', lag)
# update and save real observation
last_ob[0] = observation
numpy.save('man_obs.npy', last_ob)
```

Listing 27.14: Complete example of updating observations for a model of the Daily Female Births dataset.

We have focused on one-step forecasts. These methods would work just as easily for multi-step forecasts, by using the model repetitively and using forecasts of previous time steps as input lag values to predict observations for subsequent time steps.

# 27.7 Extensions

Generally, it is a good idea to keep track of all the observations. This will allow you to:

+   - Provide a context for further time series analysis to understand new changes in the data.
- Train a new model in the future on the most recent data.
- Back-test new and different models to see if performance can be improved.

For small applications, perhaps you could store the raw observations in a file alongside your model. It may also be desirable to store the model coefficients and required lag data and last observation in plain text for easy review. For larger applications, perhaps a database system could be used to store the observations.

# 27.8 Summary

In this tutorial, you discovered how to finalize a time series model and use it to make predictions with Python. Specifically, you learned: