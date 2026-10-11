

# 利用神经元旋转调节进行优化

所提软训练中的一个重要条件要求是神经元不应长期处于失活状态，这可能会引入 `0 * p[i]` 和陈旧参数问题。为满足这一要求，我们会及时将长期被跳过的神经元拉回训练周期。具体而言，在聚合过程中，每个落后者将发送其部分更新的梯度索引至全局设备。全局设备将记录所有当前被跳过的神经元并更新其跳过周期值 `C[s]`。在每个聚合周期中，`Helios` 将查询 `C[s]`。一旦某个神经元的 `C[s]` 超过预定义阈值（我们将其设为 $1 + \frac{m}{\sum p_i n_i}$），全局设备将通知相应的落后者，目标神经元将重新加入训练。

# 19.4 性能评估

我们从收敛精度和速度两方面评估 `Helios`。具体而言，我们首先剖析多个移动设备的资源配置。然后，通过调整 CPU/GPU 带宽和内存可用性的配置，我们可以在多块 Nvidia Jetson Nano 开发板上模拟这些移动设备的训练性能，并使它们作为具有不同资源能力的落后者。运行 `AlexNet` 于 `CIFAR-10` 时这些落后者设置的详细信息见 [表 19.1](#Chp019_343-352_B9780443190377000296.xhtml#t0010)。三种 CNN 模型被用作测试目标，分别为 `LeNet`、`AlexNet` 和 `ResNet-18`。上述三种 CNN 模型分别在 `MNIST`、`CIFAR-10` 和 `CIFAR-100` 上进行训练。

## 表 19.1

4 个具有异构资源的落后者。

| 约束条件 | Nano (CPU) | Raspberry | DeepLens (GPU) | DeepLens (CPU) |
| --- | --- | --- | --- | --- |
| 计算工作量 (GFLOPS) | 7 | 6 | 5.5 | 4.5 |
| 内存使用量 (MB) | 252 | 150 | 100 | 110 |
| 时间成本 (min) | 20.6 | 23.8 | 27.2 | 34 |

为展示 `Helios` 的优势，我们重新实现了其他五种 FL 方案以作比较：

1.  **同步 FL (Syn. FL)**：所有设备（包括落后者）同步更新其参数。
2.  **异步 FL (Asyn. FL)**：正常移动设备在本地训练后立即更新其参数，无需等待落后者。
3.  **Random** [[2]](#Chp019_343-352_B9780443190377000296.xhtml#br0010)：在每次训练中，落后者随机选择一个具有预期模型结构体量的部分模型。
4.  **AFO** [[14]](#Chp019_343-352_B9780443190377000296.xhtml#br0070)：一种旨在减少落后者陈旧性问题的优化异步方法。

### 19.4.1 Helios 通用性能评估

如 [表 19.1](#Chp019_343-352_B9780443190377000296.xhtml#t0010) 所示，涉及两种落后者设置：

1.  四个设备参与 FL，包含两个强力设备和两个落后设备，分别为 Strag. 1 和 Strag. 2。
2.  六个设备参与 FL，包含三个强力设备和三个落后设备，分别为 Strag. 1、Strag. 2 和 Strag. 3。

#### 精度评估

[图 19.4](#Chp019_343-352_B9780443190377000296.xhtml#f0025) 展示了收敛精度的实验结果。`x` 轴代表强力移动设备的聚合周期。我们可以发现，`Asyn. FL` 因信息退化而始终达到最低精度。至于 `Syn. FL`，由于其训练周期由落后者决定，其聚合速度比其他方法慢得多，导致精度较低。`Helios` 相比所有基线方法始终展现出最佳精度。具体而言，对于 `MNIST` 上的 `LeNet`，`Helios` 在两种落后者设置下均实现了高达 0.24% 的精度提升。对于 `CIFAR-10` 上的 `AlexNet`，`Helios` 最高有 4.64% 的精度提升。对于 `CIFAR-100` 上的 `ResNet18`，`Helios` 最高提升精度 2.11%。

![Figure 19.4 Soft-training effectiveness evaluation.](OEBPS/images/B9780443190377000296/gr004_u7.jpg)

[图 19.4](#Chp019_343-352_B9780443190377000296.xhtml#cf0135) 软训练有效性评估。

#### 收敛速度评估

显而易见，`Asyn. FL` 收敛速度最差，甚至因陈旧参数和信息丢失而无法收敛。尽管 `AFO` 优化了异步更新，但其收敛仍受落后者陈旧参数的影响。相反，`Helios` 展现出最快的收敛速度，尤其是在落后者较多的 FL 中。对于 `MNIST`、`CIFAR-10` 和 `CIFAR-100` 上的 6 节点实验，`Helios` 分别在 4、12 和 40 个聚合周期后接近收敛，而其他方法至少需要 10、18 和 50 个聚合周期。

### 19.4.2 模型聚合优化评估

在本部分中，模型聚合优化方案的有效性也在相同设置下（落后者从 1 增加到 4）进行评估。我们将无聚合优化的软训练作为基线，表示为 `S.T. Only`。[图 19.5](#Chp019_343-352_B9780443190377000296.xhtml#f0030) 展示了 `Helios` 与 `S.T. Only` 的对比结果。我们可以看到，`Helios` 最高实现了 17.37% 的精度提升，并减少了部分模型聚合导致的精度方差，而 `S.T. Only` 的精度曲线仍有明显波动。

![Figure 19.5 Model aggregation optimization evaluation.](OEBPS/images/B9780443190377000296/gr005_u7.jpg)

[图 19.5](#Chp019_343-352_B9780443190377000296.xhtml#cf0140) 模型聚合优化评估。

# 19.5 结论与未来方向

在本章中，我们证明了由于不同移动设备间的资源异构性，训练协调将成为基于移动设备的联邦学习的主要挑战。文中进一步介绍了一种资源感知的联邦学习框架，以提供潜在解决方案。考虑到普适移动 AI 系统规模和多样性的持续增长，协调问题将对未来的基于移动设备的联邦学习变得更为关键。因此，应用高效训练方法（如蒸馏）和开发新的联邦学习聚合拓扑（如分层 FL）将是极具吸引力的解决方案。

# 参考文献

*   [[1]](#Chp019_343-352_B9780443190377000296.xhtml#cf0095) Dan Alistarh, Torsten Hoefler, Mikael Johansson, Nikola Konstantinov, Sarit Khirirat, Cédric Renggli, The convergence of sparsified gradient methods, *Advances in Neural Information Processing Systems*. 2018:5973–5983.
*   [[2]](#Chp019_343-352_B9780443190377000296.xhtml#br0010) Sebastian Caldas, et al., Expanding the reach of federated learning by reducing client resource requirements, [arXiv:1812.07210](http://www.arxiv.org/abs/1812.07210); 2018.
*   [[3]](#Chp019_343-352_B9780443190377000296.xhtml#br0015) Y. Chen, et al., Asynchronous online federated learning for edge devices, [arXiv:1911.02134](http://www.arxiv.org/abs/1911.02134).
*   [[4]](#Chp019_343-352_B9780443190377000296.xhtml#cs0020_4) Yang Chen, Xiaoyan Sun, Yaochu Jin, Communication-efficient federated deep learning with asynchronous model update and temporally weighted aggregation, [arXiv:1903.07424](http://www.arxiv.org/abs/1903.07424); 2019.
*   [[5]](#Chp019_343-352_B9780443190377000296.xhtml#cs0025_1) Ido Hakimi, Saar Barkai, Moshe Gabel, Assaf Schuster, Taming momentum in a distributed asynchronous environment, [arXiv:1907.11612](http://www.arxiv.org/abs/1907.11612); 2019.

