The joint distribution is

| p(X,Y) | Y = 0 | Y = 1 |
|---|---|---|
| X = 0 | 1/8 | 3/8 |
| X = 1 | 3/8 | 1/8 |

so the joint entropy is given by

$$\mathbb{H}(X,Y) = -\left[\frac{1}{8}\log_2\frac{1}{8} + \frac{3}{8}\log_2\frac{3}{8} + \frac{3}{8}\log_2\frac{3}{8} + \frac{1}{8}\log_2\frac{1}{8}\right] = 1.81\ \text{bits}\tag{6.8}$$

Clearly the marginal probabilities are uniform: $p(X = 1) = p(X = 0) = p(Y = 0) = p(Y = 1) = 0.5$, so $\mathbb{H}(X) = \mathbb{H}(Y) = 1$. Hence $\mathbb{H}(X,Y) = 1.81$ bits $<$ $\mathbb{H}(X) + \mathbb{H}(Y) = 2$ bits. In fact, this upper bound on the joint entropy holds in general. If $X$ and $Y$ are independent, then $\mathbb{H}(X,Y) = \mathbb{H}(X) + \mathbb{H}(Y)$, so the bound is tight. This makes intuitive sense: when the parts are correlated in some way, it reduces the “degrees of freedom” of the system, and hence reduces the overall entropy.

What is the lower bound on $\mathbb{H}(X,Y)$? If $Y$ is a deterministic function of $X$, then $\mathbb{H}(X,Y) = \mathbb{H}(X)$. So

$$\mathbb{H}(X,Y) \ge \max\{\mathbb{H}(X),\mathbb{H}(Y)\} \ge 0\tag{6.9}$$

Intuitively this says combining variables together does not make the entropy go down: you cannot reduce uncertainty merely by adding more unknowns to the problem, you need to observe some data, a topic we discuss in Sec. 6.1.4.

We can extend the definition of joint entropy from two variables to $n$ in the obvious way.

# 6.1.4 Conditional entropy

The **conditional entropy** of $Y$ given $X$ is the uncertainty we have in $Y$ after seeing $X$, averaged over possible values for $X$:

$$\mathbb{H}(Y|X) \triangleq \mathbb{E}_{p(X)}[\mathbb{H}(p(Y|X))] \tag{6.10}$$ $$= \sum_x p(x)\mathbb{H}(p(Y|X=x)) = -\sum_x p(x)\sum_y p(y|x)\log p(y|x) \tag{6.11}$$ $$= -\sum_{x,y} p(x,y)\log p(y|x) = -\sum_{x,y} p(x,y)\log\frac{p(x,y)}{p(x)} \tag{6.12}$$ $$= -\sum_{x,y} p(x,y)\log p(x,y) + \sum_x p(x)\log\frac{1}{p(x)} \tag{6.13}$$ $$= \mathbb{H}(X,Y) - \mathbb{H}(X) \tag{6.14}$$

If $Y$ is a deterministic function of $X$, then knowing $X$ completely determines $Y$, so $\mathbb{H}(Y|X)=0$. If $X$ and $Y$ are independent, knowing $X$ tells us nothing about $Y$ and $\mathbb{H}(Y|X)=\mathbb{H}(Y)$. Since $\mathbb{H}(X,Y) \le \mathbb{H}(Y)+\mathbb{H}(X)$, we have

$$\mathbb{H}(Y|X) \le \mathbb{H}(Y)\tag{6.15}$$