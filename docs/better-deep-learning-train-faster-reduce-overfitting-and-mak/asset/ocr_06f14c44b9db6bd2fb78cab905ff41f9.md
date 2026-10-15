# 17.2.2 Noise Regularization in Models

The GaussianNoise layer can be used in a few different ways with a neural network model. Firstly, it can be used as an input layer to add noise to input variables directly. This is the traditional use of noise as a regularization method in neural networks. Below is an example of defining a GaussianNoise layer as an input layer for a model that takes 2 input variables.

```
...
model.add(GaussianNoise(0.01, input_shape=(2,)))
...
```

Listing 17.2: Example of adding a GaussianNoise layer to a model.

Noise can also be added between hidden layers in the model. Given the flexibility of Keras, the noise can be added before or after the use of the activation function. It may make more sense to add it before the activation; nevertheless, both options are possible. Below is an example of a GaussianNoise layer that adds noise to the linear output of a Dense layer before a rectified linear activation function, perhaps a more appropriate use of noise between hidden layers.

```
...
model.add(Dense(32))
model.add(GaussianNoise(0.1))
model.add(Activation('relu'))
model.add(Dense(32))
...
```

Listing 17.3: Example of adding a GaussianNoise layer before activation.

Noise can also be added after the activation function, much like using a noisy activation function. One downside of this usage is that the resulting values may be out-of-range from what the activation function may normally provide. For example, a value with added noise may be less than zero, whereas the relu activation function will only ever output values 0 or larger.

```
...
model.add(Dense(32, activation='reu'))
model.add(GaussianNoise(0.1))
model.add(Dense(32))
...
```

Listing 17.4: Example of adding a GaussianNoise layer after activation.

Let’s take a look at how noise regularization can be used with some common network types.

# MLP Noise Regularization

The example below adds noise between two Dense fully connected layers.

```
# example of noise between fully connected layers
from keras.layers import Dense
from keras.layers import GaussianNoise
from keras.layers import Activation
...
model.add(Dense(32))
model.add(GaussianNoise(0.1))
model.add(Activation('relu'))
model.add(Dense(1))
```