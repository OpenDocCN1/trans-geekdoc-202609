```
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
model.fit(trainX, trainy, epochs=100, verbose=0)
return model
```

Listing 10.8: Example of a function for fitting and returning a model for the blobs problem.

We can call this function to prepare the base model to which we can later add layers one at a time.

```
# get the base model
model = get_base_model(trainX, trainy)
```

Listing 10.9: Example of calling the function to fit the model on the dataset.

We need to be able to easily evaluate the performance of a model on the train and test sets. The evaluate_model() function below takes the train and test sets as arguments as well as a model and returns the accuracy on both datasets.

```
# evaluate a fit model
def evaluate_model(model, trainX, testX, trainy, testy):
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
return train_acc, test_acc
```

Listing 10.10: Example of a function to evaluate a fit model.

We can call this function to calculate and report the accuracy of the base model and store the scores away in a dictionary against the number of layers in the model (currently two, one hidden and one output layer) so we can plot the relationship between layers and accuracy later.

```
# evaluate the base model
scores = dict()
train_acc, test_acc = evaluate_model(model, trainX, trainy, testy)
print('> layers=%d, train=%.3f, test=%.3f' % (len(model.layers), train_acc, test_acc))
```

Listing 10.11: Example of summarizing the performance of a fit model.

We can now outline the process of greedy layer-wise pretraining. A function is required that can add a new hidden layer and retrain the model but only update the weights in the newly added layer and in the output layer. This requires first storing the current output layer including its configuration and current set of weights.

```
# remember the current output layer
output_layer = model.layers[-1]
```

Listing 10.12: Example of referencing the output layer.

Then removing the output layer from the stack of layers in the model.

```
# remove the output layer
model.pop()
```

Listing 10.13: Example of removing the output layer.

All of the remaining layers in the model can then be marked as non-trainable, meaning that their weights cannot be updated when the fit() function is called again.