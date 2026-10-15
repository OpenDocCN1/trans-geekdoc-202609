+   - 12: Activity is calculated as the sum of the squared values.
+   - 11_12: Activity is calculated as the sum of absolute and sum of the squared values.

Each of the 11 and 12 regularizers takes a single hyperparameter that controls the amount that each activity contributes to the sum. The 11_12 regularizer takes two hyperparameters, one for each of the 11 and 12 methods. The regularizer class must be imported and then instantiated; for example:

```
# import regularizer
from keras.regularizers import l1
# instantiate regularizer
reg = l1(0.001)
```

Listing 14.1: Example of creating an L1 regularizer.

# 14.2.2 Activity Regularization on Layers

Activity regularization is specified on a layer in Keras. This can be achieved by setting the activity_regularizer argument on the layer to an instantiated and configured regularizer class. The regularizer is applied to the output of the layer, but you have control over what the output of the layer actually means. Specifically, you have flexibility as to whether the layer output means that the regularization is applied before or after the activation function. For example, you can specify the function and the regularization on the layer, in which case activation regularization is applied to the output of the activation function, in this case, relu.

```
...
model.add(Dense(32, activation='relu', activity_regularizer=l1(0.001)))
...
```

Listing 14.2: Example of activity regularization after activation.

Alternately, you can specify a linear activation function (the default, that does not perform any transform) which means that the activation regularization is applied on the raw outputs, then, the activation function can be added as a subsequent layer.

```
...
model.add(Dense(32, activation='linear', activity_regularizer=l1(0.001)))
model.add(Activation('relu'))
...
```

Listing 14.3: Example of activity regularization before activation.

The latter is probably the preferred usage of activation regularization as described in Deep Sparse Rectifier Neural Networks in order to allow the model to learn to take activations to a true zero value in conjunction with the rectified linear activation function. Nevertheless, the two possible uses of activation regularization may be explored in order to discover what works best for your specific model and dataset. Let’s take a look at how activity regularization can be used with some common layer types.