
# 数学推导文档

## 推导过程

### 后验方差 $\widetilde{\beta}_t$

$$
\widetilde{\beta}_t = \frac{1 - \overline{\alpha}_{t - 1}}{1 - \overline{\alpha}_t}\beta_t
$$

### 后验均值 $\widetilde{\mu}(x_t, x_0)$ 的逐步化简

$$
\widetilde{\mu}(x_t, x_0) = \left( \frac{\alpha_t}{\beta_t} + \frac{1}{1 - \overline{\alpha}_{t - 1}} \right)^{-1} \left( \frac{\sqrt{\alpha_t}}{\beta_t}x_t + \frac{\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_{t - 1}}x_0 \right)
$$

$$
\widetilde{\mu}(x_t, x_0) = \left( \frac{\sqrt{\alpha_t}}{\beta_t}x_t + \frac{\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_{t - 1}}x_0 \right) \frac{1 - \overline{\alpha}_{t - 1}}{1 - \overline{\alpha}_t}\beta_t
$$

$$
\widetilde{\mu}(x_t, x_0) = \frac{\sqrt{\alpha_t}(1 - \overline{\alpha}_{t - 1})}{1 - \overline{\alpha}_t}x_t + \frac{\beta_t\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_t}x_0
$$

$$
\widetilde{\mu}(x_t, x_0) = \frac{\sqrt{\alpha_t}(1 - \overline{\alpha}_{t - 1})}{1 - \overline{\alpha}_t}x_t + \frac{\beta_t\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_t} \frac{1}{\sqrt{\overline{\alpha}_t}} \left( x_t - \varepsilon\sqrt{1 - \overline{\alpha}_t} \right)
$$

$$
\widetilde{\mu}(x_t, x_0) = \frac{\sqrt{\alpha_t}(1 - \overline{\alpha}_{t - 1})}{1 - \overline{\alpha}_t}x_t + \frac{\beta_t\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_t} \frac{x_t}{\sqrt{\overline{\alpha}_t}} - \frac{\beta_t\sqrt{\overline{\alpha}_{t - 1}}}{1 - \overline{\alpha}_t} \frac{\varepsilon}{\sqrt{\overline{\alpha}_t}}\sqrt{1 - \overline{\alpha}_t}
$$

$$
\widetilde{\mu}(x_t, x_0) = \left( \frac{\sqrt{\alpha_t}(1 - \overline{\alpha}_{t - 1})}{1 - \overline{\alpha}_t} + \frac{1}{\sqrt{\alpha_t}} \frac{\beta_t}{1 - \overline{\alpha}_t} \right)x_t - \frac{\beta_t}{\sqrt{1 - \overline{\alpha}_t}} \frac{\varepsilon}{\sqrt{\alpha_t}}
$$

$$
\widetilde{\mu}(x_t, x_0) = \frac{1}{\sqrt{\alpha_t}} \left( \frac{(\alpha_t - \overline{\alpha}_t)}{1 - \overline{\alpha}_t} + \frac{1 - \alpha_t}{1 - \overline{\alpha}_t} \right)x_t - \frac{\beta_t}{\sqrt{1 - \overline{\alpha}_t}} \frac{\varepsilon}{\sqrt{\alpha_t}}
$$

$$
\widetilde{\mu}(x_t, x_0) = \frac{1}{\sqrt{\alpha_t}} \left( x_t - \frac{1 - \alpha_t}{\sqrt{1 - \overline{\alpha}_t}}\varepsilon \right)
$$

## 变分下界损失 $L_{VLB}$

### 变分下界损失 $L_{VLB}$

$$
L_{VLB} = - \int{q(x_0)q(x_{1:T}\mid x_0)}\log \frac{p_{\theta}(x_{0:T})}{q(x_{1:T}\mid x_0)}dx_{0:T}
$$

$$
L_{VLB} = \mathbb{E}_{q(x_{0:T})}\left[ \log \frac{q(x_{1:T} \mid x_0)}{p_{\theta}(x_{0:T})} \right] = \mathbb{E}_{q}\left[ \log \frac{\prod_{t=1}^{T}q(x_t \mid x_{t-1})}{p_{\theta}(x_T)\prod_{t=1}^{T}p_{\theta}(x_{t-1} \mid x_t)} \right]
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \log \frac{\prod_{t=1}^{T}q(x_t \mid x_{t-1})}{\prod_{t=1}^{T}p_{\theta}(x_{t-1} \mid x_t)} \right] = \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=1}^{T} \log \frac{q(x_t \mid x_{t-1})}{p_{\theta}(x_{t-1} \mid x_t)} \right]
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=2}^{T} \log \frac{q(x_t \mid x_{t-1})}{p_{\theta}(x_{t-1} \mid x_t)} \right] + \log \frac{q(x_1\mid x_0)}{p_{\theta}(x_0\mid x_1)}
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=2}^{T} \log \frac{q(x_{t-1} \mid x_t)}{p_{\theta}(x_{t-1} \mid x_t)} \frac{q(x_t \mid x_0)}{q(x_{t-1} \mid x_0)} + \log \frac{q(x_1\mid x_0)}{p_{\theta}(x_0\mid x_1)} \right] \text{ 根据公式 } (9.4)
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=2}^{T} \log \frac{q(x_{t-1} \mid x_t, x_0)}{p_{\theta}(x_{t-1} \mid x_t)} \frac{q(x_t \mid x_0)}{q(x_{t-1} \mid x_0)} + \log \frac{q(x_1 \mid x_0)}{p_{\theta}(x_0 \mid x_1)} \right]
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=2}^{T} \log \frac{q(x_{t-1} \mid x_t, x_0)}{p_{\theta}(x_{t-1} \mid x_t)} + \sum_{t=2}^{T} \log \frac{q(x_t \mid x_0)}{q(x_{t-1} \mid x_0)} + \log \frac{q(x_1 \mid x_0)}{p_{\theta}(x_0 \mid x_1)} \right]
$$

$$
= \mathbb{E}_{q}\left[ -\log p_{\theta}(x_T) + \sum_{t=2}^{T} \log \frac{q(x_{t-1} \mid x_t, x_0)}{p_{\theta}(x_{t-1} \mid x_t)} + \log \prod_{t=2}^{T} \frac{q(x_t \mid x_0)}{q(x_{t-1} \mid x_0)} + \log \frac{q(x_1 \mid x_0)}{p_{\theta}(x_0 \mid x_1)} \right]
$$

### 数学推导过程

```math
= \mathbb{E}_{q}\left\lbrack {-\log p_{\theta}\left( x_{T} \right) + \sum\limits_{t = 2}^{T}{\log}\frac{q\left( {x_{t - 1} \mid x_{t},x_{0}} \right)}{p_{\theta}\left( {x_{t - 1} \mid x_{t}} \right)} + \log \frac{q\left( {x_{T} \mid x_{0}} \right)}{q\left( {x_{1} \mid x_{0}} \right)} + \log \frac{q\left( {x_{1} \mid x_{0}} \right)}{p_{\theta}\left( {x_{0} \mid x_{1}} \right)}} \right\rbrack
```

```math
= \mathbb{E}_{q}\left\lbrack {-\log p_{\theta}\left( x_{T} \right) + \sum\limits_{t = 2}^{T}{\log}\frac{q\left( {x_{t - 1} \mid x_{t},x_{0}} \right)}{p_{\theta}\left( {x_{t - 1} \mid x_{t}} \right)} + \log \frac{q\left( {x_{T} \mid x_{0}} \right)}{p_{\theta}\left( {x_{0} \mid x_{1}} \right)}} \right\rbrack
```

```math
= \mathbb{E}_{q}\left\lbrack {\log \frac{q\left( {x_{T} \mid x_{0}} \right)}{p_{\theta}\left( x_{T} \right)} + \sum\limits_{t = 2}^{T}{\log}\frac{q\left( {x_{t - 1} \mid x_{t},x_{0}} \right)}{p_{\theta}\left( {x_{t - 1} \mid x_{t}} \right)} - \log p_{\theta}(x_{0}\mid x_{1})} \right\rbrack
```

```math
= \int q\left( x_{0:T} \right)\log \frac{q\left( {x_{T} \mid x_{0}} \right)}{p_{\theta}\left( x_{T} \right)}dx_{0:T} + \sum\limits_{t = 2}^{T}{\mathbb{E}_{q}\left\lbrack {\log \frac{q\left( {x_{t - 1} \mid x_{t},x_{0}} \right)}{p_{\theta}\left( {x_{t - 1} \mid x_{t}} \right)}} \right\rbrack} - \mathbb{E}_{q}\left\lbrack {\log p_{\theta}\left( x_{0}\mid x_{1} \right)} \right\rbrack
```

```math
= D_{KL}(q(x_{T}\mid x_{0})\parallel p_{\theta}\left( x_{T} \right)) + \sum\limits_{t = 2}^{T}{D_{KL}\left( q\left( x_{t - 1}\mid x_{t},x_{0} \right)\parallel p_{\theta}\left( x_{t - 1}\mid x_{t} \right) \right)} - \mathbb{E}_{q}\left\lbrack {\log p_{\theta}\left( x_{0}\mid x_{1} \right)} \right\rbrack
```

```math
= L_{T} + \sum\limits_{t = 2}^{T}L_{t - 1} + L_{0}
```

## 附录

### J 避免 FAISS 问题的项目 11.3.1 改进版本

![](img/bk978-0-7503-6244-3app1uf26_pr.gif)

### K 用于乐高 3D 场景合成的 Tiny NeRF 代码

![](img/bk978-0-7503-6244-3app1uf21_pr.gif)

![](img/bk978-0-7503-6244-3app1uf22_pr.gif)

![](img/bk978-0-7503-6244-3app1uf23_pr.gif)

![](img/bk978-0-7503-6244-3app1uf24_pr.gif)

![](img/bk978-0-7503-6244-3app1uf25_pr.gif)
