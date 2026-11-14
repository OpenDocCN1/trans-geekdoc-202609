where \(\tilde{k}_{nn} = k_{nn} - \mathbf{k}_n^\mathsf{T} \mathbf{K}_{Z,Z}^{-1} \mathbf{k}_n\), \(\mathbf{k}_n\) is the \(n\)'th column of \(\mathbf{K}_{Z,X}\) and \(\mathbf{\Lambda}_n = \beta \mathbf{K}_{Z,Z}^{-1} \mathbf{k}_n \mathbf{k}_n^\mathsf{T} \mathbf{K}_{Z,Z}^{-1}\). Hence the overall ELBO has the form

\(\mathcal{L}(q) = \log \mathcal{N}(\mathbf{y}|\mathbf{K}_{X,Z}\mathbf{K}_{Z,Z}^{-1}\mathbf{m}, \beta^{-1}\mathbf{I}_N) - \frac{1}{2}\beta\text{tr}(\mathbf{K}_{X,Z}\mathbf{K}_{Z,Z}^{-1}\mathbf{S}\mathbf{K}_{Z,Z}^{-1}\mathbf{K}_{Z,X}) \tag{18.149}\)

\(-\frac{1}{2}\beta\text{tr}(\mathbf{K}_{X,X} - \mathbf{Q}_{X,X}) - D_{\text{KL}}(q(\mathbf{f}_Z) \| p(\mathbf{f}_Z)) \tag{18.150}\)

where \(\mathbf{Q}_{X,X} = \mathbf{K}_{X,Z}\mathbf{K}_{Z,Z}^{-1}\mathbf{K}_{Z,X}\). To compute the gradients of this, we leverage the following result [OA09]:

\(\frac{\partial}{\partial \mu} \mathbb{E}_{\mathcal{N}(x|\mu,\sigma^2)}[h(x)] = \mathbb{E}_{\mathcal{N}(x|\mu,\sigma^2)} \left[ \frac{\partial}{\partial x} h(x) \right] \tag{18.151}\)

\(\frac{\partial}{\partial \sigma^2} \mathbb{E}_{\mathcal{N}(x|\mu,\sigma^2)}[h(x)] = \frac{1}{2} \mathbb{E}_{\mathcal{N}(x|\mu,\sigma^2)} \left[ \frac{\partial^2}{\partial x^2} h(x) \right] \tag{18.152}\)

We then substitute \(h(x)\) with \(\log p(y_n|f_n)\). Using this, one can show

\(\nabla_\mathbf{m} \mathcal{L}(q) = \beta \mathbf{K}_{Z,Z}^{-1} \mathbf{K}_{Z,X} \mathbf{y} - \mathbf{\Lambda m} \tag{18.153}\)

\(\nabla_\mathbf{S} \mathcal{L}(q) = \frac{1}{2} \mathbf{S}^{-1} - \frac{1}{2} \mathbf{\Lambda} \tag{18.154}\)

Setting the derivatives to zero gives the optimal solution:

\(\mathbf{S} = \mathbf{\Lambda}^{-1} \tag{18.155}\)

\(\mathbf{\Lambda} = \beta \mathbf{K}_{Z,Z}^{-1} \mathbf{K}_{Z,X} \mathbf{K}_{X,Z} \mathbf{K}_{Z,Z}^{-1} + \mathbf{K}_{Z,Z}^{-1} \tag{18.156}\)

\(\mathbf{m} = \beta \mathbf{\Lambda}^{-1} \mathbf{K}_{Z,Z}^{-1} \mathbf{K}_{Z,X} \mathbf{y} \tag{18.157}\)

This is called sparse GP regression or SGPR [Tit09]. With these parameters, the lower bound on the log marginal likelihood is given by

\(\log p(\mathbf{y}) \ge \log \mathcal{N}(\mathbf{y}|\mathbf{0}, \mathbf{K}_{X,Z} \mathbf{K}_{Z,Z}^{-1} \mathbf{K}_{Z,X} + \beta^{-1} \mathbf{I}) - \frac{1}{2} \beta \text{tr}(\mathbf{K}_{X,X} - \mathbf{Q}_{X,X}) \tag{18.158}\)

(This is called the “collapsed” lower bound, since we have marginalized out \(\mathbf{f}_z\).) If \(Z = X\), then \(\mathbf{K}_{Z,Z} = \mathbf{K}_{Z,X} = \mathbf{K}_{X,X}\), so the bound becomes tight, and we have \(\log p(\mathbf{y}) = \log \mathcal{N}(\mathbf{y}|\mathbf{0}, \mathbf{K}_{X,X} + \beta^{-1} \mathbf{I})\). Equation (18.158) is almost the same as the log marginal likelihood for the DTC model in Equation (18.134), except for the trace term; it is this latter term that prevents overfitting, due to the fact that we treat \(\mathbf{f}_Z\) as variational parameters of the posterior rather than model parameters of the prior.

# 18.5.4.2 Non-Gaussian likelihood

In this section, we briefly consider the case of non-Gaussian likelihoods, which arise when using GPs for classification or for count data (see Section 18.4). We can compute the gradients of the expected log likelihood by defining \(h(f_n) = \log p(y_n|f_n)\) and then using a Monte Carlo approximation to Equation (18.151) and Equation (18.152). In the case of a binary classifier, we can use the results in Table 18.2 to compute the inner \(\frac{\partial}{\partial f_n} h(f_n)\) and \(\frac{\partial^2}{\partial f_n^2} h(f_n)\) terms. Alternatively, we can use numerical integration techniques, such as those discussed in Section 8.5.1.4. (See also [WSS21].)