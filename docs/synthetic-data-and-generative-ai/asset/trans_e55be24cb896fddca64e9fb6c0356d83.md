
我在我的 `GAN` 增强版中解决了这些问题。要使用它，请在 [10.7.2 节](#Chp010_169-201_B978044321857600014X.xhtml#s0115) 的 Python 代码中设置 `mode='Enhanced'`。给定一个对应特定 `seed` 的 `GAN` 实例，它将根据您选择的距离函数保留最佳合成数据（换句话说，由 `Keras` 产生的最佳模型），而不是最后一个 epoch 获得的、且高度依赖损失函数的数据。在我的代码中，我对擅长模仿真实数据集中相关结构的合成数据感兴趣，因此编写了自己的函数 `gan_distance`，用于测量每个 epoch 中真实数据与合成数据之间的相关距离。它基于 `correlation matrix distance`。当然，您可以修改该函数以满足您自己的需求。

迄今所述的增强技术属于前端：它们不修改 `GAN` 的内部组件。它们也易于理解和实现，有助于可解释 AI。但您也可以深入 `GAN` 的黑盒内部，修改一些底层组件。`Keras` 库在一定程度上便利了这一点，它提供了一些工具，例如自定义损失函数。这些后端增强需要更多关于 `GAN` 工作原理的知识。您可以编写自己的函数 `custom_distance`，并通过在 `GAN` 模型中选择选项 `model.compile(metrics=[custom_distance])` 让 `Keras` “消化”它。请参阅此处[文档](https://www.tensorflow.org/guide/keras/save_and_serialize)和此处[文档](https://datascience.stackexchange.com/questions/116811/define-a-custom-distance-between-classes-in-keras)以获取更多资料。另一种可能性是使用自适应 `learning rate`；请看这里[如何操作](https://towardsdatascience.com/learning-rate-schedule-in-practice-an-example-with-keras-and-tensorflow-2-0-2f48b2888a0c)。最后，借助 `reinforcement learning` [[Wiki](https://en.wikipedia.org/wiki/Reinforcement_learning)] 奖励那些最小化您自己的前端距离函数（而非默认损失函数）的配置，这将很有帮助，参见 [[11]](#Chp010_169-201_B978044321857600014X.xhtml#br0055)。配置是指在每个 epoch 结束时获得的更新模型及其更新后的权重集合。

总之，我的实现增强版具有以下升级：

- 可复现的结果
- 单独处理缺失数据
- 运行多个版本，每个版本使用不同的 `seed`，采用最佳版本
- 二进制数据：0 和 1 由两个不同的 `GAN` 处理（未来版本可用）
- 当真实数据与合成数据之间的自定义距离最小时停止

最后一项功能需要在 Python 代码中设置 `mode='Enhanced'`。增强版性能的提升可见于 [图 10.2](#Chp010_169-201_B978044321857600014X.xhtml#f0025)，对比了标准模式（左）与增强模式（右）。此外，[图 10.7](#Chp010_169-201_B978044321857600014X.xhtml#f0060)（右图）中的 `GAN` 合成使用了增强模式。它展示了一个表格数据示例，其中 `GAN` 优于 Copula。另一项升级是将 Copula 方法与 `GAN` 融合。这在 `SDV` 库中实现；请参阅 [10.4.1 节](#Chp010_169-201_B978044321857600014X.xhtml#s0050) 中的代码。最后，正如本节开头所讨论的，对去相关数据应用 `GAN`（随后进行重相关步骤）保证保留真实数据中的确切相关结构。此操作完全可逆。

### 10.4.6 通过层次聚类或连通分量进行特征聚类

对于对 `feature clustering` 算法感兴趣的人，文献中已很好地涵盖了该主题；例如参见 [[6]](#Chp010_169-201_B978044321857600014X.xhtml#br0030)。这里我提供一种简单方法，即在相关矩阵中寻找 `connected components` [[Wiki](https://en.wikipedia.org/wiki/Component_(graph_theory))]。主程序是对 [16.2.4.3 节](#Chp016_293-327_B9780443218576000205.xhtml) 中用于检测最近邻图中连通分量的版本的轻微改编。如果两个特征的相关性高于 Python 代码中名为 `threshold` 的某个参数，则它们相连。一个特征簇就是相关无向图 `undirected graph` 的一个连通分量。

我将该方法应用于医疗数据集（真实数据），使用 [图 10.4](#Chp010_169-201_B978044321857600014X.xhtml#f0035) 底部的相关矩阵，设 `threshold=0.4`。检测到五个特征簇：{0, 7}, {1, 4, 8}, {3, 5}, {2}, {6}![Image](images/B978044321857600014X/si21.png)。例如，特征 0 对应妊娠次数，1 对应葡萄糖，2 对应血压，依此类推。这意味着，得益于这 5 个簇之间的低相关性，可以对每个簇分别应用 Copula 或 `GAN`，从而将一个 9D 问题拆分为多个小维度问题，每个问题的维度不超过 3。Python 代码 `featureClustering.py` 也在 GitHub 上，[这里](https://github.com/VincentGranville/Main/blob/main/featureClustering.py)。

基于相关矩阵的特征聚类具有尺度不变性。您也可以通过交换特征和观测值，将此方法用于传统聚类。例如，针对 `wide data`（宽数据），即观测值较少（假设少于 ![Image](images/B978044321857600014X/fx015.jpg)）但特征很多的情况，如临床试验。

我提供了特征聚类过程的两种实现。第一种使用 `Scipy` 库进行 `hierarchical clustering`。在 [图 10.6](#Chp010_169-201_B978044321857600014X.xhtml#f0050) 中，`ρ` 为相关性，X 轴为特征标签。代码可在 GitHub 获取，[这里](https://github.com/VincentGranville/Main/blob/main/featureClusteringScipy.py)。第二种基于连通分量。代码也可在[这里](https://github.com/VincentGranville/Main/blob/main/featureClustering.py)获取。

![图 10.6 使用 Scipy 进行特征聚类；Y 轴为 1 − |ρ|。](images/B978044321857600014X/gr013.jpg)

图 10.6 使用 Scipy 进行特征聚类；Y 轴为 1 − |`ρ`|。

![](images/B978044321857600014X/gr011.jpg)

以下实现基于连通分量。它提供与基于层次聚类和树状图的前一种实现相同的结果。[图 10.6](#Chp010_169-201_B978044321857600014X.xhtml#f0050) 展示了层次聚类版本。

![](images/B978044321857600014X/gr014.jpg)

## 10.5 GAN 与 Copula 方法的比较

在医疗数据集上，Copula 方法表现更好，如 [图 10.3](#Chp010_169-201_B978044321857600014X.xhtml#f0030) 和 [图 10.4](#Chp010_169-201_B978044321857600014X.xhtml#f0035) 所示，且速度快得多。与我在 [10.2.1 节](#Chp010_169-201_B978044321857600014X.xhtml#s0020) 中的 Copula 方法不同，许多 `GAN` 实现无法产生可复现的结果。然而，我在 [10.7 节](#Chp010_169-201_B978044321857600014X.xhtml#s0105) 中的实现解决了这个问题。此外，`GAN` 对初始配置（即 `seed`）非常敏感，且从一个 epoch 到下一个 epoch 的振荡相当大，即使经过 ![Image](images/B978044321857600014X/fx015.jpg) 个 epochs 后也是如此。后一个问题实际上可能是一个优势：尝试不同的 seed 和/或使用基于任意给定 epoch 中合成质量的停止规则，可带来显著改进。
