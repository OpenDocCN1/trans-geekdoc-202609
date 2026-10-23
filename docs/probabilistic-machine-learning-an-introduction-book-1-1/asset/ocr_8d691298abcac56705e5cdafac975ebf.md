# 6.3.4 Conditional mutual information

We can define the **conditional mutual information** in the obvious way

$\mathbb{I}(X;Y|Z) \triangleq \mathbb{E}_{p(Z)}[\mathbb{I}(X;Y)|Z]$  (6.53)
$= \mathbb{E}_{p(x,y,z)}\left[\log\frac{p(x,y|z)}{p(x|z)p(y|z)}\right]$  (6.54)
$= \mathbb{H}(X|Z)+\mathbb{H}(Y|Z)-\mathbb{H}(X,Y|Z)$  (6.55)
$= \mathbb{H}(X|Z)-\mathbb{H}(X|Y,Z)=\mathbb{H}(Y|Z)-\mathbb{H}(Y|X,Z)$  (6.56)
$= \mathbb{H}(X,Z)+\mathbb{H}(Y,Z)-\mathbb{H}(Z)-\mathbb{H}(X,Y,Z)$  (6.57)
$= \mathbb{I}(Y;X,Z)-\mathbb{I}(Y;Z)$  (6.58)

The last equation tells us that the conditional MI is the extra (residual) information that $X$ tells us about $Y$, excluding what we already knew about $Y$ given $Z$ alone.

We can rewrite Eq. (6.58) as follows:

$\mathbb{I}(Z,Y;X)=\mathbb{I}(Z;X)+\mathbb{I}(Y;X|Z)$  (6.59)

Generalizing to $N$ variables, we get the **chain rule for mutual information**:

$\mathbb{I}(Z_1,\dots,Z_N;X)=\sum_{n=1}^N \mathbb{I}(Z_n;X|Z_1,\dots,Z_{n-1})$  (6.60)

# 6.3.5 Normalized mutual information

For some applications, it is useful to have a normalized measure of dependence, between 0 and 1. We now discuss one way to construct such a measure.

First, note that

$\mathbb{I}(X;Y)=\mathbb{H}(X)-\mathbb{H}(X|Y)\le\mathbb{H}(X)$  (6.61)
$=\mathbb{H}(Y)-\mathbb{H}(Y|X)\le\mathbb{H}(Y)$  (6.62)

so

$0\le\mathbb{I}(X;Y)\le\min(\mathbb{H}(X),\mathbb{H}(Y))$  (6.63)

Therefore we can define the **normalized mutual information** as follows:

$NMI(X,Y)=\frac{\mathbb{I}(X;Y)}{\min(\mathbb{H}(X),\mathbb{H}(Y))}\le1$  (6.64)

This normalized mutual information ranges from 0 to 1. When $NMI(X,Y)=0$, $\mathbb{I}(X;Y)=0$ so $X$ and $Y$ are independent. Without loss of generality assume $X$ has the higher entropy: $NMI(X,Y)=1\implies\mathbb{I}(X;Y)=\mathbb{H}(X)-\mathbb{H}(X|Y)=\mathbb{H}(X)\implies\mathbb{H}(X|Y)=0$ and so $X$ is a deterministic function of $Y$.