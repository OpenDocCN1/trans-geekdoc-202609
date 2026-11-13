+   • In total, this means the total number of values to optimize is

```
$$\mathcal{N} = \sum_{l=1}^L (U_{l-1} + 1) U_l + U_L + 1$$
```

As in any model, the number of parameters should be much smaller than the number of instances. There is no fixed ratio, but it is preferable if the sample size is at least ten times larger than the number of parameters. Below a ratio of 5, the risk of overfitting is high. Given the amount of data readily available, this constraint is seldom an issue, unless one wishes to work with a very large network.

The number of hidden layers in current financial applications rarely exceeds three or four. The number of units per layer ($U_k$) is often chosen to follow the geometric pyramid rule (see, e.g., Masters (1993)). If there are $L$ hidden layers, with $I$ features in the input and $O$ dimensions in the output (for regression tasks, $O=1$), then, for the $k^{th}$ layer, a rule of thumb for the number of units is

```
$$U_k \approx \left[ O \frac{I}{O}^{\frac{L+1-k}{L+1}} \right].$$
```

If there is only one intermediate layer, the recommended proxy is the integer part of $\sqrt{IO}$. If not, the network starts with many units and the number of unit decreases exponentially towards the output size. Often, the number of layers is a power of two because, in high dimensions, networks are trained on Graphics Processing Units (GPUs) or Tensor Processing Units (TPUs). Both pieces of hardware can be used optimally when the inputs have sizes equals to powers of two.

Several studies have shown that very large architectures do not always perform better than more shallow ones (e.g., Gu et al. (2020b) and Orioloye et al. (2019) for high frequency data, i.e., not factor-based). As a rule of thumb, a maximum of three hidden layers seem to be sufficient for prediction purposes.

# 7.3.2 Frequency of weight updates and learning duration

In the expression (7.2), it is implicit that the computation is performed for one given instance. If the sample size is very large (hundreds of thousands or millions of instances), updating the weights according to each point is computationally too costly. The updating is then performed on groups of instances which are called batches. The sample is (randomly) split into batches of fixed sizes and each update is performed following the rule:

```
$$\mathbf{W} \leftarrow \mathbf{W} - \eta \frac{\partial_{i \in \text{batch}} D(\hat{y}_i)/\text{card(batch)}}{\partial \mathbf{W}}.\quad (7.11)$$
```

The change in weights is computed over the average loss computed over all instances in the batch. The terminology for training includes:

+   • epoch: one epoch is reached when each instance of the sample has contributed to the update of the weights (i.e., the training). Often, training a NN requires several epochs and up to a few dozen.

+   • batch size: the batch size is the number of samples used for one single update of weights.