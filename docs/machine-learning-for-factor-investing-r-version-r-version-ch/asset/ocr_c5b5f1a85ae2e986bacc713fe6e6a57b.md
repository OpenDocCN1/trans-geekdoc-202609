predictions to be based on the most recent trends. In Section 14.2 below, we introduce other theoretical and practical options.

# 14.1 Causality

Traditional machine learning models aim to uncover relationships between variables but do not usually specify *directions* for these relationships. One typical example is the linear regression. If we write $y = a + bx + \epsilon$, then it is also true that $x = b^{-1}(y - a - \epsilon)$, which is of course also a linear relationship (with respect to $y$). These equations do not define causation whereby $x$ would be a clear determinant of $y$ ($x \rightarrow y$, but the opposite could be false).

# 14.1.1 Granger causality

The most notable tool first proposed by Granger (1969) is probably the simplest. For simplicity, we consider only two stationary processes, $X_t$ and $Y_t$. A strict definition of causality could be the following. $X$ can be said to cause $Y$, whenever, for some integer $k$,

$$(Y_{t+1}, ..., Y_{t+k})|(\mathcal{F}_{Y,t} \cup \mathcal{F}_{X,t}) \stackrel{d}{=} (Y_{t+1}, ..., Y_{t+k})|\mathcal{F}_{Y,t},$$

that is, when the distribution of future values of $Y_t$, conditionally on the knowledge of both processes is not the same as the distribution with the sole knowledge of the filtration $\mathcal{F}_{Y,t}$. Hence $X$ does have an impact on $Y$ because its trajectory alters that of $Y$.

Now, this formulation is too vague and impossible to handle numerically, thus we simplify the setting via a linear formulation. We keep the same notations as section 5 of the original paper by Granger (1969). The test consists of two regressions:

$$X_t = \sum_{j=1}^m a_j X_{t-j} + \sum_{j=1}^m b_j Y_{t-j} + \epsilon_t$$
$$Y_t = \sum_{j=1}^m c_j X_{t-j} + \sum_{j=1}^m d_j Y_{t-j} + \nu_t$$

where for simplicity, it is assumed that both processes have zero mean. The usual assumptions apply: the Gaussian noises $\epsilon_t$ and $\nu_t$ are uncorrelated in every possible way (mutually and through time). The test is the following: if one $b_j$ is nonzero, then it is said that $Y$ Granger-causes $X$ and if one $c_j$ is nonzero, $X$ Granger-causes $Y$. The two are not mutually exclusive and it is widely accepted that feedback loops can very well occur.

Statistically, under the null hypothesis, $b_1 = \cdots = b_m = 0$ (resp. $c_1 = \cdots = c_m = 0$), which can be tested using the usual Fischer distribution. Obviously, the linear restriction can be dismissed but the tests are then much more complex. The main financial article in this direction is Hiemstra and Jones (1994).

There are many R packages that embed Granger causality functionalities. One of the most widespread is `lmtest`, so we work with it below. The syntax is incredibly simple. The *order* is the maximum lag $m$ in the above equation. We test if market capitalization averaged over