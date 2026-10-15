
PGD 对抗攻击算法 \[[148](#refbib.xhtml#refbib148)\] 已经使用 CleverHans 库 \[[65](#refbib.xhtml#refbib65)\] 实现。硬件模型使用 NASCaps 库实现，该库基于通过 Synopsys Design Compiler 工具合成的 CapsAcc 架构，采用 45nm 工艺节点和 3 ns 时钟周期。DNN 的训练和测试，使用 TensorFlow \[[1](#refbib.xhtml#refbib1)\] 实现，运行在配备四块 NVIDIA Tesla V100-SXM2 GPU 的 GPU‑HPC 计算节点上。注意，我们的实验使用快速评估方法运行了 2000 个 GPU 小时，完整的训练和 PGD 攻击评估则运行了 8000 个 GPU 小时。如果没有这些时间缩短，或者在考虑更复杂的优化问题（例如更深的 DNN 模型或更大的数据集），探索时间将会持续数月 GPU 时间。

搜索算法初始化为包含 10 个随机个体的种群，遗传循环最多运行 20 次。后代种群大小为 10，变异概率为 10%。每个卷积层可以由 3×3、5×5 或 9×9 核组成，步幅为 1 或 2。通道数和胶囊维度范围在 1 到 64 之间。

#### 5.3.3.2 NAS 中选择对抗扰动的方法

对抗扰动的大小是进行 NAS 时的关键参数。按照上述流程，NASCaps 库的 Pareto‑最优 DNN 在不同的对抗扰动 ε 值下接受 PGD 攻击测试。结果如 [Figure 5.10](#chapter5.xhtml#fig5_10) 所示，预期的趋势是 ε 越大，DNN 精度下降越快。NAS 选用的数值详见 [Table 5.5](#chapter5.xhtml#tbl5_5)。选择过程遵循 [Algorithm 22](#chapter5.xhtml#comp05_2)。*One EPS* 列表示使用单一 ε 值进行搜索，*Two EPS* 列表示使用两个不同的 ε 值（记为 ε<sub>low</sub> 与 ε<sub>high</sub>）进行搜索。注意，像 MNIST 这样简单的数据集需要相对较大的对抗扰动才能影响 DNN 的鲁棒性；相反，像 CIFAR10 这样更复杂的数据集，较小的扰动已经足以误导特定输入。

![Figure 5.10: 分析在不同对抗扰动值下 DNN 的鲁棒性（a）MNIST，（b）Fashion‑MNIST，（c）CIFAR10。](images/fig5_10.jpg)

[Figure 5.10:](#chapter5.xhtml#b5fig5_10) 分析在不同对抗扰动值下 DNN 的鲁棒性（a）MNIST，（b）Fashion‑MNIST，（c）CIFAR10。

[Table 5.5:](#chapter5.xhtml#b5tbl5_5) NAS 中选用的对抗扰动 ε 值，针对 MNIST、Fashion‑MNIST 和 CIFAR10 数据集。同时报告了 *Two EPS* 搜索的 ε<sub>low</sub> 与 ε<sub>high</sub> 值。

|  | Two EPS ε<sub>low</sub> | One EPS ε | Two EPS ε<sub>high</sub> |
| --- | --- | --- | --- |
| MNIST | 3e-3 | 3e-2 | 1e-1 |
| F‑MNIST | 1e-3 | 1e-2 | 3e-2 |
| CIFAR10 | 3e-5 | 3e-4 | 1e-3 |

#### 5.3.3.3 Fast DNN Robustness Evaluation for RoHNAS

为降低探索时间，我们的算法仅训练 DNN 限定的 epoch 数，从而实现快速的鲁棒性评估。通过 Pearson Correlation Coefficient \[[208](#refbib.xhtml#refbib208)\] 衡量与全训练鲁棒性的相似性，具体方法见 [Section 5.2](#chapter5.xhtml#sec5_2)。CIFAR10 数据集使用 10 个训练 epoch，Fashion‑MNIST 和 MNIST 使用 5 个 epoch，这是在高相关系数与低训练时间之间的折中。

*RoHNAS - One EPS* 的快速鲁棒性评估结果如 [Figure 5.11](#chapter5.xhtml#fig5_11) 所示。算法最早的代建生成的 DNN 解不佳，而大多数 Pareto‑最优解出现在最后的代。注意，针对 CIFAR10 数据集的 *RoHNAS* 评估中，最后代的 DNN 对 PGD 攻击的鲁棒性较差，但仍位于 Pareto 前沿，因为能耗极低。相反，最早代的若干候选 DNN 对 PGD 攻击极为敏感，会被 Pareto 前沿的选择机制自动剔除。

![Figure 5.11: RoHNAS 快速评估 DNN 在 PGD 攻击下的鲁棒性，展示能耗、延迟和记忆占用的权衡。（a）CIFAR10，（b）Fashion‑MNIST，（c）MNIST。](images/fig5_11.jpg)

[Figure 5.11:](#chapter5.xhtml#b5fig5_11) *RoHNAS* 快速评估 DNN 在 PGD 攻击下的鲁棒性，展示能耗、延迟和记忆占用的权衡。（a）CIFAR10，（b）Fashion‑MNIST，（c）MNIST。

#### 5.3.3.4 RoHNAS 精确结果对 Pareto‑最优 DNN

前一阶段选出的 Pareto‑最优 DNN 在此阶段进行了完整训练，以获得精确的鲁棒性评估。MNIST 和 Fashion‑MNIST 的 DNN 训练了 100 个 epoch，CIFAR10 则使用了 300 个 epoch。结果如 [Figure 5.12](#chapter5.xhtml#fig5_12) 所示，展示了设计目标之间的权衡。

在 [Figure 5.12a](#chapter5.xhtml#fig5_12) 中，*RoHNAS* 框架为 CIFAR10 找到的 Pareto‑最优解实现 86.07% 的准确率，内存占用 11.85 MiB，能耗 38.63 mJ，延迟 4.47 ms。类似地，[Figure 5.12b](#chapter5.xhtml#fig5_12) 中的 Fashion‑MNIST 解在 93.40% 准确率的同时，延迟 6.40 ms，能耗 61.19 mJ，内存 16.82 MiB。值得注意的是，*Two EPS* 搜索在中等能耗区域找到 Pareto‑最优解，而 *One EPS* 搜索则发现了若干低能耗的有趣解。MNIST 数据集的 Pareto‑最优搜索覆盖了更为异质的数值范围，充分利用了不同目标之间的权衡。

![Figure 5.12: RoHNAS 对 Pareto‑最优 DNN 的精确鲁棒性评估（PGD 攻击），展示硬件效率的权衡。（a）CIFAR10，（b）Fashion‑MNIST，（c）MNIST。](images/fig5_12.jpg)

[Figure 5.12:](#chapter5.xhtml#b5fig5_12) *RoHNAS* 对 Pareto‑最优 DNN 的精确鲁棒性评估（PGD 攻击），展示硬件效率的权衡。（a）CIFAR10，（b）Fashion‑MNIST，（c）MNIST。

*RoHNAS* 框架已与其他最先进的 DNN 和 CapsNet 架构以及包含胶囊层的 NAS 方法进行比较。[Figure 5.13](#chapter5.xhtml#fig5_13) 展示了我们的 *RoHNAS*（One EPS 设置）与 NASCaps、CapsNet \[[236](#refbib.xhtml#refbib236)\] 和 DeepCaps \[[220](#refbib.xhtml#refbib220)\] 的对比。对于 MNIST 数据集，使用 *RoHNAS* 框架生成的 Pareto‑最优解在较大范围的 ε 扰动下尤为鲁棒，精度下降大约在 NASCaps 的一阶大小以上 ε 处才出现。Fashion‑MNIST 上的 Pareto‑最优解鲁棒性行为与 CapsNet 相似。而在 CIFAR10 数据集上，*RoHNAS* 的 DNN 行为在低 ε 值时与 DeepCaps 相当，而在较高的对抗扰动下，仍有一个 Pareto‑最优解表现出良好的鲁棒性。 
