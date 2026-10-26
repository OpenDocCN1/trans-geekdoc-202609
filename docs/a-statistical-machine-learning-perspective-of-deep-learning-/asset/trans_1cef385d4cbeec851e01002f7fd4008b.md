
## 生成对抗网络 (GANs)
- [Goodfellow et al., 2014]
- 生成模型 $x = G_\theta(z),\ z \sim p(z)$
  - 将噪声变量 $z$ 映射到数据空间 $x$
  - 定义 $x$ 上的 *隐式分布*：$p_{g_\theta}(x)$
    - 一个模拟数据 $x$ 的随机过程
    - 难以评估似然
- 判别器 $D_\phi(x)$
  - 输出 $x$ 来自数据而非生成器的概率
- 没有显式的推理模型
- 与像 VAE 这样具有推理网络的先前模型没有明显联系
  - 我们稍后将建立 GANs 与 VAEs 之间的形式化联系

## 生成对抗网络 (GANs)
- 学习
  - 训练 $G$ 以欺骗判别器
  - 当 $D$ 过强时，原始损失会遭受梯度消失
  - 实践中改用以下公式
    $\max_G \mathcal{L}_G = \mathbb{E}_{\boldsymbol{x}\sim G(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z})} [\log D(\boldsymbol{x})]$

![](img/cb490ed30bca4eda5fbba81c52a2c173_121_0.png)

[图源自：Kim 的幻灯片]

![](img/cb490ed30bca4eda5fbba81c52a2c173_124_0.png)

## 深度生成模型动物园
- 变分自编码器 (VAEs) [Kingma & Welling, 2014]
  - 对抗自编码器 [Makhzani et al., 2015]
  - 重要性加权自编码器 [Burda et al., 2015]
  - 隐式变分自编码器 [Mescheder et al., 2017]
- 生成对抗网络 (GANs) [Goodfellow et al., 2014]
  - InfoGAN [Chen et al., 2016]
  - CycleGAN [Zhu et al., 2017]
  - Wasserstein GAN [Arjovsky et al., 2017]
- 自回归神经网络
  - PixelRNN / PixelCNN [Oord et al., 2016]
  - RNN（例如，用于语言建模）
- 生成矩匹配网络 (GMMNs) [Li et al., 2015; Dziugaite et al., 2015]
- 受限玻尔兹曼机 (RBMs) [Smolensky, 1986]

## 炼金术 vs 现代化学

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_2.png)

© Mind Juice Media Inc. 版权所有

## 大纲
- 深度生成模型进展概述
- 深度生成模型的理论背景
  - Wake sleep 算法
  - 变分自编码器
  - 生成对抗网络
- 深度生成模型的统一视角
  - 深度生成模型的新表述
  - 潜变量和显变量的对称建模

Z Hu, Z Yang, R Salakhutdinov, E Xing,
“On Unifying Deep Generative Models”, arxiv 1706.00550

## 对抗域适应 (ADA)
- 让我们从 ADA 开始
  - 对抗方法在域适应上的应用
  - 我们随后展示 GANs 可以被视为 ADA 的特例
  - 元素对应关系：

| 元素 | GANs | ADA |
|---|---|---|
| *x* | 数据/生成 | 特征 |
| *z* | 代码向量 | 源/目标域数据 |
| *y* | 真/假指示器 | 源/目标域指示器 |

![](img/cb490ed30bca4eda5fbba81c52a2c173_128_0.png)

## ADA：传统表述
- 训练 $D_\phi$ 以区分域

$\max_\phi \mathcal{L}_\phi = \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log D_\phi(\boldsymbol{x})] + \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_\phi(\boldsymbol{x}))]$

- 训练 $G_\theta$ 以欺骗 $D_\phi$

$\max_\theta \mathcal{L}_\theta = \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log(1 - D_\phi(\boldsymbol{x}))] + \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_\phi(\boldsymbol{x})]$

## ADA：新表述
- 为了揭示与传统变分方法的联系，让我们以类似变分 EM 的格式重写目标
- $\boldsymbol{x}$ 上的隐式分布 $\boldsymbol{x} \sim p_\theta(\boldsymbol{x}|y)$
  $\boldsymbol{x} = G_\theta(\boldsymbol{z}), \ \boldsymbol{z} \sim p(\boldsymbol{z}|y)$
- 判别器分布 $q_\phi(y|\boldsymbol{x})$
  $q_\phi^r(y|\boldsymbol{x}) = q_\phi(1 - y|\boldsymbol{x})$
- 以新形式重写目标（在常数尺度因子范围内）
  $\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}[\log q_\phi(y|\boldsymbol{x})]$
  $\max_\theta \mathcal{L}_\theta = \mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}[\log q_\phi^r(y|\boldsymbol{x})]$
  - $\boldsymbol{z}$ 被封装在隐式分布 $p_\theta(\boldsymbol{x}|y)$ 中
    $\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(\boldsymbol{x}|y=0)p(y=0)}[\log q_\phi(y=0|\boldsymbol{x})] + \mathbb{E}_{p_\theta(\boldsymbol{x}|y=1)p(y=1)}[\log q_\phi(y=1|\boldsymbol{x})]$
    $= \frac{1}{2}\mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_\phi(\boldsymbol{x}))] + \frac{1}{2}\mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log D_\phi(\boldsymbol{x})]$
  - （忽略常数尺度因子 1/2）

![](img/cb490ed30bca4eda5fbba81c52a2c173_132_0.png)

## ADA：新表述
- 新表述

$$\max_{\phi}\mathcal{L}_{\phi}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}(y\mid x)\right]$$

$$\max_{\theta}\mathcal{L}_{\theta}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}^{r}(y\mid x)\right]$$

- 优化 $\theta$ 和 $\phi$ 之间唯一的 **区别**：$q$ 与 $q^{r}$

- 这就是 **对抗** 机制产生的所在

## ADA 与变分 EM
### 变分 EM
- **目标**
  - $$\max_{\phi}\mathcal{L}_{\phi,\theta}=\mathbb{E}_{q_{\phi}(z|x)}[\log p_{\theta}(x|z)]+KL\left(q_{\phi}(z|x)\|p(z)\right)$$
  - $$\max_{\theta}\mathcal{L}_{\phi,\theta}=\mathbb{E}_{q_{\phi}(z|x)}[\log p_{\theta}(x|z)]+KL\left(q_{\phi}(z|x)\|p(z)\right)$$
- θ 和 φ 共享单一目标
- 通过 $p(z)$ 的额外先验正则化

### ADA
- **目标**
  - $$\max_{\phi}\mathcal{L}_{\phi}=\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q_{\phi}(y|x)\right]$$
  - $$\max_{\theta}\mathcal{L}_{\theta}=\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q_{\phi}^{r}(y|x)\right]$$
- 两个目标
- 在博弈论视角下具有全局最优状态

## ADA 与变分 EM
### 变分 EM
- 目标
  max_φ L_{φ,θ} = E_{q_φ(z|x)}[log p_θ(x|z)] + KL(q_φ(z|x)||p(z))
  max_θ L_{φ,θ} = E_{q_φ(z|x)}[log p_θ(x|z)] + KL(q_φ(z|x)||p(z))
- θ 和 φ 共享单一目标
- 通过 p(z) 的额外先验正则化
- 重构项：最大化 x 的条件对数似然，使用生成分布 p_θ(x|z)，条件于由 q_φ(z|x) 推断的潜代码 z
- p_θ(x|z) 是生成模型
- q_φ(z|x) 是推理模型

### ADA
- 目标
  max_φ L_φ = E_{p_θ(x|y)p(y)}[log q_φ(y|x)]
  max_θ L_θ = E_{p_θ(x|y)p(y)}[log q_φ^r(y|x)]
- 两个目标
- 在博弈论视角下具有全局最优状态
- 目标：最大化 y（或 1 − y）的条件对数似然，使用分布 q_φ(y|x)，条件于由 p_θ(x|y) 推断的潜特征 x
- 将 q_φ(y|x) 解释为生成模型
- 将 p_θ(x|y) 解释为推理模型

## ADA：图形模型
定义：
- 实线箭头 ($x \to y$)：
  - 生成过程
- 虚线箭头 (y, z -> $x$)：
  - 推理
- 空心箭头 (z -> $x$)：
  - 确定性变换
  - 导致隐式分布
- 蓝色箭头 ($x \to y$)：
  - 对抗机制
  - 涉及 $q_\phi(y|\boldsymbol{x})$ 和 $q_\phi^r(y|\boldsymbol{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_135_0.png)

max$_\phi$ $\mathcal{L}_\phi$ = $\mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}$ [$\log q_\phi(y|\boldsymbol{x})$]
max$_\theta$ $\mathcal{L}_\theta$ = $\mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}$ [$\log q_\phi^r(y|\boldsymbol{x})$]

