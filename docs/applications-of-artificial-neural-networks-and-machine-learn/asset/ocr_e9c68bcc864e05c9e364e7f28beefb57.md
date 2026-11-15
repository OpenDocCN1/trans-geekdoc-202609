![](bbox=[0.21, 0.08, 0.79, 0.4])

Fig. 1.10 Parametric rectifier activation function

# ## 1.5.6 Exponential Linear Unit Activation Function (ELU)

ELUs activation function or exponential linear unit activation function is one of the types of RELU activation function, which considers a slope for the negative input values of the function. In the activation functions of Leaky RELU and Parametric RELU, the graph of the functions in the negative area is a straight line. The ELU activation function defines a logarithmic curve for this area. One of the advantages of the ELU activation function compared to other RELU functions is that the slope of the ELU function curve is very gentle and this feature continues until reaching the value of -\(\alpha\). Such a gentle slope is not seen in the activation function of RELU. This function prevents the deterioration of the function by considering a logarithmic curve for negative input values. Also, this feature makes the weights and bias values learned correctly.

And also the limitations of the ELU activation function is that due to performing exponential calculations, the calculation time increases. And in the ELU function, there is no parameter (similar to parameter a in the Parametric RELU function) whose value is also learned during neural network learning. To be Gradient explosion problem may also occur when using this function. Exponential Linear Unit Activation Function shown in Fig. 1.11.

The formula of the ELU function is:

```
f(x) = \begin{cases} x & \text{if } x \ge 0 \\ \alpha(e^x - 1) & \text{if } x < 0 \end{cases} (1.6)
```