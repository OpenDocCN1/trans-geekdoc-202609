
### 2.5.3 Articles
- How many hidden layers should I use?, comp.ai.neural-nets FAQ.
http://www.faqs.org/faqs/ai-faq/neural-nets/part3/section-9.html

## 2.6 Summary
In this tutorial, you discovered how to control the capacity of a neural network model and how capacity impacts what a model is capable of learning. Specifically, you learned:
- Neural network model capacity is controlled both by the number of nodes and the number of layers in the model.
- A model with a single hidden layer and a sufficient number of nodes has the capability of learning any mapping function, but the chosen learning algorithm may or may not be able to realize this capability.
- Increasing the number of layers provides a short-cut to increasing the capacity of the model with fewer resources, and modern techniques allow learning algorithms to successfully train deep models.

### 2.6.1 Next
In the next tutorial, you will discover how the batch size controls the precision of the estimate of the error gradient that in turn controls the stability and speed of convergence.

## Chapter 3
## Configure Gradient Precision with Batch Size
Neural networks are trained using gradient descent where the estimate of the error used to update the weights is calculated based on a subset of the training dataset. The number of examples from the training dataset used in the estimate of the error gradient is called the batch size and is an important hyperparameter that influences the dynamics of the learning algorithm. It is important to explore the dynamics of your model to ensure that you’re getting the most out of it. In this tutorial, you will discover three different flavors of gradient descent and how to explore and diagnose the effect of batch size on the learning process. After completing this tutorial, you will know:
- Batch size controls the accuracy of the estimate of the error gradient when training neural networks.
- Batch, Stochastic, and Minibatch gradient descent are the three main flavors of the learning algorithm.
- There is a tension between batch size and the speed and stability of the learning process.

Let’s get started.

## 3.1 Batch Size and Gradient Descent
Neural networks are trained using the stochastic gradient descent optimization algorithm. This involves using the current state of the model to make a prediction, comparing the prediction to the actual values, and using the difference as an estimate of the error gradient. This error gradient is then used to update the model weights and the process is repeated. The error gradient is a statistical estimate. The more training examples used in the estimate, the more accurate this estimate will be and the more likely that the weights of the network will be adjusted in a way that will improve the performance of the model. The improved estimate of the error gradient comes at the computational cost of having to use the model to make many more predictions before the estimate can be calculated, and in turn, the weights updated.

Optimization algorithms that use the entire training set are called batch or deterministic gradient methods, because they process all of the training examples simultaneously in a large batch.

— Page 278, *Deep Learning*, 2016.

Alternately, using fewer examples results in a less accurate estimate of the error gradient that is highly dependent on the specific training examples used. This results in a noisy estimate that, in turn, results in noisy updates to the model weights, e.g. many updates with perhaps quite different estimates of the error gradient. Nevertheless, these noisy updates can result in faster learning and sometimes a more robust model.

Optimization algorithms that use only a single example at a time are sometimes called stochastic or sometimes online methods. The term online is usually reserved for the case where the examples are drawn from a stream of continually created examples rather than from a fixed-size training set over which several passes are made.

— Page 278, *Deep Learning*, 2016.

The number of training examples used in the estimate of the error gradient is a hyperparameter for the learning algorithm called the *batch size*, or simply the *batch*. A batch size of 32 means that 32 samples from the training dataset will be used to estimate the error gradient before the model weights are updated. One training epoch means that the learning algorithm has made one pass through the training dataset (using every example once), where examples were separated into randomly selected *batch size* groups.

Historically, a training algorithm where the batch size is set to the total number of training examples is called *batch gradient descent* and a training algorithm where the batch size is set to 1 training example is called *stochastic gradient descent* or *online gradient descent*. A configuration of the batch size anywhere in between (e.g. more than 1 example and less than the number of examples in the training dataset) is called *minibatch gradient descent*.

- **Batch Gradient Descent**. Batch size is set to the total number of examples in the training dataset.
- **Stochastic Gradient Descent**. Batch size is set to one.
- **Minibatch Gradient Descent**. Batch size is set to more than one and less than the total number of examples in the training dataset.

For shorthand, the algorithm is often referred to as stochastic gradient descent regardless of the batch size. Given that very large datasets are often used to train deep learning neural networks, the batch size is rarely set to the size of the training dataset. Smaller batch sizes are used for two main reasons:
- Smaller batch sizes are noisy, offering a regularizing effect and lower generalization error.
- Smaller batch sizes make it easier to fit one batch worth of training data in memory (i.e. when using a GPU that has access to less local memory than system RAM).

A third reason is that the batch size is often set at something small, such as 32 examples, and is not tuned by the practitioner. Small batch sizes such as 32 do work well generally.

... [batch size] is typically chosen between 1 and a few hundreds, e.g. [batch size] = 32 is a good default value

> — *Practical recommendations for gradient-based training of deep architectures*, 2012.

The presented results confirm that using small batch sizes achieves the best training stability and generalization performance, for a given computational cost, across a wide range of experiments. In all cases the best results have been obtained with batch sizes m = 32 or smaller, often as small as m = 2 or m = 4.

> — *Revisiting Small Batch Training for Deep Neural Networks*, 2018.

Nevertheless, the batch size impacts how quickly a model learns and the stability of the learning process. It is an important hyperparameter that should be well understood and tuned by the deep learning practitioner.

## 3.2 Gradient Descent Keras API
Keras allows you to train your model using stochastic, batch, or minibatch gradient descent. This can be achieved by setting the `batch_size` argument on the call to the `fit()` function when training your model. Let’s take a look at each approach in turn.

### 3.2.1 Batch Size Keras API
The example below sets the `batch_size` argument to 1 for stochastic gradient descent.

```
...
model.fit(trainX, trainY, batch_size=1)
```

Listing 3.1: Example of stochastic gradient descent in Keras.

### 3.2.2 Batch Gradient Descent in Keras
The example below sets the `batch_size` argument to the number of samples in the training dataset for batch gradient descent.

```
...
model.fit(trainX, trainY, batch_size=len(trainX))
```

Listing 3.2: Example of batch gradient descent in Keras.

### 3.2.3 Minibatch Gradient Descent in Keras
The example below uses the default batch size of 32 for the batch_size argument, which is more than 1 for stochastic gradient descent and less than the size of your training dataset for batch gradient descent.

```
...
model.fit(trainX, trainY)
```

Listing 3.3: Example of minibatch gradient descent with default batch size in Keras.

Alternately, the batch_size can be specified to something other than 1 or the number of samples in the training dataset, such as 64.

```
...
model.fit(trainX, trainY, batch_size=64)
```

Listing 3.4: Example of minibatch gradient descent in Keras.

## 3.3 Batch Size Case Study
In this section, we will demonstrate how to use gradient descent batch size to control learning with a MLP on a simple classification problem. This example provides a template for exploring batch size with your own neural network for classification and regression problems.

### 3.3.1 Multiclass Classification Problem
We will use a small multiclass classification problem as the basis to demonstrate the effect of batch size on learning. The scikit-learn class provides the make_blobs() function that can be used to create a multiclass classification problem with the prescribed number of samples, input variables, classes, and variance of samples within a class. The problem can be configured to have two input variables (to represent the x and y coordinates of the points) and a standard deviation of 2.0 for points within each group. We will use the same random state (seed for the pseudorandom number generator) to ensure that we always get the same data points.

```
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
```

Listing 3.5: Example of generating samples for the blobs problem.

The results are the input and output elements of a dataset that we can model. In order to get a feeling for the complexity of the problem, we can plot each point on a two-dimensional scatter plot and color each point by class value. The complete example is listed below.

```
# scatter plot of blobs dataset
from sklearn.datasets.samples_generator import make_blobs
from matplotlib import pyplot
from numpy import where
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
# scatter plot for each class value
for class_value in range(3):
    # select indices of points with the class label
