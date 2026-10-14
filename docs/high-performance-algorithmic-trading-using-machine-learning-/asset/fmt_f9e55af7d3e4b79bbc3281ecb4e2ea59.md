
在线学习的效用体现在其能够即时适应数据中的新模式和变化[18](#chap07.xhtml#footnote-076)，从而在一段时间内保持模型的相关性和准确性。当在整个数据集上训练模型的计算成本过高，或者数据集太大无法放入内存时，它特别有用。

然而，在线学习也带来了自身的挑战集。主要困难在于需要仔细设计算法以防止过拟合，因为模型不断接触新数据，而这些数据可能不代表整体分布。出于类似的原因，在在线学习中最小化异常值的影响至关重要，以防止模型朝错误方向学习。如果管理不当，异常值会不成比例地影响增量学习过程，导致预测偏差。此外，算法必须足够高效，能够在没有显著延迟的情况下实时更新模型。

在线学习确实面临着机器学习中许多最复杂的挑战，从管理非平稳环境和概念漂移到处理异常值，并确保模型随时间推移保持稳健和相关。

在交易领域，在线学习有几个引人注目的应用。例如，在高频交易（HFT）中，模型可以快速适应突然的市场变动。

在实现方面，在线学习有两个值得注意的库：`Scikit-multiflow` 和 `Vowpal Wabbit`：

• `Scikit-multiflow`[19](#chap07.xhtml#footnote-075) 为流式学习提供了广泛的工具，允许在流式数据上评估和训练模型。它秉持类似 `Scikit-learn` 的易用性理念，使广大受众都能上手。如果您刚进入这个领域，这是我推荐的工具。

• `Vowpal Wabbit`[20](#chap07.xhtml#footnote-074) 则专为高速（得益于其 C++ 实现）、大规模学习和流式数据而设计。它支持在线学习、特征哈希和核外学习等高级功能，使其适合寻求机器学习解决方案高效率和可扩展性的高级专家。

#### 使用 Scikit-multiflow 实现在线回归

我们继续使用 1 分钟频率的印度指数（NIFTY50）数据。这种日内频率不属于 HFT。然而，它足够快，可以考虑在线学习方法。我们在日内数据流上预测价差的值。

首先，安装 `Scikit-multiflow` 并导入所需工具：

```
!pip install -q scikit-multiflow
```

```
from skmultiflow.data import DataStream
from skmultiflow.meta import AdaptiveRandomForestRegressor
from skmultiflow.evaluation import EvaluatePrequential
```

```
# Initialize the AdaptiveRandomForestRegressor
regressor = AdaptiveRandomForestRegressor(n_estimators=20)
pred_stream = []
```

我们将迭代处理（`DataStream(data=...)` 函数）数据集以模拟数据流，模拟生产环境中典型的高速数据涌入。这种方法允许我们预测下一个结果，并及时使用最新数据更新（`partial_fit` 函数）模型，确保模型尽可能准确：

```
# Convert the DataFrame to a DataStream object for skmultiflow
stream = DataStream(data=np.column_stack((X_test, y_test)))

# Training the model with the streaming data
while stream.has_more_samples():
    # acquire new data
    X_stream, y_stream = stream.next_sample()
    y_pred = regressor.predict(X_stream)
    # keep track predictions
    pred_stream.append(y_pred[0])
    # refit model
    regressor = regressor.partial_fit(X_stream, y_stream)
```

```
from sklearn.metrics import mean_squared_error
mean_squared_error(pred_stream, y_test)
```

```
1.1329364818706054
```

该流及其预测结果在下图中表示：

![](images/fig-7-8.png)

该图直观展示了我们的在线回归模型在预测一系列传入数据点的价差值方面的性能。红点代表实际观测到的价差值，而绿线对应模型的实时预测。

我们可以看到，模型有效地捕捉了价差的整体趋势和波动，并随着新数据的到来动态适应。然而，仍存在一些偏差，尤其是在极端值处，这表明潜在的进一步改进领域，例如改进特征选择、超参数调优或替代在线学习方法。

## 结论

在本章结束时，我们获得了将先进机器学习技术应用于算法交易的能力。我们现在可以实现集成方法，如装袋和提升，以提高预测准确性并缓解过拟合。我们还可以应用高级回归技术，如 LASSO 和核方法，以实现更准确的金融预测。此外，我们了解了如何使用在线学习使模型适应实时市场条件，以及如何使用 `Scikit-Optimize` 微调超参数以获得最佳性能。

本章的一项关键成就是开发了一个用于预测波动率范围动态的高精度模型，从而实现更好的风险评估和交易执行。读者现在还可以使用 LASSO 进行特征选择，这提高了模型的可解释性和效率。掌握这些技能后，他们将准备好构建复杂的、数据驱动的交易策略，这些策略能动态适应复杂的市场行为，并超越传统的监督学习方法。

在下一章中，我们将探讨 AutoML 和低代码平台如何彻底改变交易策略的机器学习，使先进模型更易获得，并自动化关键步骤，如特征选择、模型调优和策略优化。我们还将考察它们在全球宏观建模中的应用，利用宏观经济特征预测利率，并将其性能与传统的手工算法进行比较。

***

**加入我们书籍的 Discord 空间**

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布和作者专场：

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/Discord.png)

# 第 8 章

**面向交易策略的 AutoML 和低代码**

## 简介

基于机器学习开发交易算法需要广泛的领域知识，不仅涉及金融，还涉及统计和机器学习技术。这种双重要求是该领域许多专业人士的重要准入障碍。然而，自动化机器学习（AutoML）和低代码平台的出现已经开始彻底改变这一领域，提供了强大的工具，使复杂交易策略的开发民主化。

低代码和 AutoML 平台显著降低了开发机器学习模型的准入门槛，使其能被更广泛的受众使用，包括那些没有深厚编程背景的人。这与普及先进数据分析和模型开发工具的主题非常契合，特别是在金融交易策略的背景下，用户群体可以从高技术的数据科学家到编码经验有限的金融分析师。

## 结构

在本章中，我们将涵盖以下主题：

• [AutoML 和低代码简介](#chap08.xhtml#h36)

• [全球宏观建模](#chap08.xhtml#h37)

• [手工算法作为基准](#chap08.xhtml#h38)

• [AutoML 的核心组件](#chap08.xhtml#h39)

• [与手动方法的结果对比](#chap08.xhtml#h40)

## 目标
