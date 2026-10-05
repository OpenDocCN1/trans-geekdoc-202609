

# 森林 503

| xi | j | infogains | bitmap. |
| :--- | :--- | :--- | :--- |
| 0 | 1 | 's=0 1 2 1!1 0f 5.9 1 → 00000000. | |
| 0 | 1 | 's=0 1 2 1 1 0f 5.9 1 → 00000000. | |
| 0 | 2 | 's=1 2 3!0.0408967 0.1110365 0.0535186 1 4.8 0.1110365 00000000. | |
| 1 | 1 | 's=0 2 3!0.640432 0.8729883 0.8729883 1 1.7 0001000. | |
| 1 | 2 | 's=0 1 2!0.06381 0.167048 0.3867211 2 4.4 0.3867211 0000000. | |
| 1 | 3 | 's=0 1 3!0.9709506 0.2170506 0.2170506 0 6.1 0.9709506 0000000. | |
| 1 | 3 | 's=0 1 3!0.9709506 0.2170506 0.2170506 0 6.1 0.9709506 0000000. | |
| 1 | 4 | 's=1 2 3!0.0987123 0.08305719 0.0455253 2 2.6 00011723. | |
| 1 | 5 | 's=1 2 3!0.2234528 0.7219281 0.7219281 1 3 0.7219281 0000000. | |
| 1 | 5 | 's=1 2 3!0.2364528 0.7219281 0.7219281 1 3 0.7219281 0000000. | |
| 1 | 6 | 's=0 1 3!0.0956002 0.0714817 0.06809513 0 5.9 0.0956002 111001. | |
| 2 | 1 | 's=0 1 3!0.6051125 0.2930229 0.9709506 2 0.6 0.9709506 10.. | |

## 25.3. 预测

使用构建好的随机森林来预测新数据点的分类。该数据点将遍历森林中的每棵树，最终的分类结果将基于多数投票决定。

```
quantQ rf.predictOnRF:{y;ensemble;data}
// y 预测向量
// ensemble -- 一个随机森林：
// tree: 树列表
// oob: 袋外（out-of-bag）预测值的表
// ibi: 每个样本的特征索引，即 X[i]
// 返回基于多数规则的分类结果
rf:{data;tree}
prediction: quantQ.trees.predictOnTree[select from tree where B=b]
data: update ibi: enlist b from prediction][data;tree;ensemble]
```

## 504 机器学习

记住袋外（out-of-bag）样本存储在单独的键中，通过对它们运行预测来验证已学习树的预测能力。现在让我们使用熟悉的 Iris 数据集，尝试通过输入之前章节中使用的每个物种的平均值来预测分类，预测：avgSepLength, avgSepW, avgPetalLength, avgPetalWidth。

| class | avgSepL | devSepL | avgSepW | devSepW |
| :--- | :--- | :--- | :--- | :--- |
| Iris-setosa | 5.006 | 0.34947 | 3.418 | 0.377149 |
| Iris-versicolor | 5.936 | 0.5109834 | 2.77 | 0.3106445 |
| Iris-virginica | 6.588 | 0.6294887 | 2.974 | 0.3192554 |

```
quantQ.rf.predictOnRF [params y; forest;5.006 3.418 1.464 0.244]
prediction | 1
mean_error | 0.5155709
dev_error | 0.57385
```

预测再次是错误的，因为输出是 1（versicolor），而我们的输入是 0 组（setosa）。

```
quantQ.rf.predictOnRF [params y; forest;5.936 2.77 4.26 1.326]
prediction | 2
mean_error | 0.5155709
dev_error | 0.57385
```

遗憾的是，预测再次错误，因为输出是 2（virginica），而我们的输入是 1 组（versicolor）。

## 森林 505

最后，

```
quantQ.rf.predictOnRF[params y; forest;6.588 2.974 5.552 2.026]
prediction | 2
mean_error | 0.5155709
dev_error | 0.57385
```

给了我们组 2 的正确预测。

观察袋外误差的平均误差和标准差，我们发现这些值太高，无法获得可靠结果。这与我们上面的实验一致，该实验仅产生了 3 个中的 1 个正确预测。

让我们尝试在样本中使用所有特征，但通过选择较小的数据集保持计算成本：

```
forest : quantQ.rf.randomForest params,B(4;125;10)
```

上面我们将样本量从 150 减少到 125，但在每个树节点分裂的选择标准中保留了所有 4 个特征。通过减少样本量，尽管我们现在使用了所有 4 个特征，但我们的预测准确性也提高了吗？

让我们看看：

```
quantQ.rf.predictOnRF[params y; forest;5.006 3.418 1.464 0.244]
prediction | 0
mean_error | 0.0464018
dev_error | 0.2104795
```

```
quantQ.rf.predictOnRF[params y; forest;5.936 2.77 4.26 1.326]
prediction | 1
mean_error | 0.0464018
dev_error | 0.2104795
```

```
quantQ.rf.predictOnRF[params y; forest;6.588 2.974 5.552 2.026]
prediction | 2
mean_error | 0.5155709
dev_error | 0.57385
```

