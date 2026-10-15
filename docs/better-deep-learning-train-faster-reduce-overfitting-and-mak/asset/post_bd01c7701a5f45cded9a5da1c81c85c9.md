
## Mean Squared Error

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_210_0.png)

Figure 8.2: Line Plot of Mean Squared Error Loss for the Train (blue) and Test (orange) Datasets Over Training Epochs With Gradient Norm Scaling.

There is nothing special about the vector norm value of 1.0, and other values could be evaluated and the performance of the resulting model compared.

### 8.3.4 MLP With Gradient Value Clipping

Another solution to the exploding gradient problem is to clip the gradient if it becomes too large or too small. We can update the training of the MLP to use gradient clipping by adding the clipvalue argument to the optimization algorithm configuration. For example, the code below clips the gradient to the range [-5 to 5].

```
# compile model
opt = SGD(lr=0.01, momentum=0.9, clipvalue=5.0)
model.compile(loss='mean_squared_error', optimizer=opt)
```

Listing 8.16: Example of updating the optimizer to use gradient value clipping.

The complete example of training the MLP with gradient clipping is listed below.

### 8.3. Gradient Clipping Case Study

```
# mlp with unscaled data for the regression problem with gradient clipping
from sklearn.datasets import make_regression
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from matplotlib import pyplot
# generate regression dataset
X, y = make_regression(n_samples=1000, n_features=20, noise=0.1, random_state=1)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(20, input_dim=20, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='linear'))
# compile model
opt = SGD(lr=0.01, momentum=0.9, clipvalue=5.0)
model.compile(loss='mean_squared_error', optimizer=opt)
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
# evaluate the model
train_mse = model.evaluate(trainX, trainy, verbose=0)
test_mse = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_mse, test_mse))
# plot loss during training
pyplot.title('Mean Squared Error')
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
pyplot.show()
```

Listing 8.17: Example of fitting and evaluating an MLP with gradient value clipping on the regression problem.

Running this example fits the model and evaluates it on the train and test sets, printing the mean squared error.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

We can see that in this case, the model is able to learn the problem without exploding gradients achieving an MSE of below 10 on both the train and test sets.

```
Train: 9.487, Test: 9.985
```

Listing 8.18: Example output from fitting and evaluating an MLP with gradient value clipping on the regression problem.

A line plot is also created showing the means squared error loss on the train and test datasets over training epochs. The plot shows that the model learns the problem fast, achieving a sub-100 MSE loss within just a few training epochs.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_212_0.png)

Figure 8.3: Line Plot of Mean Squared Error Loss for the Train (blue) and Test (orange) Datasets Over Training Epochs With Gradient Value Clipping.

A clipped range of [-5, 5] was chosen arbitrarily; you can experiment with different sized ranges and compare performance of the speed of learning and final model performance.

### 8.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- **Vector Norm Values.** Update the example to evaluate different gradient vector norm values and compare performance.
- **Vector Clip Values.** Update the example to evaluate different gradient value ranges and compare performance.
- **Vector Norm and Clip.** Update the example to use a combination of vector norm scaling and vector value clipping on the same training run and compare performance.

If you explore any of these extensions, I’d love to know.

### 8.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 8.5.1 Books

- Section 8.2.4: Cliffs and Exploding Gradients, *Deep Learning*, 2016.
- https://amzn.to/2NJW3gE
- Section 10.11.1: Clipping Gradients, *Deep Learning*, 2016.
- https://amzn.to/2NJW3gE

### 8.5.2 Papers

- *On the difficulty of training Recurrent Neural Networks*, 2013.
- https://arxiv.org/abs/1211.5063
- *Generating Sequences With Recurrent Neural Networks*, 2013.
- https://arxiv.org/abs/1308.0850

### 8.5.3 APIs

- Keras Optimizers API.
- https://keras.io/optimizers/
- Keras Optimizers Source Code.
- https://github.com/keras-team/keras/blob/master/keras/optimizers.py
- `sklearn.datasets.make_regression` API.
- http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_regression.html

### 8.6 Summary

In this tutorial, you discovered the exploding gradient problem and how to improve neural network training stability using gradient clipping. Specifically, you learned:

- Training neural networks can become unstable, leading to a numerical overflow or underflow referred to as exploding gradients.
- The training process can be made stable by changing the error gradients, either by scaling the vector norm or clipping gradient values to a range.
- How to update an MLP model for a regression predictive modeling problem with exploding gradients to have a stable training process using gradient clipping methods.

### 8.6.1 Next

In the next tutorial, you will discover how to accelerate the training process through the use of batch normalization.

## Chapter 9

## Accelerate Learning with Batch Normalization

Training deep neural networks with tens of layers is challenging as they can be sensitive to the initial random weights and configuration of the learning algorithm. One possible reason for this difficulty is the distribution of the inputs to layers deep in the network may change after each minibatch when the weights are updated. This can cause the learning algorithm to forever chase a moving target. This change in the distribution of inputs to layers in the network is referred to by the technical name *internal covariate shift*. Batch normalization is a technique for training very deep neural networks that standardizes the inputs to a layer for each minibatch. This has the effect of stabilizing the learning process and dramatically reducing the number of training epochs required to train deep networks. In this tutorial, you will discover the batch normalization method used to accelerate the training of deep learning neural networks. After reading this tutorial, you will know:

- Deep neural networks are challenging to train, not least because the input from prior layers can change after weight updates.
- Batch normalization is a technique to standardize the inputs to a network, applied to either the activations of a prior layer or inputs directly.
- Batch normalization accelerates training, in some cases by halving the number of epochs (or better), and provides some regularization effect, reducing generalization error.

Let’s get started.

### 9.1 Batch Normalization

In this section you will discover batch normalization, the effect it has on the training process and the tips for using batch normalization on your own deep learning models.

### 9.1.1 Problem of Training Deep Networks

Training deep neural networks, e.g. networks with tens of hidden layers, is challenging. One aspect of this challenge is that the model is updated layer-by-layer backward from the output to
