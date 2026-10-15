

- 引导聚合（bagging）集成。
- 随机训练子集集成。

- 不同模型
  - 多次训练运行集成（第20章和第21章）。
  - 超参数调优集成。
  - 快照集成（第24章）。
  - 横向轮次集成（第23章）。
  - 垂直表示集成。

- 不同组合
  - 模型平均集成（第20章）。
  - 加权平均集成（第21章）。
  - 堆叠泛化（stacking）集成（第25章）。
  - 提升集成。
  - 模型权重平均集成（第26章）。

没有唯一最好的集成方法；也许可以尝试几种方法，或者让项目的约束条件来指导你。

## 19.5 进一步阅读

如果你希望深入了解，本节提供更多关于该主题的资源。

### 19.5.1 书籍

- 9.6节 网络委员会，*《神经网络模式识别》*，1995年。
  https://amzn.to/2I9gNMP
- 7.11节 袋装与其他集成方法，*《深度学习》*，2016年。
  https://amzn.to/2NJW3gE
- 7.3.3节 模型集成，*《Python深度学习》*，2017年。
  https://amzn.to/2NJq1pf
- 8.2节 袋装、随机森林、提升，*《统计学习导论：基于R应用》*，2013年。
  https://amzn.to/2zxHR5E

### 19.5.2 论文

- *《神经网络集成》*，1990年。
  https://ieeexplore.ieee.org/abstract/document/58871/
- *《神经网络集成、交叉验证与主动学习》*，1994年。
  https://dl.acm.org/citation.cfm?id=2998716
- *《当网络不一致：混合神经网络的集成方法》*，1995年。
  https://www.worldscientific.com/doi/abs/10.1142/9789812795885_0025
- *《快照集成：训练1次，免费获得M个》*，2017年。
  https://arxiv.org/abs/1704.00109
- *《SGDR：带热重启的随机梯度下降》*，2016年。
  https://arxiv.org/abs/1608.03983
- *《用于分类的深度表示水平与垂直集成》*，2013年。
  https://arxiv.org/abs/1306.2759
- *《堆叠泛化》*，1992年。
  https://www.sciencedirect.com/science/article/pii/S0893608005800231
- *《平均权重带来更宽的极值和更好的泛化》*，2018年。
  https://arxiv.org/abs/1803.05407

### 19.5.3 文章

- 集成学习，维基百科。
  https://en.wikipedia.org/wiki/Ensemble_learning
- 引导聚合，维基百科。
  https://en.wikipedia.org/wiki/Bootstrap_aggregating
- 提升（机器学习），维基百科。
  https://en.wikipedia.org/wiki/Boosting_(machine_learning)

## 19.6 总结

在本教程中，你了解了用于深度学习神经网络的集成方法，以降低方差并提高预测性能。具体来说，你学到了：

- 神经网络模型是非线性的，并且具有高方差，这在准备最终模型进行预测时可能令人沮丧。
- 集成学习结合多个神经网络模型的预测，以减少预测的方差并降低泛化误差。
- 集成学习的技术可以根据变化的元素进行分组，例如训练数据、模型以及预测的组合方式。

## 19.6. 总结

在下一个教程中，你将了解如何对多个神经网络模型做出的预测进行平均。

## 第20章

### 使用模型平均集成组合多次运行的模型

深度学习神经网络模型是高度灵活的非线性算法，能够学习近乎无限数量的映射函数。这种灵活性带来的一个困扰是最终模型的高方差。同一个神经网络模型在相同数据集上训练，每次运行都可能找到许多不同的*足够好*解决方案之一。模型平均是一种集成学习技术，通过牺牲模型性能的分散性（以及可能更好的得分）来降低最终神经网络模型的方差，从而获得对模型预期性能的信心。在本教程中，你将了解如何在Keras中开发模型平均集成，以降低最终模型的方差。完成本教程后，你将了解：

- 模型平均是一种集成学习技术，可用于降低深度学习神经网络模型的预期方差。
- 如何在Keras中为分类和回归预测建模问题实现模型平均。
- 如何解决多类分类问题，并使用模型平均来降低最终模型的方差。

让我们开始吧。

### 20.1 模型平均集成

深度学习神经网络模型是通过随机训练算法学习的非线性方法。这意味着它们高度灵活，在给定足够资源的情况下，能够学习变量之间的复杂关系并逼近任何映射函数。这种灵活性的缺点是模型具有高方差。这意味着模型高度依赖于用于训练模型的特定训练数据，以及初始条件（随机初始权重）和训练过程中的偶然性。结果是，每次在相同数据集上训练相同模型配置时，最终模型都会做出不同的预测。

在训练最终模型用于对新数据进行预测时（例如在运营中或机器学习竞赛中），这可能会令人沮丧。通过为问题训练多个模型并组合它们的预测，可以解决该方法的高方差问题。这种方法称为模型平均，属于称为集成学习的技术家族。

### 20.2 Keras中的集成

在Keras中开发模型平均集成的最简单方法是在相同数据集上训练多个模型，然后组合每个已训练模型的预测。

### 20.2.1 训练多个模型

训练多个模型可能消耗大量资源，具体取决于模型的大小和训练数据的大小。你可能需要在同一台硬件上顺序训练模型。对于非常大的模型，使用云基础设施（如Amazon Web Services）并行训练模型可能是值得的。

集成所需的模型数量可能因问题和模型的复杂性而异。这种方法的一个好处是，你可以继续创建模型，将它们添加到集成中，并通过在保留测试集上进行预测来评估它们对性能的影响。对于小型模型，你可以顺序训练模型，并将它们保留在内存中以供实验使用。例如：

```
...
# train models and keep them in memory
n_members = 10
models = list()
for _ in range(n_members):
    # define and fit model
    model = ...
    # store model in memory as ensemble member
    models.append(model)
...
```

清单20.1：在内存中训练多个模型的示例。

对于大型模型，可能在不同硬件上训练，你可以将每个模型保存到文件。

```
...
# train models and keep them to file
n_members = 10
for i in range(n_members):
    # define and fit model
    model = ...
    # save model to file
    filename = 'model_' + str(i + 1) + '.h5'
    model.save(filename)
    print('Saved: %s' % filename)
...
```

清单20.2：训练多个模型并将其保存到文件的示例。

```
...
# make predictions
yhats = [model.predict(testX) for model in models]
yhats = array(yhats)
# sum across ensembles
summed = numpy.sum(yhats, axis=0)
# argmax across classes
outcomes = argmax(summed, axis=1)
```

清单20.6：计算类别概率的argmax示例。

这些组合Keras模型预测的方法同样适用于多层感知器、卷积神经网络和循环神经网络。既然我们知道了如何在Keras中对多个神经网络模型的预测进行平均，让我们来研究一个案例。

### 20.3 模型平均集成案例研究

在本节中，我们将演示如何使用模型平均集成来降低MLP在简单多类分类问题上的方差。此示例为将模型平均集成应用于你自己的分类和回归神经网络提供了模板。

### 20.3.1 多类分类问题

我们将使用一个小型多类分类问题作为演示模型平均集成的基础。scikit-learn类提供了make_blobs()函数，该函数可用于创建具有指定样本数、输入变量、类别数和类内样本方差的多类分类问题。我们使用此问题，包含500个样本，两个输入变量（表示点的x和y坐标），每个组内点的标准差为2.0。我们将使用相同的随机状态（伪随机数生成器的种子），以确保我们总是得到相同的500个点。

```
# generate 2d classification dataset
X, y = make_blobs(n_samples=500, centers=3, n_features=2, cluster_std=2, random_state=2)
```

清单20.7：为blobs问题生成样本的示例。

结果是我们可以建模的数据集的输入和输出元素。为了了解问题的复杂性，我们可以将每个点绘制在二维散点图上，并按类别值着色。完整示例如下。

```
# scatter plot of blobs dataset
from sklearn.datasets.samples_generator import make_blobs
from matplotlib import pyplot
from numpy import where
# generate 2d classification dataset
X, y = make_blobs(n_samples=500, centers=3, n_features=2, cluster_std=2, random_state=2)
# scatter plot for each class value
for class_value in range(3):
    # select indices of points with the class label
    row_ix = where(y == class_value)
```

