
# 第 12 章 组合学习器

我们可以使用第 5.6 节中介绍的偏差-方差术语来讨论 bagging 的一些实际问题。（你还以为那只是纯理论的空谈！）我们组合多个预测的过程在平衡高方差方面做得很好：概念上，我们可以接受基础模型过拟合。我们会过拟合，然后让平均——或者在这里，使用众数取最大票数者——平滑掉粗糙的边缘。Bagging 对偏差没有帮助，但可以显著降低方差。实践中，我们希望 `base_model` 具有较低的偏差。

概念上，由于我们的学习器是从有放回抽样的样本创建的，学习器彼此独立。如果我们真的想，可以在不同的计算机上训练每个基础模型，然后在最后将它们组合在一起。如果我们想使用并行计算来加快训练过程，我们可以很好地利用这种分离。

## 12.3.3 通过随机森林

随机森林（RFs）是一种建立在决策树之上的特定类型的 bagged 学习器。RFs 使用我们见过的决策树的变体。标准决策树取所有特征中评估最好的特征来创建决策节点。相比之下，RFs 子选择一组随机特征，然后取该子集中的最好者。目标是迫使树彼此不同。你可以想象，即使在随机选择示例的情况下，某个特征可能与目标紧密相关。这个 alpha 特征然后很可能会被选为每棵树中的顶部分割点。让我们打倒山头的君主。

与其让单个特征成为许多 bootstrap 树的顶层决策点，我们将有选择地忽略一些特征并引入一些随机性来制造混乱。随机性迫使不同的树考虑各种特征。原始的随机森林算法依赖于我们为 bagging 描述的相同类型的多数投票。然而，`sklearn` 的 RF 版本从森林中每棵树提取类别概率，然后对这些概率进行平均以获得最终答案：平均概率最高的类别获胜。

如果我们从上面的 `bagged_learner` 代码开始，我们仍然需要修改第 8.2 节中的树创建代码——即组件模型构建步骤。这是一个相当简单的修改，我用*斜体*标出：

- 0. *随机选择该树要考量的一部分特征。*
- 1. 评估所选特征与划分，并选出最佳的特征及划分。
- 2. 在树上添加一个节点来表示特征划分。
- 3. 对于每个子节点，使用匹配的数据进行处理，并按以下情况之一操作：
  - 如果目标足够相似，返回一个预测目标。
  - 如果不是，则回到步骤 1 并重复。

使用该伪代码作为我们的基础估计器，连同 `bagged_learner` 代码，我们就能快速得到一个随机森林学习系统的原型。

## 极端随机森林与特征划分

另一种变体——另一种装袋树（YABT）——被称为*极端随机森林*。不，这不是决策树运动的 X-Games。在这里，*极端*是指在模型创建过程中再增加一个随机性维度。给计算机科学家一个想法——用随机性取代确定性方法——他们就会到处应用它。在极端随机森林中，我们对组件树的构建过程做如下修改：

- 1. 随机选择划分点，并从中选出最佳者。

所以，除了随机选择涉及哪些特征之外，我们还通过抛硬币的方式来确定哪些值重要。令人惊奇的是，这种技术是有效的——而且确实可能很有效。到目前为止，我还没有深入探讨划分选择过程的细节。我也不太想去探讨，因为关于这方面的讨论已经很多了。我特别喜欢 Foster 和 Provost 在本章结尾引用的那本书中的处理方法。

让我用一个例子来说明良好划分点的思路。假设我们想通过简单的生物特征数据来预测优秀的篮球运动员。不幸的是，对于像我这样的人来说，身高是预测篮球成功的一个非常好的指标。所以，我们可以先考虑身高与一组成功的——以及像我一样不成功的——篮球运动员数据之间的关系。如果我们把所有身高排序，可能会发现从 4'5'' 到 6'11'' 的人都尝试过打篮球。如果我在 5'0'' 处引入一个划分点，那么小于这一侧可能会有很多不成功的运动员。按篮球成功与否分组时，这一组是相对相似的群体。但在大于那一侧，很可能是两个类别的真正混合。我们说划分点之上纯度较低，划分点之下纯度较高。同样，如果我把划分点设在 6'5''，那么高的一侧可能有很多成功的人，但低的一侧则相当混杂。我们的目标是找到身高中那个*恰到好处*的划分点，它能够让我获得尽可能多的关于成功衡量标准的信息——无论对较高还是较矮的人来说。将高身高和低身高分别划分开，能让我获得大量信息。而在中间，其他因素，比如打篮球的时间，则关系重大。

所以，极端随机森林并不考虑所有可能的划分点。它们只是随机选择一部分点来考量，评估这些点，然后从有限的集合中选出最佳者。

我记得用闪卡来准备词汇和地理考试。我不知道“App 一代”是否知道这些东西。它们是些小纸片——双面的，和大多数纸片一样——一面写上单词、名词或概念，另一面写上定义或该事物的重要特征。例如，一面可能是 gatto，另一面是 cat（用于意大利语词汇测试）；或者一面是 Lima，另一面是秘鲁首都（用于世界地理测试）。

![](img/d94e4cd766940d79abed0bc6ba4e4344_426_0.png)

从牌堆中取出卡片的过程有点像对这些卡片出现的可能性进行加权，但方式很极端：它把概率降为零。如果我真想做到彻底，除了移除简单的卡片，我还可以添加困难卡片的副本。效果会类似：困难卡片会更常出现，简单卡片则更少出现。区别在于过程是渐进的。

我们可以将同样的想法——专注于困难样本——应用于学习系统。我们首先在一些困难数据上拟合一个 Simple-McSimple 模型。毫不奇怪，我们会弄错很多样本。但令人惊讶的是，我们确实会对一些样本判断正确。我们重新将精力集中在更困难的样本上，然后再次尝试。这种反复将精力集中在困难样本上——并把较容易的样本视为（差不多）已完成——的过程，就是 boosting（提升）的核心。

### 12.4.1 Boosting 细节

通过 boosting，我们学习一个简单模型。然后，不是从基础数据集中等概率地重采样，而是专注于我们出错的样本，并开发另一个模型。我们重复这个过程，直到满意或时间用完。因此，boosting 是一种顺序方法，后期阶段开发的学习器依赖于前期阶段发生的事情。虽然 boosting 可以应用于任何学习模型作为基本组件模型，但我们通常使用决策树桩——只有一个划分点的决策树。决策树桩的深度为 1。

我们还没有讨论带权重数据的学习意味着什么。你可以从两个不同的角度来理解。首先，如果我们想要进行加权训练，并且样本 A 的权重是样本 B 的两倍，那么我们只需在训练集中将样本 A 复制两次，然后收工。另一种方式是将权重纳入误差或损失度量中。我们可以用样本权重对误差进行加权，得到加权误差。然后，我们针对加权误差寻找最佳的参数设置，而不是原始误差。

用非常原始的伪代码形式，这些步骤如下：

- 1. 将样本权重初始化为 $\frac{1}{N}$，并将 $m$ 初始化为零。
- 2. 重复直到完成：
  - 1. 递增 $m$。
  - 2. 在加权数据上拟合一个新的分类器（通常是树桩）$C_m$。
  - 3. 计算新分类器的加权误差。
  - 4. 分类器权重 $\text{wgt}_m$ 是加权误差的函数。
  - 5. 根据旧的样本权重、分类器误差和分类器权重来更新样本权重。
- 3. 对于新样本和 $m$ 次重复，根据 $C$ 按 `wgt` 加权的多数投票输出预测。

我们可以冒一些巨大的风险（请勿在家尝试！），写一些 Python 风格的伪代码：

```python
In [11]:
def my_boosted_classifier(base_classifier, bc_args,
                          examples, targets, M):
    N = len(examples)
    data_weights = np.full(N, 1/N)
    models, model_weights = [], []

    for i in range(M):
        weighted_dataset = reweight((examples,targets),
                                    data_weights)
        this_model = base_classifier(*bc_args).fit(*weighted_dataset)

        errors = this_model.predict(examples) != targets
        weighted_error = np.dot(weights, errors)

# magic reweighting steps

this_model_wgt = np.log(1-weighted_error)/weighted_error

data_weights *= np.exp(this_model_wgt * errors)

data_weights /= data_weights.sum() # normalize to 1.0

models.append(this_model)

model_weights.append(this_model_wgt)

return ensemble.VotingClassifier(models,
                                voting='soft',
                                weights=model_weights)
```

你会注意到这里的一些事情。我们凭空选了一个 `M` 值。当然，这给了我们一个确定的停止点：我们只会进行 `M` 次迭代。但我们可以在这里引入更多的灵活性。例如，当准确率达到 100% 或 `this_model` 开始比抛硬币还差时，`sklearn` 就会停止其离散 AdaBoost——一种与我们这里所用的类似的特定 boosting 变体。另外，除了重新加权样本，我们还可以执行加权自助采样——这不过是一种对某些数据给予比其他数据更高优先级的不同方式。

Boosting 非常自然地处理学习系统中的偏差。通过组合许多简单、高度有偏的学习器，boosting 降低了结果的整体偏差。Boosting 也能降低方差。

在 boosting 中，与 bagging 不同，我们不能并行构建原始模型。我们需要等待一轮的结果，以便在开始下一轮之前重新加权数据并专注于困难样本。

#### 12.4.1.1 通过 Boosting 迭代改进

`sklearn` 中两个主要的 boosting 分类器是 `GradientBoostingClassifier` 和 `AdaBoostClassifier`。每个都可以通过 `n_estimators` 指定要使用的最大组件估计器数量——即我们传给 `my_boosted_classifier` 的 `M` 参数。关于这些 boosting 算法的细节我会留在结尾注释中，但这里有几个小贴士。AdaBoost 是现代 boosting 算法的经典先驱。Gradient Boosting 是一种新的变体，允许我们插入不同的损失函数，从而得到不同的模型。例如，如果在 `GradientBoostingClassifier` 中设置 `loss="exponential"`，我们得到的模型基本上就是 AdaBoost。结果给出的代码类似于 `my_boosted_classifier`。

由于 boosting 是一个迭代过程，我们可以合理地询问模型在重新加权的循环中是如何改进的。`sklearn` 使得通过 `staged_predict` 访问该进展相对容易。`staged_predict` 的操作方式类似于 `predict`，但它是跟踪学习过程中每一步（或每个阶段）对样本所做的预测。如果我们想要量化进展，就需要将这些预测转换为评估指标。

```python
In [12]:
model = ensemble.AdaBoostClassifier()

stage_preds = (model.fit(iris_train_ftrs, iris_train_tgt)
    .staged_predict(iris_test_ftrs))

stage_scores = [metrics.accuracy_score(iris_test_tgt,
    pred) for pred in stage_preds]

fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(stage_scores)
ax.set_xlabel('# steps')
ax.set_ylabel('accuracy');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_429_0.png)

## 12.5 比较树集成方法

现在让我们比较这些基于团队的方法在 `digits` 数据上的表现。我们将从两个简单的基线开始：单个决策桩（相当于 `max_depth=1` 的树）和单个 `max_depth=3` 的树。我们还将构建 100 个不同的森林，其中树桩的数量从 1 到 100。

```python
In [13]:
def fit_predict_score(model, ds):
    return skms.cross_val_score(model, *ds, cv=10).mean()

stump = tree.DecisionTreeClassifier(max_depth=1)
dtree = tree.DecisionTreeClassifier(max_depth=3)
forest = ensemble.RandomForestClassifier(max_features=1, max_depth=1)
```

```python
tree_classifiers = {'stump' : stump, 'dtree' : dtree, 'forest': forest}

max_est = 100
data = (digits_ftrs, digits_tgt)

stump_score  = fit_predict_score(stump, data)
tree_score   = fit_predict_score(dtree, data)

forest_scores = [fit_predict_score(forest.set_params(n_estimators=n),
    data)
    for n in range(1,max_est+1)]
```

我们可以图形化地查看这些结果：

```python
In [14]:
fig, ax = plt.subplots(figsize=(4,3))
xs = list(range(1,max_est+1))
ax.plot(xs, np.repeat(stump_score, max_est),  label='stump')
ax.plot(xs, np.repeat(tree_score, max_est),  label='tree')
ax.plot(xs, forest_scores, label='forest')
ax.set_xlabel('Number of Trees in Forest')
ax.set_ylabel('Accuracy')
ax.legend(loc='lower right');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_430_0.png)

将森林与两个基线进行比较可以看出，单桩森林的行为与——毫不意外地——桩非常相似。但是，随着桩的数量增加，我们很快甚至超过了中等大小的树。

现在，为了观察 boosting 方法随时间的变化并利用交叉验证——确保我们在比较同类事物——我们需要手动管理一部分交叉验证过程。这并不复杂，但有点丑陋。本质上，我们需要使用 `StratifiedKFold` 手动生成折索引（我们在第 5.5.2 节中讨论过它），然后使用这些索引来选择数据集的适当部分。我们本可以将这段代码直接内联在下面，但那样会真正掩盖我们想要做的事情。

```python
In [15]:
def my_manual_cv(dataset, k=10):
    ' manually generate cv-folds from dataset '
    # expect ftrs, tgt tuple
    ds_ftrs, ds_tgt = dataset
    manual_cv = skms.StratifiedKFold(k).split(ds_ftrs,
                                            ds_tgt)
    for (train_idx, test_idx) in manual_cv:
        train_ftrs = ds_ftrs[train_idx]
        test_ftrs  = ds_ftrs[test_idx]
        train_tgt  = ds_tgt[train_idx]
        test_tgt   = ds_tgt[test_idx]
        yield (train_ftrs, test_ftrs,
               train_tgt, test_tgt)
```

对于本次比较，我们将为梯度提升分类器使用 `deviance` 损失。结果是我们的分类器表现得像逻辑回归。我们调整一个重要参数，以便 `AdaBoostClassifier` 在 `digits` 数据上有一个合理的成功机会。我们调整 `learning_rate`，它是对估计器权重的一个额外因子——literally，一个乘数。你可以把它想象成在 `my_boosted_classifier` 中乘以 `this_model_weight`。

```python
In [16]:
AdaBC = ensemble.AdaBoostClassifier
GradBC = ensemble.GradientBoostingClassifier

boosted_classifiers = {'boost(Ada)' : AdaBC(learning_rate=2.0),
                       'boost(Grad)' : GradBC(loss="deviance")}

mean_accs = {}
```
