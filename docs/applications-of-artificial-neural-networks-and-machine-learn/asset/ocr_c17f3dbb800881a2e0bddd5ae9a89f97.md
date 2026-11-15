![](bbox=[0.205, 0.085, 0.805, 0.405])

# Fig. 1.12 Softmax activation function

translation. An advantage of this function is that, as the value of x tends to negative infinity, the value of y approaches a constant value. As the value of x tends to positive infinity, the value of y also tends to positive infinity. The Swish function is a continuous and differentiable function. The slope of the Swish function curve is gentle and does not suddenly change direction like the RELU activation function (when the value of x is close to zero). In other words, the curve of this function changes its direction slowly from the value of 0 to a value smaller than 0 and then to values greater than 0.

In the RELU activation function, negative values were converted to 0; While these negative values may contain important information of data patterns. In the Swish function, due to the sparsity problem, only large negative values are converted to zero.

The Swish function is a “non-monotonous” function, which helps to learn the weights of the network. The problem of the deterioration of the RELU activation function does not occur in the Swish function.

Also, the disadvantages of this function are that the Swish function uses the sigmoid function in its calculations. For this reason, the calculations of this function are heavier than RELU activation functions.

Based on the investigations, the performance of this function is unstable and its output cannot be predicted in advance. Swish Activation Function shown in Fig. 1.13. The Swish formula is f (x) = x × sigmoid (x), where sigmoid(x) is normalized.