# 7.2. SGD optimization

and let $\Theta: \mathbb{N}_0 \times \Omega \to \mathbb{R}^{\mathfrak{D}}$ be the stochastic process which satisfies for all $n \in \mathbb{N}$ that

$\Theta_0 = \xi$ 
 and 
 $\Theta_n = \Theta_{n-1} - \gamma_n \left[\frac{1}{J_n} \sum_{j=1}^{J_n} (\nabla_\theta \ell^\epsilon)(\Theta_{n-1}, X_{n,j})\right]$. (7.53)

Then

(i) it holds for all $n \in \mathbb{N}$, $\vartheta \in \mathbb{R}^{\mathfrak{D}}$ that

$\left(\mathbb{E}\bigl[\|\Theta_n - \vartheta\|^2\bigr]\right)^{1/2} \geq \varepsilon \left(\frac{\gamma_n}{(J_n)^{1/2}}\right)$ (7.54)

and

(ii) it holds for all $\vartheta \in \mathbb{R}^{\mathfrak{D}}$ that

$\liminf_{n \to \infty} \left(\mathbb{E}\bigl[\|\Theta_n - \vartheta\|^2\bigr]\right)^{1/2} \geq \varepsilon \left(\liminf_{n \to \infty} \left[\frac{\gamma_n}{(J_n)^{1/2}}\right]\right).$ (7.55)

Proof of Corollary 7.2.10. Throughout this proof, let $\mathcal{V}: \mathbb{R}^{\mathfrak{D}} \to [0, \infty]$ satisfy for all $\theta \in \mathbb{R}^{\mathfrak{D}}$ that

$\mathcal{V}(\theta) = \mathbb{E}\bigl[\|(\nabla_\theta \ell^\epsilon)(\theta, X_{1,1}) - \mathbb{E}[(\nabla_\theta \ell^\epsilon)(\theta, X_{1,1})]\|^2\bigr].$ (7.56)

Note that (7.52) demonstrates that for all $\theta \in \mathbb{R}^{\mathfrak{D}}$ it holds that

$\mathcal{V}(\theta) \geq \varepsilon^2.$ (7.57)

Lemma 7.2.9 therefore ensures that for all $n \in \mathbb{N}$, $\vartheta \in \mathbb{R}^{\mathfrak{D}}$ it holds that

$\left(\mathbb{E}\bigl[\|\Theta_n - \vartheta\|^2\bigr]\right)^{1/2} \geq \frac{\gamma_n}{(J_n)^{1/2}} \left(\mathbb{E}\bigl[\mathcal{V}(\Theta_{n-1})\bigr]\right)^{1/2} \geq \left[\frac{\gamma_n}{(J_n)^{1/2}}\right] (\varepsilon^2)^{1/2} = \frac{\gamma_n \varepsilon}{(J_n)^{1/2}}.$ (7.58)

This shows item (i). Observe that item (i) implies item (ii). The proof of Corollary 7.2.10 is thus complete. $\square$

Lemma 7.2.11 (Lower bound for the SGD optimization method). Let $\mathfrak{D} \in \mathbb{N}$, $(\gamma_n)_{n \in \mathbb{N}} \subseteq (0, \infty)$, $(J_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $\xi: \Omega \to \mathbb{R}^{\mathfrak{D}}$ be a random variable, let $X_{n,j}: \Omega \to \mathbb{R}^{\mathfrak{D}}$, $j \in \{1, 2, \ldots, J_n\}$, $n \in \mathbb{N}$, be i.i.d. random variables with $\mathbb{E}\bigl[\|X_{1,1}\|_2\bigr] < \infty$, assume that $\xi$ and $(X_{n,j})_{(n,j) \in \{(k, \ell) \in \mathbb{N}^2: \ell \leq J_k\}}$ are independent, let $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{\mathfrak{D}} \times \mathbb{R}^{\mathfrak{D}}}: \mathbb{R}^{\mathfrak{D}} \times \mathbb{R}^{\mathfrak{D}} \to \mathbb{R}$ satisfy for all $\theta, x \in \mathbb{R}^{\mathfrak{D}}$ that

$\ell(\theta, x) = \frac{1}{2}\|\theta - x\|_2^2,$ (7.59)

and let $\Theta: \mathbb{N}_0 \times \Omega \to \mathbb{R}^{\mathfrak{D}}$ be the stochastic process which satisfies for all $n \in \mathbb{N}$ that

$\Theta_0 = \xi$ 
 and 
 $\Theta_n = \Theta_{n-1} - \gamma_n \left[\frac{1}{J_n} \sum_{j=1}^{J_n} (\nabla_\theta \ell^\epsilon)(\Theta_{n-1}, X_{n,j})\right].$ (7.60)

Then