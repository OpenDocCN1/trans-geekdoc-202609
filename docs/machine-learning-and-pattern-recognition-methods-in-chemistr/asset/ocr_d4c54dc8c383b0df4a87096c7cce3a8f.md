# Autoencoders in generative modeling

![](bbox=[0.313, 0.103, 0.718, 0.373])

**Fig. 6.3** Stacked autoencoder training process. Stacked autoencoder is trained in a greedy layer-wise manner.

#  1.4 Sparse autoencoder

The main idea of sparsity was first introduced in computational neuroscience (Olshausen & Field, 1997) and later used in machine learning. Overcomplete architecture, the code consists of a large number of nodes. However, the activation value of these nodes in most instances is zero. In other words, the average activation value for each node is close to zero. Finding a representation for the input instances that extracts only the essential features is the main logic of this approach. To train a sparse autoencoder, we use an objective function that includes the regularization penalty:

```
$L(x, g(f(x))) + \Omega(z) \quad (6.1)$
```

where $g(z)$ is the encoder output, $z=f(x)$ is the encoder output or code, and $\Omega(z)$ is a sparsity penalty. The effect of the sparsity component on the