Also

\(\frac{\partial Q_n(\boldsymbol{\beta}|S_1)}{\partial \hat{\beta}^*_{s_3}} = \gamma_n \left( \begin{matrix} \mathbf{0}_{p_{1n}+p_{2n}} \\ \hat{\beta}^{\text{ridgeR}}_{s_3} (\gamma_n) \\ \end{matrix} \right) = \left( \begin{matrix} \mathbf{0}_{p_{1n}+p_{2n}} \\ \mathbf{0}_{p_n-p_{1n}-p_{2n}} \\ \end{matrix} \right),\) (10.4.12)

where \(\hat{\beta}^{\text{ridgeR}}_{s_3} (\gamma_n) = \mathbf{0}\) with probability one by Theorem 10.1 (given later).

Next, using asymptotic linearity results, we have

\(\sup_{\|\mathbf{w}_{s_3^c}\|<\kappa} n^{-\frac{1}{2}} \left\| \mathbf{L}_{s_3^c} \left( \boldsymbol{\beta}^*_{s_3^c}, \mathbf{0} \right) - \mathbf{L}_{s_3^c} \left( \mathbf{0}, \mathbf{0} \right) + \gamma(\phi, f) \mathbf{C} \mathbf{w}_{s_3^c} \right\| \xrightarrow{P} 0.\) (10.4.13)

Thus, together with Eq. (10.4.10) we obtain

\(\mathbf{w}_{s_3^c} = \sqrt{n} \left( \hat{\beta}^{\text{RR}}_{s_3^c} (\gamma_n) - \beta^*_{s_3^c} \right) = \gamma^{-1}(\phi, f) \mathbf{C}_n^{-1} \left[ \mathbf{L}_{s_3^c} \left( \mathbf{0}, \mathbf{0} \right) - \gamma_n \left( \begin{matrix} \mathbf{0} \\ \hat{\beta}^{\text{ridgeR}}_{s_2} (\gamma_n) \\ \end{matrix} \right) \right] + o_p(1) = \gamma^{-1}(\phi, f) \mathbf{C}_n^{-1} \mathbf{L}_{s_3^c} \left( \mathbf{0}, \mathbf{0} \right) + o_p(1).\) (10.4.14)

To understand Eq. (10.4.14), using \(\mathbf{d}_n = (\mathbf{d}_{1n}^\top, \mathbf{d}_{2n}^\top)^\top\), we can write

\(\gamma^{-1}(\phi, f) n^{-\frac{1}{2}} \gamma_n \mathbf{d}_n^\top \mathbf{C}_n^{-1} \left( \begin{matrix} \mathbf{0} \\ \hat{\beta}^{\text{ridgeR}}_{s_2} (\gamma_n) \\ \end{matrix} \right) \le \varsigma_{1n}^{-1} n^{-\frac{1}{2}} \gamma_n \mathbf{d}_{2n}^\top \hat{\beta}^{\text{ridgeR}}_{s_2} (\gamma_n) \quad \text{from B(ii)} = O_p(\varsigma_{1n}^{-1} n^{-\frac{1}{2}} \gamma_n \mathbf{d}_{2n}^\top \beta^*_{s_3^c}) \quad \text{from B(i)} \le O_p(\varsigma_{1n}^{-1} n^{-\frac{1}{2}} \gamma_n \|\mathbf{d}_{2n}\| \|\beta^*_{s_3^c}\|) \quad \text{Cauchy--Schwartz inequality} \le O_p(\varsigma_{1n}^{-1} n^{-(\frac{1}{2}-\tau)} \gamma_n) \quad \text{from A(ii)} = o_p(1),\) (10.4.15)

since \(\gamma_n = o(n^{(1/2)-\tau})\) for \(\alpha < 1/4 - \tau/2\) for \(0 < \tau < 1/2\). See Sections 10.1 and 10.6 for definitions of A(ii), B(i) and B(ii).

Now, from Eq. (10.4.14), we may exactly see that

\(\gamma^{-1}(\phi, f) \mathbf{C}_n^{-1} \mathbf{L}_{s_3^c} (\mathbf{0}, \mathbf{0}) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_{1n}+p_{2n}} (\mathbf{0}, \eta^2 \mathbf{C}^{-1}).\) (10.4.16)