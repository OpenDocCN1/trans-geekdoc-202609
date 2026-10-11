
首先，我们加载相关数据。这些数据包含在一个文本文件中，其中每一行对应我们数据集的一个样本（第 22 号染色体的 101 碱基片段）。每一行包含样本 ID，后跟一个数字，指示该区域在 HepG2 细胞中有多容易被访问。我们将其读入一个 Python 字典：

```
span_accessibility = {}

for line in open('accessibility.txt'):
    fields = line.split()
    span_accessibility[fields[0]] = float(fields[1])
```

我们选择的模型与前一节几乎相同，仅有两个细微变化。首先，我们需要一个额外的输入来接收可访问性值，该值由每个样本的一个数字组成：

```
accessibility = layers.Feature(shape=(None, 1))
```

接下来，我们将可访问性值纳入计算。为此有多种方法。在本例中，我们使用一种特别简单的方法。在前一节中，我们将最后一个卷积层的输出展平，然后将其作为输入传给一个计算结果的 Dense 层。

```
logits = layers.Dense(out_channels=1, in_layers=layers.Flatten(prev))
```

这里我们做同样的操作，然后再加上可访问性卷积层：

```
prev = layers.Concat([layers.Flatten(prev), accessibility])
logits = layers.Dense(out_channels=1, in_layers=prev)
```

模型搭建完成！现在对其进行训练。

此时存在一个问题：我们的模型有两个不同的特征层！到目前为止，我们的模型恰好有一个特征层、一个标签层，以及可能还有一个权重层。它们通过调用 `fit(dataset)` 进行训练，该方法会自动将正确的数据与每一层关联：数据集的 X 对应特征，y 对应标签，w 对应权重。然而，当模型拥有多个特征时，这行不通。

借助 DeepChem 的一项高级功能，可以解决这个问题。我们不再向模型传递数据集，而是可以编写一个 Python 生成器函数，用于迭代批次。每个批次由一个字典表示，其键为输入层，其值为将用于这些层的 NumPy 数组：

```
def generate_batches(dataset, epochs):
    for epoch in range(epochs):
        for X, y, w, ids in dataset.iterbatches(batch_size=1000, pad_batches=True):
            yield {
                features: X,
                accessibility: np.array([span_accessibility[id] for id in ids]),
                labels: y,
                weights: w
            }
```

请注意，数据集为我们处理了批次的迭代。它提供每个批次的数据，我们据此构建模型所需的输入。

训练和评估按原方式进行。我们只是用生成器替换了数据集：

```
for i in range(20):
    model.fit_generator(generate_batches(train, 10))
    print(model.evaluate_generator(generate_batches(train, 1), [metric], labels=[labels], weights=[weights]))
    print(model.evaluate_generator(generate_batches(valid, 1), [metric], labels=[labels], weights=[weights]))
```

结果如[图 6-3](#Chapter06_9783960103516.xhtml#abb6-3)所示。与忽略染色质可访问性的模型相比，训练集和验证集上的得分均有所提高。ROC AUC 得分现在为训练数据 0.91，验证数据 0.80。

![image](Images/p96-1.png)

*图 6-3：考虑染色质可访问性时，训练数据（虚线）和验证数据（实线）在训练过程中 ROC AUC 得分的变化*。

### RNA 干扰

对于最后一个示例，我们转向 RNA。与 DNA 类似，它是一种由四种称为碱基的重复单元组成的聚合物。严格来说，四个碱基中有三个与其 DNA 版本几乎相同，仅多一个氧原子不同。第四个碱基略有不同。RNA 不含胸腺嘧啶 (T)，而是含有一种称为尿嘧啶 (U) 的碱基。当 DNA 序列被转录为 RNA 时，每个 T 都会被 U 替换。

碱基 G 和 C 是*互补*的，因此它们有很强的结合倾向。同样，碱基 A 和 T（或 U）也是互补的。如果存在两条 DNA 或 RNA 链，且一条链的每个碱基都与另一条链对应位置的碱基互补，则两条链会结合在一起。这一事实在许多生物过程中起关键作用，包括转录和翻译，以及细胞分裂时的 DNA 复制。

这也是*RNA 干扰*的核心。这一现象直到 1990 年代才被发现，并因此获得了 2006 年诺贝尔奖。一段序列与信使 RNA 某部分互补的短 RNA 片段，可以与该 mRNA 结合。当这种情况发生时，mRNA 被“沉默”，从而阻止其被翻译成蛋白质。执行沉默功能的分子称为小干扰 RNA (siRNA)。

然而，该过程远不止于此。RNA 干扰是一种复杂的生物学机制，而非仅仅是两条孤立的 RNA 链碰巧粘在一起的副产物。它始于 siRNA 与一组称为*RNA 诱导沉默复合体* (RISC) 的蛋白质结合。RISC 利用 siRNA 作为模板，在细胞中寻找并降解匹配的 mRNA。这既作为基因表达调控的机制，也作为抗病毒防御机制。

此外，它还是生物学和医学中的强大工具。借助它，任何目标基因都可以被暂时“关闭”。它可用于治疗疾病，或用于研究基因失活时会发生什么。只需确定要阻断的 mRNA，选择其一个短片段，并创建一个具有互补序列的 siRNA 分子。

当然，事情没那么简单。人们不能随便随机选择 mRNA 的任意片段，因为（当然！）RNA 分子不仅仅是由四个字母组成的抽象模式。它们是具有个体特性的实体，而这些特性取决于序列。一些 RNA 分子比其他分子更稳定。一些比其他分子更强地结合其互补序列。一些折叠成的形状使得 RISC 难以结合。因此，一些 siRNA 序列比其他序列效果更好，如果您想将 RNA 干扰作为工具使用，就必须知道如何挑选一个好的！

生物学家已经开发出许多用于选择 siRNA 序列的启发式规则。例如，最开始的碱基应该是 A 或 G，G 和 C 碱基应占序列的 30% 到 50% 等。这些经验法则很有帮助，但也许机器学习能做得更好。

我们使用一个包含 2,431 个 siRNA 分子的文库来训练模型，每个分子长 21 个碱基。^([1](#Footnote_9783960103516.xhtml#ch6fn1)) 每个分子都经过实验测试，并被标记为 0 到 1 之间的值，指示其沉默目标基因的有效程度。较小的值表示无效分子，而较高的值表示更有效的分子。模型以序列为输入，尝试预测有效性。

创建模型使用以下代码：

```
model = dc.models.TensorGraph()
features = layers.Feature(shape=(None, 21, 4))
labels = layers.Label(shape=(None, 1))
prev = features
for i in range(2):
```
