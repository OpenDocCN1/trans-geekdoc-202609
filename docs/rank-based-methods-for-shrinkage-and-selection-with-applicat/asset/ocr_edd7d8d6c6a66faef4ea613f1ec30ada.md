+   (e)
+   
+   \( ADL_2\text{-risk}(\hat{\beta}^{SSR+}_{S_1}(\gamma_n)) = ADL_2\text{-risk}(\hat{\beta}^{SSR}_{S_1}(\gamma_n) )\)
+   
+   \( - \eta^2 \left[ \text{tr}(\mathbf{C}_{22.1}^{-1}) \left\{ \mathbb{E} \left[ \left( 1 - d \chi_{p_{2n}+2}^{-2}(\Delta^2) \right)^2 I \left( \chi_{p_{2n}+2}^2(\Delta^2) < d \right) \right] \right\} \right.\)
+   
+   \( \left. + \delta_{S_2}^{*\top} \mathbf{M} \delta_{S_2}^* \left\{ 2 \mathbb{E} \left[ \left( 1 - d \chi_{p_{2n}+2}^{-2}(\Delta^2) \right) I \left( \chi_{p_{2n}+2}^2(\Delta^2) < d \right) \right] \right. \right.\)
+   
+   \( \left. \left. - \mathbb{E} \left[ \left( 1 - d \chi_{p_{2n}+4}^{-2}(\Delta^2) \right)^2 I \left( \chi_{p_{2n}+4}^2(\Delta^2) < d \right) \right] \right] \right] \)
+   
+   where \( d = s_2 - 2 \) and \( \mathbb{E}[\chi_q^{-2r}(\Delta^2)] = \int_0^\infty x^{-r} d\mathcal{H}_q(x; \Delta^2) \).

It will be shown that for all \( \Delta^2 \in \mathbb{R}^+ \)

+   (i)
+   
+   \( ADL_2\text{-risk}(\hat{\beta}^{SSR+}_{S_1}(\gamma_n)) \leq ADL_2\text{-risk}(\hat{\beta}^{SSR+}_{S_1}(\gamma_n)) \leq ADL_2\text{-risk}(\hat{\beta}^{ridgeR}_{S_1}(\gamma_n)) \).
+   
+   (10.7.5)

+   (ii) Under \( \Delta^2 = 0 \),
+   
+   \( ADL_2\text{-risk}(\hat{\beta}^{RR}_{ln}(\gamma_n)) \leq ADL_2\text{-risk}(\hat{\beta}^{SSR+}_{S_1}(\gamma_n)) \leq ADL_2\text{-risk}(\hat{\beta}^{ridgeR}_{S_1}(\gamma_n)) \)
+   
+   (10.7.6)

where \( = \) holds for \( s_2 \to \infty \).

# 10.8 Asymptotic Distributional Risk Efficiency

In this section, we briefly elaborate on the asymptotic distributional risk efficiency (ADRE). Note that if \( \mathbf{C}_{12} = \mathbf{0} \), we have \( \mathbf{M} = \mathbf{0} \) and \( \mathbf{C}_{11.2} = \mathbf{C}_{11} \) and hence, all the \( ADL_2\text{-risk}_2\)-risk expressions reduce to the common value \( \eta^2 \text{tr} \mathbf{C}_{11}^{-1} \) for all \( \Delta^2 \in \mathbb{R}^+ \). So, we assume \( \mathbf{C}_{12} \neq \mathbf{0} \). Then, let \( \mathbf{M}^* = \mathbf{C}_{21} \mathbf{C}_{11}^{-1} \mathbf{C}_{11.2} \mathbf{C}_{12}^{-1} \mathbf{C}_{12} \) and \( \mathbf{M}^o = \mathbf{C}_{12} \mathbf{C}_{22}^{-1} \mathbf{C}_{21} \mathbf{C}_{11}^{-1} \). Then, we have the following theorem.

# Theorem 10.5 Under the conditions of Theorem 10.3, we have

+   (a)
+   
+   \( ADL_2\text{-risk}(\hat{\beta}^{ridgeR}_{S_1}(\gamma_n)) \geqslant ADL_2\text{-risk}(\hat{\beta}^{RR}_{ln}) \)
+   
+   accordingly as \( \eta^2 (\delta_{S_2}^{*\top} \mathbf{M}^* \delta_{S_2}^*) \geqslant \text{tr}(\mathbf{M}^o) \).