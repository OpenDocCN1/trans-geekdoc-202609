

![](img/4048998719320644ee88964326fd7995_40_0.png)

Fig. 1.15 Scaled exponential linear unit activation function

SELU activation function compared to the RELU activation function is that the convergence process in neural networks made from the SELU activation function happens faster because the speed of internal normalization is faster than the speed of external normalization. The problems of gradient fading and gradient explosion do not occur for neural networks made from SELU activation function. Since the activation function of SELU is considered a new function, its exact performance in all existing models in deep learning such as the CNN model is still unclear, and it is necessary to check its performance in all models. Scaled Exponential Linear Unit Activation Function shown in Fig. 1.15.

The SELU function formula is as follows:

```
f(x) = \begin{cases} \lambda(\alpha e^x - \alpha) & \text{for } x < 0 \\ \lambda x & \text{for } x \ge 0 \end{cases} (1.8)
```

## 1.5.11 Softplus Activation Function

Softplus is a non-linear activation function that is commonly used to generate positive and normalized outputs in neural networks. This function converts the input values to a positive and normalized value and is also useful for solving the gradient fading problem. One of the advantages of this function is that it produces a positive and normal output, and it is also suitable for preventing gradient fading. The limitation of this method is that it may require more extensive calculations for some problems. Softplus Activation Function shown in Fig. 1.16.

![](img/4048998719320644ee88964326fd7995_41_0.png)

Fig. 1.16 Softplus activation function

Softplus formula is:

```
f(x) = log(1 + e^x)
(1.9)
```

## 1.5.12 Mish Activation Function

The Mish activation function is a recently introduced nonlinear activation function and is the main source of communication between the Sigmoid and Tanh functions and the innovative features of ReLU.

One of the advantages of this function is the improved performance compared to ReLU and sharp points between Sigmoid and Tanh, as well as the soft properties of the function curve resulting from the combination of Sigmoid and Tanh. One of the drawbacks of this function is that there have not been many experiments and studies regarding Mish's performance and superiority over common activation functions. Mish Activation Function shown in Fig. 1.17.

![](img/4048998719320644ee88964326fd7995_42_0.png)

Fig. 1.17 Mish activation function

Mish's formula is as follows:

```
f(x) = x * tanh(softplus(x))
```

## 1.5.13 Randomized Leaky Rectified Linear Unit Activation Function (RReLU)

RReLU is a modified variation of the Leaky ReLU function that uses a random interval of positive values for the leaky parameter in negative regions. These variations are learned by the layers of the neural network itself and help the model to be more flexible and perform better for classification problems. This activation function offers more flexibility to the negative areas than the normal ReLU and can help to avoid the problem related to the negative areas that occurs in the normal ReLU functions. Its limitations include the need for the most accuracy in choosing random parameters. In the negative areas to improve the function pointed out. Randomized Leaky Rectified Linear Unit Activation Function shown in Fig. 1.18. This activation function is defined as follows:

```
yij = xij if xij ≥ 0
yij = αijxij if xij < 0
```

![](img/4048998719320644ee88964326fd7995_43_0.png)

Fig. 1.18 Randomized leaky rectified linear unit activation function

where

```
\alpha_{ij} \sim U(l, u), l < u \text{ and } l, u \in [0,1) (1.12)
```

where \((\alpha_{ij})\) is a random value of a specified interval that is different for each neuron in the neural network.

## 1.5.14 HardSwish Activation Function

HardSwish is an activation function that is a combination of ReLU and Linear functions and works in a non-linear way. This function is derived from the harder activity functions (hard) and is used to limit the range of input values to reasonable values.

Its advantages are avoiding the problem of gradient fading, normalization of input values, and better performance than other stiffness functions, as well as the least negative impact on network efficiency and speed. Among its limitations is the need for proper initialization for correct calculations. HardSwish Activation Function shown in Fig. 1.19.

The HardSwish formula is as follows:

![](img/4048998719320644ee88964326fd7995_44_0.png)

Fig. 1.19 HardSwish activation function

```
f(x) = \left\{ \begin{array}{ll} 0 & \text{if } x \le -3 \\ x & \text{if } x \ge +3 \\ x \cdot (x+3)/6 & \text{otherwise} \end{array} \right. \quad (1.13)
```

## 1.5.15 Softsign Activation Function

The Softsign activation function is a nonlinear function that is generally used as an activation function in neural networks. A form of this function behaves linearly for input values of x close to zero, but for values far from zero, the function has an “S” shaped curve. This function is a combination of the absolute functions (|x|) and the enumerator \(\frac{x}{1+|x|}\). The advantage of this function is that it normalizes the input values to values between –1 and 1, and this makes the model for training information. Near zero, the Softsign function behaves linearly, which can help in training models. Also, this function has no potential restrictions on input values and theoretically always has a derivative. One of the limitations of this function is that although it works linearly close to zero, it works non-linearly outside this range, which may not control positive and negative points in some special cases.

And for large values, Softsign’s output quickly tends to 1 or –1, which may be inappropriate in some problems. Softsign Activation Function shown in Fig. 1.20.

![](img/4048998719320644ee88964326fd7995_45_0.png)

Fig. 1.20 Softsign activation function

Softsign formula is:

```
f(x) = x/(1 + |x|)
```

## 1.5.16 HardTanh Activation Function

HardTanh is a harder and non-linear version of the hyperbolic tangent function (Tanh) that normalizes the input values to the standard range. This function converts positive points to 1 and negative points to -1. Its advantages are simplicity and high efficiency, preventing Saturation in negative areas as well as converting the input values to acceptable and suitable values. The limitation of this function is the alternation of negative and positive points, which may cause some problems. HardTanh Activation Function shown in Fig. 1.21.

HardTanh formula is:

```
f(x) = max(-1, min(1, x))
```

![](img/4048998719320644ee88964326fd7995_46_0.png)

Fig. 1.21 HardTanh activation function

## 1.5.17 HardSigmoid Activation Function

HardSigmoid is a harder, non-linear version of the sigmoid function that normalizes input values to a standard range. This function is the tangent function of the derivative on the linearization of the sigmoid function.

The advantages of that function cut point is the range between 0 and 1 and converting the output to a linear between these two points, as well as simplicity and high efficiency for networks. This function may not be suitable for some problems that require more accurate and complex activation functions. HardSigmoid Activation Function shown in Fig. 1.22.

Hard Sigmoid formula is:

```
f(x) = max(0, min(1, x))
(1.16)
```

## 1.5.18 Tanh Shrink Activation Function

Tanh Shrink is an activation function that is normalized and works in a way dependent on the hyperbolic tangent. This function is mapped to tanh(x) – λx, where λ is a coefficient that can be normalized and limited by adjusting it. The advantages of normalization the output of the hyperbolic tangent and control over the intensity is

![](img/4048998719320644ee88964326fd7995_47_0.png)

Fig. 1.22 HardSigmoid activation function

to reduce the intensity value. Its limitation is the need to determine and accurately control the values of the coefficient \(\lambda\). Tanh shrink Activation Function shown in Fig. 1.23.

Tanh Shrink formula is:

```
\(f(x) = \tanh(x) - \lambda x\) (1.17)
```

## 1.5.19 Soft Shrink Activation Function

Soft Shrink is an activation function that is generally used to remove small parts and unimportant noise from the input. This function is generally similar to the Threshold function and converts the input values below a threshold to zero and above it. Its advantages are removing noise and small parts from the input as well as normalizing the output based on the threshold value. But it needs to be adjusted. It is accurate and suitable for the limit of \(\lambda\). Soft shrink activation function shown in Fig. 1.24.

Soft Shrink formula is:

```
\(f(x) = sign(x) * max(0, |x| - \lambda)\) (1.18)
```

