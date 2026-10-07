

```python
from sklearn.metrics import precision_recall_curve
```

precisions, recalls, thresholds = precision_recall_curve(y_train_5, y_scores)
最后，你可以使用 Matplotlib（图 3-4）将精确率和召回率绘制为阈值的函数：
```python
def plot_precision_recall_vs_threshold(precisions, recalls, thresholds):
    plt.plot(thresholds, precisions[:-1], "b--", label="Precision")
    plt.plot(thresholds, recalls[:-1], "g-", label="Recall")
    [... # 突出显示阈值，添加图例、轴标签和网格

plot_precision_recall_vs_threshold(precisions, recalls, thresholds)
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_122_0.png)

图 3-4. 精确率与召回率随决策阈值

你可能会好奇为什么精确率曲线比召回率曲线波动更大，因为当你提高阈值时，精确率有时会下降（尽管通常情况下会下降）。为了理解这一点，回看图 3-3，注意当你从中间阈值开始并向右仅移动一位时会发生什么：精确率从 4/5 (80%) 下降到 3/4 (75%)。另一方面，当阈值增加时，召回率只能下降，这解释了为什么它的曲线看起来很平滑。

选择良好的精确率/召回率平衡的另一种方法是将精确率直接对召回率绘图，如图 3-5 所示（突出显示了之前的相同阈值）。

![](img/0684d2da98e09085c0a622d4fd69aaad_123_0.png)

图 3-5. 精确率与召回率

你可以看到精确率在召回率 80% 左右开始急剧下降。你可能想在该下降之前选择一个精确率/召回率平衡——例如，在 60% 的召回率处。但当然，选择取决于你的项目。

所以，假设你决定目标是 90% 的精确率。你查看了第一个图，发现你需要使用大约 8,000 的阈值。为了更精确，你可以搜索提供至少 90% 精确率的最低阈值（`np.argmax()` 将给我们最大值的索引，在这种情况下意味着第一个 True 值）：

```python
threshold_90_precision = thresholds[np.argmax(precisions >= 0.90)] # -7816
```

为了进行预测（目前在训练集上），与其调用分类器的 `predict(method)`，不如你只需要运行这段代码：

```python
>>> precision_score(y_train_5, y_train_pred_90)
0.9006380083618396
>>> recall_score(y_train, y_train_pred_90)
0.43681979492714
```

让我们检查这些预测的精确率和召回率：

太棒了，你有一个 90% 精确率的分类器！如你所见，创建一个具有任何你所需的精确率的分类器都是相当容易的：只需设置一个足够高的阈值即可。嗯，别那么快。如果召回率太低，高精确率的分类器并没有什么用处！

# ROC 曲线

接收者工作特征（ROC）曲线是二分类器使用的另一种常用工具。它与精确率/召回率曲线非常相似，但 ROC 曲线不是绘制精确率对召回率，而是绘制真正例率（召回率的另一个名称）对假正例率。FPR 是被错误分类为正例的负实例比例。它等于 1 减去真负例率，真负例率是被正确分类为负例的负实例比例。TNR 也称为特异性（specificity）。因此，ROC 曲线是敏感度（召回率）对比 1 – 特异性。

要绘制 ROC 曲线，你首先需要使用 `roc_curve()` 函数计算各种阈值对应的 TPR 和 FPR：

```python
from sklearn.metrics import roc_curve

fpr, tpr, thresholds = roc_curve(y_train_5, y_scores)

def plot_roc_curve(fpr, tpr, linewidth=2, label=label):
    plt.plot([0, 1], ['k--']) # 虚对角线
    [...] # 添加轴标签和网格
```

然后你可以使用 Matplotlib 绘制 FPR 对 TPR 的图。这段代码生成图 3-6 所示的图：

```python
plt.roc_curve(fpr, tpr)
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_125_0.png)

再次，存在权衡：召回率（TPR）越高，假正例越多。良好的分类器的 ROC 曲线越接近左上角。

比较分类器的另一种方法是计算曲线下的面积（AUC）。完美分类器的 AUC 等于 1，而随机分类器的 AUC 等于 0.5。Scikit-Learn 提供了一个函数来计算 AUC：

```python
from sklearn.metrics import roc_auc_score
```from sklearn.metrics import precision_score, recall_score

>>> roc_auc_score(y_train_5, y_scores)
0.991
```

由于精确率/召回率曲线（或 ROC）非常相似，你可能想知道选择哪个。根据经验法则，当正例稀少时，你应该倾向于使用 ROC 曲线；而当你更关心假正例时，使用精确率/召回率曲线。例如，通过 ROC 曲线，你可以看到分类器的性能。

分类器的权衡：召回率（TPR）越高，假正例越多。

```python
def plot_precision_recall_vs_threshold(precisions, recalls, thresholds)
```

```     曲线，，  



现在你现在准备好 绘制  曲线了（图 3-7）：

![](img/0684d2da98e09085c0a622d4fd69aaad_126_0.png)

图 3-7. 比较 ROC 曲线

如你从图 3-7 所示，RandomForestClassifier 的曲线看起来比 SGDClassifier 好得多，更接近左上角。结果，它的 ROC AUC 分也显著提高：

```python
>>> roc_auc_score(y_train_5, y_scores)
0.998346371328145
```

测量精确率和召回率：你会发现 99.0% 的精确率和 86.6% 的召回率。不赖！

希望你现在已经了解如何训练二分类器、为任务选择合适的指标、通过交叉验证评估分类器、使用 ROC 曲线和 ROC AUC 分数比较各种模型。现在让我们尝试检测不仅仅 5。

# 多类分类

二分类器区分两个类，多类分类器（多分类器）可以区分超过两个类。

某些算法（如随机森林分类器或朴素贝斯分类器）能够处理多个类。其他算法（如支持向量分类器或线性分类器）是严格的二分类器。然而，有某些策略可以使用二分类器来进行多类分类。

例如，创建一个可以将数字图像分类为10 类的系统的一种方法是训练 10 个二分类器，每个数字一个（0 检测器、1 检测器、2 检测器等）。当你想要对图像进行分类时，获取每个分类器对该图像的分，并选择得分最高的类别。这被称为一对全（OvA）策略（也称为一对余）。

