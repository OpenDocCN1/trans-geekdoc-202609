the posterior, where $Z_0$ is the normalization constant for the prior. To simplify notation, we let $f_0(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta})$ be the prior.
We will approximate the posterior as follows:

```
\( q(\boldsymbol{\theta}) = \frac{1}{Z_q} \tilde{q}(\boldsymbol{\theta}), \quad \tilde{q}(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta}) \prod_{k=1}^K \tilde{f}_k(\boldsymbol{\theta}) \)
```

where \(\tilde{f}_k \in \mathcal{Q}\) is the approximate local factor, and \(\mathcal{Q}\) is some tractable family in the exponential family, usually a Gaussian [Gel+14b].

We will optimize each \(\tilde{f}_i\) in turn, keeping the others fixed. We initialize each \(\tilde{f}_i\) using an uninformative distribution from the family \(\mathcal{Q}\). so \(q(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta})\). To compute the new local factor \(\tilde{f}_i^{\text{new}}\), we proceed as follows. First we compute the **cavity distribution** by deleting the \(\tilde{f}_i\) from the approximate posterior by dividing it out:

```
\( q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) = \frac{q(\boldsymbol{\theta})}{\tilde{f}_i(\boldsymbol{\theta})} \propto \prod_{k \neq i} \tilde{f}_k(\boldsymbol{\theta}) \)
```

This division operation can be implemented by subtracting the natural parameters, as explained in Section 2.3.3.2. The cavity distribution represents the effect of all the factors except for \(f_i\) (which is approximated by \(\tilde{f}_i\)).

Next we (conceptually) compute the **tilted distribution** by multiplying the exact factor \(f_i\) onto the cavity distribution:

```
\( q_i^{\text{tilted}}(\boldsymbol{\theta}) = \frac{1}{Z_i} f_i(\boldsymbol{\theta}) q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) \)
```

where \(Z_i = \int q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) f_i(\boldsymbol{\theta}) d\boldsymbol{\theta}\) is the normalization constant for the tilted distribution. This is the result of combining the current approximation, excluding factor \(i\), with the exact \(f_i\) term.

Unfortunately, the resulting tilted distribution may be outside of our model family (e.g., if we combine a Gaussian prior with a non-Gaussian likelihood). So we will approximate the tilted distribution as follows:

```
\( q_i^{\text{proj}}(\boldsymbol{\theta}) = \text{proj}(q_i^{\text{tilted}}) \triangleq \underset{\tilde{q} \in \mathcal{Q}}{\text{argmin}} D(q_i^{\text{tilted}} || \tilde{q}) \)
```

This can be thought of as projecting the tilted distribution into the approximation family. If \(D(q_i^{\text{tilted}} || q) = D_{\text{KL}}(q_i^{\text{tilted}} || q)\), this can be done by moment matching, as shown in Section 5.1.4.2. For example, suppose the cavity distribution is Gaussian, \(q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) = \mathcal{N}_c(\boldsymbol{\theta}|\mathbf{r}_{-i}, \mathbf{Q}_{-i})\), using the canonical parameterization. Then the log of the tilted distribution is given by

```
\(\log q_i^{\text{tilted}}(\boldsymbol{\theta}) = \alpha \log f_i(\boldsymbol{\theta}) - \frac{1}{2} \boldsymbol{\theta}^\top \mathbf{Q}_{-i} \boldsymbol{\theta} + \mathbf{r}_{-i}^\top \boldsymbol{\theta} + \text{const}\)
```

Let \(\hat{\boldsymbol{\theta}}\) be a local maximum of this objective. If \(\mathcal{Q}\) is the set of Gaussians, we can compute the projected tilted distribution as a Gaussian with the following parameters:

```
\(\mathbf{Q}_{\backslash i} = -\nabla_{\boldsymbol{\theta}}^2 \log q_i^{\text{tilted}}(\boldsymbol{\theta})|_{\boldsymbol{\theta}=\hat{\boldsymbol{\theta}}}, \quad \mathbf{r}_{\backslash i} = \mathbf{Q}_{\backslash i} \hat{\boldsymbol{\theta}}\)
```