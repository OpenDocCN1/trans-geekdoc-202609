# 5 Conclusions

To the question “How can we generate a graph with the right patterns?”, we give a two-step answer: first generate the patterns, then optimize the graph. We choose to focus on patterns that we can learn from random walks. The reason is that many downstream applications use random walks, so graphs generated this way can have a significant impact. The optimization step makes the graph robust to noise in the generated patterns. It also lets us impose constraints on the graph, such as desired degree distributions.

GRAPHWEAVE puts this idea into practice via a fast, interpretable, and simple algorithm. GRAPHWEAVE learns to predict random walk trajectories, which show how random walks transform a vector of node attributes. Then, using this predictor, we generate new trajectories. Finally, we find the optimal graph that fits these trajectories. The algorithm only requires a transformer and an optimizer. Experiments on several simulated and benchmark datasets show that GRAPHWEAVE outperforms the state of the art, and is among the fastest methods.

# A Smoothed Normalized Adjacency Matrix

**Lemma 1.** Let $A$, $d'_i$, and $L$ be defined as in Definition 1. Let $D' = \text{diag}(d'_i)$. Let $\beta_1 \ge \dots \ge \beta_n$ be the eigenvalues of $L$. Then, $\beta_1 = 1$ with the corresponding eigenvector being $(D'^{1/2}\mathbf{1})/\|D'^{1/2}\mathbf{1}\|$, and $\beta_n > -1$.

_Proof._ We have $L = D'^{-1/2}((1 - \alpha)A + \alpha I)D'^{-1/2}$. Since $A\mathbf{1} = D\mathbf{1}$, we have $LD'^{1/2}\mathbf{1} = D'^{-1/2}((1 - \alpha)A + \alpha I)\mathbf{1} = D'^{-1/2}((1 - \alpha)D + \alpha I)\mathbf{1} = D'^{1/2}\mathbf{1}$. So, $\mathbf{1}$ is an eigenvalue of $L$ with eigenvector $(D'^{1/2}\mathbf{1})/\|D'^{1/2}\mathbf{1}\|$. To show that it is the largest eigenvalue, we show that $I - L$ is positive semidefinite. We have

\( I - L = D'^{-1/2}(D' - (1 - \alpha)A - \alpha I)D'^{-1/2} = (1 - \alpha)D'^{-1/2}(D - A)D'^{-1/2} \
= (1 - \alpha)D'^{-1/2}D^{1/2}(I - D^{-1/2}AD^{-1/2})D^{1/2}D'^{-1/2} . \)

Now, $D$ and $D'$ are positive definite, and so is $I - D^{-1/2}AD^{-1/2}$, since

\(\boldsymbol{x}^T(I - D^{-1/2}AD^{-1/2})\boldsymbol{x} = \sum_i \boldsymbol{x}_i^2 - \sum_{(i,j) \in E} \frac{2x(i)x(j)}{\sqrt{d'_id'_j}} = \sum_{(i,j) \in E} \left( \frac{x(i)}{\sqrt{d'_i}} - \frac{x(j)}{\sqrt{d'_j}} \right)^2 \ge 0,\)

for any $\boldsymbol{x}$. So $I - L$ is positive semidefinite. Similarly, we show that $L$'s smallest eigenvalue is greater than $-1$ by showing that $I + L$ is positive definite.

\( I + L = D'^{-1/2}(D' + (1 - \alpha)A + \alpha I)D'^{-1/2} = (1 - \alpha)D'^{-1/2}(D + A)D'^{-1/2} + 2\alpha D'^{-1} \
= (1 - \alpha)D'^{-1/2}D^{1/2}(I + D^{-1/2}AD^{-1/2})D^{1/2}D'^{-1/2} + 2\alpha D'^{-1} . \)

The second term is positive definite. The first term is positive semidefinite since

\(\boldsymbol{x}^T(I + D^{-1/2}AD^{-1/2})\boldsymbol{x} = \sum_{(i,j) \in E} \left( \frac{x(i)}{\sqrt{d'_i}} + \frac{x(j)}{\sqrt{d'_j}} \right)^2 \ge 0.\)