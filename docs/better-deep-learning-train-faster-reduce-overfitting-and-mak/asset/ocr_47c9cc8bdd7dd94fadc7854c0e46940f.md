```
```python
y = to_categorical(y)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# create directory for models
makedirs('models')
# fit and save models
n_members = 5
for i in range(n_members):
    # fit model
    model = fit_model(trainX, trainy)
    # save model
    filename = 'models/model_' + str(i + 1) + '.h5'
    model.save(filename)
    print('>Saved %s' % filename)
```
```

Listing 25.13: Example of fitting and saving MLP ensemble members.

Running the example creates the models/ subfolder and saves five trained models with unique filenames.

```
```
>Saved models/model_1.h5
>Saved models/model_2.h5
>Saved models/model_3.h5
>Saved models/model_4.h5
>Saved models/model_5.h5
```
```

Listing 25.14: Example output from fitting and saving MLP ensemble members.

Next, we can look at training a meta-learner to make best use of the predictions from these submodels.

# 25.2.4 Separate Stacking Model

We can now train a meta-learner that will best combine the predictions from the submodels and ideally perform better than any single submodel. The first step is to load the saved models. We can use the load_model() Keras function and create a Python list of loaded models.

```
```python
# load models from file
def load_all_models(n_models):
    all_models = list()
    for i in range(n_models):
        # define filename for this ensemble
        filename = 'models/model_' + str(i + 1) + '.h5'
        # load model from file
        model = load_model(filename)
        # add to list of members
        all_models.append(model)
        print('>loaded %s' % filename)
    return all_models
```
```

Listing 25.15: Example of a function for loading saved ensemble members.

We can call this function to load our five saved models from the models/ sub-directory.