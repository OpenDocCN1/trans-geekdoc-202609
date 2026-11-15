
## Algorithm 1 ET-DSGT: Event-triggering decentralized stochastic gradient tracking algorithm.

**Initialization:** Each agent \( i \in \mathcal{V} \) initializes \( x_{t_0}^i = x_0^i \in \mathbb{R}^d \) and \( y_{t_0}^i = y_0^i = \nabla g(x_{t_0}^i, s_0^i) \in \mathbb{R}^d \).

**Local Updates:** Each agent \( i \in \mathcal{V} \) repeats, for \( j \in \mathcal{N}_i \)

- 1: for all \( t = 0, 1, \cdots \) do
- 2: Update estimator \( x_{t+1}^i \) according to:
  \[
  x_{t+1}^i = x_t^i + \sum_{j=1}^N w^{ij}(x_{t_k^j}^j - x_{t_k^i}^i) - \alpha_t y_t^i, \quad (4.5a)
  \]
  where \( w^{ij} \) is the weight between agent \( i \) and its neighbor \( j \) and the decaying step-size \( \alpha_t = a/(t+1), a > 0 \).
- 3: Update \( y_{t+1}^i \) according to:
  \[
  y_{t+1}^i = y_t^i + \sum_{j=1}^N w^{ij}(y_{t_k^j}^j - y_{t_k^i}^i) + \nabla g^i(x_{t+1}^i, S_{t+1}^i) - \nabla g^i(x_t^i, S_t^i), \quad (4.5b)
  \]
  where \( S_0^i, S_1^i, \dots \) are independent and identically distributed samples of \( S^i \).
- 4: Measure \( e_t^{i,x}, e_t^{i,y} \) in (4.4), and then check whether (4.3) is satisfied.
- 5: **if** (4.3) is satisfied **then**
- 6: Broadcast \( x_{t+1}^i \) and \( y_{t+1}^i \) to \( j \in \mathcal{N}^i \), and refresh the triggering time.
- 7: **else**
- 8: Agent \( j \) keeps local estimators unchanged.
- 9: **end if**
- 10: **end for**

transmitting its real-time state estimators \( x_{t+1}^i \) and \( y_{t+1}^i \), even after the computations have been finalized. In other words, agent \( i \) maintains its local estimators without any modifications. As a result, through the implementation of the event-triggering mechanism, the ET-DSGT algorithm circumvents the need for continuous real-time communication.

Drawing from (4.4) and Assumption 4.2, the iterative updating steps in Algorithm 1 can be articulated in the following manner:

\[
x_{t+1}^i = \sum_{j=1}^N w^{ij} x_t^j + \hat{e}_t^{i,x} - \alpha_t y_t^i, \quad (4.6a)
\]

\[
y_{t+1}^i = \sum_{j=1}^N w^{ij} y_t^j + \hat{e}_t^{i,y} + \nabla g_{t+1}^i - \nabla g_t^i, \quad (4.6b)
\]

where \(\hat{e}_t^{i,x} = \sum_{j=1}^N w^{ij}(e_t^{j,x} - \hat{e}_t^{i,x})\) and \(\hat{e}_t^{i,y} = \sum_{j=1}^N w^{ij}(e_t^{j,y} - \hat{e}_t^{i,y})\).

For analytical purposes, we denote the subsequent notations: \(x_t = [(x_t^1)^\mathrm{T}, ..., (x_t^N)^\mathrm{T}]^\mathrm{T}\), \(y_t = [(y_t^1)^\mathrm{T}, ..., (y_t^N)^\mathrm{T}]^\mathrm{T}\), \(\hat{e}_t^x = [(\hat{e}_t^{1,x})^\mathrm{T}, ..., (\hat{e}_t^{N,x})^\mathrm{T}]^\mathrm{T}\), \(\hat{e}_t^y = [(\hat{e}_t^{1,y})^\mathrm{T}, ..., (\hat{e}_t^{N,y})^\mathrm{T}]^\mathrm{T}\), \(\nabla G_t = [(\nabla g_t^1)^\mathrm{T}, ..., (\nabla g_t^N)^\mathrm{T}]^\mathrm{T}\), and \(\hat{W} = W \otimes I_d\). Subsequently, Algorithm 1 can be expressed in a condensed manner as follows:

\[
x_{t+1} = \hat{W} x_t + \hat{e}_t^x - \alpha_t y_t, \quad (4.7a)
\]
\[
y_{t+1} = \hat{W} y_t + \hat{e}_t^y + \nabla G_{t+1} - \nabla G_t. \quad (4.7b)
\]

**Remark 4.3.** In comparison to the current decentralized event-triggering techniques referenced in [38–41] and decentralized stochastic gradient tracking approaches mentioned in [14,16,17,36], Algorithm 1 successfully fulfills both objectives. Specifically, Algorithm 1 enhances communication efficiency while also ensuring precise convergence. Therefore it can be inferred that this chapter presents a unique decentralized optimization algorithm.

## 4.3 Convergence guarantees

In this section, we examine the convergence characteristics of ET-DSGT in terms of mean square convergence.

### 4.3.1 Preliminary results

For analytical purposes, we introduce two supporting sequences, denoted as \(\{y'_t\}\) and \(\{\xi_t\}\) and defined as follows:

\[
y'_{t+1} = \hat{W} y'_t + \nabla F_{t+1} - \nabla F_t, \quad y'_0 = \nabla F_0, \quad (4.8)
\]
\[
\xi_{t+1} = \hat{W} \xi_t + \hat{e}_t^y + \varepsilon_{t+1} - \varepsilon_t, \quad \xi_0 = \varepsilon_0, \quad (4.9)
\]

where \(\varepsilon_t^i := \nabla g^i(x_t^i, \zeta_t^i) - \nabla f^i(x_t^i)\), \(\varepsilon_t = \nabla G_t - \nabla F_t\), and \(\nabla F_t = [\nabla f^1(x_t^1)^\mathrm{T}, ..., \nabla f^N(x_t^N)^\mathrm{T}]^\mathrm{T}\). Furthermore, we establish the following definitions:

\[
\bar{x}_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) x_t, \quad \bar{y}'_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) y'_t.
\]

Subsequently, by recalling (4.4) and Assumption 4.2(ii), the subsequent conclusions can be clearly inferred:

\[
\frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^x = 0, \quad \frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^y = 0, \quad \forall t \ge 0.
\]

Additionally, we revisit the matrix norm denoted as \(||\cdot||\) that was introduced in [34]. This norm possesses the subsequent characteristic:

\[
\tau_w := ||\hat{W} - \frac{1}{N} \mathbf{1}_N \mathbf{1}_N^\mathrm{T} \otimes I_d|| < 1. \quad (4.10)
\]

Prior to deriving the supplementary findings, we present a useful inference in Lemma 4.1, whose proof can be found in reference [14].

**Lemma 4.1.** There is a positive constant \(c_\rho\) such that the inequality \(\sum_{l=0}^{t-1} \tau_w^{t-l} \alpha_l \le c_\rho \alpha_t\) holds, wherein \(\tau_w\) is defined in (4.10).

Furthermore, in Lemma 4.2, we present an expansion of Lemma 4.3 that was originally suggested in [43]. The proof for this lemma can be examined in [43].

**Lemma 4.2.** Assume that the positive sequences \(\{\gamma_t\}\), \(\{\rho_t\}\), \(\{\varphi_t\}\) fulfill the subsequent criteria:

- (i) The sequences \(\{\gamma_t\}\) and \(\{\rho_t\}\) consist of values ranging from 0 to 1, satisfying the conditions that \(\sum_{t=0}^\infty \gamma_t^2 < \infty\) and \(\rho_t < 1\),

- (ii) \(\limsup_{t \to \infty} (\gamma_t \sqrt{\varphi_t} + \varphi_{t-1}/\varphi_t) < \infty\), \(\sum_{t=0}^\infty \varphi_t^{-1} < \infty\) and \(\liminf_{t \to \infty} (\gamma_t \sqrt{\varphi_t})^{-1} (\varphi_{t-1}/\varphi_t - \rho_t) > 0\).

Provided that the scalars \(M > 0\) and \(0 < p < 1\), the sequences \(u_t\) and \(v_t\) fulfill the condition that \(t \ge t_0\),

\[
\begin{aligned} u_{t+1} \le & \rho_t u_t + M \gamma_t \sqrt{u_t(1+u_t+v_t)} \\ & + M \gamma_t (\gamma_t + \sum_{l=0}^t \gamma_l p^{t-l} u_l + \sum_{l=0}^t \gamma_l p^{t-l} v_l), \end{aligned} \quad (4.11)
\]

\[
\begin{aligned} v_{t+1} \le & v_t + M u_t + M \gamma_t \sqrt{u_t(1+u_t+v_t)} \\ & + M \gamma_t (\gamma_t + \sum_{l=0}^t \gamma_l p^{t-l} u_l + \sum_{l=0}^t \gamma_l p^{t-l} v_l), \end{aligned} \quad (4.12)
\]

then

\[
\sup_t v_t < \infty, \quad \limsup_{t \to \infty} \varphi_t u_t < \infty.
\]

### 4.3.2 Auxiliary results

In this subsection, several supporting findings are presented, enabling the primary conclusions to be outlined with clarity.

**Lemma 4.3.** Suppose that Assumptions 4.1–4.3 are valid. Consequently, we can deduce that

\[
\sup_t \mathbb{E}[||\xi_t||^2] \le \frac{2 c_w N}{(1-\tau_w)^2} (\frac{C \pi^2}{6} + U_1). \quad (4.13)
\]

_Proof._ Based on the definition of the sequence \(\{\xi_t\}\), we can infer

\[
\xi_t = \sum_{l=0}^{t-1} \hat{W}(t, l) e_l^\gamma + \sum_{l=0}^t \hat{W}(t, l) \varepsilon_l,
\]

where

\[
\hat{W}(t, l) := \hat{W}^{t-l-1}(\hat{W} - I_{Nd})(l < t),
\]
\[
\hat{W}(t, t-1) := \hat{W} - I_{Nd}, \hat{W}(t, t) := I_{Nd}.
\]

Subsequently, it results in

\[
\mathbb{E}[||\xi_t||^2] \le 2 \sum_{l_1=0}^{t-1} \sum_{l_2=0}^{t-1} ||\hat{W}(t, l_1)|| ||\hat{W}(t, l_2)|| \mathbb{E}[||e_{l_1}^y|| ||e_{l_2}^y||] + 2 \sum_{l_3=0}^{t} \sum_{l_4=0}^{t} ||\hat{W}(t, l_3)|| ||\hat{W}(t, l_4)|| \mathbb{E}[||\epsilon_{l_3}|| ||\epsilon_{l_4}||].
\]

According to Assumption 4.2, we obtain

\[
||\hat{W}^t(\hat{W} - I_{Nd})|| = ||(\hat{W} - \frac{1_N 1_N^T}{N} \otimes I_d)\hat{W}^{t-1}(\hat{W} - I_{Nd})|| \le \tau_w ||\hat{W}^{t-1}(\hat{W} - I_{Nd})|| \le \cdots \le \tau_w^t ||\hat{W} - I_{Nd}||,
\]

where \(\tau_w\) is defined in (4.10). Denote \(c_w := \max\{1, ||\hat{W} - I_{Nd}||^2/\tau_w^2\}\). Based on this, we can further derive

\[
\mathbb{E}[||\xi_t||^2] \le 2c_w \sum_{l_1=0}^{t-1} \sum_{l_2=0}^{t-1} \tau_w^{2t-l_1-l_2} \mathbb{E}[||e_{l_1}^y|| ||e_{l_2}^y||] + 2c_w \sum_{l_3=0}^{t} \sum_{l_4=0}^{t} \tau_w^{2t-l_3-l_4} \mathbb{E}[||\epsilon_{l_3}|| ||\epsilon_{l_4}||] \le 2c_w \sum_{l_1=0}^{t-1} \tau_w^{t-l_1} \sum_{l_2=0}^{t-1} \tau_w^{t-l_2} \mathbb{E}[\frac{||e_{l_1}^y||^2 + ||e_{l_2}^y||^2}{2}] + 2c_w \sum_{l_3=0}^{t} \tau_w^{t-l_3} \sum_{l_4=0}^{t} \tau_w^{t-l_4} \mathbb{E}[\frac{||\epsilon_{l_3}||^2 + ||\epsilon_{l_4}||^2}{2}] \le \frac{2c_w N}{(1-\tau_w)^2}(\frac{C\pi^2}{6} + U_1),
\]

where the last inequality is deduced from Assumption 4.3(ii), the condition \(\tau_w < 1\), and the observation that \(||e_t^{i,y}||^2 \le C/(t+1)^2\). Consequently, (4.13) is valid. \(\square\)

**Lemma 4.4.** The sequence \(\{y_t\}, \forall t \ge 1,\) is upper-bounded by

\[
\mathbb{E}[||y_t||^2] \le 4\mathbb{E}[||y'_t - 1_N \otimes \bar{y}'_t||^2] + 4L^2\mathbb{E}[||x_t - 1_N \otimes \bar{x}_t||^2] + \frac{4L^2}{N}\mathbb{E}[||\bar{x}_t - x^*||^2] + \frac{8c_w N}{(1-\tau_w)^2}(\frac{C\pi^2}{6} + U_1).
\]
