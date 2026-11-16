```
$$ h^{(i)} = \begin{cases} w^{(i)T}x, & w^{(i)T}x > 0, \\ \varepsilon \times w^{(i)T}x, & w^{(i)T}x \le 0, \end{cases} $$
```

where \(\varepsilon\) is nonzero small constant and \(w\) is the weight of neuron. The setting of \(\varepsilon\) ensures that inactive neurons receive a nonzero gradient value, so that the neuron has the possibility of being activated.

Based on the above analysis, a deep network framework for hyperspectral data classification based on deep convolutional neural network is proposed in Figure 1.

In the proposed deep CNN model, the first layer, the third layer, and the fifth layer are convolution layers, which realized feature extraction from lower level to higher level. The second layer, the fourth layer, and the sixth layer are lower sampling layers, used for feature dimension reduction. The final layer is the output layer which is whole connection layer and output of the final extraction features.

# EXPONENTIAL MOMENTUM GRADIENT DESCENT ALGORITHM

# Error Transfer

Error transmission descends by two steps through forward propagation and reverse gradient, to conduct weight generation and adjustment. Using gradient descent method to update weight is shown in formula (2), and bias updating method is shown in formula (3) [30]:

```
$$ w^l_{new} = w^l_{old} + \eta \left(-\frac{\partial E}{\partial w^l_{old}}\right), $$ $$ b^l_{new} = b^l_{old} + \eta \left(-\frac{\partial E}{\partial b^l_{old}}\right). $$
```

![](bbox=[0.14, 0.775, 0.86, 0.885])

Figure 1. Classification framework based on EM-CNN.