
```python
from sklearn.linear_model import LogisticRegression
from keras.models import load_model
from keras.utils import to_categorical
from numpy import dstack

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

# create stacked model input dataset as outputs from the ensemble
def stacked_dataset(members, inputX):
    stackX = None
    for model in members:
        # make prediction
        yhat = model.predict(inputX, verbose=0)
        # stack predictions into [rows, members, probabilities]
        if stackX is None:
            stackX = yhat
        else:
            stackX = dstack((stackX, yhat))
    # flatten predictions to [rows, members x probabilities]
    stackX = stackX.reshape((stackX.shape[0], stackX.shape[1]*stackX.shape[2]))
    return stackX

# fit a model based on the outputs from the ensemble members
def fit_stacked_model(members, inputX, inputy):
    # create dataset using ensemble
    stackedX = stacked_dataset(members, inputX)
    # fit standalone model
    model = LogisticRegression(solver='lbfgs', multi_class='multinomial')
    model.fit(stackedX, inputy)
    return model

# make a prediction with the stacked model
def stacked_prediction(members, model, inputX):
    # create dataset using ensemble
    stackedX = stacked_dataset(members, inputX)
    # make a prediction
    yhat = model.predict(stackedX)
    return yhat

# generate 2d classification dataset
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

```
# load all models
n_members = 5
members = load_all_models(n_members)
print('Loaded %d models' % len(members))
# evaluate standalone models on test dataset
for model in members:
    testy_enc = to_categorical(testy)
    _, acc = model.evaluate(testX, testy_enc, verbose=0)
    print('Model Accuracy: %.3f' % acc)
# fit stacked model using the ensemble
model = fit_stacked_model(members, testX, testy)
# evaluate model on test set
yhat = stacked_prediction(members, model, testX)
acc = accuracy_score(testy, yhat)
print('Stacked Test Accuracy: %.3f' % acc)
```

Listing 25.23: Example of fitting a logistic regression stacking model.

Running the example first loads the submodels into a list and evaluates the performance of each. We can see that the best performing model is the final model with an accuracy of about 81.3%.

Note: Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

```
>loaded models/model_1.h5
>loaded models/model_2.h5
>loaded models/model_3.h5
>loaded models/model_4.h5
>loaded models/model_5.h5
Loaded 5 models
Model Accuracy: 0.805
Model Accuracy: 0.806
Model Accuracy: 0.804
Model Accuracy: 0.809
Model Accuracy: 0.813
```

Listing 25.24: Example output from loading and evaluating standalone MLP models.

Next, a logistic regression meta-learner is trained on the predicted probabilities from each submodel on the test set, then the entire stacking model is evaluated on the test set. We can see that in this case, the meta-learner out-performed each of the submodels on the test set, achieving an accuracy of about 82.4%.

```
Stacked Test Accuracy: 0.824
```

Listing 25.25: Example output from evaluating the stacking model.

## 25.2.5 Integrated Stacking Model

When using neural networks as submodels, it may be desirable to use a neural network as a meta-learner. Specifically, the sub-networks can be embedded in a larger multi-headed neural network that then learns how to best combine the predictions from each input submodel. It
allows the stacking ensemble to be treated as a single large model. The benefit of this approach is that the outputs of the submodels are provided directly to the meta-learner. Further, it is also possible to update the weights of the submodels in conjunction with the meta-learner model, if this is desirable. This can be achieved using the Keras functional interface for developing models.

After the models are loaded as a list, a larger stacking ensemble model can be defined where each of the loaded models is used as a separate input-head to the model. This requires that all of the layers in each of the loaded models be marked as not trainable so the weights cannot be updated when the new larger model is being trained. Keras also requires that each layer has a unique name, therefore the names of each layer in each of the loaded models will have to be updated to indicate to which ensemble member they belong.

```python
# update all layers in all models to not be trainable
for i in range(len(members)):
    model = members[i]
    for layer in model.layers:
        # make not trainable
        layer.trainable = False
        # rename to avoid 'unique layer name' issue
        layer.name = 'ensemble_' + str(i+1) + '_' + layer.name
```
```

Listing 25.26: Example of updating layer names and layers to be non-trainable.

Once the submodels have been prepared, we can define the stacking ensemble model. The input layer for each of the submodels will be used as a separate input head to this new model. This means that *k* copies of any input data will have to be provided to the model, where *k* is the number of input models, in this case, 5. The outputs of each of the models can then be merged. In this case, we will use a simple concatenation merge, where a single 15-element vector will be created from the three class-probabilities predicted by each of the 5 models. We will then define a hidden layer to interpret this *input* to the meta-learner and an output layer that will make its own probabilistic prediction. The `define_stacked_model()` function below implements this and will return a stacked generalization neural network model given a list of trained submodels.

```python
# define stacked model from multiple member input models
def define_stacked_model(members):
    # update all layers in all models to not be trainable
    for i in range(len(members)):
        model = members[i]
        for layer in model.layers:
            # make not trainable
            layer.trainable = False
            # rename to avoid 'unique layer name' issue
            layer.name = 'ensemble_' + str(i+1) + '_' + layer.name
    # define multi-headed input
    ensemble_visible = [model.input for model in members]
    # concatenate merge output from each model
    ensemble_outputs = [model.output for model in members]
    merge = concatenate(ensemble_outputs)
    hidden = Dense(10, activation='relu')(merge)
    output = Dense(3, activation='softmax')(hidden)
    model = Model(inputs=ensemble_visible, outputs=output)
    # plot graph of ensemble
    plot_model(model, show_shapes=True, to_file='model_graph.png')
    # compile
```

```
model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
return model
```

Listing 25.27: Example of a function for defining a stacked MLP model.

A plot of the network graph is created when this function is called to give an idea of how the ensemble model fits together.

```python
# define ensemble model
stacked_model = define_stacked_model(members)
```

Listing 25.28: Example of defining a stacked MLP model.

Creating the plot requires that pygraphviz is installed. If this is a challenge on your workstation, you can comment out the call to the plot_model() function.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_531_0.png)

Figure 25.3: Visualization of Stacked Generalization Ensemble of Neural Network Models.

Once the model is defined, it can be fit. We can fit it directly on the holdout test dataset. Because the submodels are not trainable, their weights will not be updated during training and only the weights of the new hidden and output layer will be updated. The fit_stacked_model() function below will fit the stacking neural network model on for 300 epochs.

```python
# fit a stacked model
def fit_stacked_model(model, inputX, inputy):
    # prepare input data
    X = [inputX for _ in range(len(model.input))]
    # encode output data
    inputy_enc = to_categorical(inputy)
    # fit model
    model.fit(X, inputy_enc, epochs=300, verbose=0)
```

Listing 25.29: Example of a function for fitting the stacked MLP model.

We can call this function providing the defined stacking model and the test dataset.

```python
# fit stacked model on test dataset
fit_stacked_model(stacked_model, testX, testy)
```

Listing 25.30: Example of fitting the stacked MLP model.

Once fit, we can use the new stacked model to make a prediction on new data. This is as simple as calling the predict() function on the model. One minor change is that we require k copies of the input data in a list to be provided to the model for each of the k submodels. The predict_stacked_model() function below simplifies this process of making a prediction with the stacking model.
