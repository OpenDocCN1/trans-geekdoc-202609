
\[
\|\nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\| \le L\|\theta_t - \theta_{t-1}\|.
\]
因此，由于 \(\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\rangle \le \|\xi_{t-1}\|\|\nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\|\)，根据 Cauchy–Schwarz 不等式，我们得到 \(\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) - \nabla\mathcal{L}_H(\theta_t)\rangle \le L\|\xi_{t-1}\|\|\theta_t - \theta_{t-1}\|\)。

将上述不等式代入 (6.18)，我们得到
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \beta_t^2L^2\|\theta_t - \theta_{t-1}\|^2 + 2\beta_t^2L\|\xi_{t-1}\|\|\theta_t - \theta_{t-1}\|.
\]

由 (6.3) 将 \(\theta_t = \theta_{t-1} - \gamma_{t-1}\hat{m}_{t-1}\) 代入上式，我们得到
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \beta_t^2L^2\gamma_{t-1}^2\|\hat{m}_{t-1}\|^2 + 2\beta_t^2L\gamma_{t-1}\|\xi_{t-1}\|\|\hat{m}_{t-1}\|.
\]

由于 \(2\|\xi_{t-1}\|\|\hat{m}_{t-1}\| \le \|\xi_{t-1}\|^2 + \|\hat{m}_{t-1}\|^2\)，由上式可得
\[
\mathbb{E}_t[\|\xi_t\|^2] \le (1+\gamma_{t-1}L)\beta_t^2\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + \gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\hat{m}_{t-1}\|^2. \tag{6.19}
\]

根据 (6.5) 中 \(\delta_t\) 的定义，我们有 \(\hat{m}_{t-1} = \delta_{t-1} + m_{t-1}^H\)。于是，利用三角不等式和 Jensen 不等式，我们有 \(\|\hat{m}_{t-1}\|^2 \le 2\|\delta_{t-1}\|^2 + 2\|m_{t-1}^H\|^2\)。类似地，根据 (6.17) 中 \(\xi_t\) 的定义，我们有 \(\|m_{t-1}^H\|^2 \le 2\|\xi_{t-1}\|^2 + 2\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\)。将后者代入前者，我们得到 \(\|\hat{m}_{t-1}\|^2 \le 2\|\delta_{t-1}\|^2 + 4\|\xi_{t-1}\|^2 + 4\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\)。

将上述结果代入 (6.19)，我们得到
\[
\mathbb{E}_t[\|\xi_t\|^2] \le \beta_t^2(1+\gamma_{t-1}L)(1+4\gamma_{t-1}L)\|\xi_{t-1}\|^2 + (1-\beta_t)^2\frac{\sigma^2}{b(n-f)} + 2\gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\delta_{t-1}\|^2 + 4\gamma_{t-1}L(1+\gamma_{t-1}L)\beta_t^2\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.
\]

至此证明完成。

## 大动量系数增加偏差

为简化起见，假设我们有一个常数学习率 \(\gamma\) 和一个常数动量系数 \(\beta\)。那么，注意到引理 6.3 中分析的偏差的增长速率有效地由因子 \((1+\gamma L)(1+4\gamma L)\beta^2\) 给出。为了使偏差稳定，即最终被有限值所界定，该因子需要小于或等于 1。具体而言，如果 \(\beta^2\) 大于 \(\frac{1}{1+\gamma L}\)，则诚实节点的平均动量可以任意偏离其局部梯度的平均值，这可能会阻止学习算法收敛到平稳点。这一观察在没有对抗节点的情况下也成立。偏差 \(\xi_t\) 相对于 \(\beta\) 的增长速率与聚合误差 \(\delta_t\) 的增长速率相反。虽然控制前者对算法的收敛很重要，但后者对对抗节点的鲁棒性至关重要。在下一节中，我们提出一个动量系数的候选值，该值有利于控制局部动量对偏差和聚合误差的相反影响。

## 6.2 鲁棒分布式小批量重球法的弹性

在本节中，我们分析鲁棒 DMHB，即算法 6 的弹性（和平稳弹性）特性。对于分析，我们利用了关于聚合误差和动量偏差的上述结果，即分别引理 6.2 和 6.3。我们首先给出一个重要的子结果，该结果涉及算法 6 中参数向量 \(\theta_t\) 轨迹上损失函数 \(\mathcal{L}_H(\theta_t)\) 的增长。虽然研究损失函数的增长对于表征鲁棒 DMHB 的最终收敛至关重要，但它本身是不够的，这与鲁棒 DMGD 的情况不同。我们需要解决一个额外的复杂性。具体而言，非消失的动量偏差导致学习过程中出现随机偏差，必须仔细控制。

### 6.2.1 分布式动量下的损失函数增长

我们在引理 6.4 中分析鲁棒 DMHB，即算法 6 的任意迭代 \(t > 1\) 时当前损失 \(\mathcal{L}_H(\theta_t)\) 与前一损失 \(\mathcal{L}_H(\theta_{t-1})\) 之间的差异。如预期，损失函数的增长取决于聚合误差 \(\delta_{t-1}\) 和偏差 \(\xi_{t-1}\) 两者。

**Lemma 6.4** *假设假设 3.1。考虑批大小为 \(b \in [1, m)\) 的算法 6。那么，对于任意迭代 \(t > 1\)，以下成立：*

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le -\gamma_{t-1}\left(\frac{1}{2} - 2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + \gamma_{t-1}(1 + 2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + \gamma_{t-1}(1 + \gamma_{t-1}L)\|\delta_{t-1}\|^2
\]

*证明* 考虑任意迭代 \(t > 1\)。由于 \(\mathcal{L}_H\) 是根据假设 3.1 具有系数 \(L\) 的 Lipschitz 平滑函数，我们有

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le \langle \theta_t - \theta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \frac{L}{2}\|\theta_t - \theta_{t-1}\|^2
\]

有关上述推导的详细内容，请参见附录 A.1 中的引理 A.1。由 (6.4) 代入 \(\theta_t = \theta_{t-1} - \gamma_{t-1}\mathbf{m}_{t-1}^H - \gamma_{t-1}\delta_{t-1}\)，我们得到

\[
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le -\gamma_{t-1}\langle \mathbf{m}_{t-1}^H, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle - \gamma_{t-1}\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \gamma_{t-1}^2\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2
\]

由 (6.17) 代入 \(\mathbf{m}_{t-1}^H = \nabla\mathcal{L}_H(\theta_{t-1}) + \xi_{t-1}\)，我们得到

\[
\begin{aligned}
\mathcal{L}_H(\theta_t) - \mathcal{L}_H(\theta_{t-1}) \le &-\gamma_{t-1}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 - \gamma_{t-1}\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle \\
&- \gamma_{t-1}\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1}) \rangle + \gamma_{t-1}^2\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \tag{6.20}
\end{aligned}
\]

接下来，我们分别分析右端最后三个项。

首先，根据 Cauchy–Schwarz 不等式，由于 \(2a_1a_2 \le \frac{1}{a_3}a_1^2 + a_3a_2^2\)，\(\forall a_3 > 0\)，我们得到

\[
2|\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\xi_{t-1}\|\|\nabla\mathcal{L}_H(\theta_{t-1})\| \le 2\|\xi_{t-1}\|^2 + \frac{1}{2}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.21}
\]

其次，与 (6.21) 类似，我们得到

\[
2|\langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\delta_{t-1}\|^2 + \frac{1}{2}\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.22}
\]

最后，利用三角不等式和 Jensen 不等式，我们得到

\[
\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 2\|\mathbf{m}_{t-1}^H\|^2 + 2\|\delta_{t-1}\|^2.
\]

代入 \(\mathbf{m}_{t-1}^H = \nabla\mathcal{L}_H(\theta_{t-1}) + \xi_{t-1}\)，并重复上述基于三角不等式和 Jensen 不等式的推理，我们得到

\[
\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 4\|\xi_{t-1}\|^2 + 4\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + 2\|\delta_{t-1}\|^2. \tag{6.23}
\]

由 (6.21)、(6.22) 和 (6.23)，我们得到

\[
\begin{aligned}
&-\langle \xi_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle - \langle \delta_{t-1}, \nabla\mathcal{L}_H(\theta_{t-1})\rangle + \gamma_{t-1}\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \\
&\le (1 + 2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + (1 + \gamma_{t-1}L)\|\delta_{t-1}\|^2 + \left(\frac{1}{2} + 2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.
\end{aligned}
\]

将两边乘以 \(\gamma_{t-1}\)，然后将所得不等式代入 (6.20) 即完成证明。

### 动量偏差带来的复杂性

我们注意到，与鲁棒 DMGD 的情况相比，鲁棒 DMHB 中的损失函数增长取决于一个额外的量，即动量偏差 \(\xi_t\)。回想一下，从引理 6.3 可知，与引理 6.2 中的聚合误差不同，我们没有动量偏差的统一界，这使得算法 6 的收敛分析更加复杂。为了克服这一挑战，我们采用 Lyapunov 分析的一般技术。本质上，在 Lyapunov
