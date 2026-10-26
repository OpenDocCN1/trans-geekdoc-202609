$f(\mathcal{D}) \le f(\mathcal{S}_n) + O\left(\epsilon_n(\mathcal{F},\mathcal{D}) + \sqrt{\frac{2c_0^2\ln(1/\delta)}{n}} + \frac{M\ln(1/\delta)}{n}\right).$

If $c_0$ is small, then this result improves Corollary 6.19 with $h = 0$ since $M$ is replaced by a potentially smaller quantity $c_0$ in the $O(1/\sqrt{n})$ term.

# Example 6.43

In Theorem 6.41, assume that $f(Z) \in [0,1]$. Then we can take $h(f)=f(\mathcal{D})$ so that the variance condition holds with $c_0 = 0$ and $c_1 = 1$. In such case, we may take $\alpha$ as a constant. This implies the following bound:

$(1 - 5\alpha)f(\mathcal{D}) \le f(\mathcal{S}_n) + 5\bar r_n^h(\alpha,\mathcal{F},\mathcal{D}) + O\left(\frac{(1 + \alpha)\ln(1/\delta)}{\alpha n}\right).$

This leads to a $O(1/n)$ concentration term. This result can be used to improve the concentration of the multiplicative bound in Example 6.24. We leave it as an exercise.

While the Chernoff-style bound of Corollary 6.19 only implies an oracle inequality for ERM with convergence rate no better than $O(1/\sqrt{n})$, the Bennett-style bound in Theorem 6.41 can lead to faster convergence rate. We state the following result, which is a direct consequence of Theorem 6.41.

# Corollary 6.44

Let $\phi(w,z)=L(f(w,x),y)-L_s(x,y)$ for an appropriately defined $L_s(x,y)$ so that $\phi(w,\mathcal{D})\ge0$. Assume $\sup_w\sup_{z,z'}[\phi(w,z)-\phi(w,z')]\le M$, and the variance condition (3.13) holds. Consider $h_0(w)\ge0$, and let $h(w,\mathcal{S}_n)=5\alpha h_0(w)$. Then for $\delta$ such that $\ln(2/\delta)\ge1$, with probability at least $1-\delta$, for all $\alpha>0$, the approximate ERM method (6.1) satisfies

$(1 - 5\alpha)\phi(\hat w,\mathcal{D}) \le \inf_{w\in\Omega}[(1 + 6\alpha)\phi(w,\mathcal{D}) + 10\alpha h_0(w)] + \epsilon' + 5\bar r_n^{h'}(\alpha,\mathcal{G},\mathcal{D}) + 7\sqrt{\frac{2c_0^2\ln(2/\delta)}{n}} + \frac{(7c_1 + 10\alpha M)\ln(2/\delta)}{\alpha n},$
where $h'(w)=h_0(w)+\phi(w,\mathcal{D})$ and $\mathcal{G}=\{\phi(w,z):w\in\Omega\}$. Moreover, with probability at least $1-\delta$, we have

$(1 - 5\alpha)\phi(\hat w,\mathcal{D}) \le \inf_{w\in\Omega}[(1 + 11\alpha)\phi(w,\mathcal{D}) + 15\alpha h_0(w)] + \epsilon' + 10\epsilon_n^{0.5\alpha h'}(\mathcal{G},\mathcal{D}) + 7\sqrt{\frac{2c_0^2\ln(2/\delta)}{n}} + \frac{(7c_1 + 10\alpha M)\ln(2/\delta)}{\alpha n}.$

# Proof

For any $w \in \Omega$, we know from Bennett's inequality that with probability