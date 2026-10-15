
In this case, we can see comparable performance of the model on both the train and test set of about 84% accuracy, very similar to what we saw in the previous section, if not a little bit better.

```
Train: 0.842, Test: 0.846
```

Listing 9.21: Example output from evaluating an MLP with batch normalization after activation on the two circles problem.

A graph of the learning curves is also created showing classification accuracy on both the train and test sets for each training epoch. In this case, we can see that the model has learned the problem faster than the model in the previous section without batch normalization. Specifically, we can see that classification accuracy on the train and test datasets leaps above 80% within the first 20 epochs, as opposed to 30-to-40 epochs in the model without batch normalization. The plot also shows the effect of batch normalization during training. We can see lower performance on the training dataset than the test dataset: scores on the training dataset that are lower than the performance on the test dataset at the end of the training run. This is likely the effect of the input collected and updated each minibatch.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_229_0.png)

Figure 9.3: Line Plot Classification Accuracy of MLP With Batch Normalization After Activation Function on Train and Test Datasets Over Training Epochs.

We can also try a variation of the model where batch normalization is applied prior to the activation function of the hidden layer, instead of after the activation function.

```
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(Dense(1, activation='sigmoid'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
```

Listing 9.22: Example of updating the model to use batch normalization before the activation function.

The complete code listing with this change to the model is listed below.

```
# mlp for the two circles problem with batchnorm before activation function
from sklearn.datasets import make_circles
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Activation
from keras.layers import BatchNormalization
from keras.optimizers import SGD
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(Dense(1, activation='sigmoid'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
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

Listing 9.23: Example evaluating an MLP with batch normalization before activation on the two circles problem.

Running the example first prints the classification accuracy of the model on the train and test dataset.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

In this case, we can see comparable performance of the model on the train and test datasets, but slightly worse than the model without batch normalization.

```
Train: 0.832, Test: 0.834
```

Listing 9.24: Example output from evaluating an MLP with batch normalization before activation on the two circles problem.

The line plot of the learning curves on the train and test sets also tells a different story. The plot shows the model learning perhaps at the same pace as the model without batch normalization, but the performance of the model on the training dataset is much worse, hovering around 70% to 75% accuracy, again likely an effect of the statistics collected and used over each minibatch. At least for this model configuration on this specific dataset, it appears that batch normalization is more effective after the rectified linear activation function.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_232_0.png)

Figure 9.4: Line Plot Classification Accuracy of MLP With Batch Normalization Before Activation Function on Train and Test Datasets Over Training Epochs.

## 9.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- **Without Beta and Gamma.** Update the example to not use the beta and gamma parameters in the batch normalization layer and compare results.
- **Without Momentum.** Update the example to not use momentum in the batch normalization layer during training and compare results.
- **Input Layer.** Update the example to use batch normalization after the input to the model and compare results.

If you explore any of these extensions, I’d love to know.

## 9.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 9.5.1 Books

- Section 8.7.1: Batch Normalization, *Deep Learning*, 2016.  
  https://amzn.to/2NJW3gE
- Section 7.3.1: Advanced architecture patterns, *Deep Learning With Python*, 2017.  
  https://amzn.to/2Ck4ImT

### 9.5.2 Papers

- *Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift*, 2015.  
  https://arxiv.org/abs/1502.03167
- *Batch Renormalization: Towards Reducing Minibatch Dependence in Batch-Normalized Models*, 2017.  
  https://arxiv.org/abs/1702.03275
- *How Does Batch Normalization Help Optimization? (No, It Is Not About Internal Covariate Shift)*, 2018.  
  https://arxiv.org/abs/1805.11604

### 9.5.3 APIs

- Keras Regularizers API.  
  https://keras.io/regularizers/
- Keras Core Layers API.  
  https://keras.io/layers/core/
- Keras Convolutional Layers API.  
  https://keras.io/layers/convolutional/
- Keras Recurrent Layers API.  
  https://keras.io/layers/recurrent/
- BatchNormalization Keras API.  
  https://keras.io/layers/normalization/
- sklearn.datasets.make_circles API.  
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_circles.html

### 9.5.4 Articles

- Batch normalization, Wikipedia.  
  https://en.wikipedia.org/wiki/Batch_normalization
- Batch Normalization before or after ReLU?, Reddit.  
  https://www.reddit.com/r/MachineLearning/comments/67gonq/d_batch_normalization_before_or_after_relu/
- The Batch Normalization layer of Keras is broken, Vasilis Vryniotis, 2018.  
  http://blog.datumbox.com/the-batch-normalization-layer-of-keras-is-broken/
- Studies of Batch Normalization Before and After Activation Function.  
  https://github.com/ducha-aiki/caffenet-benchmark/blob/master/batchnorm.md

## 9.6 Summary

In this tutorial, you discovered the batch normalization method used to accelerate the training of deep learning neural networks. Specifically, you learned:

- Deep neural networks are challenging to train, not least because the input from prior layers can change after weight updates.
- Batch normalization is a technique to standardize the inputs to a network, applied to either the activations of a prior layer or inputs directly.
- Batch normalization accelerates training, in some cases by halving the number of epochs (or better), and provides some regularization effect, reducing generalization error.

### 9.6.1 Next

In the next tutorial, you will discover how to develop deeper neural network models with greedy layer-wise pretraining.
