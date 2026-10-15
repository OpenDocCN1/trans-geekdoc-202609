
network types like CNNs. This is because the activation function looks and acts like a linear function, making it easier to train and less likely to saturate, but is, in fact, a nonlinear function, forcing negative inputs to the value 0. It is claimed as one possible approach to addressing the vanishing gradients problem when training deeper models. When using the rectified linear activation function (or ReLU for short), it is good practice to use the He weight initialization scheme. We can define the MLP with five hidden layers using ReLU and He initialization, listed below.

```
# define model
model = Sequential()
model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='sigmoid'))
```

Listing 7.22: Example of defining a much deeper ReLU-based MLP.

Tying this together, the complete code example is listed below.

```
# deeper mlp with relu for the two circles classification problem (5 hidden layers)
from sklearn.datasets import make_circles
from sklearn.preprocessing import MinMaxScaler
from keras.layers import Dense
from keras.models import Sequential
from keras.optimizers import SGD
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
scaler = MinMaxScaler(feature_range=(-1, 1))
X = scaler.fit_transform(X)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
model.add(Dense(1, activation='sigmoid'))
# compile model
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=500, verbose=0)
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
# plot loss learning curves
pyplot.subplot(211)
pyplot.title('Cross-Entropy Loss', pad=-40)
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
# plot accuracy learning curves
pyplot.subplot(212)
pyplot.title('Accuracy', pad=-40)
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.legend()
pyplot.show()
```

Listing 7.23: Example of evaluating a deeper ReLU-based MLP for the two circles problem.

Running the example prints the performance of the model on the train and test datasets.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

In this case, we can see that this small change has allowed the model to learn the problem, achieving about 84% accuracy on both datasets, outperforming the single layer model using the tanh activation function.

```
Train: 0.842, Test: 0.846
```

Listing 7.24: Example output from evaluating a deeper ReLU-based MLP for the two circles problem.

A line plot of model accuracy on the train and test sets over training epochs is also created. The plot shows quite different dynamics to what we have seen so far. The model appears to rapidly learn the problem, converging on a solution in about 100 epochs.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_196_0.png)

Figure 7.5: Line Plot of Train and Test Set Accuracy of Over Training Epochs for Deep MLP with ReLU in the Two Circles Problem.

Use of the ReLU activation function has allowed us to fit a much deeper model for this simple problem, but this capability does not extend infinitely. For example, increasing the number of layers results in slower learning to a point at about 20 layers where the model is no longer capable of learning the problem, at least with the chosen configuration. For example, below is a line plot of train and test accuracy of the same model with 15 hidden layers that shows that it is still capable of learning the problem (at least some of the time).

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_197_0.png)

Figure 7.6: Line Plot of Train and Test Set Accuracy of Over Training Epochs for Deep MLP with ReLU with 15 Hidden Layers.

Below is a line plot of train and test accuracy over epochs with the same model with 20 layers, showing that the configuration is no longer capable of learning the problem (at least some of the time).

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_198_0.png)

Figure 7.7: Line Plot of Train and Test Set Accuracy of Over Training Epochs for Deep MLP with ReLU with 20 Hidden Layers.

Although use of the ReLU worked, we cannot be confident that use of the tanh function failed because of vanishing gradients and ReLU succeed because it overcame this problem.

## 7.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- **Weight Initialization**. Update the deep MLP with tanh activation to use Xavier uniform weight initialization and report the results.
- **Learning Algorithm**. Update the deep MLP with tanh activation to use an adaptive learning algorithm such as Adam and report the results.
- **Weight Changes**. Update the tanh and relu examples to record and plot the L1 vector norm of model weights each epoch as a proxy for how much each layer is changed during training and compare results.
- **Study Model Depth**. Create an experiment using the MLP with tanh activation and report the performance of models as the number of hidden layers is increased from 1 to 10.
- **Increase Breadth**. Increase the number of nodes in the hidden layers of the MLP with tanh activation from 5 to 25 and report performance as the number of layers are increased from 1 to 10.

If you explore any of these extensions, I’d love to know.

## 7.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 7.5.1 Books

- Section 6.3.1: Rectified Linear Units and Their Generalizations, *Deep Learning*, 2016.
  https://amzn.to/2QHVwmW

### 7.5.2 Papers

- *What is the best multi-stage architecture for object recognition?*, 2009
  https://ieeexplore.ieee.org/document/5459469
- *Rectified Linear Units Improve Restricted Boltzmann Machines*, 2010.
  https://dl.acm.org/citation.cfm?id=3104425
- *Deep Sparse Rectifier Neural Networks*, 2011.
  http://proceedings.mlr.press/v15/glorot11a
- *Rectifier Nonlinearities Improve Neural Network Acoustic Models*, 2013.
  http://ai.stanford.edu/~amaas/papers/relu_hybrid_icml2013_final.pdf
- *Understanding the difficulty of training deep feedforward neural networks*, 2010.
  http://proceedings.mlr.press/v9/glorot10a.html
- *Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification*, 2015.
  https://arxiv.org/abs/1502.01852
- *Maxout Networks*, 2013.
  https://arxiv.org/abs/1302.4389
- *Random Walk Initialization for Training Very Deep Feedforward Networks*, 2014.
  https://arxiv.org/abs/1412.6558
- *Gradient Flow in Recurrent Nets: the Difficulty of Learning Long-Term Dependencies*, 2001.
  http://www.iro.umontreal.ca/~lisa/publications2/index.php/publications/show/55
