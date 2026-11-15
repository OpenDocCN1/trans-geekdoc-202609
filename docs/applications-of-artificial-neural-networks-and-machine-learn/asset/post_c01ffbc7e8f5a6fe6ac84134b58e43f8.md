
![](img/4048998719320644ee88964326fd7995_34_0.png)

Fig. 1.9 Leaky rectifier activation function

gradients. And the value of the gradient is very small for negative input values. This problem makes neural network learning time-consuming. Leaky Rectifier Activation Function shown in Fig. 1.9.

## 1.5.5 Parametric Rectifier Activation Function (PReLU)

The Parametric ReLU activation function is another type of ReLU function designed to address the issue of the ReLU function decay for negative inputs. It introduces a parameter, which determines the slope of the function’s curve in the negative segment, and is adjusted during neural network training and backpropagation. Compared to the Leaky ReLU function, the Parametric ReLU offers distinct advantages. Despite the Leaky ReLU’s attempt to mitigate signal loss by employing a small slope for negative inputs, it still struggles to fully combat the problem of inactive nodes in the network, resulting in the loss of crucial input information. The Parametric ReLU function’s formula is f (x) = max(αx, x), where α is a learnable parameter set to one for negative inputs. However, a drawback of the Parametric ReLU is its dependency on the parameter value, producing varying behaviors across different problems. Parametric Rectifier Activation Function shown in Fig. 1.10.

![](img/4048998719320644ee88964326fd7995_35_0.png)

Fig. 1.10 Parametric rectifier activation function

## 1.5.6 Exponential Linear Unit Activation Function (ELU)

ELU's activation function or exponential linear unit activation function is one of the types of RELU activation function, which considers a slope for the negative input values of the function. In the activation functions of Leaky RELU and Parametric RELU, the graph of the functions in the negative area is a straight line. The ELU activation function defines a logarithmic curve for this area. One of the advantages of the ELU activation function compared to other RELU functions is that the slope of the ELU function curve is very gentle and this feature continues until reaching the value of -\(\alpha\). Such a gentle slope is not seen in the activation function of RELU. This function prevents the deterioration of the function by considering a logarithmic curve for negative input values. Also, this feature makes the weights and bias values learned correctly.

And also the limitations of the ELU activation function is that due to performing exponential calculations, the calculation time increases. And in the ELU function, there is no parameter (similar to parameter a in the Parametric RELU function) whose value is also learned during neural network learning. To be Gradient explosion problem may also occur when using this function. Exponential Linear Unit Activation Function shown in Fig. 1.11.

The formula of the ELU function is:

```
f(x) = \begin{cases} x & \text{if } x \ge 0 \\ \alpha(e^x - 1) & \text{if } x < 0 \end{cases} (1.6)
```

![](img/4048998719320644ee88964326fd7995_36_0.png)

Fig. 1.11 Exponential linear unit activation function

## 1.5.7 Softmax Activation Function

The idea of designing the Softmax function is taken from the sigmoid function. As mentioned, based on the output of the sigmoid function, which is between 0 and 1, this function is used to calculate the probability. However, the sigmoid activation function has a fundamental problem. If several outputs are produced as 0.8, 0.9, 0.6, 0.7 and 0.8, the sum of all outputs will be greater than 1; while the sum of probabilities must be 1. Softmax activation function is considered a type of sigmoid function. In other words, the Softmax function is a combination of several sigmoid functions that calculate relative probabilities. In other words, the Softmax function determines the probabilities of several classes. Usually, in “Multi-Class Classification” tasks, the Softmax activation function is used in the last layer of the neural network. The Softmax formula is f (xi ) = e^xi /sum(e^x ), where xi is the value of each input node and sum(e^x ) is the sum of all input values. Softmax Activation Function shown in Fig. 1.12.

## 1.5.8 Swish Activation Function

Swish is a non-linear activation function introduced in 2017 by Google Brain. This function offers high flexibility and better performance than ReLU. The Swish activation function is used in problems such as “Image Classification” and machine translation. An advantage of this function is that, as the value of x tends to negative infinity, the value of y approaches a constant value. As the value of x tends to positive infinity, the value of y also tends to positive infinity. The Swish function is a continuous and differentiable function. The slope of the Swish function curve is gentle and does not suddenly change direction like the RELU activation function (when the value of x is close to zero). In other words, the curve of this function changes its direction slowly from the value of 0 to a value smaller than 0 and then to values greater than 0.

In the RELU activation function, negative values were converted to 0; While these negative values may contain important information of data patterns. In the Swish function, due to the sparsity problem, only large negative values are converted to zero.

The Swish function is a “non-monotonous” function, which helps to learn the weights of the network. The problem of the deterioration of the RELU activation function does not occur in the Swish function.

Also, the disadvantages of this function are that the Swish function uses the sigmoid function in its calculations. For this reason, the calculations of this function are heavier than RELU activation functions.

Based on the investigations, the performance of this function is unstable and its output cannot be predicted in advance. Swish Activation Function shown in Fig. 1.13. The Swish formula is f (x) = x × sigmoid (x), where sigmoid(x) is normalized.

![](img/4048998719320644ee88964326fd7995_37_0.png)

Fig. 1.12 Softmax activation function

translation. An advantage of this function is that, as the value of x tends to negative infinity, the value of y approaches a constant value. As the value of x tends to positive infinity, the value of y also tends to positive infinity. The Swish function is a continuous and differentiable function. The slope of the Swish function curve is gentle and does not suddenly change direction like the RELU activation function (when the value of x is close to zero). In other words, the curve of this function changes its direction slowly from the value of 0 to a value smaller than 0 and then to values greater than 0.

In the RELU activation function, negative values were converted to 0; While these negative values may contain important information of data patterns. In the Swish function, due to the sparsity problem, only large negative values are converted to zero.

The Swish function is a “non-monotonous” function, which helps to learn the weights of the network. The problem of the deterioration of the RELU activation function does not occur in the Swish function.

Also, the disadvantages of this function are that the Swish function uses the sigmoid function in its calculations. For this reason, the calculations of this function are heavier than RELU activation functions.

Based on the investigations, the performance of this function is unstable and its output cannot be predicted in advance. Swish Activation Function shown in Fig. 1.13. The Swish formula is f (x) = x × sigmoid (x), where sigmoid(x) is normalized.

![](img/4048998719320644ee88964326fd7995_38_0.png)

Fig. 1.13 Swish activation function

## 1.5.9 Gaussian Error Linear Unit Activation Function (GELU)

The performance of Gaussian Error Linear Unit activation function, or GELU for short, is compatible with top models in the field of Natural Language Processing (NLP) such as Bert, ROBERTa, and ALBERT models. This activation function uses the features of the RELU function and model regularization methods such as dropout and zoneout.

The role of the RELU function and the random removal operation is to specify the output value of the node. In other words, the RELU function multiplies the input by 0 or 1 based on the input value, and in the process of random deletion, the values of the inputs are randomly multiplied by 0. The regulator of the current neural network model also randomly multiplies the input values by 1 so that these values are preserved in the output. In the GELU activation function, these three operations are combined. In other words, at first, the input values are randomly multiplied by the numbers 0 and 1, and finally the resulting values are sent to the GELU function to calculate the output of the function.

The inputs of the nodes follow the normal distribution after the Batch Normalization process. The input x is multiplied by the value m, where m is equal to m ~ Bernoulli(Φ(x)).

One of the advantages of GELU activation function is that in recent deep learning models, especially in the field of NLP, this function performed best compared to other functions. The GELU activation function avoids the gradient fading problem.

![](img/4048998719320644ee88964326fd7995_39_0.png)

Fig. 1.14 Gaussian error linear unit activation function

Since the activation function of GELU is considered a new function (although this function was introduced in 2016), its exact performance in all existing models in deep learning is still unclear, and its performance in all models needs to be investigated. Gaussian Error Linear Unit Activation Function shown in Fig. 1.14.

GELU formula:

```
f(x) = 0.5 \times x \times \left( 1 + \tanh\left( \sqrt{\frac{2}{\pi}} \right) (x + 0.044715x^3) \right) \quad (1.7)
```

## 1.5.10 Scaled Exponential Linear Unit Activation Function (SELU)

SELU activation function, which stands for Scaled Exponential Linear Unit, is a relatively new activation function in neural networks, which is based on the ELU (Exponential Linear Unit) function and the connection parameter delay. This function performs network normalization. In other words, this function keeps the mean and variance values of each layer. The SELU function uses both positive and negative input values to shift the average value, while RELU function ignores negative values. In this function, the gradient is used to set the variance value. SELU has special features such as self-normalization for depth models. The main advantage of the
