
\[
\|\nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\| \le L\|\theta_t - \theta_{t-1}\|.
\]
Therefore, as \(\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\rangle \le \|\xi_{t-1}\|\|\nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\|\), owing to the Cauchy–Schwarz inequality, we obtain that \(\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\rangle \le L\|\xi_{t-1}\|\|\theta_t - \theta_{t-1}\|\).

Using the above inequalities in (6.18), we obtain that
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \beta_t^2L^2\|\theta_t - \theta_{t-1}\|^2 + 2\beta_t^2L\|\xi_{t-1}\|\|\theta_t - \theta_{t-1}\|.
\]

Substituting, from (6.3), \(\theta_t = \theta_{t-1} - \gamma_{t-1}\hat{m}_{t-1}\) in the above, we obtain that
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \beta_t^2L^2\gamma_{t-1}^2\|\hat{m}_{t-1}\|^2 + 2\beta_t^2L\gamma_{t-1}\|\xi_{t-1}\|\|\hat{m}_{t-1}\|.
\]

As \(2\|\xi_{t-1}\|\|\hat{m}_{t-1}\| \le \|\xi_{t-1}\|^2 + \|\hat{m}_{t-1}\|^2\), from the above, we obtain that
\[
\mathbb{E}_t[\|\xi_t\|^2] \le (1+\gamma_{t-1}L)\beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\hat{m}_{t-1}\|^2. \tag{6.19}
\]

By the definition of \(\delta_t\) in (6.5), we have \(\hat{m}_{t-1} = \delta_{t-1} + m_{t-1}^H\). Thus, using the triangle and Jensen’s inequalities, we have \(\|\hat{m}_{t-1}\|^2 \le 2\|\delta_{t-1}\|^2 + 2\|m_{t-1}^H\|^2\). Similarly, by the definition of \(\xi_t\) in (6.17), we have \(\|m_{t-1}^H\|^2 \le 2\|\xi_{t-1}\|^2 + 2\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\). Substituting from the latter in the former, we obtain that \(\|\hat{m}_{t-1}\|^2 \le 2\|\delta_{t-1}\|^2 + 4\|\xi_{t-1}\|^2 + 4\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\).

Substituting from the above in (6.19), we obtain that
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2(1+\gamma_{t-1}L)(1+4\gamma_{t-1}L)\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + 2\gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\delta_{t-1}\|^2 + 4\gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.
\]

This concludes the proof.

## Large Momentum Coefficient Increases Deviation

For simplicity, suppose that we have a constant learning rate \(\gamma\) and a constant momentum coefficient \(\beta\). Then, observe that the rate of growth of the deviation analyzed in Lemma 6.3 is effectively given by the factor \((1+\gamma L)(1+4\gamma L)\beta^2\). For the deviation to be stable, i.e., to be bounded eventually by a finite value, this factor needs to be less than (or equal to) 1. Specifically, if \(\beta^2\) is larger than \(\frac{1}{1+\gamma L}\), the honest nodes’ average momentum can deviate arbitrarily from the average of their local gradients, which could prevent the learning algorithm from converging to a stationary point. This observation is also valid in the case when there are no adversarial nodes. This rate of growth of the deviation \(\xi_t\), with respect to \(\beta\), is contrary to that of the aggregation error \(\delta_t\). Although controlling the former is important to the convergence of the algorithm, the latter is critical to the robustness against adversarial nodes. In the following section, we present a candidate for the momentum coefficient that favorably controls the opposing consequences of local momentum on deviation and aggregation error.

## 6.2 Resilience of Robust Distributed Mini-Batch Heavy Ball

In this section, we analyze the resilience (and stationary resilience) property of Robust DMHB, i.e., Algorithm 6. For the analysis, we make use of the above results pertaining to the aggregation error and the momentum deviation, i.e., Lemmas 6.2 and 6.3, respectively. We begin by presenting an important sub-result that concerns the growth of the loss function \(\mathcal{L}_H(\theta_t)\) over the trajectory of the parameter vector \(\theta_t\) in Algorithm 6. Although studying the loss function growth is essential to characterizing the final convergence of Robust DMHB, it is not sufficient on its own, unlike the case of Robust DMGD. We need to address an additional complication. Specifically, the presence of non-vanishing momentum deviation leads to a stochastic bias in the learning procedure that must be carefully controlled.

### 6.2.1 Loss Function Growth Under Distributed Momentum

We analyze, in Lemma 6.4, the difference between the current loss \(\mathcal{L}_H(\theta_t)\) and the previous loss \(\mathcal{L}_H(\theta_{t-1})\) for an arbitrary iteration \(t > 1\) of Robust DMHB, i.e., Algorithm 6. As expected, the loss function growth depends upon both the aggregation error \(\delta_{t-1}\) and the deviation \(\xi_{t-1}\).

**Lemma 6.4** *Suppose Assumption 3.1. Consider Algorithm 6 with batch-size \(b \in [1, m)\). Then, for any iteration \(t > 1\), the following holds true:*

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le -\gamma_{t-1}\left(\frac{1}{2} - 2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + \gamma_{t-1}(1 + 2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + \gamma_{t-1}(1 + \gamma_{t-1}L)\|\delta_{t-1}\|^2
\]

*Proof* Consider an arbitrary iteration \(t > 1\). Since \(\mathcal{L}_H\) is a Lipschitz-smooth function with coefficient \(L\), owing to Assumption 3.1, we have

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le \langle \theta_t - \theta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \frac{L}{2}\|\theta_t - \theta_{t-1}\|^2
\]

For details on the derivation of the above, see Lemma A.1 in Appendix A.1. Substituting from (6.4), \(\theta_t = \theta_{t-1} - \gamma_{t-1}\mathbf{m}_{t-1}^H - \gamma_{t-1}\delta_{t-1}\), we obtain that

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le -\gamma_{t-1}\langle \mathbf{m}_{t-1}^H, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle - \gamma_{t-1}\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \gamma_{t-1}^2\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2
\]

Substituting from (6.17), \(\mathbf{m}_{t-1}^H = \nabla\mathcal{L}_H(\theta_{t-1}) + \xi_{t-1}\), we obtain that

\[
\begin{aligned}
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le &-\gamma_{t-1}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 - \gamma_{t-1}\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle \\
&- \gamma_{t-1}\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \gamma_{t-1}^2\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \tag{6.20}
\end{aligned}
\]

Next, we separately analyze the last three terms on the right-hand side.

First, by Cauchy–Schwarz inequality, as \(2a_1a_2 \le \frac{1}{a_3}a_1^2 + a_3a_2^2\), \(\forall a_3 > 0\), we obtain that

\[
2|\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\xi_{t-1}\|\|\nabla\mathcal{L}_H(\theta_{t-1})\| \le 2\|\xi_{t-1}\|^2 + \frac{1}{2}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.21}
\]

Second, similarly to (6.21), we obtain that

\[
2|\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\delta_{t-1}\|^2 + \frac{1}{2}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.22}
\]

Last, using the triangle and Jensen’s inequalities, we obtain that

\[
\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 2\|\mathbf{m}_{t-1}^H\|^2 + 2\|\delta_{t-1}\|^2.
\]

Substituting \(\mathbf{m}_{t-1}^H = \nabla\mathcal{L}_H(\theta_{t-1}) + \xi_{t-1}\), and repeating the above reasoning due to the triangle and Jensen’s inequalities, we obtain that

\[
\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 4\|\xi_{t-1}\|^2 + 4\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + 2\|\delta_{t-1}\|^2. \tag{6.23}
\]

From (6.21), (6.22), and (6.23), we obtain that

\[
\begin{aligned}
&-\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle - \langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle + \gamma_{t-1}\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \\
&\le (1 + 2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + (1 + \gamma_{t-1}L)\|\delta_{t-1}\|^2 + \left(\frac{1}{2} + 2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.
\end{aligned}
\]

Multiplying both sides by \(\gamma_{t-1}\) and then plugging the resulting inequality in (6.20) concludes the proof.

### Complications Due to Momentum Deviation

We note that, compared to the case of Robust DMGD, the loss function growth in Robust DMHB depends on an additional quantity that is the momentum deviation \(\xi_t\). Recall, from Lemma 6.3, that we do not have, unlike the aggregation error in Lemma 6.2, a uniform bound on momentum deviation at our disposal, which makes the convergence analysis of Algorithm 6 more intricate. To overcome this challenge, we resort to the general technique of Lyapunov analysis. Essentially, in Lyapunov
