Proof We apply Theorem 13.24 with $d=1$ and $m=K$. We consider a family of $K$ distributions $\mathcal{P}_{\mathcal{Z}}=\{q^{\tau},\tau=1,\dots,K\}$, and for each arm $a$, the distribution $q^{\tau}(a)$ is a Bernoulli distribution $r\in\{0,1\}$ with mean $\mathbb{E}[r]=0.5+\epsilon\mathbb{1}(a=\tau)$ with $\epsilon\in(0,0.1]$ to be determined later. We also define $q_{0}(a)$ as a Bernoulli distribution $r\in\{0,1\}$ with mean $\mathbb{E}[r]=0.5$. By construction $q^{\tau}\sim_{1}q^{\tau'}$ for all $\tau,\tau'\in[K]$, we can map them all to $q_{1}^{\tau}=q_{0}$.

If we pull an arm $\theta$, we have

$$Q(\theta,q^{\tau})=\epsilon\mathbb{1}(\theta\neq\tau).$$

It is clear that $[Q(\theta,q^{\tau})+Q(\theta,q^{\tau'})]\ge\epsilon$ for $\tau\neq\tau'$. Consider $n\le T$ samples generated sequentially by an arbitrary bandit algorithm and $q^{\tau}(a)$, and let the resulting distribution generate $\mathcal{S}_{n}$ as $p^{\tau}(\mathcal{S}_{n})$, where $\mathcal{S}_{n}=\{a_{1},r_{1},\dots,a_{n},r_{n}\}$.

Let $\epsilon=\min\left(0.1,0.24\sqrt{K/T}\right)$. We have for all $a_{t}$,

$$\frac{1}{K}\sum_{\tau=1}^{K}\mathrm{KL}\left(q_{0}(a_{l})||q^{\tau}(a_{l})\right)=\frac{1}{K}\sum_{\tau=1}^{K}\mathrm{KL}\left(q_{0}(a_{t})||q^{\tau}(a_{t})\right)\mathbb{1}(a_{l}=\tau)$$ 
$$=\frac{1}{K}\mathrm{KL}(0.5||0.5+\epsilon)\le\frac{0.5\epsilon^{2}}{K(0.5+\epsilon)(0.5-\epsilon)}\le\frac{2.1}{K}\epsilon^{2}.$$

The first inequality is left as Exercise 16.4. The second inequality used $\epsilon\le0.1$. Theorem 13.24 (with $d=1$, $m=K$, and $\beta_{1,t}^{2}=\frac{2.1}{K}\epsilon^{2}$) implies that at the end of the $n$th iteration, $\hat{\theta}$ of any learning algorithm satisfies

$$\frac{1}{K}\sum_{\tau=1}^{K}\mathbb{E}_{q^{\tau}}\mathbb{E}_{\theta}Q(\hat{\theta},q^{\tau})\ge0.5\epsilon\left(1-\sqrt{2\times2.1\,(n/K)\epsilon^{2}}\right)$$ 
$$\ge0.25\epsilon=0.25\min\left(0.1,0.24\sqrt{K/T}\right).$$

The second inequality used $(n/K)\epsilon^{2}\le0.24^{2}$. Since this holds for all steps $n\le T$, we obtain the desired bound. $\square$

It is worth noting that due to the special structure of MAB, Theorem 13.22 is not suitable because $\hat{q}(\mathcal{S}_{t-1})$ may pick an arm $a_{t}=\tau$ for any $q^{\tau}$, and in such case, $\mathrm{KL}(q^{\tau}||q^{\tau'})=\mathrm{KL}(0.5+\epsilon||0.5)$ for all $\tau'\neq\tau$. Therefore a direct application of Theorem 13.22 can only lead to a loose lower bound of $\Omega(\sqrt{T})$. We leave the detailed calculation to an exercise.

# 16.4 Arm Elimination Algorithm for Stochastic Linear Bandits

In the standard MAB problem, the regret bound scales with the number of arms $K$. This might not be desirable for problems that contain many arms. In order to deal with such problems, we need to impose additional structures that model correlations among arms. A popular model for such problems is stochastic linear bandits, which allow large action (arm) space. In this section, we assume that