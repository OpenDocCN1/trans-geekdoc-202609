

# 452

结果存储在对象 modelA 中，它本质上是一个表：

```
meta modelA
c      | t f a
      |--|--|-
outout     | J
parsHid2Out|
parsIn2Hid |
Error    | f
Counter | j
```

该表每个迭代步骤都有一行。第一行是例程的初始化。列对应于定义的 `pars` 字典。让我们关注 `Error` 并分析它在算法迭代过程中是如何演变的。这可以通过以下方式实现：

```
select Counter, Error from modelA where i>0
```

其中我们排除了表的第一行。图 22.1 描绘了神经网络学习过程中的误差。误差随迭代索引绘制的。排除第一行的原因是 `Error` 被设置为 0.0，这没有任何意义。在学习的初始阶段（大约前 20 步），误差会下降。然后，随着模型的不断改进，误差下降的斜率开始放缓。从大约 200 步开始，模型的改进速度显著变；模型进入了

![](img/97f7581128bd0bdf85683d4c69d94242_476_0.png)

**图 22.1** 四个带有异或操作二进制变量分类问题的学习路径（误差）

一个没有进一步进展的平台。理想的学习应该避免过度训练。训练应在到达平台之前停止。

一旦我们训练了模型，我们需要在测试数据集上验证模型的有效性。我们的数据集在可能值的空间内相当简单。特征可以取 16 种不同的配置，我们的样本量远超需求。我们鼓励读者在特征中引入微小噪声后重复练习。

我们的关注更多在于实现问题；我们在训练结束时提取模型参数和权重（这是我们在不监控性能选项下观察到的）。权重恢复如下：

```
pHid2OutA: exec last parsHid2Out from modelA;
pin2HidA: exec last parsIn2Hid from modelA;
```

定义一个包含特征空间所有 16 种配置的表：

```
tmpA:flip t cross t cross t:(-1.0 1.0);
tabA:update y:neg[2][]x1+x2+x3+x4;1;0] from ([][] x1: tmpA[0]; x2: tmpA[1]; x3: tmpA[2]; x4: tmpA[3]);
```

我们列出该表：

```
tabA

x1 x2 x3 x4 y
-1 -1 -1 -1 0
-1 -1 1 1 1
-1 -1 1 -1 1
-1 -1 1 1 0
-1 1 -1 -1 0
-1 1 -1 1 1
-1 1 1 -1 0
-1 1 1 1 0
1 -1 -1 -1 0
1 -1 -1 1 0
1 -1 1 1 0
1 1 -1 -1 0
1 1 1 -1 0
1 1 1 1 0
```

我们在表 `tabA` 中添加一个额外列作为因变量的预测值；我们称之为 `yPredict`。预测仅仅是将神经网络层层堆叠并在输入数据上对其评估：

```
tabA: update yPredict:quantQ.nn.funcNN[classifier]([1.0,.:quantQ.nn.
s sigmoid((1.0,.'flip[tmpA]) mmu pin2HidA]) mmu pHid2Out) from tabA;
```

更新后的表以及预测的有效性在这种情况下可以检查：

| x1 x2 x3 x4 yPredict |
|---|---|---|---|---|
| -1 -1 -1 -1 0 | 0.010704 |
| -1 -1 1 1 1 | 0.9987026 |
| -1 -1 1 -1 1 | 0.9980297 |
| -1 -1 1 1 0 | 0.00034203 |
| -1 1 -1 -1 1 | 0.9936351 |
| -1 -1 1 -1 0 | 0.00013963 |
| -1 1 -1 -1 0 | 0.00075248 |
| -1 1 1 1 0 | 0.00040118 |
| 1 -1 -1 -1 0 | 0.9980993 |
| 1 -1 -1 1 0 | 0.00036194 |
| 1 -1 1 1 0 | 0.00021807 |
| 1 1 -1 -1 0 | 0.00021807 |
| 1 1 1 -1 0 | 0.00202497 |
| 1 1 1 1 0 | 0.00049725 |
| 1 1 1 -1 0 | 0.439039 |
| 1 1 1 1 0 | 0.073104 |

预测值是 `[0, 1]` 之间的实数值。我们可以进一步将数字转换为 0 和 1，以获得整数格式。表 `B` 显示了 `y` 和 `yPredict` 之间的完美一致，将接近 1 的值视为真（true）。

## 22.3 M 类分类

第二个示例涉及 M 分类，因变量可以取 M 个值。我们在 鸢尾花数据上测试我们的实现。回想数据的变量含义：

- 特征 1：花长（cm）
- 特征 2：花宽（cm）
- 特征 3：瓣长（cm）
- 特征 4：瓣宽（cm）
- 因变量：类别（Setosa, Versicolor, Virginica）

数据有 150 行。我们假设数据在本地驱动器（根目录）。首先，我们加载数据：

```
irisData("irisData.csv")
```

并验证带有所有变量名的表结构：

| meta IrisData c | t | a |
|---|---|---|
| sepalLength | f | |
| sepalWidth | f | |
| petalLength | f | |
| petalWidth | f | |
| class | s | | |

进一步，我们将数据集分为 100 个观测值的训练样本和 50 个观测值的测试样本。由于数据集本身可以根据类别排序，我们对数据进行随机划分：

```
randomDraw100:count irisData;irisDataIN: select from irisData where i in randomDraw100;irisDataOUT: select from irisData where not i in randomDraw100;
```

我们验证训练样本中包含了三个类别：

```
distinctClass:distinct irisDataIN`class;
```

- Setosa
- Versicolor
- Virginica

我们使用隐藏层中的 8 个神经元来训练模型，学习率参数为 0.01，并运行算法 1000 步。我们监控算法的收敛情况：

```
modelB:quantQ.nn.modelNN[(flip (irisDataIN`allWidth;irisDataIN`length;irisDataIN`sepalWidth;irisDataIN`length;irisDataIN`petalWidth);quantQ.nn.encoderMulti[distinctClass] irisDataIN`class;8;count;0.01;1;multiClassifier];
```

图 22.2 描绘了鸢尾花数据集神经网络学习过程中的误差。学习模式在迭代期间显示出复杂的阶段。

![](img/97f7581128bd0bdf85683d4c69d94242_479_0.png)

图 22.2 鸢尾花数据集 M 类分类的学习路径（误差）

改进有些波动，并在误差恶化时显示出短暂的爆发，整体改进是显而易见的。在学习过程的最后阶段，误差在两个值之间波动，两者都代表改进。这表明算法无法停留在最优值，而是在周围略微震荡。可以通过在迭代过程的最后阶段降低学习率来防止。

数据提取如下：

```
select Counter, Error from modelB where i>0
```

进一步，我们在训练过程中提取模型参数：

```
pHid2Out: exec last parsHidOut from modelB;
pIn2Hid: exec last parsIn2Hid from modelB;
```

我们将输出数据排列到新表 `tabB` 中，并添加一个编码因变量：

```
tabB:update classEnc: ..quantQ.nn.encoderMulti[distinctClass] class from irisData;
```

然后，我们使用训练好的模型预测鸢尾花的类别。预测通过堆叠网络完成：

```
tabB: update classPredict: ..quantQ.nn.funcNN['multiClassifier'][(1.0.,;
	quantQ.nn.sigmoid(1.0, 'Flip'(irisDataOUTlength,irisDataOUTsepalWidth,irisDataOUTpetalLength,irisDataOUTpetalWidth))]
mmu pHid2Out from tabB;
```

预测的 `classPredict` 是三个值的数组，每个值表示给定观测属于给定类别的概率。我们可以这样检查预测模型的准确性：

```
exec sum {(where y=max y)(where x=max x)}[classPredict;classEnc] from
tabB
```

列表 47

模型预测了 50 个案例中的 47 个，准确率为 94%。让我们进一步检查表本身；为了说明查看 10 行：

```
10select classPredict, classEnc from tabB
```

classEncPredict classEnc
--------------------------------------
0.00434627 0.9956356 1.813319-e005 0 1
0.9973335 0.00266495 1.273018-e009 1 0
0.00607452 0.9939817 1.008583-e005 0 1
0.00607452 0.9939817 1.008583-e005 0 1
3.073432-e005 0.6700523 0.3299169 0 1
0.00988061 0.9901043 7.592463-e006 0 1
0.00013963 0.99986037 0 1

