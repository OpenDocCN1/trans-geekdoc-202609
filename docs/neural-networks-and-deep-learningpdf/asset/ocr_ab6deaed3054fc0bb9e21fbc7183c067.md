This suggests that a possible approach to computing $\frac{\partial C}{\partial w_{jk}^l}$ is to carefully track how a small change in $w_{jk}^l$ propagates to cause a small change in $C$. If we can do that, being careful to express everything along the way in terms of easily computable quantities, then we should be able to compute $\partial C / \partial w_{jk}^l$.

Let's try to carry this out. The change $\Delta w_{jk}^l$ causes a small change $\Delta a_j^l$ in the activation of the $j^{th}$ neuron in the $l^{th}$ layer. This change is given by

![](bbox=[0.32, 0.275, 0.65, 0.31])

The change in activation $\Delta a_j^l$ will cause changes in $all$ the activations in the next layer, i.e., the $(l + 1)^{th}$ layer. We'll concentrate on the way just a single one of those activations is affected, say $a_q^{l+1}$,

![](bbox=[0.13, 0.42, 0.63, 0.55])

In fact, it'll cause the following change:

![](bbox=[0.31, 0.59, 0.65, 0.625])

Substituting in the expression from Equation (48), we get:

![](bbox=[0.29, 0.675, 0.65, 0.71])

Of course, the change $\Delta a_q^{l+1}$ will, in turn, cause changes in the activations in the next layer. In fact, we can imagine a path all the way through the network from $w_{jk}^l$ to $C$, with each change in activation causing a change in the next activation, and, finally, a change in the cost at the output. If the path goes through activations $a_j^l, a_q^{l+1}, \dots, a_m^{L-1}, a_m^L$ then the resulting expression is

![](bbox=[0.23, 0.86, 0.65, 0.9])