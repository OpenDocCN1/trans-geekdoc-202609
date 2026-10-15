![](bbox=[0.16, 0.14, 0.81, 0.48])

Figure 18.2: Line Plots of Loss on Train and Test Datasets While Training Showing an Overfit Model.

# 18.3.3 Overfit MLP With Early Stopping

We can update the example and add very simple early stopping. As soon as the loss of the model begins to increase on the test dataset, we will stop training. First, we can define the EarlyStopping callback.

```
```python
# simple early stopping
es = EarlyStopping(monitor='val_loss', mode='min', verbose=1)
```
```

Listing 18.29: Example of defining an early stopping callback for the MLP.

We can then update the call to the fit() function and specify a list of callbacks via the callback argument.

```
```python
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=4000, verbose=0, callbacks=[es])
```
```

Listing 18.30: Example of fitting the MLP with the early stopping callback.

The complete example with the addition of simple early stopping is listed below.

```
```python
# mlp overfit on the moons dataset with simple early stopping
```
```