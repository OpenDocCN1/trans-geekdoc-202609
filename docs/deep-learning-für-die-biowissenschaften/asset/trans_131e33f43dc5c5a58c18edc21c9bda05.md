
# 图 5-10：来自 PDBBind 数据集的 2D3U 蛋白-配体复合物的可视化

请注意，为了简化可视化，蛋白质以卡通形式表示，而配体（位于右上角）则以球棒模型显示。

正如您所见，配体位于蛋白质的一种口袋中。为了看得更清楚，您可以旋转可视化视图，从不同角度进行观察。

## 蛋白质可视化工具

鉴于蛋白质可视化对于相关工作的重要性，为此提供了一系列工具。`NGLview` 与 Jupyter 具有出色的协作性。药物开发人员经常使用 `VMD` ([https://www.ks.uiuc.edu/Research/vmd/](https://www.ks.uiuc.edu/Research/vmd/))、`PyMOL` ([https://pymol.org](https://pymol.org)) 或 `Chimera` ([https://www.cgl.ucsf.edu/chimera/](https://www.cgl.ucsf.edu/chimera/))。请注意，这些工具通常并非完全开源，且并不总是提供对开发者友好的 API。然而，如果您花费大量时间处理蛋白质结构，使用这些成熟工具之一仍然值得权衡利弊。

# 在 PDBBind 数据集中开发特征

首先，我们创建一个可供检查的 `RdkitGridFeaturizer` 对象：

```python
import deepchem as dc

grid_featurizer = dc.feat.RdkitGridFeaturizer(
    voxel_width=2.0,
    feature_types=['hbond', 'salt_bridge', 'pi_stack',
                   'cation_pi', 'ecfp', 'splif'],
    sanitize=True, flatten=True)
```

这里使用了多个选项，我们稍作详细了解。选项 `sanitize=True` 要求特征生成器尝试清理所有结构。正如您所记得的，我们之前提到过结构经常存在错误。此清理步骤尝试修复它检测到的所有明显错误。选项 `flatten=True` 要求特征生成器为每个输入结构输出一个一维特征向量。

选项 `feature_types` 设定 `RdkitGridFeaturizer` 尝试在输入结构中识别的生物物理和化学特征类型。请注意，其中包含了我们在本章前面讨论的许多化学键：氢键、离子键等。最后，选项 `voxel_width=2.0` 将构成网格的体素大小设置为 2 埃。`RdkitGridFeaturizer` 将蛋白质转换为体素化表示，以提取有用特征。对于每个空间网格点，都会统计生物物理特征并计算局部指纹向量。`RdkitGridFeaturizer` 计算两种不同的指纹，即 `ECFP` 和 `SPLIF`。

## 体素化

什么是体素化？一般来说，体素是像素的 3-D 对应物（见图 5-11）。正如基于像素的图像表示对于处理图像数据非常有用一样，基于体素的表示对于处理 3-D 数据可能至关重要。

![图 5-11：球体的体素化表示。每个体素代表一个空间输入立方体。](Images/p79-1.png)

现在我们可以加载 PDBBind 数据集。为此，我们其实不需要刚才定义的特征生成器，`MoleculeNet` 会自动为我们处理。如果在加载数据集时使用选项 `featurizer="grid"`，它会自动执行网格特征化：

```python
tasks, datasets, transformers = dc.molnet.load_pdbbind(
    featurizer="grid", split="random", subset="core")

train_dataset, valid_dataset, test_dataset = datasets
```

使用上述代码，我们加载了 PDBBind 的“Core”子集并生成了特征。在一台快速计算机上，代码应能在十分钟内运行完成。对“Refined”子集进行特征化在现代服务器上需要数小时。

既然数据已准备就绪，我们可以开始构建一些机器学习模型。首先，我们训练一个名为*随机森林*的经典模型：

```python
from sklearn.ensemble import RandomForestRegressor

sklearn_model = RandomForestRegressor(n_estimators=100)
model = dc.models.SklearnModel(sklearn_model)
model.fit(train_dataset)
```

或者，我们也将尝试创建一个神经网络来预测蛋白-配体结合。我们可以利用 `dc.models.MultitaskRegressor` 类创建一个具有两个隐藏层的 MLP。隐藏层的宽度分别设置为 2,000 和 1,000，并使用 50% 的 Dropout 来减少过拟合：

```python
n_features = train_dataset.X.shape[1]

model = dc.models.MultitaskRegressor(
    n_tasks=len(pdbbind_tasks),
    n_features=n_features,
    layer_sizes=[2000, 1000],
    dropouts=0.5,
    learning_rate=0.0003)

model.fit(train_dataset, nb_epoch=250)
```

## 基线模型

深度学习模型有时难以优化。即使是经验丰富的用户，在调整此类模型时也会犯错。因此，创建一个更稳健的基线模型非常重要，即使其性能可能略低。

随机森林是作为基线的良好选择。它们在相对较少的调参情况下，通常能在学习任务中提供强劲的性能。随机森林分类器创建许多“决策树”分类器，每个分类器仅使用可用特征的一个随机子集，然后通过多数投票将这些分类器的单独决策组合起来。

`Scikit-learn` 是构建简单机器学习基线不可或缺的包。在本章中，我们使用 `scikit-learn` 创建一个基线模型，并用 `RdkitGridFeaturizer` 将复合物标记化作为随机森林的输入。

现在我们有了训练好的模型，可以检查其准确性。为了评估模型准确性，我们首先必须定义一个合适的指标。我们选择皮尔逊 R² 分数。这是一个介于 -1 和 1 之间的数字，其中 0 表示真实标签与预测标签之间无相关性，1 表示完美相关：

```python
metric = dc.metrics.Metric(dc.metrics.pearson_r2_score)
```

现在我们可以根据此指标评估模型在训练集和测试集上的准确性。两个模型的代码是相同的：

```python
print("Evaluating model")
train_scores = model.evaluate(train_dataset, [metric], transformers)
test_scores = model.evaluate(test_dataset, [metric], transformers)

print("Train scores")
print(train_scores)
print("Test scores")
print(test_scores)
```

## 许多架构可产生相似效果

本节提供了使用具有网格特征化的 MLP 在 DeepChem 中对蛋白-配体结构进行建模的代码示例。请注意，存在多种替代的深度学习架构，可产生相似的效果。已有一系列工作利用 3D 卷积神经网络，基于基于体素的特征化来预测蛋白-配体结合相互作用。其他工作则使用了上一章所述图卷积的变体来处理大分子复合物。
