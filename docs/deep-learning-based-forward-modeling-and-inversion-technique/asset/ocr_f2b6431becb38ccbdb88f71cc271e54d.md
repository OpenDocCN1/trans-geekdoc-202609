# Deep Learning-Based Forward Modeling and Inversion Techniques

![](bbox=[0.318, 0.125, 0.638, 0.345])

FIGURE 2.15
The structure of the residual module.

it has

$b_j = \frac{1}{N} \sum_{x=1}^{N} a_i \quad (2.36)$

In addition, the network also introduces the residual module [34] (shown in Figure 2.15) to eliminate the precision saturation. As is well-known, deep neural networks often suffer from degradation problems. With the increase network depth, the precision gets saturated and then degrades rapidly. Surprisingly, this degradation is not caused by overfitting, and the introduction of residual structure can alleviate this phenomenon.

Assuming that the final function to be fitted is $\mathcal{H}(x)$, and the network first fits $\mathcal{F}(x) = \mathcal{H}(x)-x$. Then, the original $\mathcal{H}(x)$ can be expressed by $\mathcal{F}(x)+x$. Related research has demonstrated that fitting identical mapping is much easier than direct fitting functions. Besides, the operator $\mathcal{F}(x)+x$ can be conveniently achieved by the skip connection, greatly enhancing the practicality of the residual structure. Consequently, it is possible to construct deep networks with more than 100 layers.

# 2.3.4 Loss Functions

For supervised learning, the loss function is a nonnegative real value $f$ selected from the hypothesis space $\mathcal{F}$ to measure the predicting error. During the network training, the direction of the optimization is determined by the gradient of loss function, hence an appropriate loss function is significant in the training. Several commonly used loss functions are listed below:

+   - A. 0-1 loss function