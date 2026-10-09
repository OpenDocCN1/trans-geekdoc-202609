# # Test Strategy

Candidate models will be evaluated using walk-forward validation. This is because a rolling-forecast type model is required from the problem definition. This is where one-step forecasts are needed given all available data. The walk-forward validation will work as follows:

+   1. The first 50% of the dataset will be held back to train the model.
2. The remaining 50% of the dataset will be iterated and test the model.
3. For each step in the test dataset:
    (a) A model will be trained.
    (b) A one-step prediction made and the prediction stored for later evaluation.
    (c) The actual observation from the test dataset will be added to the training dataset for the next iteration.
4. The predictions made during the iteration of the test dataset will be evaluated and an RMSE score reported.

Given the small size of the data, we will allow a model to be re-trained given all available data prior to each prediction. We can write the code for the test harness using simple NumPy and Python code. Firstly, we can split the dataset into train and test sets directly. We're careful to always convert a loaded dataset to `float32` in case the loaded data still has some String or Integer data types.

```
```
# prepare data
X = series.values
X = X.astype('float32')
train_size = int(len(X) * 0.50)
train, test = X[0:train_size], X[train_size:]
```
```

Listing 30.5: Example of splitting data into train and test sets.

Next, we can iterate over the time steps in the test dataset. The train dataset is stored in a Python list as we need to easily append a new observation each iteration and NumPy array concatenation feels like overkill. The prediction made by the model is called `ŷhat` for convention, as the outcome or observation is referred to as $y$ and `ŷhat` (a $y$ with a mark above) is the mathematical notation for the prediction of the $y$ variable. The prediction and observation are printed each observation for a sanity check prediction in case there are issues with the model.

```
```
# walk-forward validation
history = [x for x in train]
predictions = list()
for i in range(len(test)):
    # predict
    yhat = ...
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
    print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
```
```

Listing 30.6: Example of walk-forward validation.