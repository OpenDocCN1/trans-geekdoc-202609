# 204 Multi-Criteria Decision-Making with Machine Learning

We use SNS to represent uncertain MCDM issues using Python programming to analyze a real-world decision-making problem.

# 15.2 BASIC CONCEPTS

# 15.2.1 SPHERICAL NEUTROSPHIC SET

First, an SNS, calculated as $A = \{(A_r(p), A_i(p), A_f(p)) : p \in X\}$ on $\mathbb{X}$, satisfies the following properties:

+   (i) $A_r(p), A_i(p), A_f(p) \in [0,1]
(ii) $0 \leq A_r(p) + A_i(p) + A_f(p) \leq 1$\n(iii) $0 \leq A_r(p)^2 + A_i(p)^2 + A_f(p)^2 \leq 1$, for all $p \in \mathbb{X}$

The family of SNSs on $\mathbb{X}$ is denoted $SPH_N_S(\mathbb{X})$.

# 15.2.2 OPERATION OF SNS

Let $\mathcal{M}$ and $\mathcal{L}$ be any two $SPH_N_S$ on $\mathbb{X}$. Then

+   (i) $\mathcal{M}^c = \{\mathcal{M}(p), 1-\mathcal{M}(p), \mathcal{M}(p) : p \in \mathbb{X}\}$ is the complement of $\mathcal{M}$
(ii) $\mathcal{M}\Pi\mathcal{L} = \{\langle\mathcal{M}(p) \wedge \mathcal{L}(p), \mathcal{M}(p) \wedge \mathcal{L}(p), \mathcal{M}(p) \vee \mathcal{L}(p)\rangle\}$
(iii) $\mathcal{M}\\Pi\mathcal{L} = \{\langle\mathcal{M}(p) \vee \mathcal{L}(p), \mathcal{M}(p) \vee \mathcal{L}(p), \mathcal{M}(p) \wedge \mathcal{L}(p)\rangle\}\n(iv) $O_{SNS} = \{(0,0,1) : p \in \mathbb{X}\}$ is a Null $SPH_N_S$ on $\mathbb{X}$
(v) $I_{SNS} = \{(1,0,0) : p \in \mathbb{X}\}$ is a Full $SPH_N_S$ on $\mathbb{X}$

# 15.2.3 SIMILARITY MEASURES BETWEEN SNSs

The similarity between the two $SPH_N_S_s$ and $\mathcal{H}$ is defined as $\varrho(\mathcal{G}, \mathcal{H}) = \varrho_w(\mathcal{G}, \mathcal{H}), \varrho_i(\mathcal{G}, \mathcal{H}), \varrho_f(\mathcal{G}, \mathcal{H}))$ where $\varrho: SPH_N_S(\mathbb{X}) \times SPH_N_S(\mathbb{X}) \to [0,1]$ which satisfies the following properties of:

+   (i) $\varrho(\mathcal{G}, \mathcal{H}) = \varrho(B \ A)$
(ii) $\varrho(\mathcal{G}, \mathcal{H}) = 1_{SNS}$ if $A=B$ for all $\mathcal{G}, \mathcal{H} \in SPH_N_S(\mathbb{X})$
(iii) $\varrho_w(\mathcal{G}, \mathcal{H}) \geq 0$ and $\varrho_i(\mathcal{G}, \mathcal{H}) \geq 0$\n(iv) If $\mathcal{G} \subseteq \mathcal{D}$ for all $\mathcal{G}, \mathcal{D} \in SPH_N_S(\mathbb{X})$, then $\varrho(\mathcal{G}, \mathcal{H}) \geq \varrho(\mathcal{G}, \mathcal{D})$ and $\varrho(\mathcal{H}, \mathcal{D}) \geq \varrho(\mathcal{G}, \mathcal{D})$

where $\varrho_w(\mathcal{G}, \mathcal{H}), \varrho_i(\mathcal{G}, \mathcal{H})$, and $\varrho_f(\mathcal{G}, \mathcal{H})$ represented as the degrees of $\mathbb{T}, \mathbb{I},$ and $\mathbb{F}$ similarity between $\mathcal{G}$ and $\mathcal{H}$, respectively.