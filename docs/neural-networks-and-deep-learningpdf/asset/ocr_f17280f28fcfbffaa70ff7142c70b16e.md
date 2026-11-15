![](bbox=[0.2, 0.085, 0.55, 0.245])

This shape is a smoothed out version of a step function:

![](bbox=[0.2, 0.315, 0.55, 0.475])

If \(\sigma\) had in fact been a step function, then the sigmoid neuron would be a perceptron, since the output would be 1 or 0 depending on whether \(w \cdot x + b\) was positive or negative*. By using the actual \(\sigma\) function we get, as already implied above, a smoothed out perceptron. Indeed, it's the smoothness of the \(\sigma\) function that is the crucial fact, not its detailed form. The smoothness of \(\sigma\) means that small changes \(\Delta w_j\) in the weights and \(\Delta b\) in the bias will produce a small change \(\Delta \text{output}\) in the output from the neuron. In fact, calculus tells us that \(\Delta \text{output}\) is well approximated by

> *Actually, when \(w \cdot x + b = 0\) the perceptron outputs 0, while the step function outputs 1. So, strictly speaking, we'd need to modify the step function at that one point. But you get the idea.

```
\(\Delta \text{output} \approx \sum_j \frac{\partial \text{output}}{\partial w_j} \Delta w_j + \frac{\partial \text{output}}{\partial b} \Delta b, \quad (5)\)
```

where the sum is over all the weights, \(w_j\), and \(\partial \text{output}/\partial w_j\) and \(\partial \text{output}/\partial b\) denote partial derivatives of the output with respect to \(w_j\) and \(b\), respectively. Don't panic if you're not comfortable with partial derivatives! While the expression above looks complicated, with all the partial derivatives, it's actually saying something very simple (and which is very good news): \(\Delta \text{output}\) is a *linear function* of the changes \(\Delta w_j\) and \(\Delta b\) in the weights and bias. This linearity