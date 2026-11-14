

然后计算权重和偏置更新的梯度为

$$
\frac{\partial \mathcal{L}}{\partial W^{(l)}} = \delta^{(l)}(a^{(l-1)})^\top
$$ (246)

和

$$
\frac{\partial \mathcal{L}}{\partial b^{(l)}} = \delta^{(l)},
$$ (247)

分别。梯度下降的动态深受损失面曲率的影响，由黑塞矩阵封装

$$
H(\theta) = \nabla_\theta^2 \mathcal{L}(\theta).
$$ (248)

对于较小的步长 \(\eta\)，损失函数的变化可近似为

$$
\Delta \mathcal{L} \approx -\eta \| \nabla_\theta \mathcal{L}(\theta) \|^2 + \frac{\eta^2}{2} (\nabla_\theta \mathcal{L}(\theta))^\top H(\theta) \nabla_\theta \mathcal{L}(\theta).
$$ (249)

这表明，收敛性不仅由梯度幅值决定，还取决于沿梯度方向的损失面曲率。\(H(\theta)\) 的特征值 \(\lambda_1, \lambda_2, \dots, \lambda_d\) 决定了局部几何，较大的条件数 \(\kappa = \frac{\lambda_{max}}{\lambda_{min}}\) 由于病态而减慢收敛。随机梯度下降（SGD）通过基于单个数据样本 \((x_i, y_i)\) 计算更新来修改标准梯度下降，从而得到

$$
\theta^{(k+1)} = \theta^{(k)} - \eta \nabla_\theta \ell(\theta; x_i, y_i).
$$ (250)

虽然 SGD 将方差引入更新中，但这种随机性有助于逃离以零梯度但混合曲率为特征的鞍点。为了平衡计算效率和稳定性，小批量 SGD 在随机选定的大小为 \(|\mathcal{B}|\) 的子集 \(\mathcal{B} \subset \{1, \dots, N\}\) 上计算梯度，得到

$$
\nabla_\theta \mathcal{L}_\mathcal{B}(\theta) = \frac{1}{|\mathcal{B}|} \sum_{i \in \mathcal{B}} \nabla_\theta \ell(\theta; x_i, y_i).
$$ (251)

动量方法通过融入过去梯度的记忆来增强收敛性。速度项

$$
v^{(k+1)} = \gamma v^{(k)} + \eta \nabla_\theta \mathcal{L}(\theta)
$$ (252)

累积梯度信息，参数更新为

$$
\theta^{(k+1)} = \theta^{(k)} - v^{(k+1)}.
$$ (253)

在 \(H(\theta)\) 的特征空间中分析动量，其中 \(H = Q \Lambda Q^\top\)，揭示了每个特征方向上的有效步长为

$$
\eta_{\text{eff}, i} = \frac{\eta}{1 - \gamma \lambda_i},
$$ (254)

这表明动量在低曲率方向上加速收敛，同时抑制高曲率方向上的振荡。自适应梯度方法（如 AdaGrad、RMSProp 和 Adam）为单个参数优化学习率。在 AdaGrad 中，自适应学习率为

$$
\eta_i^{(k+1)} = \frac{\eta}{\sqrt{G_{ii}^{(k+1)} + \epsilon}},
$$ (255)

其中

$$
G_{ii}^{(k+1)} = G_{ii}^{(k)} + (\nabla_{\theta_i} \mathcal{L}(\theta))^2.
$$ (256)

RMSProp 使用指数加权平均对其进行修改

$$
G_{ii}^{(k+1)} = \beta G_{ii}^{(k)} + (1 - \beta) (\nabla_{\theta_i} \mathcal{L}(\theta))^2.
$$ (257)

Adam 将 RMSProp 与动量相结合，其中一阶矩和二阶矩为

$$
m^{(k+1)} = \beta_1 m^{(k)} + (1 - \beta_1) \nabla_\theta \mathcal{L}(\theta)
$$

和

$$
v^{(k+1)} = \beta_2 v^{(k)} + (1 - \beta_2) \left( \nabla_\theta \mathcal{L}(\theta) \right)^2.
$$

偏差校正得到

$$
\hat{m}^{(k+1)} = \frac{m^{(k+1)}}{1 - \beta_1^k}, \quad \hat{v}^{(k+1)} = \frac{v^{(k+1)}}{1 - \beta_2^k}.
$$

最终参数更新为

$$
\theta^{(k+1)} = \theta^{(k)} - \eta \frac{\hat{m}^{(k+1)}}{\sqrt{\hat{v}^{(k+1)} + \epsilon}}.
$$

总之，梯度下降及其变体为优化神经网络参数提供了丰富的框架。虽然标准梯度下降提供了一种基本方法，但动量和自适应梯度等高级方法通过根据损失面的景观和训练动态定制更新，显著增强了收敛性。

## 6.2.1 SGD（随机梯度下降）优化器

文献综述：Lauand 和 Meyn (2025) [175] 使用马尔可夫动力学为 SGD 建立了理论框架，以改进收敛特性。它将准周期线性系统集成到 SGD 中，增强了其在非平稳环境中的鲁棒性。Maranjyan 等人 (2025) [176] 开发了一种异步 SGD 算法，满足时间复杂度的理论下界。它引入了基于环的通信，以优化并行执行而不降低收敛率。Gao 和 Gündüz (2025) [177] 提出了一种基于随机梯度下降的方法，用于优化无线网络中的图神经网络。它严谨地分析了随机优化问题，并证明了其收敛保证。Yoon 等人 (2025) [178] 研究了多代理学习中的联邦 SGD，并推导了其通信效率的理论保证，同时实现平衡。Verma 和 Maiti (2025) [179] 为基于 SGD 的优化器提出了周期性学习率（使用正弦和余弦函数），理论上证明了其在稳定性和计算效率方面的优势。Borowski 和 Miasojedow (2025) [180] 扩展了 Robbins-Monro 定理以分析 SGD 的收敛保证，深化了对投影随机逼近算法的理论理解。Dong 等人 (2025) [181] 将随机梯度下降应用于脑网络建模，为优化神经控制策略提供了理论框架。Jiang 等人 (2025) [182] 分析了去中心化 SGD 中的偏差-方差权衡，证明了收敛率，并为有偏梯度提出了误差纠正机制。Sonobe 等人 (2025) [183] 将 SGD 与贝叶斯推断相联系，提出了随机优化方法如何逼近后验分布的理论分析。Zhang 和 Jia (2025) [184] 考察了强化学习中策略梯度的理论特性，证明了随机最优控制问题的收敛保证。

随机梯度下降（SGD）优化器是一种迭代方法，旨在通过沿负梯度方向更新参数向量 \(\mathbf{w}\) 来最小化目标函数 \(f(\mathbf{w})\)。基本优化问题可表示为

$$
\min_{\mathbf{w}} f(\mathbf{w}),
$$

其中

$$
f(\mathbf{w}) = \frac{1}{N} \sum_{i=1}^N \ell(\mathbf{w}; \mathbf{x}_i, y_i)
$$

表示从数据集 \(\{(\mathbf{x}_i, y_i)\}_{i=1}^N\) 构建的经验风险。这里，\(\ell(\mathbf{w}; \mathbf{x}_i, y_i)\) 表示损失函数，\(\mathbf{w} \in \mathbb{R}^d\) 是参数向量，\(N\) 是数据集大小，\(f(\mathbf{w})\) 近似真实总体风险

\(\mathbb{E}_{\mathbf{x},y}[\ell(\mathbf{w}; \mathbf{x}, y)].\) (264)

标准梯度下降涉及更新规则

\(\mathbf{w}^{(t+1)} = \mathbf{w}^{(t)} - \eta \nabla f(\mathbf{w}^{(t)}),\) (265)

其中 \(\eta > 0\) 是学习率，且

\(\nabla f(\mathbf{w}) = \frac{1}{N} \sum_{i=1}^N \nabla \ell(\mathbf{w}; \mathbf{x}_i, y_i)\) (266)

是全梯度。然而，对于大规模数据集，计算 \(\nabla f(\mathbf{w})\) 在计算上变得不可行，这促使采用随机逼近。随机逼近依赖于使用单个数据点或一小批数据点来估计梯度 \(\nabla f(\mathbf{w})\) 的想法。表示迭代 \(t\) 中采样的随机索引为 \(i_t\)，随机梯度可写为

\(\widehat{\nabla} f(\mathbf{w}^{(t)}) = \nabla \ell(\mathbf{w}^{(t)}; \mathbf{x}_{i_t}, y_{i_t}).\) (267)

因此，更新规则变为

\(\mathbf{w}^{(t+1)} = \mathbf{w}^{(t)} - \eta \widehat{\nabla} f(\mathbf{w}^{(t)}).\) (268)

对于大小为 \(m\) 的小批量 \(\mathcal{B}_t\)，随机梯度推广为

\(\widehat{\nabla} f(\mathbf{w}^{(t)}) = \frac{1}{m} \sum_{i \in \mathcal{B}_t} \nabla \ell(\mathbf{w}^{(t)}; \mathbf{x}_i, y_i).\) (269)

\(\widehat{\nabla} f(\mathbf{w})\) 的一个重要性质是其无偏性：

\(\mathbb{E}[\widehat{\nabla} f(\mathbf{w})] = \nabla f(\mathbf{w}).\) (270)

然而，\(\widehat{\nabla} f(\mathbf{w})\) 的方差定义为

\(\text{Var}[\widehat{\nabla} f(\mathbf{w})] = \mathbb{E}[\|\widehat{\nabla} f(\mathbf{w}) - \nabla f(\mathbf{w})\|^2],\) (271)

将随机噪声引入更新中，其中 \(\text{Var}[\widehat{\nabla} f(\mathbf{w})] \approx \frac{\sigma^2}{m}\) 且

\(\sigma^2 = \mathbb{E}[\|\nabla \ell(\mathbf{w}; \mathbf{x}) - \nabla f(\mathbf{w})\|^2]\) (272)

是梯度的方差。为了分析 SGD 的收敛特性，我们假设 \(f(\mathbf{w})\) 是 \(L\)-光滑的，即

\(\|\nabla f(\mathbf{w}_1) - \nabla f(\mathbf{w}_2)\| \leq L \|\mathbf{w}_1 - \mathbf{w}_2\|,\) (273)

且 \(f(\mathbf{w})\) 下界由 \(f^* = \inf_{\mathbf{w}} f(\mathbf{w})\) 界定。使用泰勒展开，我们可以写成

\(f(\mathbf{w}^{(t+1)}) \leq f(\mathbf{w}^{(t)}) - \eta \|\nabla f(\mathbf{w}^{(t)})\|^2 + \frac{\eta^2 L}{2} \|\widehat{\nabla} f(\mathbf{w}^{(t)})\|^2.\) (274)

取期望得到

\(\mathbb{E}[f(\mathbf{w}^{(t+1)})] \leq \mathbb{E}[f(\mathbf{w}^{(t)})] - \frac{\eta}{2} \mathbb{E}[\|\nabla f(\mathbf{w}^{(t)})\|^2] + \frac{\eta^2 L}{2} \sigma^2,\) (275)

