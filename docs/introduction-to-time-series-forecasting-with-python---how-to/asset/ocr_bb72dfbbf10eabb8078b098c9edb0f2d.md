# ## 26.2 Evaluate ARIMA Model

We can evaluate an ARIMA model by preparing it on a training dataset and evaluating predictions on a test dataset. This approach involves the following steps:

+   1. Split the dataset into training and test sets.
2. Walk the time steps in the test dataset.
    (a) Train an ARIMA model.
    (b) Make a one-step prediction.
    (c) Store prediction; get and store actual observation.
3. Calculate error score for predictions compared to expected values.

We can implement this in Python as a new standalone function called evaluate_arima_model() that takes a time series dataset as input as well as a tuple with the p, d, and q parameters for the model to be evaluated. The dataset is split in two: 66% for the initial training dataset and the remaining 34% for the test dataset.

Each time step of the test set is iterated. Just one iteration provides a model that you could use to make predictions on new data. The iterative approach allows a new ARIMA model to be trained each time step. A prediction is made each iteration and stored in a list. This is so that at the end of the test set, all predictions can be compared to the list of expected values and an error score calculated. In this case, a root mean squared error score is calculated and returned. The complete function is listed below.

```
```
# evaluate an ARIMA model for a given order (p,d,q)
def evaluate_arima_model(X, arima_order):
    # prepare training dataset
    train_size = int(len(X) * 0.66)
    train, test = X[0:train_size], X[train_size:]
    history = [x for x in train]
    # make predictions
    predictions = list()
    for t in range(len(test)):
        model = ARIMA(history, order=arima_order)
        model_fit = model.fit(disp=0)
        yhat = model_fit.forecast()[0]
        predictions.append(yhat)
        history.append(test[t])
    # calculate out-of-sample error
    rmse = sqrt(mean_squared_error(test, predictions))
    return rmse
```
```

Listing 26.1: Function to evaluate an ARIMA model using out-of-sample error.

Now that we know how to evaluate one set of ARIMA hyperparameters, let's see how we can call this function repeatedly for a grid of parameters to evaluate.