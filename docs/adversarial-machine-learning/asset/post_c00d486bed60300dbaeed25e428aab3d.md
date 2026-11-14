
\ell' (y, \hat{y}) \text{ the subdifferential } \partial_y \ell (y, \hat{y}) .
N \left\langle \partial_w R_{\text{emp}} (\mathbf{w}^{(D)}, \mathbb{D}) - \partial_w R_{\text{emp}} (\mathbf{w}^{(D')}, \mathbb{D}'), \mathbf{w}^{(D)} - \mathbf{w}^{(D')} \right\rangle
= \sum_{i=1}^N \left\langle \partial_w \ell (y^{(i)}, f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(i)})) - \partial_w \ell (\hat{y}^{(i)}, f_{\mathbf{w}^{(D')}} (\hat{\mathbf{x}}^{(i)})), \mathbf{w}^{(D)} - \mathbf{w}^{(D')} \right\rangle
= \sum_{i=1}^{N-1} \left( \ell' (y^{(i)}, f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(i)})) - \ell' (y^{(i)}, f_{\mathbf{w}^{(D')}} (\mathbf{x}^{(i)})) \right) (f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(i)}) - f_{\mathbf{w}^{(D')}} (\mathbf{x}^{(i)}))
+ \ell' (y^{(N)}, f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(N)})) (f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(N)}) - f_{\mathbf{w}^{(D')}} (\mathbf{x}^{(N)}))
- \ell' (\hat{y}^{(N)}, f_{\mathbf{w}^{(D')}} (\hat{\mathbf{x}}^{(N)})) (f_{\mathbf{w}^{(D)}} (\hat{\mathbf{x}}^{(N)}) - f_{\mathbf{w}^{(D')}} (\hat{\mathbf{x}}^{(N)}))
\ge \ell' (y^{(N)}, f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(N)})) (f_{\mathbf{w}^{(D)}} (\mathbf{x}^{(N)}) - f_{\mathbf{w}^{(D')}} (\mathbf{x}^{(N)}))
- \ell' (\hat{y}^{(N)}, f_{\mathbf{w}^{(D')}} (\hat{\mathbf{x}}^{(N)})) (f_{\mathbf{w}^{(D)}} (\hat{\mathbf{x}}^{(N)}) - f_{\mathbf{w}^{(D')}} (\hat{\mathbf{x}}^{(N)})) .

Here the second equality follows from \(\partial_w \ell (y, f_w(x)) = \ell' (y, f_w(x)) \phi (x)\), and \(\hat{x}^{(i)} = x^{(i)}\) and \(\hat{y}^{(i)} = y^{(i)}\) for each \(i \in [N-1]\). The inequality follows from the convexity of \(\ell\) in its second argument.\(^5\) Combined with the existence of nonpositive \(r \in \tilde{R}(w^{(D)})\) this yields that there exists

```
g \in \ell' (\hat{y}^{(N)}, f_{w^{(D')}} (\hat{x}^{(N)})) (f_{w^{(D)}} (\hat{x}^{(N)}) - f_{w^{(D')}} (\hat{x}^{(N)}))
- \ell' (y^{(N)}, f_{w^{(D)}} (x^{(N)})) (f_{w^{(D)}} (x^{(N)}) - f_{w^{(D')}} (x^{(N)}))
```

such that

```
0 \ge \frac{N}{C} r
\ge g + \frac{N}{2C} \left\| w^{(D)} - w^{(D')} \right\|_2^2 .
```

And since \(|g| \le 2L \left\| f_{w^{(D)}} - f_{w^{(D')}} \right\|_\infty\) by the Lipschitz continuity of \(\ell\), this in turn implies

```
\frac{N}{2C} \left\| w^{(D)} - w^{(D')} \right\|_2^2 \le 2L \left\| f_{w^{(D)}} - f_{w^{(D')}} \right\|_\infty . \quad (7.4)
```

Now by the reproducing property and Cauchy-Schwarz inequality we can upper bound the classifier difference's infinity norm by the Euclidean norm on the weight vectors: For each x

```
|f_{w^{(D)}} (x) - f_{w^{(D')}} (x)| = \left| \langle \phi (x) , w^{(D)} - w^{(D')} \rangle \right|
\le \|\phi (x)\|_2 \left\| w^{(D)} - w^{(D')} \right\|_2
= \sqrt{k (x, x)} \left\| w^{(D)} - w^{(D')} \right\|_2
\le \kappa \left\| w^{(D)} - w^{(D')} \right\|_2 .
```

Combining this with Inequality (7.4) yields \(\| \mathbf{w}^{(\mathbb{D})} - \mathbf{w}^{(\mathbb{D}')} \|_2 \le 4LC\kappa / N\) as claimed. The \(\ell_1\)-based sensitivity then follows from \(\|\mathbf{w}\|_1 \le \sqrt{F} \|\mathbf{w}\|_2\) for all \(\mathbf{w} \in \Re^F\).

For a SVM with a Gaussian kernel, we have \(L=1\) and \(\kappa = 1\). Then the bounds can be simplified as \(\|\mathbf{w}^{(\mathbb{D})} - \mathbf{w}^{(\mathbb{D}')}\|_2 \le 4C/N\) and \(\|\mathbf{w}^{(\mathbb{D})} - \mathbf{w}^{(\mathbb{D}')}\|_1 \le 4C\sqrt{F} / N\). With the weight vector’s sensitivity in hand, differential privacy follows immediately (cf. Lemma 7.3)

### THEOREM 7.10 (Privacy of PRIVATESVM-FINITE)
For any \(\beta > 0\), database \(\mathbb{D}\) of size \(N\), \(C > 0\), loss function \(\ell(y, \hat{y})\) that is convex and \(L\)-Lipschitz in \(\hat{y}\), and finite \(F\)-dimensional feature map with kernel \(k(\mathbf{x}, \mathbf{x}) \le \kappa^2\) for all \(\mathbf{x} \in \Re^D\), PRIVATESVM-FINITE run on \(\mathbb{D}\) with loss \(\ell\), kernel \(k\), noise parameter \(\lambda \ge 4LC\kappa\sqrt{F} / (\beta N)\), and regularization parameter \(C\) guarantees \(\beta\)-differential privacy.

This result states that higher levels of privacy require more noise, while more training examples reduce the level of required noise. We next establish the \((\epsilon, \delta)\)-usefulness of PRIVATESVM-FINITE, using the exponential tails of the noise vector \(\boldsymbol{\mu}\). By contrast to privacy, utility demands that the noise not be too large.

### THEOREM 7.11 (Utility of PRIVATESVM-FINITE)
Consider any \(C > 0\), \(N > 1\), database \(\mathbb{D}\) of \(N\) entries, arbitrary convex loss \(\ell\), and finite \(F\)-dimensional feature mapping \(\phi\) with kernel \(k\) and \(|\phi(\mathbf{x})_i| \le \Phi\) for all \(\mathbf{x} \in \mathcal{M}\) and \(i \in [F]\) for some \(\Phi > 0\) and \(\mathcal{M} \subseteq \Re^D\). For any \(\epsilon > 0\) and \(\delta \in (0, 1)\), PRIVATESVM-FINITE run on \(\mathbb{D}\) with loss \(\ell\), kernel \(k\), noise parameter \(0 < \lambda \le \frac{\epsilon}{2\Phi(F + \log \frac{1}{\delta})}\), and regularization parameter \(C\) is \((\epsilon, \delta)\)-useful with respect to the SVM under the \(\| \cdot \|_{\infty, \mathcal{M}}\)-norm.

In other words, run with arbitrary noise parameter \(\lambda > 0\), PRIVATESVM-FINITE is \((\epsilon, \delta)\)-useful for \(\epsilon = \Omega \left( \lambda \Phi \left( F + \log \frac{1}{\delta} \right) \right).

### Proof
Consider the SVM and PRIVATESVM-FINITE classifications on an arbitrary point \(\mathbf{x} \in \mathcal{M}\):

```
\begin{aligned}
\left| f_{\widehat{M}(\mathbb{D})}(\mathbf{x}) - f_{M(\mathbb{D})}(\mathbf{x}) \right| &= \left| \langle \hat{\mathbf{w}}, \phi(\mathbf{x}) \rangle - \langle \tilde{\mathbf{w}}, \phi(\mathbf{x}) \rangle \right| \\
&= \left| \langle \boldsymbol{\mu}, \phi(\mathbf{x}) \rangle \right| \\
\le \|\boldsymbol{\mu}\|_1 \|\phi(\mathbf{x})\|_\infty \\
\le \Phi \|\boldsymbol{\mu}\|_1 .
\end{aligned}
```

The absolute value of a zero-mean Laplace random variable with scale \(\lambda\) is exponentially distributed with scale \(\lambda^{-1}\). Moreover, the sum of \(q\) i.i.d. exponential random variables has an Erlang \(q\)-distribution with the same scale parameter. Thus we have, for Erlang \(F\)-distributed random variable \(X\) and any \(t > 0\),

```
\begin{aligned}
\forall \mathbf{x} \in \mathcal{M}, \quad \left| f_{\widehat{M}(\mathbb{D})}(\mathbf{x}) - f_{M(\mathbb{D})}(\mathbf{x}) \right| \le \Phi X \\
\Rightarrow \forall \epsilon > 0, \quad \Pr \left( \left\| f_{\widehat{M}(\mathbb{D})} - f_{M(\mathbb{D})} \right\|_{\infty, \mathcal{M}} > \epsilon \right) \le \Pr \left( X > \epsilon / \Phi \right) \\
\le \frac{\mathrm{E} \left[ e^{tX} \right]}{e^{\epsilon t / \Phi}} . \quad (7.5)
\end{aligned}
```

### Algorithm 7.3 PRIVATEERM-OBJECTIVE

**Inputs**: database \(\mathbb{D} = \{(\mathbf{x}^{(i)}, y^{(i)})\}_{i=1}^N\) with \(\mathbf{x}^{(i)} \in \Re^D, y^{(i)} \in \{-1, 1\}\); regularizer \(\rho(\cdot)\); loss function \(\ell(\cdot)\); \(c > 0\) a bound on the 2nd derivative of \(\ell\); regularization parameter \(\lambda > 0\); and privacy parameter \(\beta > 0\).

- 1 Let \(\beta' = \beta - \log \left( 1 + \frac{2c}{N\lambda} + \frac{c^2}{N^2 \lambda^2} \right)\);
- 2 If \(\beta' > 0\), then let \(\Delta = 0\); otherwise let \(\Delta = \frac{c}{N(e^{\beta/\lambda} - 1)} - \lambda\) and let \(\beta' = \beta/2\);
- 3 Sample \(\mathbf{b} \sim \exp(-\beta' \|\mathbf{b}\|_2 / 2)\); and
- 4 Return \(\mathbf{f}_{priv} = \text{argmin}_{\mathbf{f}} J_{priv}(\mathbf{f}, \mathbb{D}) + \frac{1}{2} \Delta \|\mathbf{f}\|_2^2\).

Here we have employed the Chernoff tail bound technique using Markov's inequality. The numerator of (7.5), the moment-generating function of the Erlang \(F\)-distribution with parameter \(\lambda\), is \((1 - \lambda t)^{-F}\) for \(t < \lambda^{-1}\). With the choice of \(t = (2\lambda)^{-1}\), this gives

```
\(\text{Pr} \left( \left\| f_{\widehat{M}(\mathbb{D})} - f_{M(\mathbb{D})} \right\|_{\infty, \mathcal{M}} > \epsilon \right) \leq (1 - \lambda t)^{-F} e^{-\epsilon t / \Phi}\)
\(= 2^F e^{-\epsilon / (2\lambda \Phi)}\)
\(= \exp \left( F \log_e 2 - \frac{\epsilon}{2\lambda \Phi} \right)\)
\(< \exp \left( F - \frac{\epsilon}{2\lambda \Phi} \right)\)
```

And provided that \(\epsilon \geq (2\lambda \Phi (F + \log_e \frac{1}{\delta}))\) this probability is bounded by \(\delta\).

## 7.5 Differential Privacy by Objective Perturbation

We briefly review another early independent approach to differentially private SVM learning due to Chaudhuri, Monteleoni, & Sarwate (2011). Their mechanism for linear SVM guarantees differential privacy by adding a random term to the objective, as performed previously by the same group for regularized logistic regression (Chaudhuri & Monteleoni 2009) and as is suitable for a general class of regularized empirical risk minimizers (Chaudhuri et al. 2011). While we limit our discussion to the linear SVM for clarity of exposition, all results go through essentially unchanged for SVM under finite-dimensional feature mappings. It is also notable that further general connections and treatments of (regularized) empirical risk minimization and differential privacy have been made; for example, with Bassily et al. (2014) providing matching rates under bounded Lipschitz influence of each training datum on loss and bounded parameter domains; and Duchi et al. (2013) demonstrating minimax rates for efficient convex risk minimization under a definition of local privacy (when data is unavailable to the statistician) with lower/upper bounds matching up to constant factors. We repeat here the objective of regularized empirical risk minimization, found in Equation (2.1):

```
\(J(f, \mathbb{D}) = \frac{1}{N} \sum_{(x,y) \in \mathbb{D}} \ell(y, f(x)) + \lambda \cdot \rho(f)\) ,
```
