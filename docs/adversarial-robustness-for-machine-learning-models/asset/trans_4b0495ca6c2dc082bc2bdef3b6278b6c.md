

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_217_0.png)

图 18.1 Voice2Series (V2S) 框架示意图（Yang et al., 2021b）：（a）可训练重编程层；（b）预训练声学模型（AM）；（c）源标签-目标标签映射函数。

重编程样本 \(x'_t\) 的表达式为

```
\(x'_t = \mathcal{H}(x_t; \theta) := \text{Pad}(x_t) + \underbrace{M \odot \theta}_{\triangleq \delta},\) (18.1)
```

其中 \(\text{Pad}(x_t)\) 是一个零填充函数，输出维度为 \(d_S\) 的零填充时间序列。\(x_t\) 在 \(x'_t\) 中放置的位置是一个设计参数，如 Yang et al. (2021b) 所讨论。术语 \(M \in \{0, 1\}^{d_S}\) 是一个二进制掩码，指示 \(x_t\) 在其零填充输入 \(\text{Pad}(x_t)\) 中的位置，其中 \(M\) 的第 \(i\) 个元素为 0 表示 \(x_t\) 存在（即该元素不可重编程），否则为 1（即该元素未被占用，因此可重编程）。运算符 \(\odot\) 表示逐元素乘积。最后，\(\theta \in \mathbb{R}^{d_S}\) 是一组用于对齐源域和目标域数据分布的可训练参数。术语 \(\delta \triangleq M \odot \theta\) 表示 V2S 重编程的可训练加性输入变换。为便于表示，我们将省略填充记法，并简单地使用 \(x_t + \delta\) 来表示重编程的目标数据，将运算“+”视为零填充广播函数。

预训练模型与输出标签映射。我们选择一个预训练的深度声学分类模型作为源模型 \(f_S\) 用于模型重编程。我们假设源模型以 softmax 作为最终层，并为每个源标签输出非负置信度分数（预测概率）。利用 (18.1) 中描述的变换数据输入 \(\mathcal{H}(x_t; \theta)\)，我们可以获得源模型 \(f_S\) 对重编程目标数据样本 \(x_t\) 的类别预测，表示为

```
\(P(y_s | f_S(\mathcal{H}(x_t; \theta))) \text{ for } y_s \in \mathcal{Y}_S.\) (18.2)
```

接下来，如图 18.1 所示，我们分配一个（多对一）标签映射函数 \(h\) 将源标签映射到目标标签。对于目标标签 $y_t \in \mathcal{Y}_T$，其类别预测将是分配给它的一组源标签上的类别预测的平均值。我们使用术语 $P(h(\mathcal{Y}_S)|f_S(\mathcal{H}(x_t; \theta)))$ 来表示相关真实目标标签 $y_t = h(\mathcal{Y}_S)$ 上目标任务的预测概率。最后，我们通过优化以下目标来学习数据输入重编程的最优参数 $\theta^*$：

$$ \theta^* = \underset{\theta}{\text{argmin}} \underbrace{-\log P(h(\mathcal{Y}_S)|f_S(\mathcal{H}(x_t; \theta)))}_{\text{V2S loss } \triangleq L}, \quad (18.3) $$

其中 $h(\mathcal{Y}_S) = y_t$

该优化将通过最小化在所有目标域训练数据对 $\{x_t, y_t\}$ 上评估的经验损失（V2S 损失 $L$）来实现，以求解 $\theta^*$。

在实践中，Yang et al. (2021b) 发现，与一对一标签映射相比，多对一标签映射可以提高重编程准确性。下面我们通过一个具体例子说明如何在 V2S 重编程中使用多对一标签映射。考虑将口语词项 AM 重编程用于 ECG 分类的情况。我们可以选择将源任务中的多个（但不重叠）类别（例如，AM 类别中的 “yes”、“no”、“up”、“down”）映射到目标任务中的每个类别（例如，ECG 类别中的 “Normal” 或 “Ischemia”），从而得到一个特定的映射函数 $h$。令 $\mathcal{B} \subset \mathcal{Y}_S$ 表示映射到目标标签 $y_t \in \mathcal{Y}_T$ 的源标签集合。那么基于 V2S 重编程的 $y_t$ 的类别预测是分配给源标签的聚合预测，定义为

$$ P(y_t|f_S(\mathcal{H}(x_t; \theta)) = \frac{1}{|\mathcal{B}|} \sum_{y_s \in \mathcal{B}} P(y_s|f_S(\mathcal{H}(x_t; \theta)), \quad (18.4) $$

其中 $|\mathcal{B}|$ 表示 $\mathcal{B}$ 中的标签数量。

算法 5 总结了 V2S 重编程的训练过程。

*实验结果。* 使用两个预训练语音模型 V2S$_a$ 和 V2S$_u$ 作为重编程的源模型。图 18.2 显示了它们的端到端模型架构，详情请参见 (Yang et al., 2021b)。在标准 UCR 时间序列分类基准（Dau et al., 2019）上的测试表明，Yang et al. (2021b) 显示 V2S 在 30 个数据集中的 19 个上优于或持平于最佳报告结果，表明 V2S 是一种原则明确且有效的时间序列分类方法。

```
Algorithm 5 Voice to Series (V2S) reprogramming.
1: Inputs: Pretrained acoustic model f_S, V2S loss L in (18.3), target domain training data {x_i^t, y_i^t}_{i=1}^n, mask function M, multilabel mapping function h(·), maximum number of iterations T, initial learning rate α
2: Output: Optimal reprogramming parameters θ*
3: Initialize θ randomly; set t = 0
4: #Generate reprogrammed data input
5: H(x_i^t; θ) = Pad(x_i^t) + M ⊙ θ ∀ i = {1, 2, ..., n}
6: #Compute V2S loss L from Eq. (18.3)
7: L(θ) = -1/n \sum_{i=1}^n log P(y_i^t | f_S(H(x_i^t); θ))
8: #Solve reprogramming parameters
9: Use ADAM optimizer (Kingma and Ba, 2015) to solve for θ* based on L(θ)
```

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_219_0.png)

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_219_1.png)

图 18.2. V2S 模型架构：（a）V2Sa（de Andrade et al., 2018）和（b）V2Su（Yang et al., 2021a）。

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_219_2.png)

图 18.3. 使用草莓训练集（Holland et al., 1998）和 V2Sa 的 logit 表示的 tSNE 图，适用于 V2S 重编程前后以及微调迁移学习（TF_a）的情况。

我们使用 t-分布随机邻域嵌入（tSNE）（Van der Maaten and Hinton, 2008）来可视化重编程前后以及迁移学习基线（TF_a）的草莓训练集（Holland et al., 1998）的 logit 表示。如图 18.3 所示，重编程后，tSNE 结果显示不同目标类别的嵌入之间有明显的分离，表明 V2S 确实学习了有意义且具有区分度的数据表示，以将预训练声学模型重编程用于时间序列分类。另一方面，迁移学习的嵌入可视化显示类间可分性较低。

## 18.2 将通用图像模型重编程用于医学图像分类

在本节中，我们将从两方面介绍模型重编程的能力：（i）重编程黑盒模型的能力；（ii）将通用图像模型（例如，在 ImageNet 上训练的深度神经网络分类器）重编程用于医学图像分类的能力，如 Tsai et al. (2020) 所示。

### 黑盒和资源受限环境。

原始 AR 方法（Elsayed et al., 2019）假设对预训练（源）模型有完整了解，这排除了重编程访问受限的训练有素 ML 模型的能力，例如仅根据查询数据输入揭示模型输出的预测 API 或专有软件。此外，虽然数据对大多数 ML 任务至关重要，但在医疗应用等一些场景中，大规模数据收集可能成本高昂，甚至不可能，尤其是涉及临床试验、专家注释或隐私敏感数据时。因此，在没有迁移学习的情况下，数据稀缺的实际限制可能会阻碍复杂（大规模）ML 模型（如深度神经网络 DNN）的效力。最后，即使有适量数据，研究人员也可能没有足够的计算资源或预算来训练与商业 ML 模型一样大的 DNN，或在大规模预训练 ML 模型上执行迁移学习。

### 黑盒重编程。

图 18.4 提供了 Tsai et al. (2020) 提出的黑盒对抗重编程（BAR）方法的概述。为适应黑盒环境，使用基于迭代输入-输出模型响应的零阶优化（Liu et al., 2020a）来优化与输入变换函数相关的参数，类似于第 3 章中采用的黑盒规避攻击的方法论。类似于第 18.1 节中的端到端重编程框架，我们可以使用一种输入变换函数，例如通用可训练

