models. These advances have clearly illustrated that GPs and neural networks are not competing, but complementary, and can be combined for better performance than would be achieved by deep learning alone. We describe GPs for representation learning in Section 18.6. The connections between Gaussian processes and neural networks can also be further understood by considering infinite limits of neural networks that converge to Gaussian processes with particular covariance functions, which we describe in Section 18.7. So Gaussian processes are nonparametric models which can scale and do representation learning. But why, in the age of deep learning, should we want to use a Gaussian process? There are several compelling reasons to prefer a GP, including:

+   - Gaussian processes typically provide well-calibrated predictive distributions, with a good characterization of epistemic (model) uncertainty — uncertainty arising from not knowing which of many solutions is correct. For example, as we move away from the data, there are a greater variety of consistent solutions, and so we expect greater uncertainty.
+   - Gaussian processes are often state-of-the-art for continuous regression problems, especially spatiotemporal problems, such as weather interpolation and forecasting. In regression, Gaussian process inference can also typically be performed in closed form.
+   - The marginal likelihood of a Gaussian process provides a powerful mechanism for flexible kernel learning. Kernel learning enables us to provide long-range extrapolations, but also tells us interpretable properties of the data that we didn’t know before, towards scientific discovery.
+   - Gaussian processes are often used as a probabilistic surrogate for optimizing expensive objectives, in a procedure known as Bayesian optimization (Section 6.6).

# 18.2 Mercer kernels

The generalization properties of Gaussian processes boil down to how we encode prior knowledge about the similarity of two input vectors. If we know that \(\boldsymbol{x}_i\) is similar to \(\boldsymbol{x}_j\), then we can encourage the model to make the predicted output at both locations (i.e., \(f(\boldsymbol{x}_i)\) and \(f(\boldsymbol{x}_j)\)) to be similar. To define similarity, we introduce the notion of a kernel function. The word “kernel” has many different meanings in mathematics; here we consider a Mercer kernel, also called a positive definite kernel. This is any symmetric function \(\mathcal{K} : \mathcal{X} \times \mathcal{X} \rightarrow \mathbb{R}^+\) such that

```
\sum_{i=1}^N \sum_{j=1}^N \mathcal{K}(\boldsymbol{x}_i, \boldsymbol{x}_j) c_i c_j \ge 0
```

for any set of N (unique) points \(\boldsymbol{x}_i \in \mathcal{X}\), and any choice of numbers \(c_i \in \mathbb{R}\). We assume \(\mathcal{K}(\boldsymbol{x}_i, \boldsymbol{x}_j) > 0\), so that we can only achieve equality in the above equation if \(c_i = 0\) for all i.

Another way to understand this condition is the following. Given a set of N datapoints, let us define the Gram matrix as the following \(N \times N\) similarity matrix:

```
\boldsymbol{K} = \begin{pmatrix} \mathcal{K}(\boldsymbol{x}_1, \boldsymbol{x}_1) & \cdots & \mathcal{K}(\boldsymbol{x}_1, \boldsymbol{x}_N) \\ \vdots & \ddots & \vdots \\ \mathcal{K}(\boldsymbol{x}_N, \boldsymbol{x}_1) & \cdots & \mathcal{K}(\boldsymbol{x}_N, \boldsymbol{x}_N) \end{pmatrix}
```