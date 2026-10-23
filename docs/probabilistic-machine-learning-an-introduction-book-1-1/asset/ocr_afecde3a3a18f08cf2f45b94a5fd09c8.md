# 6 Information theory

In this chapter, we introduce a few basic concepts from the field of **information theory**. More details can be found in other books such as [Mac03; CT06], as well as the sequel to this book, [Mur22].

# 6.1 Entropy

The **entropy** of a probability distribution can be interpreted as a measure of uncertainty, or lack of predictability, associated with a random variable drawn from a given distribution, as we explain below.

We can also use entropy to define the **information content** of a data source. For example, suppose we observe a sequence of symbols $X_n \sim p$ generated from distribution $p$. If $p$ has high entropy, it will be hard to predict the value of each osbervation $X_n$. Hence we say that the dataset $\mathcal{D} = (X_1, \dots, X_n)$ has high information content. By contrast, if $p$ is a degenerate distribution with 0 entropy (the minimal value), then every $X_n$ will be the same, so $\mathcal{D}$ does not contain much information. (All of this can be formalized in terms of data compression, as we discuss in the sequel to this book.)

# 6.1.1 Entropy for discrete random variables

The entropy of a discrete random variable $X$ with distribution $p$ over $K$ states is defined by

$$\mathbb{H}(X) \triangleq -\sum_{k=1}^{K} p(X=k) \log_2 p(X=k) = -\mathbb{E}_X [\log p(X)] \tag{6.1}$$

(Note that we use the notation $\mathbb{H}(X)$ to denote the entropy of the rv with distribution $p$, just as people write $\mathbb{V}[X]$ to mean the variance of the distribution associated with $X$; we could alternatively write $\mathbb{H}(p)$.) Usually we use log base 2, in which case the units are called **bits** (short for binary digits). For example, if $X \in \{1,\dots,5\}$ with histogram distribution $p = [0.25,0.25,0.2,0.15,0.15]$, we find $H = 2.29$ bits. If we use log base $e$, the units are called **nats**.

The discrete distribution with **maximum entropy** is the uniform distribution. Hence for a $K$-ary random variable, the entropy is maximized if $p(x = k) = 1/K$; in this case, $\mathbb{H}(X) = \log_2 K$. Conversely, the distribution with minimum entropy (which is zero) is any delta-function that puts all its mass on one state. Such a distribution has no uncertainty.

For the special case of binary random variables, $X \in \{0,1\}$, we can write $p(X = 1) = \theta$ and