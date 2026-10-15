
In this case, the results suggest that 0.01 or 0.001 may be sufficient and may provide good bounds for further grid searching.

```
Param: 0.100000, Train: 0.967, Test: 0.829
Param: 0.010000, Train: 1.000, Test: 0.943
Param: 0.001000, Train: 1.000, Test: 0.943
Param: 0.000100, Train: 1.000, Test: 0.929
Param: 0.000010, Train: 1.000, Test: 0.929
Param: 0.000001, Train: 1.000, Test: 0.914
```

Listing 13.20: Example output from grid searching weight regularization values for the two moons problem.

A line plot of the results is also created, showing the increase in test accuracy with larger weight regularization parameter values, at least to a point. We can see that using the largest value of 0.1 results in a large drop in both train and test accuracy.

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_302_0.png)

Figure 13.4: Line Plot of Model Accuracy on Train and Test Datasets With Different Weight Regularization Parameters.

### 13.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- **Try Alternates**. Update the example to use L1 or the combined L1L2 methods instead of L2 regularization.
- **Report Weight Norm**. Update the example to calculate the magnitude of the network weights and demonstrate that regularization indeed made the magnitude smaller.
- **Regularize Output Layer**. Update the example to regularize the output layer of the model and compare the results.
- **Regularize Bias**. Update the example to regularize the bias weight and compare the results.
- **Repeated Model Evaluation**. Update the example to fit and evaluate the model multiple times and report the mean and standard deviation of model performance.
- **Grid Search Along Order of Magnitude**. Update the grid search example to grid search within the best-performing order of magnitude of parameter values.
- **Repeated Regularization of Model**. Create a new example to continue the training of a fit model with increasing levels of regularization (e.g. 1E-6, 1E-5, etc.) and see if it results in a better performing model on the test set.

If you explore any of these extensions, I’d love to know.

### 13.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

#### 13.5.1 Books

- Section 7.1: Parameter Norm Penalties, *Deep Learning*, 2016.
  https://amzn.to/2NJW3gE
- Section 5.5: Regularization in Neural Networks, *Pattern Recognition and Machine Learning*, 2006.
  https://amzn.to/2Q2rEeP
- Section 16.5: Weight Decay, *Neural Smithing: Supervised Learning in Feedforward Artificial Neural Networks*, 1999.
  https://amzn.to/2PBsezv
- Section 4.4.2: Adding weight regularization, *Deep Learning with Python*, 2017.
  https://amzn.to/2wVqZDq
- Section 6.2: Shrinkage Methods, *An Introduction to Statistical Learning: with Applications in R*, 2013.
  https://amzn.to/2MXGK7I

#### 13.5.2 Papers

- *A Simple Weight Decay Can Improve Generalization*, 1992.
  https://papers.nips.cc/paper/563-a-simple-weight-decay-can-improve-generalization
- *Note on generalization, regularization and architecture selection in nonlinear learning systems*, 1991.
  https://ieeexplore.ieee.org/abstract/document/239541/

#### 13.5.3 APIs

- Keras Regularization API.
  https://keras.io/regularizers/
- Keras Core Layers API.
  https://keras.io/layers/core/
- Keras Convolutional Layers API.
  https://keras.io/layers/convolutional/
- Keras Recurrent Layers API.
  https://keras.io/layers/recurrent/
- `sklearn.datasets.make_moons` API.
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_moons.html
- `matplotlib.pyplot.semilogx` API.
  https://matplotlib.org/api/_as_gen/matplotlib.pyplot.semilogx.html

#### 13.5.4 Articles

- Regularization (mathematics), Wikipedia.
  https://en.wikipedia.org/wiki/Regularization_(mathematics)
- Weight Decay in Neural Networks, Metacademy.
  https://metacademy.org/graphs/concepts/weight_decay_neural_networks
- Why large weights are prohibited in neural networks?
  https://datascience.stackexchange.com/questions/23287/why-large-weights-are-prohibited-in-neural-networks

### 13.6 Summary

In this tutorial, you discovered weight regularization as an approach to reduce overfitting for neural networks. Specifically, you learned:

- Large weights in a neural network are a sign of a more complex network that has overfit the training data.
- Penalizing a network based on the size of the network weights during training can reduce overfitting.
- An L1 or L2 vector norm penalty can be added to the optimization of the network to encourage smaller weights.

#### 13.6.1 Next

In the next tutorial, discover how to update the loss function to encourage the training of models with simpler internal representations.

## Chapter 14: Sparse Representations with Activity Regularization

Deep learning models are capable of automatically learning a rich internal representation from raw input data. This is called feature or representation learning. Better learned representations, in turn, can lead to better insights into the domain, e.g. via visualization of learned features, and to better predictive models that make use of the learned features. A problem with learned features is that they can be too specialized to the training data, or overfit, and not generalize well to new examples. Large values in the learned representation can be a sign of the representation being overfit. Activity or representation regularization provides a technique to encourage the learned representations, the output or activation of the hidden layer or layers of the network, to stay small and sparse. In this tutorial, you will discover activation regularization as a technique to improve the generalization of learned features in neural networks. After reading this tutorial, you will know:

- Neural networks learn features from data and models, such as autoencoders and encoder-decoder models, and explicitly seek effective learned representations.
- Similar to weights, large values in learned features, e.g. large activations, may indicate an overfit model.
- The addition of penalties to the loss function that penalize a model in proportion to the magnitude of the activations may result in more robust and generalized learned features.

Let’s get started.

### 14.1 Activity Regularization

In this section you will discover the problem with neural networks that have large activity, a technique that you can use to encourage the development of models with sparse activity called activity regularization and tips for using this technique in your own projects.

#### 14.1.1 Problem With Learned Features

Deep learning models are able to perform feature learning. That is, during the training of the network, the model will automatically extract the salient features from the input patterns or *learn features*. These features may be used in the network in order to predict a quantity for regression or predict a class value for classification. These internal representations are tangible things. The output of a hidden layer within the network represent the learned features by the model at that point in the network.

There is a field of study focused on the efficient and effective automatic learning of features, often investigated by having a network reduce an input to a small learned feature before using a second network to reconstruct the original input from the learned feature. Models of this type are called auto-encoders, or encoder-decoders, and their learned features can be useful to learn more about the domain (e.g. via visualization) and in predictive models. The learned features, or *encoded inputs*, must be large enough to capture the salient features of the input but also focused enough to not overfit the specific examples in the training dataset. As such, there is a tension between the expressiveness and the generalization of the learned features.

> More importantly, when the dimension of the code in an encoder-decoder architecture is larger than the input, it is necessary to limit the amount of information carried by the code, lest the encoder-decoder may simply learn the identity function in a trivial way and produce uninteresting features.

> — *Unsupervised Learning of Invariant Feature Hierarchies with Applications to Object Recognition*, 2007.

In the same way that large weights in the network can signify an unstable and overfit model, large output values in the learned features can signify the same problems. It is desirable to have small values in the learned features, e.g. small outputs or activations from the encoder network.

#### 14.1.2 Encourage Small Activations

The loss function of the network can be updated to penalize models in proportion to the magnitude of their activation. This is similar to *weight regularization* where the loss function is updated to penalize the model in proportion to the magnitude of the weights. The output of a layer is referred to as its *activation* or *activity*, as such, this form of penalty or regularization is referred to as *activation regularization* or *activity regularization*.

> ... place a penalty on the activations of the units in a neural network, encouraging their activations to be sparse.

> — Page 254, *Deep Learning*, 2016.

The output of an encoder or, generally, the output of a hidden layer in a neural network may be considered the representation of the problem at that point in the model. As such, this type of penalty may also be referred to as *representation regularization*. The desire to have small activations or even very few activations with mostly zero values is also called a desire for sparsity. As such, this type of penalty is also referred to as *sparse feature learning*.

> One way to limit the information content of an overcomplete code is to make it sparse.

> — *Unsupervised Learning of Invariant Feature Hierarchies with Applications to Object Recognition*, 2007.
