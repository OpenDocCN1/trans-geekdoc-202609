# 28 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

The cost function of the neural network is defined as:

```
$$C(W,b) = \sum_{i=1}^{n} \left[ \frac{1}{2} |h_{w,b}(x(i)) - y(i)|^2 \right] + \frac{\gamma}{2} \sum_{j=1}^{m_j} \sum_{i=1}^{l_{j+1}} (W_j(i))^2$$ (2.4)
```

Adding the sparse penalty term to the cost, it can be modified as:

```
$$C_{sparse}(W,b) = C(W,b) + \beta \sum_{j=1}^{S2} K_l(|\rho_j|)$$$ (2.5)
```

where $\beta$ is the weight of the sparsity penalty.
During the coding coding, the optimal parameters of $W$ and $b$ need to be identified. Since the sparse cost function shown in Eq. (2.5) is directly related to the parameters $W$ and $b$, it can be solved by minimizing $C_{sparse}(W,b)$ to obtain these two parameters. This can be realized using the backpropagation algorithm (Rumelhart, Hinton, and Williams 1986), where the stochastic gradient descent approach is used for training and the parameters $W$ and $b$ in each iteration can be updated:

```
$$W_j(l) = W_j(l) - \varepsilon \frac{\partial}{\partial W_j(l)} C_{sparse}(W,b)$$$ (2.6)
```

```
$$b_l(l) = b_l(l) - \varepsilon \frac{\partial}{\partial b_l(l)} C_{sparse}(W,b)$$$ (2.7)
```

where $\varepsilon$ is the learning rate. A forward pass on all training examples is used to compute the average activation $\rho_j$ to get the sparse error, then the backpropagation algorithm works to update the parameters. After that, the effective sparse feature representations can be learned by the SAE.

# Denoising Autoencoder

Vincent et al. (2008) proposed a denoising AE learning algorithm based on the idea of making the feature representation robust by adding partial corruption to the input pattern, which can be used to train stacked AEs to initialize the deep architectures. It has been known that this type of learning can help obtain better feature representation with denoising, which motivates the introduction of denoising module into our study.

For the input matrix $X$, the process of denoising AE is in Figure 2.2, where the input $X$ is corrupted to get a partially destroyed $\chi$ by applying a stochastic mapping $\chi = X - qD(\chi|X)$, then $\chi$ is coded to $y$. Here distribution $qD$ describes as follows for each input, a fixed number of components are randomly chosen and their values are set to 0, while the others are kept unchanged. A joint denoising is defined as:

```
$$q^X(X, \chi, y) = q^X(X)qD(\chi|X)\delta_{f_0(X)}(y)$$$ (2.8)
```

where $\delta_{f_0(X)}(y)$ is set to 0 if $f_0(X) \neq y$. $q^X(X)$ denotes the empirical distribution associated with N training. Thus, $y$ is a deterministic function of $\chi$. Let $\theta$ be one parameter of