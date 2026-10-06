
[content]

## 6.4.3 实证分析

为了给提出的方法提供直观的解释，我们使用 MSR-WTT 数据集在各种 OOM（跨模态）场景和模态上进行了实证分析。

![](img/1aedbd555ac8a0e63b6116db31c6c2f8_143_0.png)

图 6.5. 连接效应对最大平均差异和准确率的影响。

**连接缓解了模态差异。** 为了理解我们基于 VIB 的连接学习的性能，在这里展示了其对跨模态泛化的影响。具体而言，在连接训练期间，我们计算了每个 IM（模态）数据映射与 OOM 数据之间的最大平均差异（MMD）。同时，我们在训练期间选取了 6 个点并提取了 IM 映射，将其用于分类头作为最优分类器。根据我们的理论结果，我们将这些分类器应用于 OOM 数据并计算其准确率，如图 6.5 所示。我们可以看到，随着训练的进行，每个 IM 和 OOM 数据之间的 MMD 正在减小，相应的准确率正在增加，这表明：(1) 我们的连接确实缩小了它们特征之间的模态差异；(2) IM 数据的映射越来越接近 OOM 数据，最优分类器在 OOM 数据上显示出更好的分类结果，这有利于从已知模态到未知模态的知识迁移。

**模态不歧识别别了不确定性。** 为了理解模态不歧的影响，我们通过训练 OOM 学习器仅使用标记数据进行 10 个 epoch 的训练来分析半监督场景。然后，我们利用模态不歧标准将 OOM 数据分为具有不歧和一致的数据，并展示它们的预测准确率。

## 6.4 实验

![](img/1aedbd555ac8a0e63b6116db31c6c2f8_144_0.png)

图 6.6. 分别是具有模态不歧和模态一致的 OOM 数据的预测准确率。(a) 探索之前。(b) 探索之后。

| 设置 | 消融实验 | MSR-VTT R@1 | | | |
| --- | --- | --- | --- | --- |
| Semi | w/o connection | 8.7 | 7.9 | 10.3 |
| | w/o exploration | 16.4 | 16.5 | 18.8 |
| | COX | 25.2 | 24.1 | 40.0 |
| Unsub. | w/o warm-up | 7.4 | 11.5 | 10.5 |
| | COX | 14.8 | 18.4 | 15.4 |

在图 6.6 (a) 中，我们可以看到具有不歧的 OOM 数据准确率明显低于具有一致的数据，这意味着预测不确定性（即准确率低的数据）被模态不歧有效识别了。

**模态缓解了不确定性。** 进一步，我们按照第 6.3.3 节提出的程序进行训练，并在图 6.6 (b) 中再次展示了一致和不歧 OOM 数据的准确率。我们可以看到这两类数据之间的性能差距得到了很大缓解，这证明了利用模态一致性指导探索 OOM 数据的方法合理性。结果，我们可以在两类数据上获得几乎相当的性能，有利于整体泛化。

**消融实验。** 此外，我们进行了消融实验来证明我们方法的有效性。具体来说，我们考虑了三个消融：(1) “w/o connection”，我们移除连接并直接在 IM 数据和 OOM 数据的原始特征上应用模态不歧标准；(2) “w/o exploration”，我们只利用一致的 OOM 数据进行训练；(3) 对于无监督场景，我们考虑了“w/o warm-up”，即不进行预热阶段直接训练模型。表 6.4 的结果显示，所有模块对于实现有效的 OOM 泛化都是关重要的。具体来说，连接对于 IM 数据到 OOM 数据的知识传递至关重要，没有它，泛化性能将大幅下降。该结论与连接分析一致，即跨模态直接应用最优分类器会导致糟糕的准确率。此外，移除探索也会阻碍性能，因为 OOM 数据的独特性被很大忽视了。此外，我们发现预热阶段对于无监督情况是必不可少的。由于初始化模型没有分类能力，我们需要预训练来形成与 IM 数据一致的基础特征聚类，进一步实现有效的 OOM 泛化。

**关于计算效率的讨论。** 注意，我们主要在特征空间上进行特征连接，训练 VIB 框架的计算开销是可以接受的。主要成本是训练 OOM 学习器，这是使用交叉熵损失进行优化的基础训练，可以在单块 NVIDIA 3090/4090 GPU 上实现。

## 6.5 结论与局限性

在本章中，我们研究了一种新颖且具有前景的研究方向，被称为跨模态泛化（OOM Generalization），旨在利用现有模态的知识来泛化到未知模态。我们考虑了两种场景：具有对应关系无对应关系的情况，即半监督和无监督情况。为了解决这些问题，我们提出了连接-探索（COX）方法，它首先跨模态学习连接，然后基于 OOM 数据的独特性进行探索模态不歧。广泛的实验证明了该方法。然而，我们的研究在某些方面存在局限性：首先，由于跨模态直接应用最优分类器会导致准确率低；；其次，移除探索也会阻碍性能，因为 OOM 数据的独特性被很大忽视；此外，我们发现预热阶段对于无监督情况是必不可少的。由于初始化模型没有分类能力，我们需要预训练来形成与 IM 数据一致的基础特征聚类，进一步实现有效的 OOM 泛化。

## 证明与理论分析

在本章中，我们提供了证明和理论分析，包括第 3 节的收敛性分析、第 4 节的锐度理论分析、第 5 节的通过策略的证明以及第 6 节的模态不歧。

## 7. SharpDRO 的证明

本节提供了收敛性的证明。在开始之前，我们给出一些符号：(1) 我们将期望表示 $\mathcal{L}(\theta,\omega) := \mathbb{E}_{(x,y)\sim\omega}\mathcal{L}(\theta)$，我们的目标变为 $\min_{\theta}\max_{\omega}\mathcal{L}(\theta) + \mathcal{R}(\theta)$。(2) $\kappa$ 是 Lipschitz 连续的；(3) 我们定义 $L^*(\theta) = \max_{\omega}\mathcal{L}(\theta)$ 和 $\omega^*(\theta) = \arg\max_{\omega}\mathcal{L}(\theta)$。

### 7.1 更新规则

在理论分析之前，我们需要明确更新规则。注意我们的算法并不是直接获得值，而是通过批次估计它：$g_{\theta} = \frac{1}{M}\sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \theta}(x_i, y_i)$ 和 $g_{\omega} = \frac{1}{M}\sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \omega}(x_i, y_i)$ 成立。因此迭代执行如下：
$\theta_{t+1} = \theta_t - \eta_{\theta}g_{\theta}(\theta_t, \omega_t)$;
$\omega_{t+1} = \omega_t + \eta_{\omega}g_{\omega}(\theta_t, \omega_t)$。
我们进一步给出一个符号 $\theta_{t+1/2} = \theta_t + \rho g_{\omega}(\theta_t, \omega_t)$，因此 $\theta$ 的更新简化为：
$\theta_{t+1} = \theta_t - \eta_{\theta}g_{\theta}(\theta_{t+1/2}, \omega_t)$。

### 7.1.2 假设

对于我们的问题，收敛提出一些必要假设：

假设 8（界方差）。损失函数的梯度的无偏估计有界方差：
$\mathbb{E}_{(x,y)\sim\omega}[\frac{\partial \mathcal{L}}{\partial \theta}(\theta; (x, y))] = \nabla_{\theta}L(\theta, \omega), \mathbb{E}_{(x,y)\sim\omega}[\frac{\partial \mathcal{L}}{\partial \theta}(\theta; (x, y)) - \nabla_{\theta}L(\theta, \omega)\|^2 \le \sigma^2;$

备注 9。由于 $g_{\theta}$ 和 $g_{\omega}$ 分别是平均样本：$g_{\theta} = \frac{1}{M}\sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \theta}(x_i, y_i)$ 和 $g_{\omega} = \frac{1}{M}\sum_{i=1}^M \frac{\partial \mathcal{L}}{\partial \omega}(x_i, y_i)$，它们同样具有无偏性且有界方差：
$\mathbb{E}_{(x,y)\sim\omega}[g_{\theta}(\theta; \omega; (x, y))] = \nabla_{\theta}L(\theta, \omega), \mathbb{E}_{(x,y)\sim\omega}[g_{\theta}(\theta; \omega; (x, y)) - \nabla_{\theta}L(\theta, \omega)\|^2 \le \frac{\sigma^2}{M};$
$\mathbb{E}_{(x,y)\sim\omega}[g_{\omega}(\theta; \omega; (x, y))] = \nabla_{\omega}L(\theta, \omega), \mathbb{E}_{(x,y)\sim\omega}[g_{\omega}(\theta; \omega; (x, y)) - \nabla_{\omega}L(\theta, \omega)\|^2 \le \frac{\sigma^2}{M};$
