We can expand the lower bound by using the factorizations of $p$ and $q$ (following David M. Blei, Andrew Y. Ng, and Michael I. Jordan’s “Latent Dirichlet Allocation,” *Journal of Machine Learning Research*, 2003).

$$L(\gamma,\phi;\alpha,\beta)=E_q[\log p(\theta|\alpha)]+E_q[\log p(z|\theta)] +E_q[\log p(x|z,\beta)] -E_q[\log q(\theta)]-E_q[\log q(z)] \tag{9.6}$$

Each of the five terms in $L(\gamma,\phi;\alpha,\beta)$ can be expanded as follows.

$$\begin{aligned}
L(\gamma,\phi;\alpha,\beta)={}&\log\Gamma\left(\sum_{j=1}^{k}\alpha_j\right)-\sum_{i=1}^{k}\log\Gamma(\alpha_i)\\
&+\sum_{i=1}^{k}(\alpha_i-1)\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&+\sum_{n=1}^{N}\sum_{i=1}^{k}\phi_{ni}\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&+\sum_{n=1}^{N}\sum_{i=1}^{k}\sum_{j=1}^{K}\phi_{ni}x_n^j\log\beta_{ij}\\
&-\log\Gamma\left(\sum_{j=1}^{k}\gamma_j\right)+\sum_{i=1}^{k}\log\Gamma(\gamma_i)\\
&-\sum_{i=1}^{k}(\gamma_i-1)\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&-\sum_{n=1}^{N}\sum_{i=1}^{k}\phi_{ni}\log\phi_{ni}
\end{aligned}\tag{9.7}$$

Here, $\Psi(x)=d/dx\ \log\Gamma(x)$ is the digamma function. $L(\gamma,\phi;\alpha,\beta)$ can be maximized using coordinate ascent over the variational parameters $\phi$, $\gamma$, $\alpha$.

$$\begin{aligned}
\phi_{dwk}&\propto\exp\left\{E_q[\log\theta_{dk}]+E_q[\log\beta_{kw}]\right\}\\
\gamma_{dk}&=\alpha+\sum_w n_{dw}\phi_{dwk}\\
\lambda_{kw}&=\eta+\sum_d n_{dw}\phi_{dwk}
\end{aligned}\tag{9.8}$$