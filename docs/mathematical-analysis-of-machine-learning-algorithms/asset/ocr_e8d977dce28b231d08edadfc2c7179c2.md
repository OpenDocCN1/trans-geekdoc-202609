In this derivation, the first inequality used $Q_j(\cdot) \ge 0$; $(a)$ used the assumption of the lemma, and $(b)$ used the definition of TV-norm (see Appendix B). By rearranging the last term and using the definition of $\beta$, we obtain the desired bound.

The Assouad lemma stated here is a generalization of the typical Assouad lemma that appears in the literature. The latter is often stated with

$\mathcal{P} = \{\mathcal{D}_\tau : \tau \in \{\pm1\}^d\}$,

and $M_j$ contains indices in $\{\pm1\}^d$ that may differ from $\tau$ by only one coordinate $j$. The following result is a direct application of Assouad’s lemma with this representation, and the TV-norm of product distributions is estimated by Theorem B.13.

# Theorem 12.28

Let $d \ge 1$ be an integer and $\mathcal{P}_d = \{\mathcal{D}_\tau : \tau \in \{-1,1\}^d\}$ contain $2^d$ probability measures. Suppose that the loss function $Q$ can be decomposed as

$Q(\theta, \mathcal{D}) = \sum_{j=1}^d Q_j(\theta, \mathcal{D})$, 

where $Q_j(\cdot, \cdot) \ge 0$. For any $j$ and $\tau$, let $\tau^{-[j]}$ be the index that differs with $\tau$ only by one coordinate $j$. Assume that there exists $\epsilon, \beta_j \ge 0$ such that

$\forall \tau: \quad [Q_j(\theta, \mathcal{D}_\tau) + Q_j(\theta, \mathcal{D}_{\tau^{-[j]}})] \ge \epsilon, \quad H(\mathcal{D}_\tau \| \mathcal{D}_{\tau^{-[j]}}) \le \beta_j.$

Consider randomized $\mathcal{A}(\mathcal{S}_n)$ based on $\mathcal{S}_n \sim \mathcal{D}_\tau^n$ for some $\tau$. We have

$\frac{1}{2^d} \sum_\tau \mathbb{E}_{\mathcal{S}_n \sim \mathcal{D}_\tau^n} \mathbb{E}_\mathcal{A} Q(\mathcal{A}(\mathcal{S}_n), \mathcal{D}_\tau) \ge \frac{\epsilon d}{2} - \frac{\epsilon}{2} \sum_{j=1}^d \sqrt{2 - 2(1 - 0.5 \beta_j^2)^n}$, 

where $\mathbb{E}_\mathcal{A}$ is with respect to the internal randomization in $\mathcal{A}$. This implies that

$r_n(\mathcal{P}_d, Q) \ge \frac{\epsilon d}{2} - \frac{\epsilon}{2} \sum_{j=1}^d \sqrt{2 - 2(1 - 0.5 \beta_j^2)^n}$.

In general, if we can choose $\beta_j = O(\epsilon)$, then Theorem 12.28 implies a bound of

$r_n(\mathcal{P}_d, Q) \ge \Omega(d\epsilon)$

when $n = O(1/\epsilon^2)$. The following example illustrates this with a specific application.

# Example 12.29

Consider observations $Z_i \in \{0,1\}^d$, where each $Z_i$ has $d$ components $Z_{i,j} \sim \text{Bernoulli}(\theta_j)$ for $j = 1, \dots, d$. Let $\theta = [\theta_1, \dots, \theta_d] \in (0,1)^d$ be the model parameters to be estimated. For $\tau \in \{\pm1\}^d$, we let $\theta_{\tau,j} = \epsilon^2 (1 + \tau_j)/2$, where $\epsilon \in (0,0.5)$. Let $\mathcal{D}_\tau$ be the corresponding Bernoulli distribution, and $\mathcal{P}_d = \{\mathcal{D}_\tau\}$. Define the metric

$Q(\hat{\theta}, \theta) = \sum_{j=1}^d Q_j(\hat{\theta}, \theta), \quad Q_j(\hat{\theta}, \theta) = \left| \sqrt{\hat{\theta}_j} - \sqrt{\theta_j} \right|.$