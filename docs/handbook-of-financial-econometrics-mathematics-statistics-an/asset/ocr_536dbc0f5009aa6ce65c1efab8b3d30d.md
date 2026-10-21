Thus, we have
\[
\left( \begin{array}{c} \dfrac{\tilde r_t - d}{\sqrt{h_{t-1}}} \\ \dfrac{\tilde h_t - \alpha - \delta h_{t-1}}{\sqrt{h_{t-1}}} \end{array} \bigg| \theta, h_{t-1}, \xi_t^r, \xi_t^v, J_t^r, J_t^v \right) \sim N\left( \begin{pmatrix}0\\0\end{pmatrix}, \Sigma \right).
\]

Applying the change of variable technique, we get
\[
p(\tilde r_t, \tilde h_t | \theta, h_{t-1}, \xi_t^r, \xi_t^v, J_t^r, J_t^v) \propto h_{t-1}^{-1}
\]
\[
p\left( \dfrac{\tilde r_t - d}{\sqrt{h_{t-1}}}, \dfrac{\tilde h_t - \alpha - \delta h_{t-1}}{\sqrt{h_{t-1}}} \bigg| \theta, h_{t-1}, \xi_t^r, \xi_t^v, J_t^r, J_t^v \right).
\]

Let $\tilde r = \{\tilde r_1, \tilde r_2, \dots, \tilde r_T\}$, $\tilde h = \{\tilde h_1, \tilde h_2, \dots, \tilde h_T\}$; then
\[
p(\tilde r, \tilde h | \theta, \xi^r, \xi^v, J) = p(\tilde r_1, \tilde h_1 | \bullet, h_0) p(\tilde r_2, \tilde h_2 | \bullet, h_1) \dots p(\tilde r_T, \tilde h_T | \bullet, h_{T-1})
\]
\[
\propto \prod_{t=1}^T p\left( \dfrac{\tilde r_t - d}{\sqrt{h_{t-1}}}, \dfrac{\tilde h_t - \alpha - \delta h_{t-1}}{\sqrt{h_{t-1}}} \bigg| \bullet, h_{t-1} \right)
\]
\[
\propto \prod_{t=1}^T |\Sigma|^{-1/2} e^{-\tfrac12 tr(e_t \Sigma^{-1} e_t')}
\]
\[
\propto |\Sigma|^{-T/2} e^{-\tfrac12 tr(\Sigma^{-1} A)},
\]

where $A = \sum_{t=1}^T e_t e_t'$.

To facilitate the estimation of the covariance matrix $\Sigma$, we transform from $(\rho, \sigma_v)$ to $(\psi, \Omega)$ representation. That is,
\[
\Sigma = \begin{pmatrix} 1 & \rho \sigma_v \\ \rho \sigma_v & \sigma_v^2 \end{pmatrix} = \begin{pmatrix} 1 & \psi \\ \psi & \psi^2 + \Omega \end{pmatrix}.
\]

Since $|\Sigma| = \Omega$, we have $\Sigma^{-1} = \frac{1}{\Omega} \begin{pmatrix} \psi^2 & -\psi \\ -\psi & 1 \end{pmatrix} + \begin{pmatrix} 1 & 0 \\ 1 & 0 \end{pmatrix} \equiv \frac{C}{\Omega} + \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$. Letting $a_{ij}$ be the element at the $ij$ position in matrix A, we have $\operatorname{tr}(\Sigma^{-1} A) = \operatorname{tr}(C A)/\Omega + a_{11}$. As a result,
\[
p(\psi, \Omega | \tilde r, \tilde h, d, \alpha, \delta) \propto \frac{1}{\Omega^{T/2}} e^{-\frac{tr(C A)}{2\Omega}} \operatorname{pri}(\psi, \Omega)
\]
\[
\propto \frac{1}{\Omega^{T/2}} e^{-\frac{a_{22.1} + (\psi - \hat\psi)^2 a_{11}}{2\Omega}} \operatorname{pri}(\psi, \Omega), \tag{52.5}
\]
where $a_{22.1} = a_{22} - \frac{a_{12}^2}{a_{11}}$, $\hat\psi = \frac{a_{12}}{a_{11}}$.