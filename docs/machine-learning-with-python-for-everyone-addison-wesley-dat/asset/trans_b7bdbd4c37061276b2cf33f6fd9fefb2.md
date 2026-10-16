
|  | 0 | 1 | 2 | 类别 |
|---|---|---|---|---|
| 0 | -0.5000 | 2.2500 | 1.2500 | 1 |
| 1 | 2.0000 | 1.0000 | 0.0000 | 0 |
| 2 | 2.0000 | 1.0000 | 0.0000 | 0 |
| 3 | 2.0000 | 1.0000 | 0.0000 | 0 |
| 4 | -0.5000 | 2.2500 | 1.2500 | 1 |

为了查看预测与投票的对应情况，我们可以将*实际*类别与一对一分类分数放在一起：

In [19]:

```python
# note: ugly to make column headers
mi = pd.MultiIndex([['Class Indicator', 'Vote'], [0, 1, 2]],
                   [[0]*3+[1]*3,list(range(3)) * 2])
df = pd.DataFrame(np.c_[im_test_tgt, pred_scores],
                  columns=mi)
display(df.head())
```

|  | 类别指示 |  |  | 投票 |  |  |
|---|---|---|---|---|---|---|
|  | 0 | 1 | 2 | 0 | 1 | 2 |
| 0 | 0.0000 | 1.0000 | 0.0000 | -0.5000 | 2.2500 | 1.2500 |
| 1 | 1.0000 | 0.0000 | 0.0000 | 2.0000 | 1.0000 | 0.0000 |
| 2 | 1.0000 | 0.0000 | 0.0000 | 2.0000 | 1.0000 | 0.0000 |
| 3 | 1.0000 | 0.0000 | 0.0000 | 2.0000 | 1.0000 | 0.0000 |
| 4 | 0.0000 | 1.0000 | 0.0000 | -0.5000 | 2.2500 | 1.2500 |

你可能想知道为什么一对多和一对一都有三个分类器。如果有*n*个类别，对于一对多，我们会有*n*个分类器——每个类别一个，用于区分该类别与其他所有类别；这就是为什么这里有3个。对于一对一，每对类别都有一个分类器。计算*n*个事物的配对数的公式是$\frac{n(n-1)}{2}$。对于三个类别，即$\frac{3\times2}{2}=3$。你可以这样理解这个公式：挑一个人（*n*），选择他所有可能的舞伴（*n* − 1，不能和自己跳舞），然后移除重复项（除以二），因为Chris和Sam跳舞与Sam和Chris跳舞是一样的。

## 6.4.1 多类别AUC第二部分：追求单一值

我们可以在稍有不同的方式下利用一对一的思想。不同的一对一*分类器*之间不是以《空手道小子》式锦标赛进行竞争，而是让*单个分类器*应用于整个数据集。然后，我们挑选出目标对，看看单个分类器*在每种可能的配对上表现如何*。因此，我们计算一组针对类别对的小型混淆矩阵，其中类别i作为正类，类别j作为负类。然后，我们可以从中计算AUC。我们会以两种方式都做——每一对分别作为正类和负类——并取所有这些AUC的平均值。基本上，AUC用于量化一只真实的猫比一只随机的狗更不可能被误称为狗的概率。这项技术背后的逻辑细节——我称之为Hand and Till M——可在本章末尾的参考文献中找到。

- 1. 训练一个模型。
- 2. 获取每个样本的分类分数。
- 3. 为每个类别配对创建一个空白表。
- 4. 对于每一对类别 c1 和 c2：
   - (1) 计算 c1 对 c2 的 AUC。
   - (2) 计算 c2 对 c1 的 AUC。
   - (3) c1、c2 对应的条目是这些 AUC 的平均值。
- 5. 最终值是表中所有条目的平均值。

最棘手的代码部分是只挑选出两个感兴趣类别交互的那些样本。对于控制循环的一次迭代，我们需要为这两个类别生成一条ROC曲线。因此，我们需要其中任一类别出现的样本。我们通过执行`label_binarize`来追踪这些样本，得到指示值（1和0），然后从那里提取我们需要的特定列。

In [20]:

```python
def hand_and_till_M_statistic(test_tgt, test_probs, weighted=False):
def auc_helper(truth, probs):
    fpr, tpr, _ = metrics.roc_curve(truth, probs)
    return metrics.auc(fpr, tpr)

classes = np.unique(test_tgt)
n_classes = len(classes)

indicator = skpre.label_binarize(test_tgt, classes)
avg_auc_sum = 0.0

# comparing class i and class j
for ij in it.combinations(classes, 2):
    # use sum to act like a logical OR
    ij_indicator = indicator[:, ij].sum(axis=1,
                                        dtype=np.bool)

    # slightly ugly, can't broadcast these as indexes
    # use .ix_ to save the day

ij_probs = test_probs[np.ix_(ij_indicator, ij)]
ij_test_tgt = test_tgt[ij_indicator]

i,j = ij
auc_ij = auc_helper(ij_test_tgt==i, ij_probs[:, 0])
auc_ji = auc_helper(ij_test_tgt==j, ij_probs[:, 1])

# compared to Hand and Till reference
# no / 2 ... factor is out since it will cancel
avg_auc_ij = (auc_ij + auc_ji)

if weighted:
    avg_auc_ij *= ij_indicator.sum() / len(test_tgt)
    avg_auc_sum += avg_auc_ij

# compared to Hand and Till reference
# no * 2 ... factored out above and they cancel
M = avg_auc_sum / (n_classes * (n_classes-1))
return M
```

要使用我们定义的Hand and Till方法，我们需要提取评分/排序/概率这一技巧。我们将实际目标和我们对类别的评分输入`hand_and_till_M_statistic`，然后得到一个值。

In [21]:

```python
knn = neighbors.KNeighborsClassifier()
knn.fit(iris_train_ftrs, iris_train_tgt)
test_probs = knn.predict_proba(iris_test_ftrs)
hand_and_till_M_statistic(iris_test_tgt, test_probs)
```

Out[21]:

```
0.9915032679738562
```

我们这样编写`hand_and_till_M_statistic`有一个很大的好处。我们可以使用sklearn中的一个辅助例程，将我们的Hand and Till代码变成一个评分函数，该函数可以很好地与sklearn交叉验证例程配合使用。然后，使用我们的新评估指标进行10折交叉验证等操作就像在公园里散步一样简单：

In [22]:

```python
fig,ax = plt.subplots(1, 1, figsize=(3, 3))
htm_scorer = metrics.make_scorer(hand_and_till_M_statistic,
                                 needs_proba=True)
cv_auc = skms.cross_val_score(model,
                              iris.data, iris.target,
                              scoring=htm_scorer, cv=10)
```

```python
sns.swarmplot(cv_auc, orient='v')
ax.set_title('10-Fold H&T Ms');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_213_0.png)

当我们想传递一个不使用sklearn预定义默认值的评分参数时，我们也会使用`make_scorer`。我们很快就会看到相关示例。

由于Hand and Till M方法在评估时使用且仅使用一个分类器，因此分类器的性能与分类器本身之间存在直接联系。当我们对分类器使用一对多封装时，我们就失去了这种直接联系；相反，我们看到的是像我们关心的分类器在共享数据集上的类似场景中的行为。总之，这里的M方法与多类别预测用例有更强的关联。另一方面，一些学习方法不能直接用于多类别问题。这些方法需要一对多或一对一分类器来进行多类别预测。在这种情况下，一对多/一对一设置让我们更细致地了解分类器的配对性能。

## 6.5 精确率-召回率曲线

正如我们可以通过ROC曲线观察敏感性与特异性之间的权衡一样，我们也可以评估精确率与召回率之间的权衡。回想第6.2.3节，精确率是正类预测的价值，召回率是我们对实际为正类的样本的有效性。你可以念念下面两句话：“精确率——正类预测”，“召回率——正类实际”。

### 6.5.1 关于精确率-召回率权衡的说明

敏感度-特异度曲线与精确率-召回率曲线之间有一个非常重要的区别。对于敏感度-特异度，这两个值代表行总计的部分。权衡是在真实正类和真实负类上的表现之间进行的。对于精确率-召回率，我们处理的是混淆矩阵中的一列和一行。因此，它们的独立性更强，可以更独立地变化。更重要的是，精确率的提高并不意味着召回率的提高。注意，敏感度和1 − 特异度是权衡的：当我们从左下角绘制ROC曲线时，我们可以向上或向右移动，绝不会向下或向左移动。而精确率-召回率曲线可以回退：它可能下降而不是上升。

这里有一个具体例子。从初始状态开始，精确率为5/10，召回率为5/10：

|  | 预测正 | 预测负 |
|---|---:|---:|
| **实际正** | 5 | 5 |
| **实际负** | 5 | 5 |

考虑当我们提高将样本判定为正类的阈值时会怎样。假设预测为正类的样本中各有两个——两个实际为正类，两个预测为正类但实际为负类——被移到预测为负类：

|  | 预测正 | 预测负 |
|---|---:|---:|
| **实际正** | 3 | 7 |
| **实际负** | 3 | 7 |

我们的精确率现在是3/6 = .5——与之前相同——但召回率降到了3/10，低于.5。情况变糟了。

作为比较，这里我们提高阈值，使得只有一个案例从真正例（TP）变为假负例（FN）。

|  | 预测正 | 预测负 |
|---|---:|---:|
| **实际正** | 4 | 6 |
| **实际负** | 5 | 5 |

我们的精确率变为4/9，约为.44。召回率为4/10 = .4。因此，两者都比原始示例低。

也许可视化这种行为的最简单方式是思考当你移动预测条时会发生什么。非常重要的是，移动预测条完全不会影响现实状态。没有样本会在行之间上下移动。然而，根据定义，移动预测条可能会移动预测结果：东西可能会在列之间移动。

### 6.5.2 构建精确率-召回率曲线

撇开这些细节不谈，计算和显示PR曲线（PRC）的技术与ROC曲线非常相似。一个实质性的区别是，精确率和召回率都应该是高的——接近1.0。因此，PRC右上角的点对我们来说是完美的。从视觉上看，如果一个分类器优于另一个，它的曲线会更靠近右上角。
