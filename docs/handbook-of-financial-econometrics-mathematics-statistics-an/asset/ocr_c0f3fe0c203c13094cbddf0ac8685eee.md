$$\Delta x_t=\kappa_{0x}^{Q}+\kappa_{1x}^{Q}x_{t-1}+\Sigma_x\epsilon_t^{Q},$$

$$r_t=\rho_{0x}+\rho_{1x}x_t.$$

In equations (61.18)–(61.20), $r_t$ is the one-period spot rate, $\Sigma_x\Sigma_x^T$ is the conditional covariance matrix of $x_t$, and $\epsilon_t\sim N(0,I_N)$. Based on this characterization, prices for a zero coupon yield of maturity $m$ can be expressed as

$$D_{t,m}=E_t^Q\left[e^{-\sum_{i=0}^{m-1}r_{t+i}}\right]=e^{A_m+B_mx_t}.$$

Taking the natural logarithm of equation (61.21) leads to the following expression for zero coupon yields as shown

$$y_t=A_m+B_mx_t.$$

In equation (61.22), $(A_m,B_m)$ satisfy the well-known Riccati difference equations

$$A_{m+1}-A_m=\kappa_0^{Q\prime}B_m+\frac{1}{2}B_m^{\prime}H_0B_m-\rho_0,$$

$$B_{m+1}-B_m=\kappa_1^{Q\prime}B_m-\rho_1,$$

subject to the initial conditions $A_0=0$ and $B_0=0$ and with loadings for the corresponding bond yields given as $a_m=-A_m/m$ and $b_m=-B_m/m^4$.

⁴JSZ remark that although all their results are specified in discrete-time, without loss of generality, all of their results apply to continuous-time models as well. In regards to the Riccati ODE, since the structure of the model is similar whether we estimate it in continuous-time or discrete-time, we can demonstrate how to obtain the Riccati ODE in continuous-time and show how it parallels the discrete-setting. The steps that follow largely follow Duffee and Kan (1996), Fisher and Gilles (1996), and Piazzesi (2010) and so we refer the reader to these papers for more information. We begin with the class of affine term structure models, such as JSZ, for which bond prices have the following form:

$$P(x,\tau)=\exp(A(\tau)+B(\tau)^Tx).$$

In the expression above, A and B are coefficients defining how bond prices and the state variable $x$ (e.g., the principal component) are related. In this footnote, we provide an explanation for how one would obtain A and B for use in estimating an affine term structure model. To obtain the state factor coefficients, we note that by the absence of arbitrage the short rate R(x) should equal the instantaneous bond return $\frac{dP}{P}$. Thus, by Itô’s lemma, we derive the process for the instantaneous bond return for which we need the following derivatives:

$$P_\tau(x,\tau)=\frac{\partial P(x,\tau)}{\partial\tau}P_x(x,\tau)=\begin{bmatrix}\frac{\partial P(x,\tau)}{\partial x_1}\\\vdots\\\frac{\partial P(x,\tau)}{\partial x_d}\end{bmatrix},\qquad P_{xx}(x,\tau)=\begin{bmatrix}\frac{\partial^2P(x,\tau)}{\partial x_1^2}&\cdots&\frac{\partial^2P(x,\tau)}{\partial x_1\partial x_d}\\\vdots&\ddots&\vdots\\\frac{\partial^2P(x,\tau)}{\partial x_d\partial x_1}&\cdots&\frac{\partial^2P(x,\tau)}{\partial x_d^2}\end{bmatrix}.$$