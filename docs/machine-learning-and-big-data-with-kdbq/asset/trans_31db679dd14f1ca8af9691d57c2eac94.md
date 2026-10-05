

## 经济学：基于代理的计算模型
591

因此，我们已经完整指定了 Ising 模型的主要对象。我们创建了一个输入参数字典，以便使用收敛操作：

```
isingModel:
(`nGrid`nAgents`alpha`beta`.getSquareAround`wallStreet`;probPositiveSpin`
priceIsing!)(`nGrid;nAgents;alpha;beta;quantQ.ephys;
		getSquareAround`wallStreet`;quantQ.ephys.probPositiveSpin;priceIsing`
));
```

现在，我们已经具备了定义主函数所需的所有要素，该函数执行 Ising 模型中的中的一步迭代。在这一步中，将随机选择一个交易者，并根据上一节描述的动力学机制更新情绪。当情绪更新时，会生成一个新价格。`oneRunning` 函数将上一个代码段中的字典作为参数，更新它并返回该对象。该函数返回：

```
quantQ.ephys.oneRunning([:isingModel]
// isModel -- 包含所有数据的对象
// 随机选择一个候选者进行更新
pivot:2[`nGrid`]
// 恢复价格
price:lastIsingModel[`priceIsing`][price];
tlastIsingModel[`priceIsing`][t];
// 计算局部能量
term1:(first spin from isingModel[`wallStreet`] where coord in
elist pivot);
ex-spin from isingModel[`wallStreet`] where coord in isingModel[`nwallStreet`]
		getSquareAround[isingModel[`nGrid`];pivot];
term2:isingModel[`alpha`][price]first spin from isingModel[`nwallStreet`]
where coord in enlist pivot;
// 正向自旋概率
pos:isingModel[`probPositiveSpin`][isingModel[`beta`];localEnergy];
// 设置新自旋
newSpin:$([`first 1.0)<cPos;1;-1];
isingModel[`update`]:update spin:newSpin from isingModel[`wallStreet`]
where coord in enlist pivot;
// 在价格线表中更新价格和时间
isingModel[`priceIsing`]:isingModel[`priceIsing`] upsert(t+1);sum exec
		spin from
			isingModel[`wallStreet`];
isingModel;
```

一次 Ising 模型迭代的运行可以这样执行：

```
quantQ.ephys.oneRunning([isingModel])
```

我们并不以字典的形式发布输出。我们感兴趣的是运行大量的步骤，为此我们使用收敛操作将输出保存到一个新对象中：

```
isingModelResult=:quantQ.ephys.oneRunning[/1000;isingModel];
```

## 592 机器学习

![](img/97f7581128bd0bdf85683d4c69d94242_616_0.png)

图 29.2 Ising 模型的价格过程

感兴趣的结果是价格过程，可以通过从 `isingModel` 对象中选择 `priceIsing` 表来查看：

```
isingModelResult['priceling']
```

图 29.2 包含了上述评估的 Ising 模型价格过程。视觉检查发现，由模拟 Ising 模型驱动的价格会发生突然下降，如索引时间 400 左右所示。然而，为了证实这些化事实（stylised facts），必须对大量的模拟进行适当的统计分析，并确认这些事实，例如收益的胖尾、序列相关性和波动性的长期记忆。

## 29.3 结论

因此我们可以得出结论，q 足够灵活，可以创建并模拟基于代理的计算模型。本节介绍的模型简单直接。它缺乏任何面向对象的方法，而这在代理建模社区中非常流行。通常情况下，代理是对象，代理之间的链接也是对象。例如，参考基于 C++ 的库 Zarja zar，它将代理和代理之间的链接定义为对象，其属性可以以模块化的方式定义。

在我们的方法中，我们的目标是展示除了与 q 连接的时间序列分析之外，处理基于代理模型的可能性。

## 经济物理学：基于代理的计算模型 593

本节介绍的模型仍然可以回答许多问题的问题，即与临界现象的出现有关的问题。介绍的模型可以通过包含多个资产并通过代理利益的相关性来分析价格相关性进行扩展。

模型捕捉金融时间序列化事实的能力为所提模型提供了另一个用途：作为用于模型/分析测试的随机金融时间序列生成器。这在需要合成数据来开发例如分析套件并测试其在真实数据下的性能时特别有用。此外，模型可以被设置为数据生成器，由行情机捕获并存储在数据库中——数据的另一种潜在用途。

我们鼓励读者运行自己的模拟，并考虑数值研究以下研究问题（但不限于）：

- 如果交互是随机的会？每次执行一次随机交互。
- 如果交易者可以与更多交易者交互会？扩展每个交易者周围的区域。使交互的交易者数量变为随机。
- 如果交易者可以交易多种资产会？扩展资产数量。
- 如果交易者可以交易多个单位会？扩展模型以处理非均匀交易量。
- 如果系统是庞大的会？扩展模型。
- 系统的化事实是什么？

## 618 结语

## 619 第 30 章

数据科学和机器学习被频繁提及。

