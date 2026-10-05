

## 线性回归

![](img/97f7581128bd0bdf85683d4c69d94242_283_0.png)

**图 13.5** 表 tabData 中真实值与预测值之间的对比

13.5 描述了因变量 tabDataMODEL[`y`] 的真实值与预测值 tabDataMODEL[`Predicted`] 之间的散点图。这些点分布在对角线周围，表明预测具有准确性。误差的从斯斯分布特性以及样本量较小，导致没有出现离群值。

我们进一步利用了表 tabDataMODEL 的结构。具体而言，让我们创建一个函数，来计算真实值与预测值之间的均方根误差，即 RMSE。*RMSE* 定义为：

> $RMSE = \sqrt{\frac{1}{N}\sum_{i=1}^{N}(y_i - y_{predicted})^2}, \quad (13.70)$

其中 $y_i$ 代表因变量的值，$y_{predicted}$，共有 $N$ 个观测值。

均方根误差是比较预测值与真实值的常用方法。文献中还有许多替代方法，例如平均绝对误差 (MAE)，它采用绝对值之和而不是平方和和平方根。其原因源于 *RMSE* 对离群值的敏感性，而离群值会被方程中的平方项所放大。

*RMSE* 被实现为一个函数，该函数假设输入表的前两列是相关列。事实上，由于平方和平方根的存在，真实变量和预测变量的顺序并不重要。此外，第二列之后的列不被考虑。该函数读取：

```python
quantols.RMSE[:tabModel] // 第一列为真实因变量的表格
-- 第二列为估计值
sqrt:tabModel[cols[:2]]
```

## 数据科学

随后可以获得 tabData 中结果的 RMSE：

```python
quantols.RMSE[tabData]
```

0.0982736

我们得到的这个值在孤立存在时并没有太大意义。我们需要一些锚点来判断 RMSE 值以及模型在样本外的表现。可能的应用是对另外两组数据进行估计，这些数据将包含在模型中的自变量。为了实现这一点，请实现一个接受三个参数的估计套件：因变量、自变量矩阵以及决定样本内和样本外划分的标志：

```python
quantols.out:(y;x;inFlag)
 // 因变量数组
 // 自变量数组，要包含的常量
 // inFlag:1=y<=0时为样本外；0=x<=0时为样本内
 // 移除缺失值
y[(til count y) except whereMissing];
x[[:whereMissing]] x:(til count x) except whereMissing]]
 // inFlag 是随机选择的样本比例
if(1=count[inFlag]); // 划分：样本外
x:tabModel[inFlag+count y] - x;
y:tabModel[inFlag+count y] - y; // 划分：样本内
x:tabModel[inFlag+count y] * x;
y:tabModel[inFlag+count y] = 0; // inFlag 是布尔数组，1为内/0为外
if(1=count[inFlag]); // 划分：样本外
yPRED:sum[IN]*x; // 输出桶
RMSE:avg:y-yPRED;
reg:Observations(count[y]);
x:flip[x] where inOut; // 样本内回归
IN:quantols.fit(y;x);
 // 样本外
yPRED:sum[IN]*x;
RMSE:avg:y-yPRED;
```

样本内和样本外的划分可以通过以下方式完成：如果 inFlag 是一个位于 0 和 1 之间的标量，它代表训练样本的比例。通过时间序列方法，样本外数据通常被认为是最新的。另一种方法是我们可以指定哪些数据用于样本内和样本外。在这种情况下，inFlag 是一个布尔数组，1 表示样本内，0 表示样本外。该标志用于评估，因此非零值被视为样本内。让我们显示 80% 的数据和 20% 的剩余数据：

```python
reg1:quantols.out[8];

| beta | errors | varcov | observations | df | SS | Rsquared | adjsquared | levels | log | ic |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1.00308 | 0.008409 | 0.008389 | 200 | 199 | 3066.72 | 0.99677 | 0.99647 | 1 | -8143.2 | -1611.9 |
```

