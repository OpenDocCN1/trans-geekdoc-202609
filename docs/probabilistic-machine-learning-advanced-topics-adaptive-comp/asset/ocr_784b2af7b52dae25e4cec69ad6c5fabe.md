![](bbox=[0.3, 0.08, 0.68, 0.26])

Figure 4.11: Left: datapoints $\mathbf{x}_n$ are conditionally independent given $\theta$. Right: Same model, using plate notation. This represents the same model as the one on the left, except the repeated $\mathbf{x}_n$ nodes are inside a box, known as a plate; the number in the lower right hand corner, $N$, specifies the number of repetitions of the $\mathbf{x}_n$ node.

random variables, $\mathbf{x}_n$, all drawn from the same distribution with common parameter $\theta$. We denote this by

```
$$\mathbf{x}_n \sim p(\mathbf{x}|\theta)$$
```

The corresponding joint distribution over the parameters and data $\mathcal{D} = \{\mathbf{x}_1, \dots, \mathbf{x}_N\}$ has the form

```
$$p(\mathcal{D}, \theta) = p(\theta)p(\mathcal{D}|\theta)$$
```

where $p(\theta)$ is the prior distribution for the parameters, and $p(\mathcal{D}|\theta)$ is the likelihood. By virtue of the iid assumption, the likelihood can be rewritten as follows:

```
$$p(\mathcal{D}|\theta) = \prod_{n=1}^N p(\mathbf{x}_n|\theta)$$
```

Notice that the order of the data vectors is not important for defining this model, i.e., we can permute the leaves of the DPGM. When this property holds, we say that the data is **exchangeable**.

In Figure 4.11(a), we see that the $\mathbf{x}$ nodes are repeated $N$ times. (The **shaded** nodes represent observed values, whereas the unshaded (hollow) nodes represent latent variables or parameters.) To avoid visual clutter, it is common to use a form of syntactic sugar called **plates**. This is a notational convention in which we draw a little box around the repeated variables, with the understanding that nodes within the box will get repeated when the model is **unrolled**. We often write the number of copies or repetitions in the bottom right corner of the box. This is illustrated in Figure 4.11(b).

# 4.2.8.1 **Example: factor analysis**

In Section 28.3.1, we discuss the factor analysis model, which has the form

```
$$p(\mathbf{z}) = \mathcal{N}(\mathbf{z}|\mu_0, \mathbf{\Sigma}_0)$$
```

```
$$p(\mathbf{x}|\mathbf{z}) = \mathcal{N}(\mathbf{x}|\mathbf{W}\mathbf{z} + \mu, \mathbf{\Psi})$$
```