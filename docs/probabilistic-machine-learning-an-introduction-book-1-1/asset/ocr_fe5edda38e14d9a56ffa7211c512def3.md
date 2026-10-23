of measuring the dependence of two random variables into a question about the similarity of their distributions. This gives rise to the notion of **mutual information** (MI) between two random variables, which we define below.

# 6.3.1 Definition

The mutual information between rv's $X$ and $Y$ is defined as follows:

$$\mathbb{I}(X;Y) \triangleq \mathbb{KL}\left(p(x,y)\|p(x)p(y)\right) = \sum_{y\in Y}\sum_{x\in X} p(x,y)\log\frac{p(x,y)}{p(x)p(y)}\tag{6.44}$$

(We write $\mathbb{I}(X;Y)$ instead of $\mathbb{I}(X,Y)$, in case $X$ and/or $Y$ represent sets of variables; for example, we can write $\mathbb{I}(X;Y,Z)$ to represent the MI between $X$ and $(Y,Z)$.) For continuous random variables, we just replace sums with integrals.

It is easy to see that MI is always non-negative, even for continuous random variables, since

$$\mathbb{I}(X;Y) = \mathbb{KL}\left(p(x,y)\|p(x)p(y)\right) \ge 0\tag{6.45}$$

We achieve the bound of 0 iff $p(x,y)=p(x)p(y)$.

# 6.3.2 Interpretation

Knowing that the mutual information is a KL divergence between the joint and factored marginal distributions tells is that the MI measures the information gain if we update from a model that treats the two variables as independent $p(x)p(y)$ to one that models their true joint density $p(x,y)$.

To gain further insight into the meaning of MI, it helps to re-express it in terms of joint and conditional entropies, as follows:

$$\mathbb{I}(X;Y) = \mathbb{H}(X) - \mathbb{H}(X|Y) = \mathbb{H}(Y) - \mathbb{H}(Y|X)\tag{6.46}$$

Thus we can interpret the MI between $X$ and $Y$ as the reduction in uncertainty about $X$ after observing $Y$, or, by symmetry, the reduction in uncertainty about $Y$ after observing $X$. Incidentally, this result gives an alternative proof that conditioning, on average, reduces entropy. In particular, we have $0 \le \mathbb{I}(X;Y) = \mathbb{H}(X) - \mathbb{H}(X|Y)$, and hence $\mathbb{H}(X|Y) \le \mathbb{H}(X)$.

We can also obtain a different interpretation. One can show that

$$\mathbb{I}(X;Y) = \mathbb{H}(X,Y) - \mathbb{H}(X|Y) - \mathbb{H}(Y|X)\tag{6.47}$$

Finally, one can show that

$$\mathbb{I}(X;Y) = \mathbb{H}(X) + \mathbb{H}(Y) - \mathbb{H}(X,Y)\tag{6.48}$$

See Fig. 6.4 for a summary of these equations in terms of an **information diagram**. (Formally, this is a signed measure mapping set expressions to their information-theoretic counterparts [Yeu91].)