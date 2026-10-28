

## 2. 强凸情形：
在假设3.3下，我们有

$\mathcal{L}(\theta_{T+1}) - \mathcal{L}^* \in O_T\left(e^{-\mu\gamma T}\right).$

将上面的 $\gamma = \frac{1}{L}$ 代入，我们得到最佳可能的收敛保证，即 $\mathcal{L}(\theta_{T+1}) - \mathcal{L}^* \in O_T\left(e^{-\frac{1}{\kappa_{\mathcal{L}}}T}\right)$。回顾一下，$\kappa_{\mathcal{L}} := \frac{L}{\mu}$ 是损失函数 $\mathcal{L}$ 的条件数。

### 证明
我们将证明分为两部分。第一部分分析非凸情形。第二部分考虑强凸情形：

- 1. **非凸情形：** 考虑任意 $t \in [T]$。类似于定理3.1证明中的(3.8)，注意到 $\theta_{t+1} = \theta_t - \gamma \nabla\mathcal{L}(\theta_t)$，我们得到

$\mathcal{L}(\theta_{t+1}) \le \mathcal{L}(\theta_t) - \gamma\langle\nabla\mathcal{L}(\theta_t),\nabla\mathcal{L}(\theta_t)\rangle + \frac{L}{2}\gamma^2\|\nabla\mathcal{L}(\theta_t)\|^2.$

重新排列右侧的项，得到以下结果：

$\mathcal{L}(\theta_{t+1}) \le \mathcal{L}(\theta_t) - \gamma\left(1 - \frac{L}{2}\gamma\right)\|\nabla\mathcal{L}(\theta_t)\|^2.$ (3.22)

这等价于

$\left(1 - \frac{L}{2}\gamma\right)\|\nabla\mathcal{L}(\theta_t)\|^2 \le \frac{\mathcal{L}(\theta_t) - \mathcal{L}(\theta_{t+1})}{\gamma}.$

最后一个不等式由 $\mathcal{L}(\boldsymbol{\theta}_{\mathbf{T}+1}) - \mathcal{L}^* \geq 0$ 这一事实得出。这完成了非凸情形的证明。

- 2. **强凸情形：** 回顾上面的(3.22)，对所有 $t \in [T]$，

$$\mathcal{L}(\boldsymbol{\theta}_{t+1}) \leq \mathcal{L}(\boldsymbol{\theta}_t) - \gamma \left(1 - \frac{L}{2}\gamma\right) \|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2.$$

在假设3.3下，$\|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2 \geq 2\mu\left(\mathcal{L}(\boldsymbol{\theta}_t) - \mathcal{L}^*\right)$。将上述结果用于上式，并注意到 $1 - \frac{L}{2}\gamma \geq \frac{1}{2}$，得到

$$\mathcal{L}(\boldsymbol{\theta}_{t+1}) \leq \mathcal{L}(\boldsymbol{\theta}_t) - \gamma \mu \left(\mathcal{L}(\boldsymbol{\theta}_t) - \mathcal{L}^*\right).$$

在上述不等式两边同时减去 $\mathcal{L}^*$，我们得到

$$\mathcal{L}(\boldsymbol{\theta}_{t+1}) - \mathcal{L}^* \leq (1 - \mu\gamma) \left(\mathcal{L}(\boldsymbol{\theta}_t) - \mathcal{L}^*\right).$$

回顾一下，当假设3.1和3.3同时成立时，$\mu \leq L$。这意味着，由于 $\gamma \leq \frac{1}{L}$，有 $1 - \mu\gamma \geq 1 - \frac{\mu}{L} \geq 0$。因此，从 $t = T$ 到 $t = 1$ 递归应用上述不等式，我们得到

$$\mathcal{L}(\boldsymbol{\theta}_{\mathbf{T}+1}) - \mathcal{L}^* \leq (1 - \mu\gamma)^T \left(\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^*\right).$$

由于 $(1 - \mu\gamma)^T \leq e^{-\mu\gamma T}$，上述结果意味着

$$\mathcal{L}(\boldsymbol{\theta}_{\mathbf{T}+1}) - \mathcal{L}^* \leq e^{-\mu\gamma T} \left(\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^*\right).$$

上述内容完成了证明。

### 注释3.4
对于给定的 $T$，为使上界因子 $e^{-\mu\gamma T}$ 达到可能的最小值，我们必须使 $\gamma$ 尽可能大，即 $\gamma = \frac{1}{L}$。由此得到的收敛速率由 $\exp\left(-\frac{T}{\mathcal{K}_L}\right)$ 给出，其中回顾 $\mathcal{K}_L := \frac{L}{\mu}$ 是损失函数 $\mathcal{L}$ 的条件数。正如预期，我们观察到条件数越小，梯度下降法收敛到最小值越快，反之亦然。

注意，与DSGD和DMGD不同，DGD的收敛速率与其集中式对应方法相同，即使用多个节点时我们没有加速。这是因为在DGD的每一步中，每个节点都计算其局部损失函数的全梯度并发送给服务器。因此，我们无法获得(3.13)中那样的“方差缩减”性质。然而，与集中式GD相比，DGD仍然减少了每个节点的计算负担。具体而言，每一步中，每个节点本地只需计算 \(m\) 个逐点梯度，而不是 \(m n\)（如果数据点收集在单台机器上）。因此，每个节点的计算成本确实被除以了 \(n\)。

### 3.3 本章注释
本章我们介绍了（基于服务器的）联邦机器学习框架，并引入了以联邦方式进行学习的主要方法，即分布式梯度下降方法。具体来说，我们通过详细分析非凸和强凸损失函数的情形，解释了小批量分布式梯度下降的基本原理。我们在两种情形下都推导了训练误差，并给出了为进一步分析梯度下降方法奠定基础的数学工具。本章给出的大多数证明都是标准的，本质上可以视为文献[13]中结果的简化版本。此外，我们在强凸性下使用计划学习率的收敛分析受到了文献[7, 15]中结果的启发。我们在本章讨论的不同方法的训练误差总结在表3.1中。

虽然本章给出的分析是自洽的，并且足以介绍本书后续章节中有用的概念，但它并不构成对分布式算法和分布式优化领域的完整介绍。关于这些主题的更全面处理，感兴趣的读者可以分别参阅[3, 10]和[1, 2]。还需要注意，出于教学原因，我们只介绍了简单的分布式梯度下降方法。然而，联邦机器学习是一种快速发展的通用新范式，可以提供许多其他解决方案，包括*局部更新*、*节点子采样*或*自适应方法*。我们建议感兴趣的读者参阅[5]以了解该领域的全面概述，包括开放问题和可能的未来进展。最后，我们选择不涵盖对等网络上的*去中心化梯度下降*方法的分析。虽然

**表3.1** DGD、DSGD 和 DMGD（批大小为 \(b\)）的收敛速率。这些结果适用于一类 $\mathcal{L}$ 为 $L$-光滑的学习问题，假设逐点梯度具有有界的（局部）协方差迹 $\sigma^2$。回顾一下，在强凸情形中，$K_{\mathcal{L}} := \frac{L}{\mu}$ 表示损失函数 $\mathcal{L}$ 的条件数。

|  | DGD | DSGD | DMGD |
|---|---|---|---|
| 非凸 | $O_T\left(\frac{1}{T}\right)$ | $O_T\left(\sqrt{\frac{\sigma^2}{nT}}\right)$ | $O_T\left(\sqrt{\frac{\sigma^2}{nbT}}\right)$ |
| $\mu$-强凸 | $O_T\left(e^{-T/K_{\mathcal{L}}}\right)$ | $O_T\left(K_{\mathcal{L}}\frac{\sigma^2}{nT}\right)$ | $O_T\left(K_{\mathcal{L}}\frac{\sigma^2}{nbT}\right)$ |

对等架构上的去中心化算法的分析与我们所考虑的联邦算法具有重要的相似性，但它们有一些重要的特殊性，尤其是在*网络拓扑*和*异步通信*对训练误差的影响方面。除了上述参考文献外，我们还想指出*去中心化优化*主题下的一些著名工作，特别是[8, 9, 12, 14]。

本章介绍的分布式梯度下降方法为联邦机器学习背景下的鲁棒性方案（在后续章节中介绍）提供了具体的基础。我们在第4章末尾提供了一些参考文献，涉及在包含多个局部更新和节点子采样（如*联邦平均* [11]）以及其他对等架构的分布式梯度下降变体中解决鲁棒性的工作。

## 参考文献
- 1. Bertsekas D, Tsitsiklis J (2015) 并行与分布式计算：数值方法. Athena Scientific, Nashua
- 2. Boyd S, Parikh N, Chu E, Peleato B, Eckstein J (2011) 通过交替方向乘子法进行分布式优化与统计学习. Found Trends Mach Learn 3(1):1–122. ISSN: 1935-8237
- 3. Cachin C, Guerraoui R, Rodrigues L (2011) 可靠与安全分布式编程导论. Springer Science & Business Media, Cham
- 4. Freund JE (1962) 数理统计. Prentice-Hall, Englewood Cliffs
- 5. Kairouz P, McMahan HB, Avent B, Bellet A, Bennis M, Bhagoji AN, Bonawitz K, Charles Z, Cormode G, Cummings R, D’Oliveira RGL, Eichner H, Rouayheb SE, Evans D, Gardner J, Garrett Z, Gascón A, Ghazi B, Gibbons PB, Gruter S, Harchaoui Z, He C, He L, Huong Z, Hutchinson B, Hsu J, Jaggi M, Javidi T, Joshi G, Khodak M, Konečný J, Korolova A, Koushanfar F, Koyejo S, Lepoint T, Liu Y, Mittal P, Mohri M, Nock R, Özgür A, Pagh R, Qi H, Ramage D, Raskar R, Raykova M, Song D, Song W, Stich SU, Sun Z, Gür H, Suresh AT, Tramèr F, Vepakomma P, Wang J, Xiong L, Xu Z, Yang Q, Yu FX, Yu H, Zhao S (2021) 联邦学习的进展与开放问题. Found Trends® Mach Learn 14(1–2):1–210. ISSN: 1935-8237
- 6. Karimi H, Nutini J, Schmidt M (2016) Polyak-Lojasiewicz条件下的梯度与近端梯度方法的线性收敛. In: Machine Learning and Knowledge Discovery in Databases: European Conference, ECML PKDD 2016, Riva del Garda, Italy, September 19–23, 2016, Proceedings, Part I 16. Springer, Berlin, pp. 795–811
- 7. Khaled A, Richtárik P (2023) 非凸世界中的SGD更好的理论. Trans Mach Learn Res . Survey Certification. ISSN: 2835-8856. https://openreview.net/forum?id=AU4qIHN2VkS
- 8. Koloskova A, Loizou N, Boreiri S, Jaggi M, Stich SU (2020) 变拓扑与局部更新下的去中心化SGD统一理论. In: Proceedings of the 37th International Conference on Machine Learning, ICML 2020, 13–18 July 2020, Virtual Event, vol. 119. Proceedings of Machine Learning Research. PMLR, pp. 5381–5393
- 9. Lian X, Zhang W, Zhang C, Liu J (2018) 异步去中心化并行随机梯度下降. In: ICML, pp. 3049–3058
- 10. Lynch NA (1996) 分布式算法. Elsevier, Amsterdam
- 11. McMahan B, Moore E, Ramage D, Hampson S, Arcas BAY (2017) 从去中心化数据中进行通信高效的深度网络学习. In: Proceedings of the 20th International Conference on Artificial Intelligence and Statistics. Singh A, Zhu J (eds), vol. 54. Proceedings of Machine Learning Research. PMLR, pp. 1273–1282

