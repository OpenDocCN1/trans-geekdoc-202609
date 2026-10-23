
其中 **H** 是负对数联合分布 $\log p(\mathcal{D}, \boldsymbol{\theta})$ 在 MAP 估计 $\hat{\boldsymbol{\theta}}_{\text{map}}$ 处计算的 Hessian 矩阵。我们可以看到，式 (7.201) 是对数似然加上若干惩罚项。如果我们采用均匀先验 $p(\boldsymbol{\theta}) \propto 1$，则可以去掉先验项，并将 MAP 估计替换为最大似然估计（MLE）$\hat{\boldsymbol{\theta}}$，从而得到

$$\log p(\mathcal{D}) \approx \log p(\mathcal{D}|\hat{\boldsymbol{\theta}}) - \frac{1}{2} \log |\mathbf{H}| \tag{7.202}$$

现在我们专注于近似 $\log |\mathbf{H}|$ 项，该项有时被称为 **Occam 因子**，因为它是模型复杂度（后验分布的体积）的一种度量。我们有 $\mathbf{H} = \sum_{i=1}^{N} \mathbf{H}_i$，其中 $\mathbf{H}_i = \nabla\nabla \log p(\mathcal{D}_i|\boldsymbol{\theta})$。让我们用固定的矩阵 $\hat{\mathbf{H}}$ 来近似每个 $\mathbf{H}_i$。于是有

$$\log |\mathbf{H}| = \log |N\hat{\mathbf{H}}| = \log(N^{D}|\hat{\mathbf{H}}|) = D \log N + \log |\hat{\mathbf{H}}| \tag{7.203}$$

其中 $D = \dim(\boldsymbol{\theta})$，并且我们假设 $\mathbf{H}$ 是满秩的。我们可以去掉 $\log |\hat{\mathbf{H}}|$ 项，因为它与 $N$ 无关，因此会被似然项淹没。将所有部分整合后，我们重新得到 BIC 得分

$$\log p(\mathcal{D}) \approx \log p(\mathcal{D}|\hat{\boldsymbol{\theta}}) - \frac{D}{2} \log N \tag{7.204}$$

然后我们可以将其乘以 -2，以与式 (7.199) 匹配。

### 7.6.5.2 赤池信息准则（Akaike information criterion）

**赤池信息准则** [Aka74] 对应使用如下形式的复杂度项

$$C(m) = 2 \times \text{dof}(m) \tag{7.205}$$

它对复杂模型的惩罚比 BIC 更轻。它可以从频率学派的视角推导得到。

### 7.6.5.3 广泛适用信息准则（WAIC）

AIC 和 BIC 的主要问题在于，模型的自由度可能很难计算，因为大多数参数高度相关，并且无法从似然中唯一识别。特别是，如果从参数到似然的映射不是一一对应的，那么该模型被称为**奇异统计模型**，因为相应的 Fisher 信息矩阵（附录 E.2）以及上面的 Hessian 矩阵 $\mathbf{H}$ 可能是奇异的（行列式为 0）。即使在这种奇异情况下也能有效工作的另一个准则是**广泛适用信息准则**（WAIC），也被称为 **Watanabe–Akaike 信息准则** [Wat10; Wat13]。

在 WAIC 中，我们用平均对数逐点预测密度（LPPD）替代偏差，得到

$$\text{LPPD}(m) = \sum_{n=1}^{N} \log \mathbb{E}[p(y_n|\mathcal{D}, m)] \approx \sum_{n=1}^{N} \log \left( \frac{1}{S} \sum_{s=1}^{S} p(y_n|\boldsymbol{\theta}_s, m) \right) \tag{7.206}$$

其中 $\boldsymbol{\theta}_s \sim p(\boldsymbol{\theta}|\mathcal{D}, m)$ 是后验样本。这一步将参数边缘化掉。此外，WAIC 使用下式近似复杂度项

$$C(m) = \sum_{n=1}^{N} \log \mathbb{V}[p(y_n|\mathcal{D}, m)] \approx \sum_{n=1}^{N} \log \left( \mathbb{V}\{p(y_n|\boldsymbol{\theta}_s, m) : s = 1, S\} \right) \tag{7.207}$$

最终准则为

$$\operatorname{WAIC}(m) = -2\operatorname{LPPD}(m) + 2C(m) \tag{7.208}$$

示例见图 21.18，其中我们用该方法选择高斯混合模型中的分量个数 $K$。

### 7.6.5.4 最小描述长度（MDL）

我们可以从信息论（第 6 章）的角度来思考如何给不同模型打分的问题。目标是让发送方将数据传达给接收方。首先，发送方需要指定使用哪一个模型 $m$；这需要占用 $C(m) = -\log p(m)$ 比特（见第 6.1 节）。然后，接收方可以通过计算 $\hat{\theta}_m$ 来拟合模型，从而大致重构数据。为了完美重构数据，发送方还需要发送模型无法解释的残差；这需要占用 $-L(m) = -\sum_n \log p(y_n \mid \hat{\theta}_m,m)$。总代价为 $J(m) = -L(m) + C(m)$。选择使 $J(m)$ 最小的模型被称为**最小描述长度**（**MDL**）原理。细节可参见例如 [HY01]。

### 7.6.6 贝叶斯假设检验

**假设检验**是模型选择的一种特殊情况，其中只有两个模型，通常称为**零假设** $M_0$ 和**备择假设** $M_1$。由于只有两个模型，方便起见，我们将**贝叶斯因子**定义为边际似然之比：

$$B_{1,0} \triangleq \frac{p(D\mid M_1)}{p(D\mid M_0)} = \frac{p(M_1\mid D)}{p(M_0\mid D)}\frac{p(M_1)}{p(M_0)} \tag{7.209}$$

（这类似于**似然比**，只是我们积分掉了参数，从而由于第 7.6.3 节所解释的贝叶斯奥卡姆剃刀效应，能够比较不同复杂度的模型。）如果 $B_{1,0} > 1$，则我们更偏好模型 1，否则更偏好模型 0。

当然，$B_{1,0}$ 可能只是略大于 1。在这种情况下，我们并不太确信模型 1 更好。Jeffreys [Jeff61] 提出了一个用于解释贝叶斯因子大小的证据等级，如表 7.1 所示。这是频率学派 p 值概念（见第 E.7.5 节）的贝叶斯替代。或者，我们可以直接将贝叶斯因子转换为模型上的后验概率。若 $p(M_1)=p(M_0)=0.5$，则有

$$p(M_0\mid D) = \frac{B_{0,1}}{1+B_{0,1}} = \frac{1}{B_{1,0}+1} \tag{7.210}$$

在第 7.6.6.1 节中，我们给出了一个计算贝叶斯因子的完整示例。

### 7.6.6.1 示例：检验一枚硬币是否公平

举个例子，假设我们观察了一些掷硬币的结果，想要判断数据是由公平硬币 $\theta = 0.5$ 产生的，还是由可能有偏的硬币产生的，其中 $\theta$ 可以是 $[0,1]$ 中的任意值。我们将第一个模型记为 $M_0$，将第二个模型记为 $M_1$。$M_0$ 下的边际似然就是

$$p(D\mid M_0) = \left(\frac{1}{2}\right)^N \tag{7.211}$$

其中 $N$ 是掷硬币的次数。由式 (7.38)，在 $M_1$ 下使用 Beta 先验的边际似然为

$$p(\mathcal{D}|M_1)=\int p(\mathcal{D}|\theta)p(\theta)d\theta=\frac{B(\alpha_1+N_1,\alpha_0+N_0)}{B(\alpha_1,\alpha_0)}\tag{7.212}$$

我们在图 7.25(a) 中绘制了 $\log p(\mathcal{D}|M_1)$ 相对于正面次数 $N_1$ 的变化曲线，假设 $N=5$ 且使用均匀先验 $\alpha_1=\alpha_0=1$。（只要先验是对称的，即 $\alpha_0=\alpha_1$，曲线形状对 $\alpha_1$ 和 $\alpha_0$ 的取值并不十分敏感。）如果我们观察到 2 次或 3 次正面，那么无偏硬币假设 $M_0$ 比 $M_1$ 更有可能，因为 $M_0$ 是更简单的模型（没有自由参数）——如果硬币有偏却恰好产生几乎正好是 50/50 的正面/反面比例，那将是一种可疑的巧合。然而，当计数结果变得更加极端时，我们会更支持有偏硬币假设。注意，如果我们绘制对数贝叶斯因子 $\log B_{1,0}$，其形状将完全相同，因为 $\log p(\mathcal{D}|M_0)$ 是一个常数。

在边际似然难以计算的情况下，我们可以使用 BIC 近似。

| 贝叶斯因子 $BF(1,0)$ | 解释 |
|---|---|
| $BF < \frac{1}{100}$ | 支持 $M_0$ 的决定性证据 |
| $BF < \frac{1}{10}$ | 支持 $M_0$ 的有力证据 |
| $\frac{1}{10} < BF < \frac{1}{3}$ | 支持 $M_0$ 的中等证据 |
| $\frac{1}{3} < BF < 1$ | 支持 $M_0$ 的微弱证据 |
| $1 < BF < 3$ | 支持 $M_1$ 的微弱证据 |
| $3 < BF < 10$ | 支持 $M_1$ 的中等证据 |
| $BF > 10$ | 支持 $M_1$ 的有力证据 |
| $BF > 100$ | 支持 $M_1$ 的决定性证据 |

*表 7.1：解释贝叶斯因子大小的 Jeffreys 证据等级。*

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_249_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_249_1.png)

*图 7.25：(a) 掷硬币示例中对数边际似然与正面次数的关系。(b) BIC 近似。（纵轴刻度是任意的，因为我们固定了 $N$。）由 coins_model_sel_demo.py 生成。*
