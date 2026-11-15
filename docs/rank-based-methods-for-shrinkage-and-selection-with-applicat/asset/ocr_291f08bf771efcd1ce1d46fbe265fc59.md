for \(x \ge 0\) and \(\mathcal{G}_m(\boldsymbol{x};\boldsymbol{\mu},\boldsymbol{\Sigma})\) be the c.d.f of the \(m\)-variate normal distribution with mean vector \(\boldsymbol{\mu}\) and covariance matrix \(\boldsymbol{\Sigma}\). Then, we have the following results.

# **Theorem 10.3** Under \(K_{(n)}\) and assumed regularity conditions for the p.d.f. \(f(x)\) with the Fisher information \(I(f)\)

+   (a)
+   \(\lim_{n\to\infty} P(\mathcal{L}_n \le x | K_{(n)}) = \mathcal{H}_{p_{2n}}(x; \Delta^2), \Delta^2 = \eta^{-2}(\boldsymbol{\delta}^*_{s_2})^\top \mathbf{C}_{22 \cdot 1} \boldsymbol{\delta}^*_{s_2}).\)

+   (b)
+   \(\lim_{n\to\infty} P\left(\sqrt{n}(\hat{\boldsymbol{\beta}}^{RR}_{\boldsymbol{\beta}1n} - \boldsymbol{\beta}^*_{s_2}) \le \boldsymbol{x} | K_{(n)}\right) = \mathcal{G}_{p_{lin}}(\boldsymbol{x} + \mathbf{C}_{11}^{-1} \mathbf{C}_{12} \boldsymbol{\delta}^*_{s_2}; \boldsymbol{0}, \eta^2 \mathbf{C}_{11}^{-1}).\)

+   (c)
+   \(\lim_{n\to\infty} P\left(\sqrt{n}(\hat{\boldsymbol{\beta}}^{\text{PTR}}_{\boldsymbol{\beta}s_2} - \boldsymbol{\beta}^*_{s_2}) \le \boldsymbol{x} | K_{(n)}\right)\)
+   \(= \mathcal{H}_{p_{2n}}(\lambda^2; \Delta^2) \mathcal{G}_{p_{lin}}(\boldsymbol{x} + \mathbf{C}_{11}^{-1} \mathbf{C}_{12} \boldsymbol{\delta}^*_{s_2}; \boldsymbol{0}, \eta^2 \mathbf{C}_{11}^{-1})\)
+   \(+ \int_{E(\boldsymbol{\delta}^*_{s_2})} \mathcal{G}_{p_{lin}}(\boldsymbol{x} - \mathbf{D}_{11}^{-1} \mathbf{D}_{12} \boldsymbol{Z}; \boldsymbol{0}, \eta^2 \mathbf{D}_{11 \cdot 2}^{-1})\)
+   \(d\mathcal{G}_{p_{2n}}(\boldsymbol{x} - \mathbf{D}_{12} \mathbf{D}_{22}^{-1} \boldsymbol{Z}; \boldsymbol{0}, \eta^2 \mathbf{D}_{22})\)

where

\(E(\boldsymbol{\delta}^*_{s_2}) = \{ \boldsymbol{Z} : \eta^{-2}(\boldsymbol{Z} + \boldsymbol{\delta}^*_{s_2})^\top \mathbf{C}_{22 \cdot 1} (\boldsymbol{Z} + \boldsymbol{\delta}^*_{s_2}) \ge \lambda^2 \}\) (10.7.2)

and \(\boldsymbol{D} = \mathbf{C}^{-1}\).

+   (d)
+   \(\sqrt{n}\left(\hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{\boldsymbol{s}_1}(\gamma_n) - \boldsymbol{\beta}^*_{s_1}\right) \stackrel{\mathcal{D}}{=} \mathbf{D}_1 \boldsymbol{U} + \frac{\eta^2 \mathbf{C}_{11}^{-1} \mathbf{C}_{12} (\mathbf{D} \boldsymbol{U} + \boldsymbol{\delta}^*_{s_2})}{(\mathbf{D}_2 \boldsymbol{U} + \boldsymbol{\delta}_{s_2})^\top \mathbf{C}_{22 \cdot 1} (\mathbf{D}_2 \boldsymbol{U} + \boldsymbol{\delta}_{s_2})}\) (10.7.3)

where \(\boldsymbol{U} \sim \mathcal{N}_{p_{1n}+p_{2n}}(\boldsymbol{0}, \eta^2 \mathbf{C})\) and \(\boldsymbol{D} = \begin{pmatrix} \mathbf{D}_1 \\ \mathbf{D}_2 \end{pmatrix} = \mathbf{C}^{-1}\).

# **Proof:** We consider the linearity results under \(K_{(n)}\)

\(\hat{\boldsymbol{\beta}}^{RR}_{1n} = \hat{\boldsymbol{\beta}}^{RR}_{s_1}(\gamma_n) + \mathbf{C}_{n11}^{-1} \mathbf{C}_{n12} \hat{\boldsymbol{\beta}}^{RR}_{s_2}(\gamma_n) + o_p(1)\)