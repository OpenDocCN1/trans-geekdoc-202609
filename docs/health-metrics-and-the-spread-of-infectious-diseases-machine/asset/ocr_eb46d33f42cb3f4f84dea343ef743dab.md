# Model Framework Application Examples

The decision of which activation function depends on the task type (classification or regression), or due to performance considerations, such as the ReLU is computationally simple and efficient. The sigmoid function is used in binary classification problems, where the output is a probability between 0 and 1. The softmax function is used in multi-class classification problems, where the output is a probability distribution over multiple classes. Sometimes, you try a few and see which works best through cross-validation or tuning.

Given an input vector $x = [x_1, x_2, \dots, x_p]$ of size $p$, the model is composed of:

+   1. First Dense Layer

$$z^{(1)} = \sum_{i=1}^{p} W_i^{(1)}x_i + b^{(1)} \quad (8.1)$$

where $W r^{	imes p}$ are the weights, $b$ is the bias, and $z$ is the output.

+   2. First Activation(ReLU):

$$a^{(1)} = ReLU(z^{(1)}) = max(0, z^{(1)}) \quad (8.2)$$

+   3. Second Dense Layer Transformation:

$$z^{(2)} = \sum_{i=1}^{p} W_i^{(2)}x_i + b^{(2)} \quad (8.3)$$

+   4. Output Activation (Sigmoid):

$$a^{(2)} = Sigmoid(z^{(2)}) = \frac{1}{1 + e^{-z^{(2)}}} \quad (8.4)$

```
model <- keras_model_sequential(input_shape = c(p))
# simple model
model %%%%
layer_dense(units = 1) %%%%
layer_activation("relu") %%%%
layer_dense(units = 1, activation = "sigmoid")
```

The model is then compiled using the compile() function with which the use of a **loss function** optimises the results matching them against a minimum required value, and metrics used to reduce the error.

$$$y = \hat{y} + \epsilon \quad (8.5)$$$

where $y$ is the true value, $\hat{y}$ is the predicted value, and $\epsilon$ is the error.

The loss function is used to measure how well the model is performing, in this case a **binary crossentropy** loss function is used, to match the difference between original data and the model output, and apply model adjustments in case the difference is too high. The formula for binary crossentropy is: