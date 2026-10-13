
其中 $p(\boldsymbol{\theta})$ 为相关先验 PDF。我们已从符号中省略了对 $\mathcal{X}$ 的依赖，以使其看起来更简洁。我们强调输入集合 $\mathcal{X} = \{\boldsymbol{x}_1, \dots, \boldsymbol{x}_N\}$ 被视为固定的，因此与输出随机变量 $\boldsymbol{y}$ 相关的所有随机性均源于噪声源。假设先验和条件 PDF 均为高斯分布，^([^(85)](#fn85))

$$
p(\boldsymbol{\theta}) = \mathcal{N}(\boldsymbol{\theta}|\boldsymbol{\theta}_0, \Sigma_\theta) \tag{12.8}
$$

以及

$$
p(\boldsymbol{y}|\boldsymbol{\theta}) = \mathcal{N}(\boldsymbol{y}|\Phi\boldsymbol{\theta}, \Sigma_\eta), \tag{12.9}
$$

其中已使用了公式 [(12.2)](#Chp012_583-634_B9780443292385000184.xhtml#deq4) 和 [(12.3)](#Chp012_583-634_B9780443292385000184.xhtml#deq5)，后验 $p(\boldsymbol{\theta}|\boldsymbol{y})$ 也呈高斯分布，其均值向量为

$$
\boldsymbol{\mu}_{\theta|y} := \mathbb{E}[\boldsymbol{\theta}|\boldsymbol{y}] = \boldsymbol{\theta}_0 + (\Sigma_\theta^{-1} + \Phi^T \Sigma_\eta^{-1} \Phi)^{-1} \Phi^T \Sigma_\eta^{-1} (\boldsymbol{y} - \Phi\boldsymbol{\theta}_0). \tag{12.10}
$$

因为高斯分布的最大值与其均值重合，所以我们有

$$
\widehat{\boldsymbol{\theta}}_{\text{MAP}} = \mathbb{E}[\boldsymbol{\theta}|\boldsymbol{y}]. \tag{12.11}
$$

在本章附录中，提供了公式 [(12.10)](#Chp012_583-634_B9780443292385000184.xhtml#deq13) 的解析证明。^([^(86)](#fn86))

$$
\widehat{\boldsymbol{\theta}}_{\text{MAP}} = (\lambda I + \Phi^T \Phi)^{-1} \Phi^T \boldsymbol{y}, \tag{12.12}
$$
