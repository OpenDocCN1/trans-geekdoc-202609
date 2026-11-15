
### Proof.

Here, our objective is to determine the appropriate ranges for $\hat{\alpha}$ and $\beta$ that result in $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$. Leveraging Lemma 13 from [49], we observe that for a five-dimensional positive vector $\boldsymbol{\gamma} = [\gamma_1, \gamma_2, \gamma_3, \gamma_4, \gamma_5]^{\mathrm{T}}$, if $\rho(\mathbf{G}_{\hat{\alpha}, \beta})\boldsymbol{\gamma} \prec \boldsymbol{\gamma}$, it implies that $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$. Based on this, we can derive the following set of inequalities:

$\beta(\gamma_3\sigma + \gamma_5\hat{\alpha}|s|) < \gamma_1(1 - \sigma) - C\hat{\alpha}, \quad (2.19\text{a})$
$\beta a_1(\gamma_3 + \gamma_5\hat{\alpha}|s|) < \gamma_2(1 - \lambda) - (\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1)\hat{\alpha}, \quad (2.19\text{b})$
$\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_3 - a_3\gamma_1 - C\hat{\alpha}, \quad (2.19\text{c})$
$\hat{\mathrm{g}}\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_4(1 - \sigma) - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - \hat{\mathrm{g}}C\hat{\alpha}, \quad (2.19\text{d})$
$\hat{\mathrm{g}}\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_5 - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - a_3\gamma_4 - \hat{\mathrm{g}}C\hat{\alpha}, \quad (2.19\text{e})$

where $C = \hat{\mathrm{g}}\sqrt{n}\gamma_1 + \hat{\mathrm{g}}\sqrt{n}\gamma_2 + \hat{\mathrm{g}}\hat{a}_3$. Initially, we dispense with the presence of $\lambda$ in (2.19b). Assuming $\hat{\alpha} < \mu$, according to Lemma 2.5, we can deduce that $\lambda = 1 - \frac{\mathbb{1}_n^{\mathrm{T}}\mathrm{diag}(\boldsymbol{\alpha})\mathbb{1}_n}{nL} \leqslant 1 - \frac{1}{L}\hat{\alpha}$. Consequently, (2.19b) can be reduced to

$\beta a_1(\gamma_3 + \gamma_5\hat{\alpha}|s|) < \gamma_2\frac{1}{L}\hat{\alpha} - (\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1)\hat{\alpha}. \quad (2.20)$

As the right-hand side of the aforementioned inequalities, i.e., (2.19a), (2.19c), (2.19d), (2.19e), and (2.20) are all positive values, it is possible to deduce that

$\hat{\alpha} < \frac{\gamma_1(1 - \sigma)}{C}, \quad (2.21\text{a})$
$\hat{\alpha} < \frac{\gamma_3 - a_3\gamma_1}{C}, \quad (2.21\text{b})$
$\hat{\alpha} < \frac{\gamma_4(1 - \sigma) - \gamma_1\hat{\mathrm{g}}\hat{a}_3}{\hat{\mathrm{g}}C}, \quad (2.21\text{c})$
$\hat{\alpha} < \frac{\gamma_5 - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - a_3\gamma_4}{\hat{\mathrm{g}}C}, \quad (2.21\text{d})$
$\gamma_2 > L(\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1). \quad (2.21\text{e})$

To guarantee that $\hat{\alpha}$ remains positive, we can establish an upper limit for the range of $\gamma_1$ in the following manner:

$\gamma_1 < \min \left\{ \frac{\gamma_3}{a_3}, \frac{\gamma_4(1 - \sigma)}{\hat{\mathrm{g}}\hat{a}_3}, \frac{\gamma_5 - a_3\gamma_4}{\hat{\mathrm{g}}\hat{a}_3} \right\}. \quad (2.22)$

Subsequently, we proceed to assign distinct values from $\gamma_1$ to $\gamma_5$. We align $\gamma_1$ and $\gamma_2$ with the values stipulated in Theorem 2.1. By integrating the permissible range of $\gamma_1$ and $\gamma_2$, we assign $\gamma_3 = a_3, \gamma_4 = \hat{\mathrm{g}}a_3, \gamma_5 = \hat{\mathrm{g}}a_3 + a_3\gamma_4$. Once these values are substituted into inequalities (2.19) and (2.21), we can determine the appropriate ranges for $\hat{\alpha}$ and $\beta$.

Drawing upon the foundations of the previous proof, we subsequently establish the overall linear convergence rate of ET-PDA. For all $t > 0$, we proceed with the iterative recursion defined in (2.16) as follows:

\[
\mathbf{v}^t \leqslant \mathbf{G}_{\hat{\alpha}, \beta}^t \mathbf{v}_0 + \sum_{l=0}^{t-1} \mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l.
\]

If $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$, it can be deduced that $\|\mathbf{G}_{\hat{\alpha}, \beta}^t\| \leqslant Q(\kappa_2)^t$, $\|\mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l\| \leqslant Q(\kappa_2)^t$ for some constants $Q$ and $0 < \max\{\kappa_1, \rho(\mathbf{G}_{\hat{\alpha}, \beta})\} \leqslant \kappa_2 < 1$. Consequently, (2.23) can be reformulated in the following manner:

\[
\begin{aligned}
\|\mathbf{v}^t\| &\leqslant \|\mathbf{G}_{\hat{\alpha}, \beta}^t\|\|\mathbf{v}^0\| + \sum_{l=0}^{t-1} \|\mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l\| \\
&\leqslant Q\|\mathbf{v}^0\|(\kappa_2)^t + \sum_{l=0}^{t-1} Q(\kappa_2)^t = w^t(\kappa_2)^t,
\end{aligned}
\]

where $w^t = Q\|\mathbf{v}^0\| + Qt$. For $\kappa_2 < \kappa_3 < 1$, the limit equality can be expressed as $\lim_{t \to \infty} \|\mathbf{v}^t\|/(\kappa_3)^t = w^t(\kappa_2/\kappa_3)^t = 0$. At this moment, given a positive constant $Q_1$ and a minute constant $r$, it is established that $\|\mathbf{v}_t\| \leqslant Q_1(\kappa_4)^t$, where $\kappa_4 = \kappa_3 + r$. The proof of Theorem 2.1 is now concluded.

### Remark 2.5.

Theorem 2.1 elucidates that despite the integration of an event-triggered mechanism, ET-PDA retains its capacity to converge linearly towards an optimal economic dispatch solution, provided that the largest step-size $\hat{\alpha}$ and momentum coefficient $\beta$ are adequately regulated within a specified set of conditions. Furthermore, the selection of the two primary parameters $E$ and $\kappa_1$ pertaining to the triggering condition is relatively straightforward, thus facilitating the implementation of the algorithm.

### Theorem 2.2.

Given the conditions of Assumptions 2.1–2.3, and assuming the sequences $\{\mathbf{x}^t\}$, $\{\mathbf{\theta}^t\}$, $\{\mathbf{y}^t\}$, $\{\hat{\mathbf{y}}^t\}$, and $\{\mathbf{z}^t\}$ are iteratively updated according to either (2.10) or (2.12), if the values of $\hat{\alpha}$ and $\beta$ adhere to the stipulations of Theorem 2.1, then the sequence $\{\mathbf{x}^t\}$ will converge towards the optimal solution $\mathbf{x}^*$ at a rate of convergence of $O((\rho(\mathbf{G}_{\hat{\alpha}, \beta})/2)^t)$.

### Proof.

Analogous to numerous decentralized algorithms subject to constraints [17, 35, 42, 43], our analysis delves into the convergence rate of the original variable sequence by scrutinizing the interplay between the primal variable and the Lagrangian multiplier. The cornerstone of proving this theorem lies in the establishment of the following inequality:

\[
\sum_{i=1}^n \frac{\mu_i}{2}(x_i^{t+1} - x^*) \leqslant \sum_{i=1}^n (\nabla q_i(\theta^*)(\theta_i^t - \theta^*) + \frac{1}{2\mu_i}(\theta_i^t - \theta^*) + \theta_i^t(x_i^* - c_i).
\]

Given that $x^*$ represents the optimal solution set for the problem (2.2), it follows that the sum of differences between the optimal variables and constants is zero, *i.e.*, $\sum_{i=1}^n (x_i^* - c_i) = 0$. Furthermore, when both $\hat{\alpha}$ and $\beta$ adhere to the prerequisites of Theorem 2.1, we can deduce that $\theta_i^t$ converges to $\theta^*$. Consequently, as $t$ approaches infinity, the right-hand side of (2.25) tends towards zero, indicating that the sequence $\{x^t\}$ converges to $x^*$ at a rate of $O((\rho(\mathbf{G}_{\hat{\alpha}, \beta})/2)^t)$. This completes the proof of Theorem 2.2.

### Remark 2.6.

Employing the bounds for $\hat{\alpha}$ and $\beta$ stipulated in Theorem 2.1, we present in Theorem 2.2 the convergence of the sequence $\{x^t\}$ towards $x^*$. Notably, the parameters $\gamma_1$, $\gamma_2$, $\gamma_3$, $\gamma_4$, and $\gamma_5$ mentioned in Theorem 2.1 are adjustable, and their specific values are determined by the network topology and the associated cost function.

### Theorem 2.3.

Assuming the prerequisites of Assumptions 2.1–2.3 are met, and provided that $\hat{\alpha}$ and $\beta$ are chosen in accordance with the requirements of Theorem 2.1, it is observed that when $E > (3Q_1 + 2Q_1 L)(1 + (\kappa_1)^2) / (\kappa_1)^2$, then it holds that $t_i^{k(i,t)+1} - t_i^{k(i,t)} \gg 2$, for all $i \in \mathcal{V}$ and for any $t > 0$.

### Proof.

Drawing upon the measurement errors denoted by (2.9) and the constraint $\|\mathbf{v}^t\| \leqslant Q_1(\kappa_4)^t$ outlined in Theorem 2.1, we can infer that

\[
\begin{aligned}
\|\epsilon_{i,o}^t\| + \|\epsilon_{i,z}^t\| \\
= \|\theta_i^{k(i,t)} - \theta_i^t\| + \|z_i^{k(i,t)} - z_i^t\| \\
\leqslant \|\theta_i^{k(i,t)} - \bar{\theta}_i^{k(i,t)}\| + \|\bar{\theta}_i^{k(i,t)} - \bar{\theta}^t\| + \|\bar{\theta}^t - \bar{\theta}_i^t\| \\
+ \|z_i^{k(i,t)} - \bar{z}_i^{k(i,t)}\| + \|\bar{z}_i^{k(i,t)} - \bar{z}^t\| + \|\bar{z}^t - z_i^t\| \\
\leqslant (3Q_1 + 2Q_1 L)(\kappa_4)^{t_i^{k(i,t)}} + (3Q_1 + 2Q_1 L)(\kappa_4)^t.
\end{aligned}
\tag{2.26}
\]

Revisiting the triggering condition (2.8), we subsequently arrive at

\[
E(\kappa_1)t_i^{k(i,t)+1} \leqslant (3Q_1 + 2Q_1 L)(\kappa_1)^{t_i^{k(i,t)+1}} + (3Q_1 + 2Q_1 L)(\kappa_1)^{t_i^{k(i,t)}}.
\tag{2.27}
\]

Given that $\kappa_1$ is less than $\kappa_4$, the following inequality emerges:

\[
t_i^{k(i,t)+1} - t_i^{k(i,t)} \geqslant \frac{\ln \frac{(3Q_1 + 2Q_1 L)}{E - (3Q_1 + 2Q_1 L)}}{\ln \kappa_1}.
\tag{2.28}
\]

Provided that $E$ falls within the specified range in Theorem 2.3, it is postulated that the interval between $t_i^{k(i,t)+1}$ and $t_i^{k(i,t)}$ is not less than 2. The proof of Theorem 2.3 is thus finalized.

### Remark 2.7.

We abandon the traditional periodic or continuous sampling format and adopt a more efficient aperiodic sampling methodology to circumvent Zeno-like phenomena, as cited in [2, 3, 17, 35, 41–43]. This shift not only validates the feasibility of Event-Triggered Predictive Data Assimilation (ET-PDA) but also significantly diminishes communication and computational overheads per iteration, thereby enhancing overall execution efficiency.
