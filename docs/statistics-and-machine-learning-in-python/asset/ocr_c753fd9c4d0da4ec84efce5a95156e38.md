Since we do not care about the magnitude of $w$, only its direction, we replaced the scalar factor $(w^T S_B w)/(w^T S_W w)$ by $\lambda$.

In the multiple-class case, the solutions $w$ are determined by the eigenvectors of $S_W^{-1} S_B$ that correspond to the $K-1$ largest eigenvalues.

However, in the two-class case (in which $S_B = (\mu_1 - \mu_0)(\mu_1 - \mu_0)^T$) it is easy to show that $w = S_W^{-1}(\mu_1 - \mu_0)$ is the unique eigenvector of $S_W^{-1} S_B$:

$S_W^{-1}(\mu_1 - \mu_0)(\mu_1 - \mu_0)^T w = \lambda w$

$S_W^{-1}(\mu_1 - \mu_0)(\mu_1 - \mu_0)^T S_W^{-1}(\mu_1 - \mu_0) = \lambda S_W^{-1}(\mu_1 - \mu_0)$

where here $\lambda = (\mu_1 - \mu_0)^T S_W^{-1}(\mu_1 - \mu_0)$. Which leads to the result

$w \propto S_W^{-1}(\mu_1 - \mu_0)$.

# 13.1.2 The separating hyperplane

The separating hyperplane is a $P-1$-dimensional hyper surface, orthogonal to the projection vector, $w$. There is no single best way to find the origin of the plane along $w$, or equivalently the classification threshold that determines whether a point should be classified as belonging to $C_0$ or to $C_1$. However, if the projected points have roughly the same distribution, then the threshold can be chosen as the hyperplane exactly between the projections of the two means, i.e. as

$T = w \cdot \frac{1}{2}(\mu_1 - \mu_0)$.

```
%matplotlib inline
import warnings
warnings.filterwarnings(action='once')
```

# 13.2 Linear discriminant analysis (LDA)

Linear discriminant analysis (LDA) is a probabilistic generalization of Fisher’s linear discriminant. It uses Bayes’ rule to fix the threshold based on prior probabilities of classes.

+   1. First compute the The class-conditional distributions of $x$ given class $C_k$: $p(x|C_k) = \mathcal{N}(x|\mu_k, S_W)$. Where $\mathcal{N}(x|\mu_k, S_W)$ is the multivariate Gaussian distribution defined over a P-dimensional vector $x$ of continuous variables, which is given by
+   
+   $\mathcal{N}(x|\mu_k, S_W) = \frac{1}{(2\pi)^{P/2}|S_W|^{1/2}} \exp\{-\frac{1}{2}(x - \mu_k)^T S_W^{-1}(x - \mu_k)\}$
+   
+   2. Estimate the prior probabilities of class $k$, $p(C_k) = N_k/N$.
+   
+   3. Compute posterior probabilities (ie. the probability of a each class given a sample) combining conditional with priors using Bayes’ rule: