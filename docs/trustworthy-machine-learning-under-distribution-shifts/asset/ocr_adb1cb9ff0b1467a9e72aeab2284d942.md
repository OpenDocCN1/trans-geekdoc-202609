# 7 PROOFS AND THEORETICAL ANALYSES

ASSUMPTION 10 (Lipschitz smooth). $\mathcal{L}(	heta; (x, y))$ is differential and $l$-Lipschitz smooth for every sample $(x, y)$:

$|\nabla_{	heta}\mathcal{L}(	heta_1; (x, y)) - \nabla_{	heta}\mathcal{L}(	heta_2; (x, y))|| \leq l|\theta_1 - \theta_2||, \quad \forall \omega, (x, y);$

$|\nabla_{\omega}\mathcal{L}(	heta; \omega_1) - \nabla_{\omega}\mathcal{L}(	heta; \omega_2)| \leq l|\omega_1 - \omega_2||, \quad \forall \theta.$

REMARK 16. So the expectation function $\mathcal{L}$ also has the Lipschitz smooth property:

$|\nabla_{	heta}\mathcal{L}(\theta_1; \omega) - \nabla_{	heta}\mathcal{L}(\theta_2; \omega)| \leq E||\nabla_{	heta}\mathcal{L}(\theta_1; (x, y)) - \nabla_{	heta}\mathcal{L}(\theta_2; (x, y))|| \leq l|\theta_1 - \theta_2||, \quad \omega$;

$|\nabla_{\omega}\mathcal{L}(\theta; \omega_1) - \nabla_{\omega}\mathcal{L}(\theta; \omega_2)| \leq E||\nabla_{\omega}\mathcal{L}(\theta; (x, y)) - \nabla_{\omega}\mathcal{L}(\theta; (x, y))|| \leq l|\omega_1 - \omega_2||, \quad \theta.$

ASSUMPTION 12 (PL condition). The loss function $\mathcal{L}(\theta, \cdot)$ satisfies PL condition on every $	heta$, there exists $\mu > 0$ such that $|\nabla_{	heta}\mathcal{L}(\theta, \omega)||^2 \geq 2\mu[|\nabla_{	heta}\mathcal{L}(\theta, \omega) - \mathcal{L}(\theta, \omega)|], \quad \forall \theta, \omega.$

# 7.1.3 Useful Lemmas

In this part, we will prove some necessary lemmas to prove the convergence bound.

And we will give the definition of the stationary point of our problem at the beginning.

DEFINITION 13 (Stationary measure). $\theta$ is defined as the $\epsilon$-stationary point of our problem if $\mathbb{E}|\nabla L^{*}(\theta)||| \leq \epsilon$ for any $\epsilon \geq 0$.

REMARK 14. For minimax problem, there are usually two ways to measure the stationary point. One is measured two-side when $\mathbb{E}||\nabla_{	heta}\mathcal{L}(\theta, \omega)||| \leq \epsilon$ and $\mathbb{E}||\nabla_{\omega}\mathcal{L}(\theta, \omega)||| \leq \epsilon$, we claim $(\theta, \omega)$ is the $(\epsilon, \epsilon)$-stationary point. It has been proved in [352] that these measures can be translated into each other when $L^{*}$ is smooth which is shown in what we compute the model parameter $\theta$ using the algorithm SharpDRO. So we choose the measure by $\mathbb{E}|L^{*}(\theta)|$ here.

LEMMA 2. [353] Under Assumption 10 and 12, $L^{*}(\theta)$ is $(1+\frac{l}{2\mu})$-Lipschitz smooth with the gradient:

$\nabla_{	heta}L^{*}(\theta) = \nabla_{	heta}\mathcal{L}(\theta, \omega^{*}).

LEMMA 3. [353] Under Assumption 10 and 12, $\omega^{*}(\cdot)$ is smooth about its variable:

$|\omega^*(\theta_1) - \omega^*(\theta_2)| \leq \frac{l}{2\mu}|\theta_1 - \theta_2||, \quad \theta_1, \theta_2.$