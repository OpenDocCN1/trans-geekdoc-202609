![](bbox=[0.34, 0.08, 0.69, 0.29])

Figure 23.6: Inverse autoregressive flow that uses affine scalar bijections. In this figure, $u$ is the input to the flow (sample from the base distribution) and $x$ is its output (sample from the transformed distribution) From [Jan18]. Used with kind permission of Eric Jang.

An example of this approach is the **masked autoregressive flow** (**MAF**) model of [PPM17]. This model is an affine autoregressive flow combined with permutation layers, as we described in Section 23.2.4.1. MAF implements the combined conditioner $\Theta$ as follows: it starts with an MLP, and then multiplies (elementwise) the weight matrix of each layer with a binary mask of the same size (different masks are used for different layers). The masks are constructed using the method of [Ger+15]. This ensures that all computational paths from $x_j$ to $\theta_i$ are zeroed out whenever $j \ge i$, effectively making $\theta_i$ only a function of $x_{1:i-1}$. Still, evaluating the masked conditioner $\Theta$ has the same computational cost as evaluating the original (unmasked) MLP. The key advantage of MAF (and of related models) is that, given $x$, all parameters $(\theta_1, \dots, \theta_D)$ can be computed efficiently with one neural network evaluation, so the computation of the inverse $f^{-1}$ is fast. Thus, we can efficiently evaluate the probability density of the flow model for arbitrary datapoints. However, in order to compute $f$, the conditioner $\Theta$ must be called a total of $D$ times, since not all entries of $x$ are available to start with. Thus, generating new samples from the flow is $D$ times more expensive than evaluating its probability density function. This makes MAF suitable for density estimation, but less so for data generation.

# 23.2.4.3 Inverse autoregressive flows

As we have seen, the parameters $\theta_i$ that yield the $i$'th output $x_i$ are functions of the previous outputs $x_{1:i-1}$. This ensures that the Jacobian $\mathbf{J}(\mathbf{f})$ is triangular, and so its determinant is efficient to compute. However, there is another possibility: we can make $\theta_i$ a function of the previous *inputs* instead, that is, a function of $u_{1:i-1}$. This leads to the following bijection, which is known as **inverse autoregressive**:

```
$x_i = h(u_i; \Theta_i(u_{1:i-1})), \quad i = 1, \dots, D.$ (23.26)
```

Like its autoregressive counterpart, this bijection has a triangular Jacobian whose determinant is also given by $\det \mathbf{J}(\mathbf{f}) = \prod_{i=1}^D \frac{dh}{du}$. Figure 23.6 illustrates an inverse autoregressive flow, for the case where $h$ is affine.