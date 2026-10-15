
George Dahl, et al. in their 2013 paper titled *Improving deep neural networks for LVCSR using rectified linear units and dropout* used a deep neural network with rectified linear activation functions and dropout to achieve (at the time) state-of-the-art results on a standard speech recognition task. They used a Bayesian optimization procedure to configure the choice of activation function and the amount of dropout.

... the Bayesian optimization procedure learned that dropout wasn’t helpful for sigmoid nets of the sizes we trained. In general, ReLUs and dropout seem to work quite well together.

## 16.1.5 Tips for Using Dropout Regularization

This section provides some tips for using dropout regularization with your neural network.

### Use With All Network Types

Dropout regularization is a generic approach. It can be used with most, perhaps all, types of neural network models, not least the most common network types of Multilayer Perceptrons, Convolutional Neural Networks, and Long Short-Term Memory Recurrent Neural Networks. In the case of LSTMs, it may be desirable to use different dropout rates for the input and recurrent connections.

### Dropout Rate

The default interpretation of the dropout hyperparameter is the probability of training a given node in a layer, where 1.0 means no dropout, and 0.0 means no outputs from the layer. A good value for dropout in a hidden layer is between 0.5 and 0.8. Input layers use a larger dropout (retention) rate, such as 0.8.

### Use a Larger Network

It is common for larger networks (more layers or more nodes) to more easily overfit the training data. When using dropout regularization, it is possible to use larger networks with less risk of overfitting. In fact, a large network (more nodes per layer) may be required as dropout will probabilistically reduce the capacity of the network. A good rule of thumb is to divide the number of nodes in the layer before dropout by the proposed dropout rate and use that as the number of nodes in the new network that uses dropout. For example, a network with 100 nodes and a proposed dropout rate of 0.5 will require 200 nodes (100/0.5) when using dropout.

> If *n* is the number of hidden units in any layer and *p* is the probability of retaining a unit [...] a good dropout net should have at least *n/p* units
>
> — *Dropout: A Simple Way to Prevent Neural Networks from Overfitting*, 2014.

### Grid Search Parameters

Rather than guess at a suitable dropout rate for your network, test different rates systematically. For example, test values between 1.0 and 0.1 in increments of 0.1. This will both help you discover what works best for your specific model and dataset, as well as how sensitive the model is to the dropout rate. A more sensitive model may be unstable and could benefit from an increase in size.

### Use a Weight Constraint

Network weights will increase in size in response to the probabilistic removal of layer activations. Large weight size can be a sign of an unstable network. To counter this effect a weight constraint can be imposed to force the norm (magnitude) of all weights in a layer to be below a specified value. For example, the maximum norm constraint is recommended with a value between 3 and 4.

> ... we can use max-norm regularization. This constrains the norm of the vector of incoming weights at each hidden unit to be bound by a constant c. Typical values of c range from 3 to 4.
>
> — Dropout: A Simple Way to Prevent Neural Networks from Overfitting, 2014.

This does introduce an additional hyperparameter that may require tuning for the model.

### Use With Smaller Datasets

Like other regularization methods, dropout is more effective on those problems where there is a limited amount of training data and the model is likely to overfit the training data. Problems where there is a large amount of training data may see less benefit from using dropout.

For very large datasets, regularization confers little reduction in generalization error. In these cases, the computational cost of using dropout and larger models may outweigh the benefit of regularization.

## 16.2 Dropout Keras API

This section demonstrates how to use dropout with the Keras API.

### 16.2.1 Dropout in Keras

Keras supports dropout regularization. The simplest form of dropout in Keras is provided by a Dropout core layer. When created, the dropout rate can be specified to the layer as the probability of setting each input to the layer to zero. This is different from the definition of dropout rate from the papers, in which the rate refers to the probability of retaining an input. Therefore, when a dropout rate of 0.8 is suggested in a paper (retain 80%), this will, in fact, be a dropout rate of 0.2 (set 20% of inputs to zero). Below is an example of creating a dropout layer with a 50% chance of setting inputs to zero.

```python
layer = Dropout(0.5)
```

Listing 16.1: Example of creating a Dropout layer.

### 16.2.2 Dropout on Layers

The Dropout layer is added to a model between existing layers and applies to outputs of the prior layer that are fed to the subsequent layer. For example, given two dense layers:

```python
...
model.add(Dense(32))
model.add(Dense(32))
...
```

Listing 16.2: Example of two Dense hidden layers.

We can insert a dropout layer between them, in which case the outputs or activations of the first layer have dropout applied to them, which are then taken as input to the next layer.

```python
...
model.add(Dense(32))
model.add(Dropout(0.5))
model.add(Dense(32))
...
```

Listing 16.3: Example of a Dropout layer between two Dense hidden layers.

Dropout can also be applied to the visible layer, e.g. the inputs to the network. This requires that you define the network with the Dropout layer as the first layer and add the input_shape argument to the layer to specify the expected shape of the input samples.

```python
...
model.add(Dropout(0.5, input_shape=(2,)))
...
```

Listing 16.4: Example of a Dropout input layer.

Let’s take a look at how dropout regularization can be used with some common network types.

### MLP Dropout Regularization

The example below adds dropout between two Dense fully connected layers.

```python
# example of dropout between fully connected layers
from keras.layers import Dense
from keras.layers import Dropout
...
model.add(Dense(32))
model.add(Dropout(0.5))
model.add(Dense(1))
...
```

Listing 16.5: Example of Dropout for an MLP.

### CNN Dropout Regularization

Dropout can be used after convolutional layers (e.g. Conv2D) and after pooling layers (e.g. MaxPooling2D). Often, dropout is only used after the pooling layers, but this is just a rough heuristic.

```python
# example of dropout for a CNN
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import Dropout
...
model.add(Conv2D(32, (3,3)))
model.add(Conv2D(32, (3,3)))
model.add(MaxPooling2D())
model.add(Dropout(0.5))
model.add(Dense(1))
...
```

Listing 16.6: Example of Dropout for a CNN.

In this case, dropout is applied to each element or cell within the feature maps. An alternative way to use dropout with convolutional neural networks is to dropout entire feature maps from the convolutional layer which are then not used during pooling. This is called spatial dropout (or Spatial Dropout).

> Instead we formulate a new dropout method which we call SpatialDropout. For a given convolution feature tensor [...] [we] extend the dropout value across the entire feature map.
>
> — Efficient Object Localization Using Convolutional Networks, 2015.

Spatial Dropout is provided in Keras via the SpatialDropout2D layer (as well as 1D and 3D versions).

```python
# example of spatial dropout for a CNN
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import MaxPooling2D
from keras.layers import SpatialDropout2D
...
model.add(Conv2D(32, (3,3)))
model.add(Conv2D(32, (3,3)))
model.add(SpatialDropout2D(0.5))
model.add(MaxPooling2D())
model.add(Dense(1))
...
```

Listing 16.7: Example of Spatial Dropout for a CNN.

### RNN Dropout Regularization

The example below adds dropout between two layers: an LSTM recurrent layer and a Dense fully connected layer.
