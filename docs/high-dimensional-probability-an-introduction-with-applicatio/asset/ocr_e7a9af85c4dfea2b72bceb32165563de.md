by lemma's assumption. Now take a union bound over all pairs of distinct functions $f, g \in \mathcal{F}$. There are at most $|\mathcal{F}|^2$ of them, so with probability at least

$$1 - |\mathcal{F}|^2 \cdot 2 \exp(-c n \varepsilon^4), \tag{8.34}$$

the bound (8.33) holds simultaneously for all distinct $f, g \in \mathcal{F}$. Since $n \ge C \varepsilon^{-4} \log |\mathcal{F}|$ by assumption, by choosing the absolute constant $C$ sufficiently big we can make the quantity in (8.34) at least 0.99.

*Proof of Theorem 8.3.13* By the packing-covering equiavalence (Lemma 4.2.8), we can find

$$N = \mathcal{N}(\mathcal{F}, L^2(\mu), \varepsilon)$$

functions in $\mathcal{F}$ that are $\varepsilon$-separated in the $L^2(\mu)$ metric. Set $n = \lceil C \varepsilon^{-4} \log N \rceil$ and apply Lemma 8.3.14 to the set of those functions. With positive probability, those functions stay $(\varepsilon/2)$-separated in the metric $L^2(\mu_n)$ defined in (8.32), so their restrictions onto $\Omega_n = \{X_1, \dots, X_n\}$ are all different.

Fix a realization of random variables $X_1, \dots, X_n$ for which this event holds. So there exists a subset $\Omega_n \subset \Omega$ with $|\Omega_n| \le n \le 2C \varepsilon^{-4} \log N$, such that the class $\mathcal{F}_n = \mathcal{F}|_{\Omega_n}$ obtained by restricting all functions onto $\Omega_n$ satisfies $|\mathcal{F}_n| \ge N$. Now apply Sauer-Shelah Lemma 8.3.9 for $\mathcal{F}_n$ and $\Omega_n$ to get

$$N \le \left(\frac{e n}{d_n}\right)^{d_n} \le \left(\frac{2C \varepsilon^{-4} \log N}{d_n}\right)^{d_n}$$

where $d_n = \mathrm{vc}(\mathcal{F}_n)$. Simplifying,$^4$ we get

$$N \le (2C \varepsilon^{-4})^{2 d_n}.$$

Finally, replace $d_n = \mathrm{vc}(\mathcal{F}_n)$ by the larger quantity $d = \mathrm{vc}(\mathcal{F})$.

# **8.3.6 VC law of large numbers**

Back in Section 8.2.2, we bounded a general empirical process over all Lipschitz functions. Now, let's replace Lipschitz by any class of Boolean functions with finite VC dimension:

**Theorem 8.3.15 (VC law of large numbers).** *Let $\mathcal{F}$ be a class of Boolean functions with finite VC dimension on some domain $\Omega$, and let $X, X_1, X_2, \dots, X_n$ be independent random points in $\Omega$ with common distribution. Then*

$$ \mathbb{E} \sup_{f \in \mathcal{F}} \left| \frac{1}{n} \sum_{i=1}^n f(X_i) - \mathbb{E} f(X) \right| \le C \sqrt{\frac{\mathrm{vc}(\mathcal{F})}{n}}. $$

$^4$ To do this, note that $\frac{\log N}{2 d_n} = \log(N^{1/2 d_n}) \le N^{1/2 d_n}$.