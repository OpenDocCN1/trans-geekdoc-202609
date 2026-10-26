

## GANs：ADA 的一种变体
- 将源域的特性迁移到目标域
- 源域：例如真实图像，$y = 1$
- 目标域：例如生成图像，$y = 0$

![](img/cb490ed30bca4eda5fbba81c52a2c173_136_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_136_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_137_0.png)

## GANs：ADA 的一种变体
- 在 $x \sim p_\theta(x\mid y)$ 上的隐式分布

$$p_\theta(x\mid y)=\begin{cases}p_{g_\theta}(x) & y=0 \quad \text{（生成图像的分布）}\\p_{data}(x) & y=1. \quad \text{（真实图像的分布）}\end{cases}$$

- $x \sim p_{g_\theta}(x) \Longleftrightarrow x=G_\theta(z),\ z\sim p(z\mid y=0)$
- $x \sim p_{data}(x)$
  - $z$ 的编码空间是退化的
  - 直接从数据中采样

## GANs：新的表述
- 再次将 GAN 目标改写为“变分-EM”形式
- 回顾：传统表述：
  $$\max_{\phi} \mathcal{L}_{\phi} = \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_{\phi}(\boldsymbol{x}))] + \mathbb{E}_{\boldsymbol{x}\sim p_{data}(\boldsymbol{x})}[\log D_{\phi}(\boldsymbol{x})]$$
  $$\max_{\theta} \mathcal{L}_{\theta} = \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_{\phi}(\boldsymbol{x})] + \mathbb{E}_{\boldsymbol{x}\sim p_{data}(\boldsymbol{x})}[\log(1 - D_{\phi}(\boldsymbol{x}))]$$
  $$= \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_{\phi}(\boldsymbol{x})]$$
- 用新形式重写：
  $$\max_{\phi} \mathcal{L}_{\phi} = \mathbb{E}_{p_{\theta}(\boldsymbol{x}|y)p(y)}[\log q_{\phi}(y|\boldsymbol{x})]$$
  $$\max_{\theta} \mathcal{L}_{\theta} = \mathbb{E}_{p_{\theta}(\boldsymbol{x}|y)p(y)}[\log q_{\phi}^{r}(y|\boldsymbol{x})]$$
- 与 ADA 完全相同！
- 与变分 EM 的对应关系也相同！

![](img/cb490ed30bca4eda5fbba81c52a2c173_138_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_141_0.png)

## GANs：最小化 KLD
- 与变分 EM 中一样，我们可以进一步将其改写为 **最小化 KLD** 的形式，以更深入地理解优化问题。

- 对于 $p_{\theta}(x|y)$ 在点 $(\theta=\theta_0,\phi=\phi_0)$ 的每一步优化，令
  - $p(y)$：均匀分布
  - $p_{\theta=\theta_0}(x)=\mathbb{E}_{p(y)}[p_{\theta=\theta_0}(x|y)]$：$x$ 的先验分布
  - $q^r(x|y)\propto q^r_{\phi=\phi_0}(y|x)p_{\theta=\theta_0}(x)$：$x$ 的后验分布

- **引理 1：** 在 $\theta_0$ 处 $\theta$ 的更新满足

$$
\left.\nabla_{\theta}\left[-\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q^r_{\phi=\phi_0}(y|x)\right]\right]\right|_{\theta=\theta_0}
=
\left.\nabla_{\theta}\left[\mathbb{E}_{p(y)}\left[KL\left(p_{\theta}(x|y)\|q^r(x|y)\right)-JSD\left(p_{\theta}(x|y=0)\|p_{\theta}(x|y=1)\right)\right]\right]\right|_{\theta=\theta_0}
$$

- KL：KL 散度
- JSD：詹森-香农散度

## GANs：最小化 KLD

![](img/cb490ed30bca4eda5fbba81c52a2c173_142_0.png)

- *引理 1*：在 θ₀ 处 θ 的更新满足
  ∇_θ[ - 𝔼_{p_θ(x|y)p(y)}[log q^r_{φ=φ₀}(y|x)] ]|_{θ=θ₀} =
  ∇_θ[ 𝔼_{p(y)}[KL(p_θ(x|y)||q^r(x|y))] - JSD(p_θ(x|y=0)||p_θ(x|y=1)) ]|_{θ=θ₀}
- 与变分推断的联系
  - 将 x 视为潜变量，y 视为可见变量
  - p_{θ=θ₀}(x)：先验分布
  - q^r(x|y) ∝ q^r_{φ=φ₀}(y|x)p_{θ=θ₀}(x) ：后验分布
  - p_θ(x|y)：变分分布
    - 摊销推断：更新模型参数 θ
- 暗示了与 VAE 的关系，我们稍后会探讨

## GANs：最小化 KLD
$p_{\theta=\theta_0}(\mathbf{x}|y=1)=p_{data}(\mathbf{x})$  $p_{\theta=\theta_0}(\mathbf{x}|y=0)=p_{g\,\theta=\theta_0}(\mathbf{x})$  $q^r(\mathbf{x}|y=0)$  $p_{\theta=\theta^{new}}(\mathbf{x}|y=0)=p_{g\,\theta=\theta^{new}}(\mathbf{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_143_0.png)

- 最小化 KLD 推动 $p_{g_\theta}(\mathbf{x})$ 趋向 $p_{data}(\mathbf{x})$  
  - 根据定义：$p_{\theta=\theta_0}(\mathbf{x}) = E_{p(y)}[p_{\theta=\theta_0}(\mathbf{x}|y)] = (p_{g\,\theta=\theta_0}(\mathbf{x}) + p_{data}(\mathbf{x}))/2$  
  - KL$(p_\theta(x|y=1)||q^r(x|y=1)) = KL(p_{data}(x)||q^r(x|y=1))$：常数，没有自由参数  
  - KL$(p_\theta(x|y=0)||q^r(x|y=0)) = KL(p_{g_\theta}(x)||q^r(x|y=0))$：参数 $\theta$ 需要优化  
    - $q^r(\mathbf{x}|y=0) \propto q^r_{\phi=\phi_0}(y=0|\mathbf{x})p_{\theta=\theta_0}(\mathbf{x})$  
      - 被视为 $p_{g\,\theta=\theta_0}(\mathbf{x})$ 和 $p_{data}(\mathbf{x})$ 的混合  
      - 混合权重由 $q^r_{\phi=\phi_0}(y=0|\mathbf{x})$ 导出  
  - 推动 $p_{g_\theta}(\mathbf{x}|y)$ 趋向 $p_{g\,\theta=\theta_0}(\mathbf{x})$ 和 $p_{data}(\mathbf{x})$ 的混合  
    - $\Rightarrow$ 推动 $p_{g_\theta}(\mathbf{x})$ 趋向 $p_{data}(\mathbf{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_143_1.png)

## GANs：最小化 KLD

![](img/cb490ed30bca4eda5fbba81c52a2c173_144_0.png)

p_{θ=θ₀}(x|y = 1) = p_{data}(x)

p_{θ=θ₀}(x|y = 0) = p_{gθ=θ₀}(x)

q^r(x|y = 0)

缺失的模式

p_{θ=θ^{new}}(x|y = 0) = p_{gθ=θ^{new}}(x)

- GAN 的模式缺失现象
  - KLD 的不对称性
    - 将 $p_\theta(x|y = 0)$ 集中于 $q^r(x|y)$ 的大模式上
      $\Rightarrow p_{g\theta}(x)$ 会缺失 $p_{data}(x)$ 的某些模式
  - JSD 的对称性
  - 不影响模式缺失的行为

KL($p_{g\theta}(x)||q^r(x|y = 0)$)
= $\int p_{g\theta}(x) \log \frac{p_{g\theta}(x)}{q^r(x|y = 0)} dx$

- 在 $q^r(x|y = 0)$ 较小的 $x$ 空间区域中，除非 $p_{g\theta}(x)$ 也很小，否则 KLD 会产生较大的正贡献
- $\Rightarrow p_{g\theta}(x)$ 倾向于避开 $q^r(x|y = 0)$ 较小的区域

![](img/cb490ed30bca4eda5fbba81c52a2c173_147_0.png)

变分 EM

作为生成的推断

GANs

两个域中的
有效 z 空间

ADA

## GAN 的变体：InfoGAN
- GAN 不提供根据数据推断编码 **z** 的功能
- InfoGAN [Chen et al., 2016]
- 引入带参数 $\boldsymbol{\eta}$ 的推断模型 $Q_{\eta}(\mathbf{z}|\mathbf{x})$
- 通过额外推断 **z** 来增强 GAN 的目标

$\max_D \mathcal{L}_D = \mathbb{E}_{\mathbf{x}\sim p_{data}(\mathbf{x})}[\log D(\mathbf{x})] + \mathbb{E}_{\mathbf{x}\sim G(\mathbf{z}),\mathbf{z}\sim p(\mathbf{z})}[\log(1 - D(\mathbf{x}))],$
$\max_{G,Q} \mathcal{L}_{G,Q} = \mathbb{E}_{\mathbf{x}\sim G(\mathbf{z}),\mathbf{z}\sim p(\mathbf{z})}[\log D(\mathbf{x}) + \log Q(\mathbf{z}|\mathbf{x})].$

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_2.png)

## InfoGAN：新的表述
- 定义条件分布 $q_\eta(z|x,y)$

  - $q_\eta(z|x,y=1)$ 是固定的，没有需要学习的自由参数

    - 因为 GAN 假设真实数据的编码空间是退化的

  - 参数 $\eta$ 仅与 $q_\eta(z|x,y=0)$ 相关

- 用新形式重写：

$$\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(x|y)p(y)}\left[\log q_\eta(z|x,y)q_\phi(y|x)\right]$$

$$\max_{\theta,\eta} \mathcal{L}_{\theta,\eta} = \mathbb{E}_{p_\theta(x|y)p(y)}\left[\log q_\eta(z|x,y)q_\phi^{(r)}(y|x)\right]$$

![](img/cb490ed30bca4eda5fbba81c52a2c173_149_0.png)

## GANs 与 InfoGAN

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_0.png)

编码 数据/生成

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_1.png)

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_φ(y|x)]
max_θ L_θ = 𝔼_{p_θ(x|y)p(y)} [log q_φ^r(y|x)]

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_2.png)

编码 数据/生成

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_3.png)

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ(y|x)]
max_{θ,η} L_{θ,η} = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ^r(y|x)]

