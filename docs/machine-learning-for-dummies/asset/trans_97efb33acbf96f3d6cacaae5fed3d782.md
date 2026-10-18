

![Remember](images/remember.png)大数定律之所以有效，是因为你对某个事件进行了许多独立试验（例如，测试硬币是否一面偏重），当你统计试验分布时，就能得到该事件的正确概率分布。同样，当你创建一片决策树森林时，如果这些树彼此独立，因此不会犯相同的错误，那么将它们汇总后得到的估计结果会更准确。Breiman 发现，如果通过对训练样本和使用的特征都进行采样来随机化决策树，那么这些树就会彼此独立。这种采样方法的预测效果优于袋装法（bagging）。这种变换调整同时对特征和样本进行采样。Breiman 与 Adele Cutler 合作，将这种新的集成方法命名为随机森林（Random Forests，RF）。

![Remember](images/remember.png)随机森林是 Leo Breiman 和 Adele Cutler 的商标。出于这个原因，开源实现通常使用不同的名称，例如 Python Scikit-learn 中的 `RandomForestClassifier`（详情见 [`https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html`](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)）。

RF 是一种分类（天然支持多类）和回归算法，它使用大量构建在不同自助采样样本和子采样特征集上的决策树模型。其创建者致力于使算法易于使用（几乎不需要预处理，且超参数很少）且易于理解（基于决策树），从而让非专家也能使用机器学习。换句话说，由于其简单性和即用性，RF 可以让任何人成功应用机器学习。该算法通过几个重复步骤工作：

1. 对训练集进行多次自助采样。算法在每次自助采样期间获得一个新集合，用于构建集成中的单棵树。

2. 在训练集中随机选择部分特征，用于每次在树中拆分样本时寻找最佳拆分特征。

3. 使用自助采样样本创建一棵完整的树。在每次拆分时评估新的子采样特征。不要限制完整树的扩展，以便让算法工作得更好。

4. 使用自助采样阶段未选择的样本（袋外估计，或 OOB）计算每棵树的性能。OOB 样本无需交叉验证或使用测试集即可提供性能指标（相当于样本外）。

5. 生成特征重要性统计信息，并计算样本在树的终端节点中的关联方式。

6. 完成集成中所有树后，对新样本计算平均值或投票。为每个样本声明平均估计值或获胜类别作为预测结果。

所有这些步骤都以牺牲一定程度的偏差（因为同时使用的特征更少）为代价，降低了预测的方差。该解决方案将每棵树构建到其最大可能的扩展，从而允许对即使是复杂的目标函数进行精细近似。此外，由于每棵树是通过拟合不同样本构建的，因此增加了森林中每棵树彼此不同的机会。这不仅仅是基于不同自助采样样本集构建的问题：树进行的每次拆分都经过强随机化——解决方案仅考虑由随机选择定义的集合中的一个特征。因此，即使一个重要特征在预测能力上占据主导地位，树不包含该选择的次数也允许树以有效的方式找到发展其分支和终端叶子的不同方式。

与袋装法的主要区别在于，在拆分树枝时有机会限制要考虑的特征数量。如果选定的特征数量较少，完整树将与其他树不同，从而向集成中添加不相关的树。另一方面，如果选择的特征数量较少，偏差会增加，因为树的拟合能力受到限制。与往常一样，确定拆分时要考虑的正确特征数量需要使用交叉验证或 OOB 估计结果。

![Tip](images/tip.png)RF 有一种称为极端随机树（Extremely Randomized Trees，ERT）的变体，它更加随机，因为它不仅随机选择拆分的特征，还随机决定拆分（详情见 [`https://scikit-learn.org/stable/modules/ensemble.html#extremely-randomized-trees`](https://scikit-learn.org/stable/modules/ensemble.html#extremely-randomized-trees））。在这个版本中，用更多的方差换取更多的偏差，在某些数据问题中，它可能比 RF 工作得更好。此外，它总是更快，因为 ERT 所需的计算更少。在集成中生成大量树木不会出现问题。树木越多，你的估计结果就会越精确和稳定。你确实需要考虑计算工作量的成本；完成一个大型集成需要很长时间。RF 是一种可以在多个 CPU 处理器上并行运行的算法。

![Tip](images/tip.png)RF 集成中的每棵树都彼此独立（毕竟，它们应该是不相关的），这意味着你可以将每棵树与其他树并行构建。鉴于所有现代计算机都具有多处理器和多线程功能，它们可以同时执行许多树的计算，这是 RF 相对于其他机器学习算法的真正优势。

### 演示 RF 算法

一个简单的演示说明了 RF 算法如何使用不断增加的树木数量来解决一个简单问题。此示例使用葡萄酒质量数据集，该数据集通过数据挖掘理化（物理和化学）特性来模拟葡萄酒偏好，结合了白葡萄酒和红葡萄酒。该数据集在 P. Cortez、A. Cerdeira、F. Almeida、T. Matos 和 J. Reis 撰写的《通过理化特性的数据挖掘建模葡萄酒偏好》（"Modeling wine preferences by data mining from physicochemical properties"）中有所描述，发表于《决策支持系统》（Decision Support Systems），见 [`https://www.sciencedirect.com/science/article/abs/pii/S0167923609001377?via%3Dihub`](https://www.sciencedirect.com/science/article/abs/pii/S0167923609001377?via%3Dihub)（Elsevier, 47(4): 547-553, 2009）。该数据集将一些葡萄牙葡萄酒的理化测试（酒精浓度、密度、酸度等）与专家的质量评估相关联。该数据集提供了将其既作为回归问题又作为分类问题处理的机会。此示例将其作为回归问题来解决。它首先加载数据并创建训练集和测试集。

```
import numpy as np
import pandas as pd
try:
    import matplotlib.pyplot as plt
    import seaborn as sns
    sns.set(style='whitegrid', palette='deep', font='sans-serif')
except:
    import matplotlib.pyplot as plt
filename = 'https://github.com/lmassaron/datasets/'
filename += 'releases/download/1.0/wine_quality.feather'
wine = pd.read_feather(filename)
np.random.seed(42)
train = (wine.groupby('quality')
    .apply(lambda x: x.sample(frac=.7))
    .reset_index(drop=True))
test = wine[~wine.index.isin(train.index)]
X_train = train.iloc[:,1:]
y_train = train.iloc[:,0]
X_test = test.iloc[:,1:]
y_test = test.iloc[:,0]
```

从本书在 GitHub 上的互联网仓库加载数据集后（详情见简介），代码使用 pandas 应用分层采样（以便响应变量 `quality` 在训练数据和测试数据中均匀分布），以保留 30% 的观测值作为测试集。

