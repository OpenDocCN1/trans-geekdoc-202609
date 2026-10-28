

请注意，我们可以将上式改写为

$$\mathbb{E}_t\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2 + (1 - \beta_t)\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2 + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

应用詹森不等式，由上式可得

$$\mathbb{E}_t\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2 + (1 - \beta_t)\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2 + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

对两边取全期望 $\mathbb{E}[\cdot]$，我们有

$$\mathbb{E}\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \mathbb{E}\Big[\big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2\Big] + (1 - \beta_t)\mathbb{E}\Big[\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2\Big] + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

回想一下，上式中的 $i$ 和 $j$ 是从 $H$ 中任意选取的。因此，对两边关于所有配对 $(i, j) \in H$ 取平均，我们得到

$$\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2\Big] + (1 - \beta_t)\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2\Big] + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

回忆注记 4.5，对于一组 $m$ 个向量 $\mathbf{v}_1,\dots,\mathbf{v}_m$，我们有 $\sum_{i,j\in[m]}\|\mathbf{v}_i - \mathbf{v}_j\|^2 = 2m\sum_{i\in[m]}\Big\|\mathbf{v}_i - \frac{1}{m}\sum_{j\in[m]}\mathbf{v}_j\Big\|^2$。将其用于上式，我们得到

$$\frac{1}{|H|}\sum_{i\in H}\mathbb{E}\left[\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{H}\|^2\right] \le \beta_t \frac{1}{|H|}\sum_{i,j\in H}\mathbb{E}\left[\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{H}\|^2\right]$$

$$+ (1 - \beta_t)\frac{1}{|H|}\sum_{i\in H}\mathbb{E}\left[\|\nabla \mathcal{L}_i(\theta_t) - \nabla \mathcal{L}_H(\theta_t)\|^2\right] + (1 - \beta_t)^2\frac{\sigma^2}{b}.$$ 

根据假设 4.1，我们有 $\frac{1}{|H|}\sum_{i\in H}\mathbb{E}\left[\|\nabla \mathcal{L}_i(\theta_t) - \nabla \mathcal{L}_H(\theta_t)\|^2\right] \le \zeta$。将其代入上式即完成证明。$\square$

## 变化的动量系数与新的李雅普诺夫函数

从上述分析中，我们指出，为了获得梯度噪声对聚合误差的递减效应（类似于非凸情形），我们必须选择与学习率 $\gamma_t$ 成比例的 $1 - \beta_t$，而学习率 $\gamma_t$ 本身可以选择为递减的。具体地，在确保整个迭代过程中 $\gamma_t \le \frac{1}{c}$（其中 $c$ 为正实数）的同时，我们选择

$$\beta_t = 1 - c\gamma_{t-1}, \quad \forall t. \tag{6.47}$$

对于第一次迭代，我们选择 $\beta_1 = 0$。在预定递减学习率下，动量系数的变化使得获得聚合误差的有用一致界变得相当困难。为克服这一问题，我们考虑一个不同的李雅普诺夫函数来分析强凸情形下 Robust DMHB 的收敛性。具体地，我们考虑如下李雅普诺夫函数：

$$V_t := (\mathcal{L}_H(\theta_t) - \mathcal{L}_H^*) + \frac{1}{64L}\left(\|\xi_t\|^2 + \kappa \frac{1}{|H|}\sum_{i\in H}\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{H}\|^2\right). \tag{6.48}$$

回想 $\xi_t := \mathbf{m}_t^{H} - \nabla \mathcal{L}_H(\theta_t)$。观察到与非凸情形中使用的李雅普诺夫函数相比，我们还加入了动量向量之间的漂移项，即 $\frac{1}{|H|}\sum_{i\in H}\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{H}\|^2$，其在变动动量速率下的瞬时增长已在上文引理 6.6 中分析。在定理 6.2 中，我们分析这一特定李雅普诺夫函数的增长。

### 定理 6.2
假设 3.1、3.2、4.1 和 4.2 成立。考虑带有 $(f,\kappa)$-鲁棒平均 $F$ 的算法 6，批大小 $b \in [1,m)$，对所有 $t$ 有 $\gamma_t \le \frac{1}{144L}$，且动量系数由 (6.47) 定义，其中 $c = 144L$。那么，对于 (6.48) 中定义的 $V_t$，对所有 $t > 1$，我们有

$$\mathbb{E}[V_t] \le \left(1 - \frac{\mu}{4}\gamma_{t-1}\right)\mathbb{E}[V_{t-1}] + 324L\left(\kappa + \frac{1}{n - f}\right)\frac{\sigma^2}{b}\gamma_{t-1}^2 + \frac{9}{4}\kappa\zeta\gamma_{t-1}.$$

### 证明
我们记 $z := \frac{1}{64L}$，以及

$$M_t^H = \frac{1}{|H|}\sum_{i\in H}\left\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^H\right\|^2.$$

考虑任意一次迭代 $t > 1$。根据 (6.48) 中 $V_t$ 的定义，我们有

$$V_t = \left(\mathcal{L}_H(\theta_t) - \mathcal{L}_H^*\right) + z\left(\|\xi_t\|^2 + \kappa M_t^H\right). \tag{6.49}$$

接下来，我们分别使用引理 6.4、6.3 和 6.6，对三项 $\mathcal{L}_H(\theta_t)-\mathcal{L}_H^*$、$\|\xi_t\|^2$ 和 $M_t^H$ 获得（期望意义下的）上界。关于 $\mathcal{L}_H(\theta_t)-\mathcal{L}_H^*$ 的界。由引理 6.4，我们有

$$\mathcal{L}_H(\theta_t)-\mathcal{L}_H^* \le \left(\mathcal{L}_H(\theta_{t-1})-\mathcal{L}_H^*\right)-\gamma_{t-1}\left(\frac{1}{2}-2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + \gamma_{t-1}(1+2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + \gamma_{t-1}(1+\gamma_{t-1}L)\|\delta_{t-1}\|^2.$$

由于聚合规则 $F$ 被假设为 $(f,\kappa)$-鲁棒平均，根据定义 4.3，对所有 $t \in [T]$ 我们有 $\|\delta_t\|^2 \le \frac{\kappa}{|H|}\sum_{i\in H}\left\|\mathbf{m}_t^{(i)}-\mathbf{m}_t^H\right\|^2 = \kappa M_t^H$。将其代入上式，我们得到

$$\mathcal{L}_H(\theta_t)-\mathcal{L}_H^* \le \left(\mathcal{L}_H(\theta_{t-1})-\mathcal{L}_H^*\right)-\gamma_{t-1}\left(\frac{1}{2}-2\gamma_{t-1}L\right)\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2 + \gamma_{t-1}(1+2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + \gamma_{t-1}(1+\gamma_{t-1}L)\kappa M_{t-1}^H.$$

注意到，由于对所有 $t \in [T]$ 有 $\gamma_t \le \frac{1}{144L}$，我们有 $1+2\gamma_{t-1}L \le 2$，以及 $1+\gamma_{t-1}L \le 2$。将其代入上式，并取全期望 $\mathbb{E}[\cdot]$，我们得到

$$\mathbb{E}[\mathcal{L}_H(\theta_t)-\mathcal{L}_H^*] \le \mathbb{E}[\mathcal{L}_H(\theta_{t-1})-\mathcal{L}_H^*] + 2\gamma_{t-1}\mathbb{E}[\|\xi_{t-1}\|^2] + 2\kappa\gamma_{t-1}\mathbb{E}[M_{t-1}^H] - \gamma_{t-1}\left(\frac{1}{2}-2\gamma_{t-1}L\right)\mathbb{E}[\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2]. \tag{6.50}$$

**关于 $\|\xi_t\|^2$ 的界。** 由引理 6.3，我们有

\[\mathbb{E}_t\left[\|\xi_t\|^2\right] \le (1 + 5L\gamma_{t-1} + 4L^2\gamma_{t-1}^2)\beta_t^2 \|\xi_{t-1}\|^2 + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ 2L\gamma_{t-1}(1 + \gamma_{t-1}L)\beta_t^2 \|\delta_{t-1}\|^2 + 4L\gamma_{t-1}(1 + \gamma_{t-1}L)\beta_t^2 \|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.\]

与上面类似，由于对所有 $t \in [T]$ 有 $\gamma_t \le \frac{1}{144L}$，我们有 $1 + 5L\gamma_{t-1} + 4L^2\gamma_{t-1}^2 \le 1 + 5L\gamma_{t-1} + L\gamma_{t-1} = 1 + 6L\gamma_{t-1}$ 以及 $1 + \gamma_{t-1}L \le 2$。将其代入上式，我们得到

\[\mathbb{E}_t\left[\|\xi_t\|^2\right] \le (1 + 6L\gamma_{t-1})\beta_t^2 \|\xi_{t-1}\|^2 + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ 4L\gamma_{t-1}\beta_t^2 \|\delta_{t-1}\|^2 + 8L\gamma_{t-1}\beta_t^2 \|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.\]

回想，由于 $F$ 是 $(f, \kappa)$-鲁棒平均，对所有 $t \in [T]$ 有 $\|\delta_t\|^2 \le \kappa M_t^H$。将其代入上式，并取全期望 $\mathbb{E}[\cdot]$，我们得到

\[\mathbb{E}\left[\|\xi_t\|^2\right] \le (1 + 6L\gamma_{t-1})\beta_t^2 \mathbb{E}\left[\|\xi_{t-1}\|^2\right] + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\tag{6.51}\]

\[+ 4L\kappa\beta_t^2\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + 8L\gamma_{t-1}\beta_t^2\mathbb{E}\left[\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\right].\]

**关于 $\mathbb{E}\left[M_t^H\right]$ 的界。** 最后，由引理 6.6，我们有

\[\mathbb{E}\left[M_t^H\right] \le \beta_t\mathbb{E}\left[M_{t-1}^H\right] + (1 - \beta_t)^2\frac{\sigma^2}{b} + (1 - \beta_t)\zeta.\tag{6.52}\]

在 (6.49) 中应用全期望 $\mathbb{E}[\cdot]$，然后代入 (6.50)、(6.51) 和 (6.52)，我们得到

\[\mathbb{E}[V_t] \le \mathbb{E}\left[\mathcal{L}_H(\theta_{t-1}) - \mathcal{L}_H^*\right] + 2\gamma_{t-1}\mathbb{E}\left[\|\xi_{t-1}\|^2\right]\]

\[+ 2\kappa\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + z(1 + 6L\gamma_{t-1})\beta_t^2\mathbb{E}\left[\|\xi_{t-1}\|^2\right]\]

\[+ z(1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ z4\kappa\beta_t^2\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + z\kappa\beta_t\mathbb{E}\left[M_{t-1}^H\right]\]

（续）

