$\forall f \in \mathcal{F}_{\gamma/2}(\mathcal{S}_n \cup \mathcal{S}'_n):\quad \frac{1}{n}\sum_{i=1}^{n}\sigma_i\left[L'(f(X_i),Y_i)-0.5\right] \leq \sqrt{\frac{\ln(N/\delta)}{2n}}.$

Lemma 4.8 (which is valid even when $\mathcal{F}$ in the lemma depends on $\mathcal{S}_n \cup \mathcal{S}'_n$) with $\psi=0$ implies that with probability at least $1-\delta_1$,

$\forall f \in \mathcal{F}_{\gamma/2}(\mathcal{S}_n \cup \mathcal{S}'_n):\quad \frac{1}{n}\sum_{i=1}^{n}L'(f(X_i'),Y_i') \leq \frac{1}{n}\sum_{i=1}^{n}L'(f(X_i),Y_i)+\sqrt{\frac{2\ln(2N/\delta_1)}{n}}.$

Since for all $f\in\mathcal{F}$, we can find $f'\in\mathcal{F}_{\gamma/2}(\mathcal{S}_n\cup\mathcal{S}'_n)$ so that $|f(x)-f'(x)|\leq\gamma/2$, it follows that

$$\begin{aligned}
\frac{1}{n}\sum_{i=1}^{n}L(f(X_i'),Y_i')&\leq \frac{1}{n}\sum_{i=1}^{n}L'(f'(X_i'),Y_i')\\
&\leq \frac{1}{n}\sum_{i=1}^{n}L'(f'(X_i),Y_i)+\sqrt{\frac{2\ln(2N/\delta_1)}{n}}\\
&\leq \frac{1}{n}\sum_{i=1}^{n}\widetilde{L}(f(X_i),Y_i)+\sqrt{\frac{2\ln(2N/\delta_1)}{n}}.
\end{aligned}$$

Note that the first and the last inequalities used (4.6). The standard additive Chernoff bound implies that for all $w\in\Omega$, with probability at least $1-\delta_2$,

$$\mathbb{E}_{(X,Y)\sim\mathcal{D}}L(f(X),Y)\leq \frac{1}{n}\sum_{i=1}^{n}L(f(X_i'),Y_i')+\sqrt{\frac{\ln(1/\delta_2)}{2n}}.$$

Therefore in Lemma 4.11, we can take symbols as defined, together with $\delta_1=2\delta/3$, and $\delta_2=\delta/3$, to obtain the desired bound.

Similarly, we obtain from Corollary 2.27 the following uniform convergence result over $\mathcal{F}_{\gamma/2}(\mathcal{S}_n\cup\mathcal{S}'_n)$. With probability $1-\delta$, $\forall f\in\mathcal{F}_{\gamma/2}(\mathcal{S}_n\cup\mathcal{S}'_n)$,

$$\begin{aligned}
\frac{1}{n}\sum_{i=1}^{n}\sigma_iL'(f(X_i),Y_i)&\leq \sqrt{\frac{2\sum_{i=1}^{n}L'(f(X_i),Y_i)^2\ln(N/\delta)}{n^2}}\\
&\leq \gamma'\frac{1}{n}\sum_{i=1}^{n}L'(f(X_i),Y_i)+\frac{\ln(N/\delta)}{2\gamma'n}.
\end{aligned}$$

Then Lemma 4.8 (which is valid even when $\mathcal{F}$ in the lemma depends on $\mathcal{S}_n\cup\mathcal{S}'_n$) implies the following uniform convergence result. With probability at least $1-\delta_1$ over $(\mathcal{S}_n,\mathcal{S}'_n)\sim\mathcal{D}^{2n}$,