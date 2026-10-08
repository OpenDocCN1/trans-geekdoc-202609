Schematically, this can be visualized as

![](bbox=[0.238, 0.206, 0.761, 0.442])

This is reminiscent of a three layer neural network with sets of hidden neurons and the linear activation function, which is the identity, each neuron. The weights of the synapses from the input to the first set of hidden neurons, the weights of the synapses from the first to the second set of hidden neurons are given by the entries of the matrix $D^T$, while the weights of the synapses from the second set of hidden neurons to the output neurons are given by the entries of the matrix $(D^T D)^{-1}$. Lastly, the weights from the second set of hidden neurons to the output neurons are given by the coefficients $c_1,\dots,c_D$. In a neural network, however, the weights of the synapses are updated iteratively in a learning process, until the output is similar enough to the input. In ordinary least squares, all is entirely determined by the matrix $D$, which only depends on the basis functions, but not $t_1,\dots,t_D$. However, if a set of training data $t_1,\dots,t_N$ is available, it can be fed through this neural network. The error of sum of squares between the predictions and the input is

```
$E(D) = \sum_{n=1}^{N} (t_n^T t_n - t_n^T (D^T D)^{-1} D^T t_n)^2,$$
```

since it is the ordinary least squares solution. The derivative with regards to the entry $D_{ij}$ of $D$ is

```
$$\frac{\partial E(D)}{\partial D_{ij}} = \sum_{n=1}^{N} ((D^T D)^{-1} D^T t_n)_j ((D^T D)^{-1} D^T t_n - t_n)_i,$
```

where the subscript of the brackets denotes the component of the vector in the brackets. It is the sum over the training data products of the latent