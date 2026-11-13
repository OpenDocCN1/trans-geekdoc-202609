
In total, this means the total number of values to optimize is

$$
\mathcal{N} = \sum_{l=1}^L (U_{l-1} + 1) U_l + U_L + 1
$$

As in any model, the number of parameters should be much smaller than the number of instances. There is no fixed ratio, but it is preferable if the sample size is at least ten times larger than the number of parameters. Below a ratio of 5, the risk of overfitting is high. Given the amount of data readily available, this constraint is seldom an issue, unless one wishes to work with a very large network.

The number of hidden layers in current financial applications rarely exceeds three or four. The number of units per layer ($U_k$) is often chosen to follow the geometric pyramid rule (see, e.g., Masters (1993)). If there are $L$ hidden layers, with $I$ features in the input and $O$ dimensions in the output (for regression tasks, $O=1$), then, for the $k^{th}$ layer, a rule of thumb for the number of units is

$$
U_k \approx \left[ O \frac{I}{O}^{\frac{L+1-k}{L+1}} \right].
$$

If there is only one intermediate layer, the recommended proxy is the integer part of $\sqrt{IO}$. If not, the network starts with many units and the number of unit decreases exponentially towards the output size. Often, the number of layers is a power of two because, in high dimensions, networks are trained on Graphics Processing Units (GPUs) or Tensor Processing Units (TPUs). Both pieces of hardware can be used optimally when the inputs have sizes equals to powers of two.

Several studies have shown that very large architectures do not always perform better than more shallow ones (e.g., Gu et al. (2020b) and Orioloye et al. (2019) for high frequency data, i.e., not factor-based). As a rule of thumb, a maximum of three hidden layers seem to be sufficient for prediction purposes.

## 7.3.2 Frequency of weight updates and learning duration

In the expression (7.2), it is implicit that the computation is performed for one given instance. If the sample size is very large (hundreds of thousands or millions of instances), updating the weights according to each point is computationally too costly. The updating is then performed on groups of instances which are called batches. The sample is (randomly) split into batches of fixed sizes and each update is performed following the rule:

$$
\mathbf{W} \leftarrow \mathbf{W} - \eta \frac{\partial_{i \in \text{batch}} D(\hat{y}_i)/\text{card(batch)}}{\partial \mathbf{W}}.\quad (7.11)
$$

The change in weights is computed over the average loss computed over all instances in the batch. The terminology for training includes:

- epoch: one epoch is reached when each instance of the sample has contributed to the update of the weights (i.e., the training). Often, training a NN requires several epochs and up to a few dozen.
- batch size: the batch size is the number of samples used for one single update of weights.
- iterations: the number of iterations can mean alternatively the ratio of sample size divided by batch size or this ratio multiplied by the number of epochs. It’s either the number of weight updates required to reach one epoch or the total number of updates during the whole training.

When the batch is equal to only one instance, the method is referred to as ‘stochastic gradient descent’ (SGD): the instance is chosen randomly. When the batch size is strictly above one and below the total number of instances, the learning is performed via ‘mini’ batches, that is, small groups of instances. The batches are also chosen randomly, but without replacement in the sample because for one epoch, the union of batches must be equal to the full training sample.

It is impossible to know in advance what a good number of epochs is. Sometimes, the network stops learning after just 5 epochs (the validation loss does not decrease anymore). In some cases when the validation sample is drawn from a distribution close to that of the training sample, the network continues to learn even after 200 epochs. It is up to the user to test different values to evaluate the learning speed. In the examples below, we keep the number of epochs low for computational purposes.

## 7.3.3 Penalizations and dropout

At each level (layer), it is possible to enforce constraints or penalizations on the weights (and biases). Just as for tree methods, this helps slow down the learning to prevent overfitting on the training sample. Penalizations are enforced directly on the loss function and the objective function takes the form

\(O = \sum_{i=1}^I \text{loss}(y_i, \hat{y}_t) + \sum_k \lambda_k ||\mathbf{W}_k||_1 + \sum_j \delta_k ||\mathbf{W}_j||_2^2\),

where the subscripts \(k\) and \(j\) pertain to the weights to which the \(L^1\) and (or) \(L^2\) penalization is applied.

In addition, specific constraints can be enforced on the weights directly during the training. Typically, two types of constraints are used:

- norm constraints: a maximum norm is fixed for the weight vectors or matrices;
- non-negativity constraint: all weights must be positive or zero.

Lastly, another (somewhat exotic) way to reduce the risk of overfitting is simply to reduce the size (number of parameters) of the model. Srivastava et al. (2014) propose to omit units during training (hence the term ‘dropout’). The weights of randomly chosen units are set to zero during training. All links from and to the unit are ignored, which mechanically shrinks the network. In the testing phase, all units are back, but the values (weights) must be scaled to account for the missing activations during the training phase.

The interested reader can check the advice compiled in Bengio (2012) and Smith (2018) for further tips on how to configure neural networks. A paper dedicated to hyperparameter tuning for stock return prediction is Lee (2020).

## 7.4 Code samples and comments for vanilla MLP

There are several frameworks and libraries that allow robust and flexible constructions of neural networks. Among them, Keras and Tensorflow (developed by Google) are probably the most used at the time we write this book (PyTorch, from Facebook, is one alternative). For simplicity and because we believe it is the best choice, we implement the NN with Keras (which is the high level API of Tensorflow, see https://www.tensorflow.org). The original Python implementation is referred on https://keras.io, and the details for the R version can be found here: https://keras.rstudio.com. We recommend a thorough installation before proceeding. Because the native versions of Tensorflow and Keras are written in Python (and accessed by R via the reticulate package), a running version of Python is required below. To install Keras, please follow the instructions provided at https://keras.rstudio.com.

In this section, we provide a detailed (though far from exhaustive) account of how to train neural networks with Keras. For the sake of completeness, we proceed in two steps. The first one relates to a very simple regression exercise. Its purpose is to get the reader familiar with the syntax of Keras. In the second step, we lay out many of the options proposed by Keras to perform a classification exercise. With these two examples, we thus cover most of the mainstream topics falling under the umbrella of feed-forward multilayered perceptrons.

## 7.4.1 Regression example

Before we head to the core of the NN, a short stage of data preparation is required. Just as for penalized regressions (glmnet package) and boosted trees (xgboost package), the data must be sorted into four parts which are the combination of two dichotomies: training versus testing and labels versus features. We define the corresponding variables below. For simplicity, the first example is a regression exercise. A classification task will be detailed below.

```
NN_train_features <- dplyr::select(training_sample, features) %>%   # Training features
as.matrix()                                   # Matrix = important
NN_train_labels <- training_sample$R1M_Usd     # Training labels
NN_test_features <- dplyr::select(testing_sample, features) %>% # Testing features
as.matrix()                                   # Matrix = important
NN_test_labels <- testing_sample$R1M_Usd      # Testing labels
```

In Keras, the training of neural networks is performed through three steps:

- 1. Defining the structure/architecture of the network;
- 2. Setting the loss function and learning process (options on the updating of weights);
- 3. Train by specifying the batch sizes and number of rounds (epochs).

We start with a very simple architecture with two hidden layers.

```
library(keras)
# install_keras() # To complete installation
model <- keras_model_sequential()
```
