b. The distribution $p(y)=\int p(y\mid x)p(x)\,dx$ is Gaussian. Compute the mean $\mu_y$ and the covariance $\Sigma_y$. Derive your result in detail.

$p(y)$ is Gaussian distributed (affine transformation of the Gaussian random variable $x$) with mean $\mu_y$ and covariance matrix $\Sigma_y$. We obtain

$$\begin{aligned}
\mu_y &= \mathbb{E}_y[y] = \mathbb{E}_{X,W}[Ax+b+w] = A\mathbb{E}_X[x]+b+\mathbb{E}_W[w]\\
&= A\mu_x+b, \qquad \text{and}\\[4pt]
\Sigma_y &= \mathbb{E}_y[yy^\mathsf{T}]-\mathbb{E}_y[y]\mathbb{E}_y[y]^\mathsf{T}\\
&= \mathbb{E}_{X,W}[(Ax+b+w)(Ax+b+w)^\mathsf{T}]-\mu_y\mu_y^\mathsf{T}\\
&= \mathbb{E}_{X,W}[Axx^\mathsf{T}A^\mathsf{T}+Axb^\mathsf{T}+Axw^\mathsf{T}+bx^\mathsf{T}A^\mathsf{T}+bb^\mathsf{T}+bw^\mathsf{T}\\
&\qquad +w(Ax+b)^\mathsf{T}+ww^\mathsf{T}]-\mu_y\mu_y^\mathsf{T}.
\end{aligned}$$

We use the linearity of the expected value, move all constants out of the expected value, and exploit the independence of $w$ and $x$:

$$\begin{aligned}
\Sigma_y &= A\mathbb{E}_X[xx^\mathsf{T}]A^\mathsf{T}+A\mathbb{E}_X[x]b^\mathsf{T}+b\mathbb{E}_X[x]^\mathsf{T}A^\mathsf{T}+bb^\mathsf{T}+\mathbb{E}_W[ww^\mathsf{T}]\\
&\qquad -(A\mu_x+b)(A\mu_x+b)^\mathsf{T},
\end{aligned}$$

where we used our previous result for $\mu_y$. Note that $\mathbb{E}_W[w]=0$. We continue as follows:

$$\begin{aligned}
\Sigma_y &= A\mathbb{E}_X[xx^\mathsf{T}]A^\mathsf{T}+A\mu_xb^\mathsf{T}+b\mu_x^\mathsf{T}A^\mathsf{T}+bb^\mathsf{T}+Q\\
&\qquad -A\mu_x\mu_x^\mathsf{T}A^\mathsf{T}-A\mu_xb^\mathsf{T}-b\mu_x^\mathsf{T}A^\mathsf{T}-bb^\mathsf{T}\\
&= A\left(\mathbb{E}_X[xx^\mathsf{T}]-\mu_x\mu_x^\mathsf{T}\right)A^\mathsf{T}+Q\\
&= A\Sigma_xA^\mathsf{T}+Q.
\end{aligned}$$

Alternatively, we could have exploited

$$\begin{aligned}
\mathbb{V}_y[y] &= \mathbb{V}_{x,w}[Ax+b+w]\mathrel{\overset{\mathrm{i.i.d.}}{=}}\mathbb{V}_x[Ax+b]+\mathbb{V}_w[w]\\
&= A\mathbb{V}_xA^\mathsf{T}+Q=A\Sigma_xA^\mathsf{T}+Q.
\end{aligned}$$

c. The random variable $y$ is being transformed according to the measurement mapping

$$z=Cy+v,$$

where $z\in\mathbb{R}^F$, $C\in\mathbb{R}^{F\times E}$, and $v\sim\mathcal{N}(v\mid 0,R)$ is independent Gaussian (measurement) noise.

+   ▪ Write down $p(z\mid y)$.

$$\begin{aligned}
p(z\mid y)&=\mathcal{N}(z\mid Cy,R)\\
&=(2\pi)^{-F/2}|R|^{-1/2}\exp\left(-\frac{1}{2}(z-Cy)^\mathsf{T}R^{-1}(z-Cy)\right).
\end{aligned}$$