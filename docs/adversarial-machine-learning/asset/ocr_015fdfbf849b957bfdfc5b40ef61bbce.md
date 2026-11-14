# **7.2.1.1 The Laplace Mechanism**

The earliest pattern of establishing differential privacy is to add (possibly multivariate) zero-mean Laplace noise to a nonprivate mechanism. Typically the nonprivate mechanism being privatized is a deterministic function of data—in our case it will be the support vector machine. The scale of the zero-mean Laplace noise depends on the level \(\beta\) of differential privacy desired and the so-called global sensitivity of the nonprivate mechanism.

**DEFINITION 7.2** Deterministic mechanism \(M\) with real-vector-valued responses, has \(\ell_1\)-global sensitivity \(\Delta > 0\) if for every pair \(\mathbb{D}^{(1)}, \mathbb{D}^{(2)}\) of neighboring databases, \(\| M(\mathbb{D}^{(1)}) - M(\mathbb{D}^{(2)}) \|_1 \leq \Delta\).

This is essentially a Lipschitz condition on the nonprivate mechanism with metric in the co-domain induced by the \(\ell_1\)-norm, and similarly on databases in the domain. Intuitively global sensitivity measures the continuity of the nonprivate map: how much does the response to be released vary with small perturbations to the input dataset.

With global sensitivity of a nonprivate mechanism in hand, it is a simple matter to prove differential privacy of suitable Laplace noise added to the nonprivate mechanism.

**LEMMA 7.3** (Dwork et al. 2006) Let \(M\) be a deterministic mechanism with \(\ell_1\)-global sensitivity \(\Delta > 0\), let \(\beta > 0\), and \(\lambda \stackrel{iid}{\sim} Laplace(\mathbf{0}, \beta/\Delta)\). Then mechanism \(M(\mathbb{D}) + \lambda\) preserves \(\beta\)-differential privacy.

Proof Consider neighboring databases \(\mathbb{D}^{(1)}, \mathbb{D}^{(2)}\), any \(t \in \mathcal{T}_M\), and two multivariate random variables \(\lambda_1, \lambda_2 \stackrel{iid}{\sim} Laplace(\mathbf{0}, \Delta/\beta)\)

\[
\frac{\Pr(M(\mathbb{D}^{(1)}) + \lambda_1 = t)}{\Pr(M(\mathbb{D}^{(2)}) + \lambda_2 = t)} = \frac{\exp(\|t - M(\mathbb{D}^{(1)})\|_1 / (\Delta/\beta))}{\exp(\|t - M(\mathbb{D}^{(2)})\|_1 / (\Delta/\beta))} \leq \exp(\|M(\mathbb{D}^{(1)}) - M(\mathbb{D}^{(2)})\|_1 / (\Delta/\beta)) \leq \exp(\beta).
\]

The equality follows from the definition of the Laplace probability density function, the first inequality follows from the triangle inequality, and the final inequality follows from the bound on global sensitivity. Taking logs of both sides yields \(\beta\)-differential privacy.

# **7.2.2 Utility**

Intuitively the more an “interesting” mechanism \(M\) is perturbed to guarantee differential privacy, the less like \(M\) the resulting mechanism \(\hat{M}\) will become. The next definition formalizes the notion of “likeness.”

**DEFINITION 7.4** Consider two mechanisms \(\hat{M}\) and \(M\) with the same domains and with response spaces \(\mathcal{T}_{\hat{M}}\) and \(\mathcal{T}_M\). Let \(\mathcal{X}\) be some set and let \(\mathcal{F} \subseteq \mathbb{R}^\mathcal{X}\) be parametrized by the response spaces: For every \(t \in \mathcal{T}_{\hat{M}} \cup \mathcal{T}_M\) define some corresponding function \(f_t \in \mathcal{F}\). Finally assume \(\mathcal{F}\) is endowed with norm \(\| \cdot \|_{\mathcal{F}}\). Then for \(\epsilon > 0\) and \(0 < \delta < 1\) we say