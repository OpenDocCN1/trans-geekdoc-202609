
{f(w,X): w ∈ Ω}，与之竞争。更一般地，我们也可以考虑非规范在线学习，其中 f̂_{t-1}(x) 可能不属于函数类 {f(w,x): w ∈ Ω}。在讨论中，我们不区分这两种情况。

为了与在线学习区分，机器学习文献中通常将标准监督学习设置称为批量学习。遗憾界分析可以被视为批量学习中预言不等式的一种推广。我们稍后将通过一种称为在线到批量转换的简单技术，展示遗憾界直接蕴含预言不等式。

## 14.2 感知机算法

在本节中，我们将研究一种称为感知机算法的简单在线学习算法，它是现代神经网络的前身。

考虑 Y ∈ {±1} 的二分类问题，以及线性函数

f(w,X) = w^T X，

其预测规则为

{
1    f(w,X) ≥ 0,
-1   否则。
}

损失函数是二分类错误：𝟙(f(w,X)Y ≤ 0)。感知机算法（Rosenblatt, 1957, 1962）是一种在线学习算法，它按顺序接收数据，如算法14.1所示。它是错误驱动的，也就是说，它仅在预测出错时才更新模型权重向量。该算法属于线性分类器家族。在许多应用中，需要手工设计线性特征。

```
Algorithm 14.1 Perceptron Algorithm
Input: Sequence (X1,Y1),..., (XT,YT)
Output: w_s
1 Let w0 = 0
2 for t = 1,2,...,T do
3   Observe Xt and predict label sign(w_{t-1}^T Xt)
4   Observe Yt and compute mistake 𝟙(w_{t-1}^T Xt Yt ≤ 0)
5   if w_{t-1}^T Xt Yt > 0 then
6     // No mistake
7     Let wt = w_{t-1}
8   else
9     // A mistake is observed
10    Let wt = w_{t-1} + Xt Yt
11 Randomly pick s from 0 to T − 1
Return: w_s
```

请注意，感知机算法中随机选择返回预测器的目的是为了在线到批量转换，我们稍后将对此进行讨论。下面，我们首先给出感知机的错误界。

### 定理 14.1

考虑算法14.1中的感知机算法。设 γ > 0 和权重向量 w_* 使得对所有 t 有

$$w_*^\top X_t Y_t \ge \gamma.$$

那么我们有如下错误界：

$$\sum_{t=1}^T \mathbf{1}(w_{t-1}^\top X_t Y_t \le 0) \le \frac{\|w_*\|_2^2 \sup\{\|X_t\|_2^2\}}{\gamma^2}.$$

证明 设 M = sup_t ||X_t||_2，令 η = γ / M^2。假设在时间步 t 出现一次错误，则有

$$(\eta w_{t-1} - w_*)^\top X_t Y_t \le 0 - w_*^\top X_t Y_t \le -\gamma.$$

这意味着

$$\|\eta w_t - w_*\|_2^2 = \|\eta w_{t-1} + \eta X_t Y_t - w_*\|_2^2 = \|\eta w_{t-1} - w_*\|_2^2 + 2\eta(\eta w_{t-1} - w_*)^\top X_t Y_t + \eta^2 \|X_t\|_2^2 \le \|\eta w_{t-1} - w_*\|_2^2 - 2\eta\gamma + \eta^2 M^2 \le \|\eta w_{t-1} - w_*\|_2^2 - \frac{\gamma^2}{M^2}.$$

还要注意，如果在时间步 t 没有错误，则 $\|\eta w_t - w_*\|_2^2 = \|\eta w_{t-1} - w_*\|_2^2$。因此，将 t = 1 到 t = T 求和，我们得到

$$0 \le \|\eta w_t - w_*\|_2^2 \le \|\eta w_0 - w_*\|_2^2 - \frac{\gamma^2}{M^2} k,$$

其中 k 是错误次数。这便推出了该界限。

感知机的错误界可以被看作第9章中讨论的间隔界的在线版本，在那里经验过程被用来为ERM方法获得类似的间隔界。分析ERM方法所需的技术要复杂得多。

每个 $x$ 的预测类别为

$$\hat{y}(w,x) \in \arg\max_{\ell} [w^{\top} \psi(x,\ell)],$$

并且真实标签为 $y$ 的样本 $x$ 的错误（或失误）为

$$\mathbb{1}(\hat{y}(w,x) \neq y).$$

### 算法14.2 多类别感知机算法

```
**Input:** Sequence $(X_1,Y_1),\dots,(X_T,Y_T)$
**Output:** $w_s$
1 Let $w_0 = 0$
2 **for** $t = 1,2,\dots,T$ **do**
3   Observe $X_t$ and predict label $\hat{Y}_t \in \arg\max_{\ell}\{w_{t-1}^{\top}\psi(X_t,\ell)\}$
4   Observe $Y_t$ and compute mistake $\mathbb{1}(\hat{Y}_t \neq Y_t)$
5   **if** $\hat{Y}_t == Y_t$ **then**
6     // No mistake
7     Let $w_t = w_{t-1}$
8   **else**
9     // A mistake is observed
10    Let $w_t = w_{t-1} + [\psi(X_t,Y_t) - \psi(X_t,\hat{Y}_t)]$
11 Randomly pick $s$ from $0$ to $T-1$
**Return:** $w_s$
```

### 定理 14.2

考虑算法14.2。我们有如下错误界：

$$\sum_{t=1}^{T} \mathbb{1}(\hat{Y}_t \neq Y_t) \le \inf_{\gamma>0,w} \left[ \sum_{t=1}^{T} 2\max\left(0,1-\gamma^{-1}\min_{\ell\neq Y_t} w^{\top}[\psi(X_t,Y_t)-\psi(X_t,\ell)]\right) \right.$$ 
$$+ \frac{\|w\|_2^2 \sup\{\|\psi(X_t,Y_t)-\psi(X_t,Y_\ell)\|_2^2\}}{\gamma^2} \right].$$

*证明* 证明过程与二分类情况基本相同。给定任意 $\gamma > 0$ 和 $w$，令 $\psi_t = \psi(X_t,Y_t) - \psi(X_t,\hat{Y}_t)$，$M = \sup\{\|\psi_t\|_2\}$，$\eta = \gamma/M^2$。假设在时间步 $t$ 出现一次错误，则有 $\hat{Y}_t \neq Y_t$，且 $w_{t-1}^{\top}\psi_t \le 0$。这意味着

$$(\eta w_{t-1} - w_*)^{\top}\psi_t \le 0 - w_*^{\top}\psi_t \le \max(0,\gamma - w_*^{\top}\psi_t) - \gamma.$$

因此通过取

$$\|\eta w_t - w_*\|_2^2 = \|\eta w_{t-1} + \eta\psi_t - w_*\|_2^2$$
$$= \|\eta w_{t-1} - w_*\|_2^2 + 2\eta(\eta w_{t-1} - w_*)^{\top}\psi_t + \eta^2\|\psi_t\|_2^2$$
$$\le \|\eta w_{t-1} - w_*\|_2^2 + 2\eta\max(0,\gamma - w_*^{\top}\psi_t) - 2\eta\gamma + \eta^2 M^2$$
$$\le \|\eta w_{t-1} - w_*\|_2^2 + 2\eta\max(0,\gamma - w_*^{\top}\psi_t) - \frac{\gamma^2}{M^2}.$$

### 命题 14.3

考虑算法14.2，其中 s 从 0 到 T − 1 中均匀随机选择。如果 Zₜ = (Xₜ, Yₜ) ∼ 𝒟 是独立同分布的观测值，则我们有

$$\mathbb{E}_{S_{T-1}}\,\mathbb{E}_{Z\sim\mathcal{D}}\mathbf{1}(\hat{y}(w_s,X)\ne Y) \\ \le \inf_{\gamma>0,w}\left[2\mathbb{E}_{Z\sim\mathcal{D}}\max\left(0,1-\gamma^{-1}\min_{\ell\neq Y_t}w^\top[\psi(X,Y)-\psi(X,\ell)]\right)+\frac{\lVert w\rVert_2^2\sup\{\lVert\psi(X,Y)-\psi(X,Y')\rVert_2^2\}}{\gamma^2T}\right].$$

其中预测规则 $\hat{y}(w,x)\in\arg\max_{\ell}w^\top\psi(x,\ell)$ 与算法14.2一致。

**证明** 我们只需注意

$$\mathbb{E}_{S_{T-1}}\sum_{t=1}^{T}\mathbb{E}_{Z\sim\mathcal{D}}\mathbf{1}(\hat{y}(w_{t-1},X)\ne Y)=\mathbb{E}_{S_T}\sum_{t=1}^{T}\mathbf{1}(\hat{y}(w_{t-1},X_t)\ne Y_t),$$

且

$$\sum_{t=1}^{T}2\mathbb{E}_{Z\sim\mathcal{D}}\max\left(0,1-\gamma^{-1}\min_{\ell\neq Y_t}w^\top[\psi(X,Y)-\psi(X,\ell)]\right) \\ =\mathbb{E}_{S_T}\sum_{t=1}^{T}2\max\left(0,1-\gamma^{-1}\min_{\ell\neq Y_t}w^\top[\psi(X_t,Y_t)-\psi(X_t,\ell)]\right).$$

现在，直接应用定理14.2可得

$$\mathbb{E}_{S_{T-1}}\sum_{t=1}^{T}\mathbb{E}_{Z\sim\mathcal{D}}\mathbf{1}(\hat{y}(w_{t-1},X)\ne Y) \\ \le \inf_{\gamma>0,w}\left[2T\mathbb{E}_{Z\sim\mathcal{D}}\max\left(0,1-\gamma^{-1}\min_{\ell\neq Y_t}w^\top[\psi(X,Y)-\psi(X,\ell)]\right)+\frac{\lVert w\rVert_2^2\sup\{\lVert\psi(X,Y)-\psi(X,Y')\rVert_2^2\}}{\gamma^2}\right].$$

这就得到了所期望的结果。□

从第13章可知，我们还可以进一步使用鞅尾概率界来获得如下形式的高概率结果：在 $S_T$ 上至少以概率 $1-\delta$ 有，

$$\sum_{t=1}^{T}\mathbb{E}_{Z\sim\mathcal{D}}\phi(w_{t-1},Z)\le\sum_{t=1}^{T}\phi(w_{t-1},Z_t)+\epsilon(\delta). \tag{14.3}$$

我们可以将该界限与(14.2)结合，得到对于从 0 到 $T-1$ 中均匀选取的随机估计量 $s$ 的如下概率界。在 $S_T$ 上至少以概率 $1-\delta$ 有，

$$\mathbb{E}_s\,\mathbb{E}_{Z\sim\mathcal{D}}\phi(w_s,Z)\le\frac{\epsilon(\delta)+\epsilon(S_T)}{T}.$$

### 命题 14.4

考虑算法14.1，其中 s 从 0 到 $T-1$ 中均匀抽取。假设对所有 $Z = (X,Y)$ 都有 $w_*^\top XY \ge \gamma > 0$。如果 $Z_t = (X_t,Y_t) \sim \mathcal{D}$，则至少以概率 $1-\delta$ 有，

$$\mathbb{E}_s \mathbb{E}_{Z \sim \mathcal{D}} \mathbb{1}(\hat{y}(w_s,X) \neq Y)$$
$$\le \inf_{\lambda>0} \left[ \frac{\lambda}{1-e^{-\lambda}} \frac{\|w_*\|_2^2 \sup_X \|X\|_2^2}{\gamma^2 T} + \frac{\ln(1/\delta)}{(1-e^{-\lambda})T} \right].$$

*证明* 令

$$\{\xi_i = \mathbb{1}(w_{i-1}^\top X_i Y_i \le 0) : i = 1,2,\dots,n\}$$

为一列随机变量。定理13.5表明，对任意 $\lambda > 0$，至少以概率 $1-\delta$ 有，

$$\frac{1}{T} \sum_{i=1}^{T} \mathbb{E}_{(X_i,Y_i)\sim\mathcal{D}} \xi_i \le \frac{\lambda}{1-e^{-\lambda}} \frac{1}{T} \sum_{i=1}^{T} \xi_i + \frac{\ln(1/\delta)}{(1-e^{-\lambda})T}.$$

还要注意，定理14.1中的错误界蕴含着

$$\sum_{i=1}^{T} \xi_i \le \frac{\|w_*\|_2^2 \sup \{\|X\|_2^2\}}{\gamma^2}.$$

由于 $\mathbb{E}_{(X,Y)\sim\mathcal{D}} \mathbb{1}(w_{i-1}^\top XY \le 0) = \mathbb{E}_{(X_i,Y_i)\sim\mathcal{D}} \xi_i$，我们便得到了所期望的结果。

## 14.4 在线凸优化

我们可以将感知机算法的分析扩展到一般的凸损失函数，从而得到所谓的在线凸优化，该概念由Zinkevich (2003)引入机器学习。在线凸优化的一种一般一阶算法，我们称之为在线梯度下降，见算法14.3。其分析见定理14.5。

### 算法14.3 在线梯度下降

**输入：** 定义在 $\Omega$ 上的损失函数序列 $\ell_1,\dots,\ell_T$
**输出：** $\hat{w}$
1 令 $w_0 = 0$
2 **对于** $t = 1,2,\dots,T$ **执行**
3   观察损失 $\ell_t(w_{t-1})$
4   令 $\tilde{w}_t = w_{t-1} - \eta_t \nabla \ell_t(w_{t-1})$
5   令 $w_t = \arg\min_{w \in \Omega} \|w - \tilde{w}_t\|_2^2$
6 令 $\hat{w} = T^{-1} \sum_{t=1}^{T} w_{t-1}$ 或 $\hat{w} = w_s$，其中 $s$ 从 0 到 $T-1$ 中随机选取
**返回：** $\hat{w}$

