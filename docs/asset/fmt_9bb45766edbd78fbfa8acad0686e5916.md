
图 12.2 展示了使用不同分箱方案创建的四个直方图：图 12.2a 展示了 `histWidth`，图 12.2b 展示了 `histSquareRoot`，图 12.2c 展示了 `histRice`，图 12.2d 展示了 `histScott`。最后一种方法似乎并不特别有用。可以理解，斯科特规则背后的假设是正态分布，因为它是均匀分布集合的并集。数据并不符合正态分布，因此选择分箱方法非常重要。

最后，我们提醒读者，绘图时选择了“柱状 (Bars)”选项。柱状的默认宽度非常小，因此几乎不可见。为了此目的，

![Figure 12.2](img/97f581128bd0df5683d4c69424218.png)

使用不同函数的直方图

# 196

# 数据科学

我们选择了“柱状 (Bars)”选项用于绘图。柱状的默认宽度非常小，因此几乎不可见。为了此目的，

## 矩 (FIRST MOMENTS)

让我们定义一个实用的工具函数，它为给定的数值数组返回带有统计信息的表格。首先我们定义统计量，然后实现它。数据 $N \le K$：

### 样本均值

样本均值定义为：

$$\mu = \frac{1}{N} \sum_{i=1}^{N} x_i. \quad (12.5)$$

### 样本标准差

样本标准差定义为：

$$\sigma = \frac{1}{N-1} \sqrt{\sum_{i=1}^{N} (x_i - \mu)^2}. \quad (12.6)$$

### 样本偏度

样本偏度定义为：

$$S = \frac{\sqrt{N(N-1)}}{N-1} \frac{\frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^3}{\frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2}. \quad (12.7)$$

其中对于单峰分布，负偏度偏左，正偏度偏右。

### 样本峰度

样本峰度定义为：

$$K = \frac{\frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^4}{\frac{1}{N-1} \sum_{i=1}^{N} (x_i - \mu)^2}. \quad (12.8)$$

并用于评估数据的尾部。如果值为正，则数据被称为尖峰态 (leptokurtic)，即相对于正态分布具有厚尾；如果值为负，则数据被称为平峰态 (platykic)，即相对于正态分布具有细尾。

## 最小值

从非空值推导出最小值。

## 最大值

从非空值推导出最大值。

## 观测数

观测数对应于 $K$。

## 缺失观测数

缺失观测数为 $K - N$。

该工具集实现在 `overviewStats` 函数中：

```q
.quantQ.stats.overviewStats:[data]
// 数值数组
// 观测数
K: count data;
// 过滤掉缺失数据
data: data where not null data;
// 非缺失数量
Kminus:K:count data;
// 样本平均
mu: avg data;
// 样本标准差
sigma: dev data;
// 样本偏度
tmp: (data-mu);
N: count data;
S: (expo([N-1-0.5]%N-2))*((1.0"%f"$N)*sum tmp*tmp*tmp)*exp([(1.0"%f"$N)
	→ sum tmp*tmp*tmp);1.5);
// 样本峰度
Kurt: (((1.0"%f"$N)*sum tmp*tmp*tmp*tmp)*exp([(1.0"%f"$N)*sum tmp*tmp)
	→ 2]);3.0;
// 最小值
mn: min data;
// 最大值
mx: max data;
[] statistics: ("样本均值";"样本标准差";Sample
	→ 偏度";"样本峰度";
	→ 最小值";"最大值";观测数";Number of
	→ missing数\nvalues: (mu, sigma; S; K; mn; mx; KminusN));
```

};

(12.9)

# 统计学概览

其中 $\Phi$ 为 $N(0,1)$ 分布的累积分布函数。更重要的是，我们需要计算逆累积分布函数，即：

```
x = \Phi^{-1}(p). (12.10)
```

我们使用数值表将前一个显示所示的 $p$ 与 $x$ 的函数关系进行映射。这种方法适用于评估统计检验的显著性，因为我们通常只对几个对应于正态置信水平的数值感兴趣。文献中常用的数值有 0.1%、1%、5% 和 10%。我们定义了一个表格：

```
.quant.stats.normTable:(0.0005;3.290527); (0.005;2.578259); (0.01;2.326348);
:(0.495;0.125347); (0.5;0);
```

我们没有列出该表来观察双侧检验中概率 $P(|z| \ge 3.2905267314190)$，于 $1-0.0005$，等价于 $P(z \le -3.2905267314190)=0.0005$。对于单侧检验，$P(|z| \ge 3.2905267314190)=0.1$。我们将表格定义在书的命名空间内，它是分析中一个干净且静态的对象。

我们可以使用此表来近似 $\Phi^{-1}(p)$。具体而言，对于给定的非负 $x$，近似累积分布函数的算法可以如下进行：逐个遍历 `normTable` 列表中的每个元素。每个元素都是一对数字。找到小于 $x$ 的最大第二个元素。报告对应的第一个元素。则累积分布函数即为所提供算法返回的 $1-$ 该值。对于负值，我们可以通过使用 $|x|$ 以相同的方式进行，且在最后不执行 $1-$ 操作。

当该方法应用于给定统计量的置信水平时，这种方法是保守的，因为它提供了显著性水平的下界。当我们近似分布以评估检验时，这是一个很好的做法。此外，如果 `normTable` 包含 0.1%、1%、5% 和 10% 的值，这将对检验执行常规的计量经济学评估。

让我们实现这些函数，它们为双侧检验、原假设 $z \ge 0$（“左侧”）的单侧检验以及针对数值的原假设检验的单侧检验执行相应的 $p$ 值计算：

```
.quant.stats.pValueSided:[x]
// -- 服从 N(0,1) 的检验统计量值
// 返回对应的 p 值
2:(reverse last flip .quant.stats.normTable) neg[1]+
(reverse last flip .quant.stats.normTable) binr x;
);
```

我们对数值进行双侧检验：

```
.quant.stats.pValueSided[2.58]
```

0.01

# 200

# 数据科学

```
.quantQ.stats.pValueTwoSided[10.0]
```

```
0.001
```

```
.quantQ.stats.pValueTwoSided[0.0]
```

```
1f
```

最小可能的输入 0 以及大值的病态情况提供了有效结果。

此外，单侧检验给出如下：

```
.quantQ.stats.pValueLeftSided:[x]
// x -- 服从 N(0,1) 的检验统计量值
// 返回单侧左侧检验对应的 p 值
$[x>0;1-(reverse first flip .quantQ.stats.normTable) neg[1]+
  (reverse last flip .quantQ.stats.normTable) binr x;(reverse first
  flip .quantQ.stats.normTable)
neg[1]+(reverse last flip .quantQ.stats.normTable) binr abs x);
```

```
;
```

给出如下结果：

```
.quantQ.stats.pValueLeftSided[-2.58]
```

0.005

```

```

.quantQ.stats.pValueLeftSided[2.58]

```

0.995
```

并且，对于第三种检验：

```
.quantQ.stats.pValueRightSided:[x]
// x -- 服从 N(0,1) 的检验统计量值
// 返回单侧右侧检验对应的 p 值
$[x<0;(reverse first flip .quantQ.stats.normTable) neg[1]+(reverse
  last flip .quantQ.stats.normTable)
binr x;1-(reverse first flip .quantQ.stats.normTable) neg[1]+(
  reverse last flip .quantQ.stats.normTable)
binr abs x);
```

```
;
```

在提供的示例上给出：

```
.quantQ.stats.pValueRightSided[-2.58]
```

0.995

# 统计学概览

.quantQ.stats.pValueRightSided[2.58]

我们可以对于服从 $N(0,1)$ 分布的给定统计量值获得 $p$ 值。

# 统计学概览（此处重复标题）

我们可以对于服从 $N(0,1)$ 分布的给定统计量值获得 $p$ 值。

# 1.3.2 相关性

我们用于评估变量 $X$ 和 $Y$ 之间依赖性的基本工具是相关性，记为 $\rho_{XY}$。定义：

$$\rho_{XY} = \frac{cov(X,Y)}{\sigma_X \sigma_Y}$$

其中 $cov$ 是协差，$\sigma_X$ 和 $\sigma_Y$ 分别代表标准差。当我们近似分布以评估检验时，这是一个很好的做法。此外，如果 `normTable` 包含 0.1%、1%、5% 和 10% 的值，这将对检验执行常规的计量经济学评估。

（注：原文中存在大量重复和逻辑混乱，此处已根据上下文尽可能翻译，部分重复的“统计学概览”等段落已按原文结构保留）

## 204 实现

12.3.3.1 $t$ 统计量的计算相当直观：

```
quantQ.stats.tTestOneSample([x1;mean])

// x1 - 需要测试的数组

// mean - 平均值

// 返回 t 统计量

// (avg[x1]-mean)%dev[x1]% sqrt(count x1);
```

输入是样本以及我们在零假设下想要评估的均值值。该函数返回统计量。测试的评估通过该函数完成，该函数将统计量映射到给定测试集对应的 p 值。在这些示例中，我们使用 $\mu$ 等于 0.45 的双侧检验。统计量的值可以计算为：

```
quantQ.stats.tTestOneSample[xTest:100?1.0;0.45]
```

结果为 1.929509，而对应的 p 值为：

```
quantQ.stats.pValueTwoSided abs quantQ.stats.tTestOneSample[xTest;0.45]
```

0.06 测试的 p 值为 6%，这表明我们可以在 6% 的置信水平下拒绝均值等于 0.45 的零假设。尽管均值为 0.5，且测试值 0.45 小了 10%，但样本量使得我们无法确信地拒绝零假设。

## 12.3.4 t 检验：双样本

在之前，我们对一个样本与静态均值值进行了测试。在实践中，我们可能想要测试两个具有相同均值的样本。让我们独立抽取的样本 $X_1, ..., X_N$，代表随机变量 $X$ 的 $N$ 次抽取，其总体均值为 $\mu_1$，标准差为 $\sigma_1$；独立抽取的样本 $y_1, ..., y_M$，代表随机变量 $Y$ 的 $M$ 次抽取，其总体均值为 $\mu_2$，标准差为 $\sigma_2$。待测试的假设形式如下：

- $H_0$：总体均值相等，$\mu_1 = \mu_2$。
- $H_a$：总体均值不同。

测试通过构建合适的检验来完成。统计量的形式取决于对 $N$ 和 $M$以及 $\sigma_1$ 和 $\sigma_2$ 分别提出的假设。假设越强，越接近渐近行为，但越容易产生模型误差。在本次测试中，我们关注限制最少的双样本 $t$ 统计量，也称为 Welch 检验（Welch's test）。在这种情况下，对 $N$ 和 $M$、$\sigma_1$ 和 $\sigma_2$ 之间的关系没有假设。Welch $t_W$ 统计量定义为：

```
$t_W = \frac{\bar{X}-\bar{Y}}{s_W} \ (12.17)$
```

其中 $s_W$ 定义为：

```
$s_W = \sqrt{\frac{\frac{1}{N-1}\sum_{i=1}^N(X_i-\bar{X})^2}{\frac{1}{M-1}\sum_{i=1}^M(Y_i-\bar{Y})^2}} \ (12.18)$
```

Welch $t_W$ 统计量在零假设下遵循 $\sim t_{Wdf}$，其中自由度为：

```
$W_{df} = \frac{(\frac{\sigma_1^2}{N}+\frac{\sigma_2^2}{M})^2}{\frac{(\frac{\sigma_1^2}{N})^2}{N-1}+\frac{(\frac{\sigma_2^2}{M})^2}{M-1}} \ (12.19)$
```

我们可以使用 $t_W$ 统计量形成以下假设：

- $H_0$：总体 $\mu_1$ 等于/小于或等于/大于总体 $\mu_2$。
- $H_a$：总体 $\mu_1$ 与总体 $\mu_2$ 不同/大于/小于。

这三项测试（即一个双侧检验和两个单侧检验）可以在上述例中进行评估。如果 $|t_W| > t_{critical,Wdf}$、$t_W < -t_{critical,Wdf}$ 且 $t_W > t_{critical,Wdf}$，则我们分别拒绝零假设。然而，我们将假设临界值 $t_{critical,Wdf}$ 取决于测试中的显著性水平、渐近行为并基于正态分布。

## 12.3.4.1 实现

$t_W$ 统计量的计算给出：

```
quantQ.stats.tTestTwoSample{x1;x2}

// x1,x2 -- 需要测试的数组，不相等

// 返回 Welch 统计量

// (avg[x1]-avg[x2])/sqrt((dev[x1]/count[x1])+(dev[x2]/count[x2]))
```

我们使用两个均值相同但大小和方差不同的样本对函数进行测试：

```
quantQ.stats.tTestTwoSample[x1:100;1.0;x2:100]
```

## 数据科学

然后使用正态分布将该值转换为对应的 p 值：

```
quantQ.stats.pValueTwoSided abs quantQ.stats.tTestTwoSample[x1;x2]
```
