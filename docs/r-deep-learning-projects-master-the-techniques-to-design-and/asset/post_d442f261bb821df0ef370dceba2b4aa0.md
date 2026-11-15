
where f(z) is an activation function. Typical choices for the activation function in simple networks include logistic function (more often called sigmoid function) and tanh function (which can be considered a re-scaled version of logistic function):

```math
sigmoid(z) = \frac{1}{1 + e^{-z}}

tanh(z) = \frac{e^{-z} - e^{z}}{e^{z} + e^{-z}} = \frac{2}{1 + e^{-2z}} - 1
```

Plots of these two functions are as follows:

![](img/da8fb67f2acf661518076e08b6ffd9b9_36_0.png)

We will be using the logistic function in our single-layered networks for now.

For a case of K possible classes, the weight matrix \( w^{(2)} \) connecting the hidden layer to the output layer is of size H by K. Each column \( w_k^{(2)} \) represents the coefficients associated with class k. The input to the output layer is the output of the hidden layer \( a^{(2)} = \{a_1^{(2)}, a_2^{(2)}, \dots, a_l^{(2)}\} \), the probability of x being class k can be expressed mathematically as (for consistency, we denote it as \( a_k^{(3)} \)):

```math
a_k^{(3)} = f(z^{(3)}) = softmax_k(W^{(2)}a^{(2)})
```

Similarly, given m training samples, to train the neural network, we learn all weights \( w = \{w^{(1)}, w^{(2)}\} \) using gradient descent with the goal of minimizing the mean squared error cost J(w).

Computation of the gradients \(\Delta w\) can be realized through the **backpropagation algorithm**.
The idea of the backpropagation algorithm is the following, we first travel through the network and compute all outputs of the hidden layers and output layer; then moving backward from the last layer, we calculate how much each node contributed to the error in the final output and propagate it back to the previous layers. In our single-layer network, the detailed steps are:

- 1. Compute \(a^{(2)}\) for the hidden layer and feed them to the output layer to compute the outputs \(a^{(3)}\)
- 2. For the output layer, compute the derivative of the cost function of one sample \(\delta_k^{(3)} = \frac{\partial}{\partial z_k^{(3)}} J(W) = -(y_k - a_k^{(3)}) \cdot f'(z_k^{(3)})\) with respect to each unit, \(\delta^{(3)} = -(y - a^{(3)}) \cdot f'(z^{(3)})\), rewritten for the entire layer
- 3. For the hidden layer, we compute the error term \(\delta^{(2)}\) based on a weighted average of \(\delta^{(3)} : \delta^{(2)} = ((W^{(2)})^T \delta^{(3)}) \cdot f'(z^{(2)})\)
- 4. Compute the gradients applying the chain rule:

```math
\triangle W^{(2)} = \frac{\partial J(W)}{\partial z_k^{(3)}} \frac{\partial z_k^{(3)}}{\partial W^{(2)}} = \delta^{(3)} (a^{(2)})^T
```

```math
\triangle W^{(1)} = \frac{\partial J(W)}{\partial z_k^{(2)}} \frac{\partial z_k^{(2)}}{\partial W^{(1)}} = \delta^{(2)} (x)^T
```

We repeatedly update all weights by taking these steps until the cost function converges.

After a brief review of the single-layer network, we can then apply it as the second solution to our digit classification project.

Again, we use the `nnet` package to implement our single-layer network:

```r
> model_nn <- nnet(label ~ ., data=data_train, size=50, maxit=300,
MaxNWts=100000, decay=1e-4)
# weights: 39760
initial value 108597.598656
iter 10 value 27708.286001
iter 20 value 16027.005297
iter 30 value 14058.141050
iter 40 value 12615.442747
iter 50 value 11793.700937
iter 60 value 11026.672273
iter 70 value 10654.855058
iter 80 value 10193.580947
iter 90 value 9854.836168
iter 100 value 9544.973159
iter 110 value 9307.192737
iter 120 value 9043.028253
iter 130 value 8845.069307
iter 140 value 8686.707561
iter 150 value 8525.104362
iter 160 value 8281.609223
iter 170 value 8140.051273
iter 180 value 7998.721024
iter 190 value 7854.388240
iter 200 value 7712.459027
iter 210 value 7636.945553
iter 220 value 7557.675909
iter 230 value 7449.854506
iter 240 value 7355.021651
iter 250 value 7259.186906
iter 260 value 7192.798089
iter 270 value 7055.027833
iter 280 value 6957.926522
iter 290 value 6866.641511
iter 300 value 6778.342997
final value 6778.342997
stopped after 300 iterations
```

We fit the model with parameters including:

- size=50: There are 50 hidden units in the hidden layer.
- MaxNWts=100000: It allows at most 100,000 weights. In our case, there are (784 input dimensions + 1 bias) * 50 hidden units = 39,250 elements in the weight matrix w<sup>(1)</sup> and (50 hidden units + 1 bias) * 10 output units = 510 elements in the weight matrix w<sup>(2)</sup>. So there are 39,760 weights in total.
- decay=1e-4: The regularization strength, the weight decay is 0.0001.
- maxit=300: The maximum number of iterations is set to be 300.

We apply the trained network model on the testing set:

```r
> prediction_nn <- predict(model_nn, data_test, type = "class")
> cm_nn = table(data_test$label, prediction_nn)
> cm_nn
```

| True \ Predicted | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 987 | 0 | 3 | 3 | 2 | 11 | 10 | 7 | 5 | 5 |
| 1 | 0 | 1134 | 9 | 6 | 0 | 2 | 0 | 5 | 11 | 4 |
| 2 | 14 | 9 | 918 | 31 | 11 | 11 | 7 | 15 | 22 | 6 |
| 3 | 3 | 1 | 17 | 966 | 0 | 41 | 3 | 14 | 24 | 18 |
| 4 | 4 | 3 | 8 | 2 | 929 | 4 | 11 | 11 | 5 | 41 |
| 5 | 12 | 2 | 6 | 17 | 5 | 851 | 15 | 9 | 26 | 5 |
| 6 | 10 | 1 | 14 | 0 | 9 | 14 | 970 | 0 | 15 | 1 |
| 7 | 4 | 4 | 23 | 6 | 5 | 2 | 0 | 1010 | 7 | 39 |
| 8 | 5 | 15 | 9 | 18 | 5 | 31 | 9 | 4 | 912 | 7 |
| 9 | 11 | 2 | 1 | 20 | 52 | 4 | 0 | 36 | 8 | 913 |

```r
> accuracy_nn = mean(prediction_nn == data_test$label)
> accuracy_nn
[1] 0.9135944
```

Better than our first attempt! Can we do better with deep learning models, say intuitively more hidden layers? Sure.

## Adding more hidden layers to the networks

We have just achieved 91.3% accuracy with a single-layer neural network model. Theoretically, we can obtain a better one with more than one hidden layer. As an example, we provide a solution of a deep neural network model with two hidden layers:

![](img/da8fb67f2acf661518076e08b6ffd9b9_39_0.png)

Weight optimization in feed-forward deep neural networks is also realized through the backpropagation algorithm, which is identical to single-layer networks. However, the more layers, the higher the computation complexity, and the slower the model convergence. One way to accelerate the weight optimization, is to use a more computational efficient activation function. The most popular one in recent years is the rectified linear unit (ReLU):

```math
relu(z) = z^+ = \max(0, z)
```

![](img/da8fb67f2acf661518076e08b6ffd9b9_40_0.png)

```math
relu'(z) = \begin{cases} 0, z < 0 \\ 1, z \ge 0 \end{cases}
```

Thanks to the properties of its derivative, there are two main advantages of using the ReLU activation function over sigmoid:

- Faster learning because of constant value of \( relu'(z) \), compared to that of the logistic function \( sigmoid'(z) = sigmoid(z) * (1 - sigmoid(z)) \).
- Less likely to have the vanishing gradient problem, exponential decrease of gradient, which can be found in networks with multiple stacked sigmoid layers. As we multiply the derivative of the activation function when calculating errors \(\delta\) for each layer, and the maximal value of \( sigmoid'(z) \) is ¼, the gradients will decrease exponentially as we stack more and more sigmoid layers.

The `nnet` package we used in previous sections is (by now) only capable of modeling a single-layer network. In this chapter, we use the `MXNet` package to implement deep neural networks with multiple hidden layers. MXNet (`https://mxnet.incubator.apache.org/`) is a deep learning framework that supports programming languages include R, Scala, Python, Julia, C++, and Perl. It is developed by the DMLC (`http://dmlc.ml/`) team, a group of experts collaborating on open-source machine learning projects. It is portable and can scale to multiple CPUs, multiple GPUs and multiple machines, for example, in the cloud. Most importantly, it allows us to flexibly and efficiently construct state-of-the-art deep learning models, including deep neural networks, CNNs and RNNs.

Let's install MXNet first:

```r
> cran <- getOption("repos")
> cran["dmlc"] <- "https://s3-us-west-2.amazonaws.com/apache-mxnet/R/CRAN/"
> options(repos = cran)
> if (!require("mxnet"))
install.packages("mxnet")
```

Now we can import MXNet and convert the data into the format preferred by the neural network models in MXNet:

```r
> require(mxnet)
> data.train <- data.matrix(data_train)
> data.train.x <- data_train[,-1]
> data.train.x <- t(data.train.x/255)
> data.train.y <- data_train[,1]
```

Note we scale the input features to a range from 0 to 1, by dividing the maximal possible value 255. Otherwise, the deep neural networks may be skewed towards some features and such skewness will accumulate over layers.

Now that the training dataset is ready, we can start constructing the network by defining its architecture as follows:

```r
> data <- mx.symbol.Variable("data")
> fc1 <- mx.symbol.FullyConnected(data, name="fc1", num_hidden=128)
> act1 <- mx.symbol.Activation(fc1, name="relu1", act_type="relu")
> fc2 <- mx.symbol.FullyConnected(act1, name="fc2", num_hidden=64)
> act2 <- mx.symbol.Activation(fc2, name="relu2", act_type="relu")
> fc3 <- mx.symbol.FullyConnected(act2, name="fc3", num_hidden=10)
> softmax <- mx.symbol.SoftmaxOutput(fc3, name="sm")
```

In the MXNet's Symbol API, we represent the network in the data type symbol. We begin with the input layer data, the input data, and follow up with the first hidden layer fc1 with 128 nodes, which fully connects with the input layer. We then attach the ReLU function to fc1 and output the activations act1 for this layer. Similarly, we chain another hidden layer fc2, with 64 nodes this time, and output ReLU-based activates act2. Finally, we end up with the output layer with a softmax function, generating 10 probabilities corresponding to 10 classes. The overall structure looks like this:
