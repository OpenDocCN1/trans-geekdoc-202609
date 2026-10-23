# 6.3.6 MI as a “generalized correlation coefficient”

Suppose that $(x, y)$ are jointly Gaussian:

$$\begin{pmatrix} x \\ y \end{pmatrix} \sim \mathcal{N}\left( \mathbf{0}, \begin{pmatrix} \sigma^2 & \rho\sigma^2 \\ \rho\sigma^2 & \sigma^2 \end{pmatrix} \right) \tag{6.65}$$

We now show how to compute the mutual information between $X$ and $Y$.

Using Eq. (6.25), we find that the entropy is

$$h(X, Y) = \frac{1}{2}\log\big[(2\pi e)^2 \det \Sigma\big] = \frac{1}{2}\log\big[(2\pi e)^2\sigma^4(1-\rho^2)\big] \tag{6.66}$$

Since $X$ and $Y$ are individually normal with variance $\sigma^2$, we have

$$h(X)=h(Y)=\frac{1}{2}\log\big[2\pi e\sigma^2\big] \tag{6.67}$$

Hence

$$I(X,Y)=h(X)+h(Y)-h(X,Y) \tag{6.68}$$ $$=\log[2\pi e\sigma^2]-\frac12\log[(2\pi e)^2\sigma^4(1-\rho^2)] \tag{6.69}$$ $$=\frac12\log[(2\pi e\sigma^2)^2]-\frac12\log[(2\pi e\sigma^2)^2(1-\rho^2)] \tag{6.70}$$ $$=\frac12\log\frac{1}{1-\rho^2}=-\frac12\log[1-\rho^2] \tag{6.71}$$

We now discuss some interesting special cases.

+   1. $\rho = 1$. In this case, $X = Y$, and $I(X,Y)=\infty$, which makes sense. Observing $Y$ tells us an infinite amount of information about $X$ (as we know its real value exactly).
+   2. $\rho = 0$. In this case, $X$ and $Y$ are independent, and $I(X,Y)=0$, which makes sense. Observing $Y$ tells us nothing about $X$.
+   3. $\rho = -1$. In this case, $X = -Y$, and $I(X,Y)=\infty$, which again makes sense. Observing $Y$ allows us to predict $X$ to infinite precision.

Now consider the case where $X$ and $Y$ are scalar, but not jointly Gaussian. In general it can be difficult to compute the mutual information between continuous random variables, because we have to estimate the joint density $p(X,Y)$. For scalar variables, a simple approximation is to **discretize** or **quantize** them, by dividing the ranges of each variable into bins, and computing how many values fall in each histogram bin [Sco79]. We can then easily compute the MI using the empirical pmf.

Unfortunately, the number of bins used, and the location of the bin boundaries, can have a significant effect on the results. Another approach is to try many different bin sizes and locations, and to compute the maximum MI achieved. This statistic, appropriately normalized, is known as the **maximal information coefficient** (MIC) [Res+11]. More precisely, define

$$m(w, h)=\frac{\max_{G\in\mathcal{G}(w,h)} \mathbb{I}\big(X(G);Y(G)\big)}{\log\min(w,h)} \tag{6.72}$$