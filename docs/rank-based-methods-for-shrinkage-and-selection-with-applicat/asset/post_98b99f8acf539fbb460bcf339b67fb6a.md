
and for \(c_0 > 0\),

\[
\begin{aligned}
P \left( |\sqrt{n}(\hat{\boldsymbol{\beta}}_{\mathcal{S}_1^c}^{\text{ridgeR}}(y_n) - \boldsymbol{\beta}_{\mathcal{S}_1^c}^*)| \ge a_n(\log(\log(n))) \right) \\
\le P \left\{ |Z| > \frac{a_n(\log(\log(n)))}{\sqrt{\text{Var}(\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n))}} - \frac{|\text{ADB}(\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n))|}{\sqrt{\text{Var}(\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n))}} \right\} \\
= 2\Phi \left\{ \frac{|\text{ADB}(\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n))| - a_n(\log(\log(n)))}{\sqrt{\text{Var}(\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n))}} \right\} \\
\le 2\Phi \left( \frac{-c_0\sqrt{\gamma_n}a_n^2}{\log(\log(n))} \right) \\
\le \exp \left( - \frac{c_0^2 \gamma_n a_n^2}{\log(\log(n))} \right)
\end{aligned}
\]

is the tail probability of the normal distribution. Thus, we have

\[
\begin{aligned}
P \left( j \notin S_1 : |\boldsymbol{\beta}_j^*| > a_n(\log(\log(n))) \subset \{ j \notin S_1 : |\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n)| > a_n \} \right) \\
\ge 1 - P \left( \cup \{ |\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n)| \le a_n \} \right) \\
\ge 1 - P \left( \cup \{ |\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n) - \boldsymbol{\beta}_j^*| \le a_n(\log(\log(n))) \} \right) \\
\ge 1 - p_n \exp \left\{ - \frac{c_0^2 \gamma_n a_n^2}{(\log(\log(n)))^2} \right\} \\
\ge 1 - \exp \left\{ - \frac{c_0^2 \gamma_n a_n^2}{(\log(\log(n)))^2} - \log(p_n) \right\} \\
\ge 1 - \exp \{ - (c_0 \log(\log(n-1))) \log(n \vee p_n) \} .
\end{aligned}
\]

For a large enough \(n\), there exists \(c_0 \log(\log(n-1)) > t > 0\) for some \(t\). Thus,

\[
\begin{aligned}
\lim_{n \to \infty} P \left( j \notin S_1 : |\boldsymbol{\beta}_j^*| > a_n(\log(\log(n))) \subset \{ j \notin S_1 : |\hat{\boldsymbol{\beta}}_j^{\text{ridgeR}}(y_n)| > a_n \} \right) \\
\ge 1 - (n \vee p_n)^{-t} \to 1.
\end{aligned}
\]

Similarly,

\[
\lim_{n \to \infty} P \left( \{ j \notin \mathcal{S}_1 : | \boldsymbol{\beta}^*_j | > a_n (\log(\log(n))) \} \supset \{ j \notin \mathcal{S}_1 : | \hat{\boldsymbol{\beta}}_j^{\text{ridgeR}} (\gamma_n) | > a_n \} \right) \ge 1 - (n \vee p_n)^{-t} \to 1.
\]

Because of the continuity of the ridge estimators and \(\lim_{n \to \infty} ((\log(\log(n)))^{-1} + 1) = 1\), we have \(\lim_{n \to \infty} P(\hat{\mathcal{S}}_2 = \mathcal{S}_2 | \hat{\mathcal{S}}_1 = \mathcal{S}_1) = 1\). \(\square\)

The above Theorem 10.1 is similar to Shao and Deng (2012) and Gao et al. (2017). It says that \(\hat{\boldsymbol{\beta}}_{\mathcal{S}_1^c}^{\text{ridgeR}} (\gamma_n)\) is able to single out the sparse set \(\mathcal{S}_3\), with high probability, if \(\mathcal{S}_1\) is pre-selected in advance such that \(P(\hat{\mathcal{S}}_1 = \mathcal{S}_1) = 1\). Note that \(\mathcal{S}_1\) can be recovered with a high probability under sparse Riesz condition (SRC) with rank \(p_1\). Here, the matrix \(\boldsymbol{X}\) satisfies the SRC with rank \(q\) and spectrum bounds \(0 < c_* < c^* < \infty\) of

\[
c_* < \frac{\| \boldsymbol{X}_{\mathcal{S}} \boldsymbol{v} \|^2}{\| \boldsymbol{v} \|^2} < c^*, \quad \forall \mathcal{S} \text{ with } | \mathcal{S} | = q \text{ and } \boldsymbol{v} \in \mathbb{R}^p. \tag{10.6.8}
\]

The LASSO penalty satisfies this condition under B(i). Suppose A(i) and B(i) are satisfied, and the sparse condition A(ii) holds for some \(0 < \eta_1 < O(p_1 \sqrt{\frac{\log(p_n)}{n}})\) and \(\boldsymbol{X}\) satisfies the SRC with rank \(p_1\). Then \(\hat{\mathcal{S}}_1\) generated from the PRD function with a LASSO penalty satisfies

\[
\lim_{n \to \infty} P \left( \{ \mathcal{S}_1 \subset \hat{\mathcal{S}}_1 \} \cap \{ \sum_{j \in \hat{\mathcal{S}}_1} | \boldsymbol{\beta}^*_j | I(\hat{\boldsymbol{\beta}}_{j n}^{\text{PRD}} = 0) = 0 \} \right) = \lim_{n \to \infty} P(\hat{\mathcal{S}}_1 = \mathcal{S}_1) = 1. \tag{10.6.9}
\]

### Corollary 10.1
If Lemma 10.1 and Theorem 10.1 conditions hold, then

\[
\lim_{n \to \infty} P ((\hat{\mathcal{S}}_2 = \mathcal{S}_2) \cap (\hat{\mathcal{S}}_1 = \mathcal{S}_1)) = 1. \tag{10.6.10}
\]

Corollary 10.1 still requires satisfying the SRC.

### Corollary 10.2
If the condition of Theorem 10.1 holds, then

\[
\lim_{n \to \infty} P (\hat{\mathcal{S}}_2 = \hat{\mathcal{S}}_1^c \cap \mathcal{S}_2) = 1. \tag{10.6.11}
\]

Theorem 10.1 and its derivatives, Corollaries 10.1 and 10.2, are important for establishing the efficiency of ridge regression estimators, \(\hat{\boldsymbol{\beta}}_{S_1}^{\text{ridgeER}}(\gamma_n)\) and \(\hat{\boldsymbol{\beta}}_{S_2}^{\text{ridgeER}}(\gamma_n)\).

### Theorem 10.2
Consider a sparse model with signal strength A(i)-A(iii) and A(ii) with \(0 < \tau < 1/2\). Further, suppose a pre-selected model such as \( S_1 \subset \hat{\mathcal{S}}_1 \subset (S_1 \cup S_2) \) is obtained with probability one. If we choose \(\gamma_n\) as in Theorem 10.1 with \(\alpha < \{(\eta - \gamma - \tau)/3, 1/4 - \tau/2\}\), then we have the following asymptotic normality for the ridge R-estimators:

\[
\sqrt{n}\left(\hat{\boldsymbol{\beta}}_{S_3^*}^{\text{ridgeER}}(\gamma_n) - \boldsymbol{\beta}_{S_3^*}^*\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_{1n}+p_{2n}}(\mathbf{0}, \eta^2 \mathbf{C}^{-1}). \tag{10.6.12}
\]

**Proof:** In Section 10.4.4, we obtained under \(\hat{\boldsymbol{\beta}}_{S_3^*}^* = \mathbf{0}\)

\[
\sqrt{n}(\hat{\boldsymbol{\beta}}_{S_3^*}^{\text{ridgeER}}(\gamma_n) - \boldsymbol{\beta}_{S_3^*}^*) = \gamma^{-1}(\phi, f)\mathbf{C}_n^{-1}\mathbf{L}_{n(2)}(\mathbf{0}, \mathbf{0}) + o_p(1)
\]

\[
\sqrt{n}(\hat{\boldsymbol{\beta}}_{S_2}^{\text{ridgeER}}(\gamma_n) - \boldsymbol{\beta}_{S_2}^*) = \gamma^{-1}(\phi, f)\mathbf{C}_{n22.1}^{-1}\mathbf{L}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^\text{RR}, \mathbf{0}) + o_p(1).
\]

Hence, Eq. (10.6.12) holds but the under local alternatives \(\boldsymbol{\beta}_{S_2}^* = n^{-1/2}\boldsymbol{\delta}_{S_2}^*\). Note that using contiguity and linearity results, we have

\[
\mathbf{L}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^\text{RR}, \mathbf{0}) = \mathbf{L}_{n(2)}(\mathbf{0}, \mathbf{0}) - \mathbf{C}_{n21}^{-1}\mathbf{C}_{n11}^{-1}\mathbf{L}_{n(1)}(\mathbf{0}, \mathbf{0}) + o_p(1) \tag{10.6.13}
\]

so that

\[
\sqrt{n}\left(\hat{\boldsymbol{\beta}}_{S_2}^{\text{ridgeER}}(\gamma_n) - n^{-\frac{1}{2}}\boldsymbol{\delta}_{S_2}^*\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_{2n}}(\mathbf{C}_{22.1}\boldsymbol{\delta}_{S_2}^*, \eta^2\mathbf{C}_{22.1}^{-1}). \tag{10.6.14}
\]

See Puri and Sen (1985) for more details. \(\square\)

## 10.7 Asymptotic Distributional L$_2$-Risk Properties

In this section, we provide performance characteristics of the estimators using the asymptotic distributional L$_2$-risk (ADL$_2$-risk). Let

\[
K_{(n)} : \hat{\boldsymbol{\beta}}_{S_2}^* = n^{-\frac{1}{2}}\boldsymbol{\delta}_{S_2}^*, \quad \boldsymbol{\delta}_{S_2}^* = (\delta_{21}^*, \dots, \delta_{2p_{2n}}^*)^\top \tag{10.7.1}
\]

be a sequence of local alternatives. Further, let \(\mathcal{H}_\nu(x; \Delta^2)\) be the c.d.f of the non-central chi-squared distribution with \(\nu\) d.f. and non-centrality parameter \(\Delta^2/2\) for \(x \ge 0\) and \(\mathcal{G}_m(\boldsymbol{x};\boldsymbol{\mu},\boldsymbol{\Sigma})\) be the c.d.f of the \(m\)-variate normal distribution with mean vector \(\boldsymbol{\mu}\) and covariance matrix \(\boldsymbol{\Sigma}\). Then, we have the following results.

### Theorem 10.3
Under \(K_{(n)}\) and assumed regularity conditions for the p.d.f. \(f(x)\) with the Fisher information \(I(f)\)

- (a)
  \[
  \lim_{n\to\infty} P(\mathcal{L}_n \le x | K_{(n)}) = \mathcal{H}_{p_{2n}}(x; \Delta^2), \quad \Delta^2 = \eta^{-2}(\boldsymbol{\delta}^*_{s_2})^\top \mathbf{C}_{22 \cdot 1} \boldsymbol{\delta}^*_{s_2}.
  \]

- (b)
  \[
  \lim_{n\to\infty} P\left(\sqrt{n}(\hat{\boldsymbol{\beta}}^{RR}_{1n} - \boldsymbol{\beta}^*_{s_2}) \le \boldsymbol{x} | K_{(n)}\right) = \mathcal{G}_{p_{lin}}(\boldsymbol{x} + \mathbf{C}_{11}^{-1} \mathbf{C}_{12} \boldsymbol{\delta}^*_{s_2}; \boldsymbol{0}, \eta^2 \mathbf{C}_{11}^{-1}).
  \]

- (c)
  \[
  \lim_{n\to\infty} P\left(\sqrt{n}(\hat{\boldsymbol{\beta}}^{\text{PTR}}_{s_2} - \boldsymbol{\beta}^*_{s_2}) \le \boldsymbol{x} | K_{(n)}\right)
  \]
  \[
  = \mathcal{H}_{p_{2n}}(\lambda^2; \Delta^2) \mathcal{G}_{p_{lin}}(\boldsymbol{x} + \mathbf{C}_{11}^{-1} \mathbf{C}_{12} \boldsymbol{\delta}^*_{s_2}; \boldsymbol{0}, \eta^2 \mathbf{C}_{11}^{-1})
  + \int_{E(\boldsymbol{\delta}^*_{s_2})} \mathcal{G}_{p_{lin}}(\boldsymbol{x} - \mathbf{D}_{11}^{-1} \mathbf{D}_{12} \boldsymbol{Z}; \boldsymbol{0}, \eta^2 \mathbf{D}_{11 \cdot 2}^{-1})
  d\mathcal{G}_{p_{2n}}(\boldsymbol{x} - \mathbf{D}_{12} \mathbf{D}_{22}^{-1} \boldsymbol{Z}; \boldsymbol{0}, \eta^2 \mathbf{D}_{22})
  \]

  where

  \[
  E(\boldsymbol{\delta}^*_{s_2}) = \{ \boldsymbol{Z} : \eta^{-2}(\boldsymbol{Z} + \boldsymbol{\delta}^*_{s_2})^\top \mathbf{C}_{22 \cdot 1} (\boldsymbol{Z} + \boldsymbol{\delta}^*_{s_2}) \ge \lambda^2 \} \tag{10.7.2}
  \]

  and \(\boldsymbol{D} = \mathbf{C}^{-1}\).

- (d)
  \[
  \sqrt{n}\left(\hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{\boldsymbol{s}_1}(\gamma_n) - \boldsymbol{\beta}^*_{s_1}\right) \stackrel{\mathcal{D}}{=} \mathbf{D}_1 \boldsymbol{U} + \frac{\eta^2 \mathbf{C}_{11}^{-1} \mathbf{C}_{12} (\mathbf{D} \boldsymbol{U} + \boldsymbol{\delta}^*_{s_2})}{(\mathbf{D}_2 \boldsymbol{U} + \boldsymbol{\delta}_{s_2})^\top \mathbf{C}_{22 \cdot 1} (\mathbf{D}_2 \boldsymbol{U} + \boldsymbol{\delta}_{s_2})} \tag{10.7.3}
  \]

  where \(\boldsymbol{U} \sim \mathcal{N}_{p_{1n}+p_{2n}}(\boldsymbol{0}, \eta^2 \mathbf{C})\) and \(\boldsymbol{D} = \begin{pmatrix} \mathbf{D}_1 \\ \mathbf{D}_2 \end{pmatrix} = \mathbf{C}^{-1}\).

### Proof:
We consider the linearity results under \(K_{(n)}\)

\[
\hat{\boldsymbol{\beta}}^{RR}_{1n} = \hat{\boldsymbol{\beta}}^{RR}_{s_1}(\gamma_n) + \mathbf{C}_{n11}^{-1} \mathbf{C}_{n12} \hat{\boldsymbol{\beta}}^{RR}_{s_2}(\gamma_n) + o_p(1)
\]
