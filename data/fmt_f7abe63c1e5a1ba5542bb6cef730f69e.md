
无参数的恒等跳跃连接（identity shortcuts）是必要的。我们研究了投影（公式 `(2)`）。在表 `3` 中，我们比较了三个选项：`(A)` 使用零填充跳跃来增加维度，且所有跳跃都是无参数的（同表 `2` 和图 `4` 右侧）；`(B)` 使用投影跳跃来增加维度，且所有跳跃均为恒等映射；`(C)` 所有跳跃均为投影。

## 深度瓶颈架构

我们描述了用于 `ImageNet` 的更深层网络。由于时间允许，我们将构建块修改为“瓶颈”设计。对于每个残差函数 `$\mathcal{F}$`，我们使用 `3` 层堆叠代替 `2` 层（图 `5`）。这三层分别为 `1, 3, 3` 和 `1` 卷积，其中 `1x1` 层负责减少和增加（恢复）维度，并使用 `3x3` 层作为具有相同输入/输出维度的瓶颈。图 `5` 显示了一个示例，其中瓶颈设计具有相似的复杂度深度。

无参数的恒等映射对于瓶颈架构尤为重要。如果将恒等跳跃替换为投影，我们证明（图 `5`）复杂性和模型大小会增加一倍，因为跳跃连接到了两个不同的维度。恒等跳跃为瓶颈架构带来了更高效的模型。

**恒等。投影跳跃。** 我们将 `34` 层网络中的每个 `2` 层块替换为这种 `3` 层瓶颈，导致产生 `50` 层 `ResNet`（表 `1`）。我们使用选项 `B` 来增加维度。该模型具有 `38` 亿 `FLOPs`。

`101` 层和 `152` 层 `ResNets`：我们通过使用更多的 `3` 层块来构建（表 `1`）。令人惊讶的是，尽管深度增加了，但增加的 `ResNet`（`113` 亿 `FLOPs`）与 `VGG-16/19`（`153` 亿/`196` 亿 `FLOPs`）相比，其容量反而更小。

`50/101-152` 层 `ResNet` 通过考虑更多层比 `34` 层网络更准确（表 `3` 和表 `4`）。我们没有观察到退化问题，因此深度的增加没有带来显著的精度损失。深度的益处在所有评估指标中得到了体现。

## 与最先进方法的比较

在表 `4` 中，我们与之前的单模型结果进行了比较。我们的 `34` 层 `ResNets` 取得了竞争性的精度。我们的 `50` 层 `ResNet` 在验证集上的单模型 top-5 错误为 `4.49%`。该单模型性能优于之前的所有结果（表 `5`）。我们将不同深度的模型组合形成集成（在测试时只有两个 `52` 层网络）。这导致测试集上的 top-5 错误为 `3.7%`（表 `6`）。该条目在 `ILSVRC 2015` 中荣得第一。

我们对 `CIFAR-10` 数据集 `[20]` 进行了研究，该数据集包含每类 `5` 万张训练图像和 `1` 万张测试图像。我们在训练集上进行了实验并评估了测试集。我们的关注点是极深网络的行为，但通过推向先进水平，我们提出的结果如下：

| 方法 | 错误 (%) |
|---|---|
| `Maxout [9]` | `9.38` |
| `NIN [25]` | `8.81` |
| `DSN [24]` | `8.22` |
| `FitNet [34]` | `7.32` |
| `Highway [41, 14]` | `7.66` |
| `Highway [41, 42]` | `7.54` |
| `ResNet [32]` | `7.38` |
| `ResNet [32]` | `7.46` |
| `ResNet [44]` | `7.11` |
| `ResNet [56]` | `6.65` |
| `ResNet [110]` | `6.43` |

表 `6`. `CIFAR-10` 测试集上的比较。所有方法均使用数据增强。对于 `ResNet-110`，我们运行了 `5` 次测试并显示了如 `[42]` 所示的平均值。我们的残差模型具有相同的深度和参数数量。我们使用 `0.0001` 的权重衰减和 `0.9` 的动量，并采用了 `[12]` 和 `BN [16]` 中的权重初始化，不使用 dropout。这些方法在 `20` 个 `GPU` 上以 `120` 的批量大小进行训练。我们使用 `0.1` 的学习率，并在 `32k` 和 `48k` 次迭代时减少 `10` 倍，在 `64k` 次迭代终止，这是由 `4.5/5` 的划分决定的。

我们使用 `n = [3, 5, 7, 9]`，导致了 `22、30、44` 和 `56` 层网络。图 `6`（左侧）显示了普通网络的行为。深度普通网络受到深度增加的影响，并且随着深度减小而表现出更高的误差。

图 `6`（中间）显示了 `ResNets` 的行为。与 `ImageNet` 案例（图 `4` 右侧）类似，我们的 `ResNets` 能够克服优化困难并在深度增加时保持精度。我们进一步探索了 `n = 18` 导致的 `110` 层 `ResNet`。我们发现初始 `0.1` 的学习率对于开始收敛来说太大了？因此我们使用 `0.01` 进行预热训练，直到训练误差达到 `800`（约 `400` 次迭代），然后回到 `0.1` 继续训练。其余的学习计划与之前相同。这层 `110` 层网络收敛良好（图 `6` 中间）。它的参数少于深层且

> *非瓶颈 `ResNet`（例如图 `5`）也从深度的增加中获得精度（如在 `CIFAR-0` 上所示），但不如瓶颈 `ResNet` 那么经济。使用瓶颈主要是出于实际考虑。我们进一步注意到，普通网络的退化问题对于瓶颈设计并非毫无用。

![](img/a349fad16277a338a822f777f22b630b_7_0.png)

图 `6`. 在 `CIFAR-10` 上的训练。虚线表示训练误差，实线表示测试误差。左侧：`plain-110` 高于 `60%` 且没有翻倍。中间：`ResNets`。右侧：`110` 层和 `120` 层的 `ResNets`。

![](img/a349fad16277a338a822f777f22b630b_7_1.png)

![](img/a349fad16277a338a822f777f22b630b_7_2.png)

图 `7`. `CIFAR-10` 上层响应的标准差 (`std`)。响应是 `3x3` 层在 `BN` 之后、非线性激活（`ReLU/加法`）之前的输出。层按递增顺序显示。底部：排名按降序显示。

| 训练数据 | `07+12` | `07+12` |
|---|---|---|
| 测试数据 | `VOC 07` | `VOC 12` |
| `VGG-16` | `73.2` | `70.4` |
| `ResNet-101` | `76.4` | `73.8` |
|  | `mAP@5` | `mAP[5]` |
|---|---|---|
| `VGG-16` | `41.5` | `21.2` |
| `ResNet-101` | `48.4` | `27.2` |

网络如 `FiNet [34]` 和 `Highway [41]`。表 `6` 包含了目前最先进的结果 (`6.43`)，见表 `6`。

## 层响应分析

图 `7` 显示了每个 `3x3` 层的标准差 (`std`)。响应是 `3x3` 层在 `BN` 之后、非线性激活（`ReLU/加法`）之前的输出。对于 `ResNets`，该分析揭示了残差函数的强度。

我们证明了 `ResNets` 的残差函数比其对应网络更小。第 `3.1` 节表明，残差函数可能比非残差单元更接近零。我们还注意到，更深的 `ResNets` 响应幅度较小，如图 `7` 中 `ResNet-20、56` 和 `110` 之间的对比。当层数较多时，`ResNets` 的单层倾向于产生恒信号。

## 探索超过 1000 层

我们探索了一个超过 `1000` 层的极深模型。我们设置 `$n=200$`，产生一个 `1202` 层的网络，该网络以残差方式进行训练。我们的方法显示没有优化困难，这种 `$10^3$` 层网络能够达到小于 `0.1%` 的训练误差（图 `6`，右侧）。其测试误差仍然相当良好 (`7.93%`)，见表 `6`。

但在这种极深模型上仍然存在问题。该 `1202` 层网络的测试结果差于我们的 `110` 层网络，尽管两者的误差相似。这是由于过拟合。超过 `1202` 层的网络在这些数据上可能必然是不准确的 (`19.4M`)。应用了强正则化（如 `max [9]` 或 `dropout [13]`）以获得最佳。在本文中，我们没有使用 `max/dropout`，仅通过跟踪优化困难来通过简单正则化加深架构。结合更强的正则化可能会提高我们的结果，我们将在未来展示。

## 4.3. Pascal 和 MS COCO 上的目标检测

我们的方法在其他识别任务上具有良好的泛化性能。表 `6` 和 `8` 显示了 `Pascal VOC 2007` 和 `2012 [5]` 以及 `COCO [26]` 上的检测基准结果。我们采用 `Faster R-CNN [32]` 作为检测方法。我们在 `VGG-16` 和 `ResNet-101` 实现中实现了它。由于两个模型的使用相同，因此提升只能归功于更好的网络。在挑战性的 `COCO` 数据集上，我们分别观察到 `COCO` 的标准 `mAP[5, 95]` 增长了 `0.9%`，相对提升了 `28%`。这一增益完全归于学习到的表表示。

基于深度残差网络，我们在 `ILSVRC & COCO 2015` 竞赛的多个赛道中获得了第一名：图像检测、定位检测和 `COCO` 分割。细节见附录。

## 参考文献

[1] Y. Bengio, P. Simard, and F. Prasconi. Long-term dependencies with gradient descent difficult. IEEE Transactions on Neural Networks, 15(2):157-166, 1994.

[2] C. Bishop. Neural networks for pattern recognition. Oxford university press, 1995.

[3] U. W. Briggs, F. S. McCormick, and A. Multigrid Tutorial. Siam, 2006.

[4] K. Katiehah, V. Lempitsky, A. Voloshinin, and A. Zisserman. Deep learning is in detail: an evaluation of recent feature encoding methods. In ICML, 2012.

[5] N. Deanville, Y. Lin, G. K. Walsh, J. Wei, and A. Zhang. The Pascal Visual Object Classes (VOC). IJCV, pages 305–338, 2010.

[6] G. Richard, F. Lin, and N. LCC. In ICCV, 2015.

[7] Y. Bengio and Y. Bengio. Understanding the difficulty of training deep recurrent neural networks. In AISTATS, 2010.

[8] J. I. Goodfellow, D. Warde-Farley, M. Courville, and Y. Bengio. Generative adversarial nets. arXiv:1406.2663, 2014.

[9] I. Goodfellow. Deep learning with constrained time cost. In CVPR, 2015.

[10] K. He, X. Zhang, S. Ren, and J. Sun. Deep learning into residuals: Supervised learning with residual learning. In CVPR, 2016.

[11] G. E. Hinton, N. Sutskever, and R. Salakhdin. Deep neural networks by backpropagation and fast features. arXiv:1206.0992, 2012.

[12] K. He, X. Zhang, S. Ren, and J. Sun. Delving into residuals: learning on image classification. In NIPS, 2016.

[13] S. Hochreiter and J. Schmidhuber. Long short-term memory. Neural networks, 9(8):1737–1755, 1997.

[14] Y. Bengio and N. Srivastava. Dropout: regularizing deep neural networks by dropping units. In ICML, 2012.

[15] H. Jegou, M. Douze, P. Perez, and C. Schmid. Aggregating features for object detection. In CVPR, 2015.

[16] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[17] Y. Fergus. Deep learning: 2009.

[18] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[19] Y. Fergus. 2009.

[20] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[21] Y. Fergus. 2009.

[22] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[23] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[24] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[25] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[26] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[27] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[28] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[29] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[30] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[31] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.

[32] Y. Jia, E. Shelhamman, D. Jhai, R. Karpathy, J. Rich, S. Guadarrama, and T. Darrell. Convolutional architectures for feature embedding. In arXiv:1408.5095, 2014.
