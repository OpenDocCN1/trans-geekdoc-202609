# CHAPTER 8. PREDICTING BEHAVIOR WITH DEEP LEARNING

will be presented. Then, the following section will introduce neural networks also known as multilayer perceptrons which are more complex models built by connecting many units and arranging them into layers.

# 8.1.1 Sigmoid and ReLU Units

As previously mentioned, perceptrons have some limitations that restrict their applicability including the fact that they are linear models. In practice, problems are complex and most of them are non-linear. One way to overcome this limitation is to introduce non-linearities and can be done by using a different type of activation function. Remember that a unit can be modeled as $f(x)=g(wx+b)$ where $g(x)$ is activation function. For the perceptron, $g(x)$ is the *step function*. However, another practical limitation not mentioned before is that the step function can change abruptly from 0 to 1 and vice versa. Small changes in $x,w$, or $b$ can completely change the output. This is a problem during learning and inference time. Instead, we would prefer a smooth version of the step function, for example, the *sigmoid function* which is also known as the **logistic function:

```
$s(x) = \frac{1}{1 + e^{-x}}$
```

This function has an 'S' shape (Figure 8.5) and as opposed to a step function, this one is smooth. The range of this function is from 0 to 1.

If we substitute the activation function in Equation (8.4) with the sigmoid function we get our **sigmoid unit**:

```
$f(x) = \frac{1}{1 + e^{-(w\cdot x+b)}}$
```

Sigmoid units have been one of the commonly used types of units when building bigger neural networks. Another advantage is that the outputs are real values that can be interpreted as probabilities. For instance, if we want to make binary decisions we can set a threshold. For example, if the output of the sigmoid unit is >0.5 then return a 1. Of course, that threshold would depend on the application. If we need more confidence about the result we set a higher threshold.

In the last years, another type of unit has been successfully applied to train neural networks, the *rectified linear unit* or **ReLU** for short. The activation function of this unit is the rectifier function: