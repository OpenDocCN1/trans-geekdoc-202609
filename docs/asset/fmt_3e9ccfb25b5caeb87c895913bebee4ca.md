
```
.qtrees.applyRule:[cbm;bmi;xi;rule;j]
// cbm 位图计数：用于预测变量的采样点数
// bmi 位图：指示此节点采样变量的索引
// xi 第 i 个预测变量
// 用来分裂的规则
// j 根据规则在点 j 处分裂 xi
(:bitmap applied!((@zb;cbm;bmi;]) not b);
// bitmap applied!((@zb:cbm@b; bmi;]) b=eval(rule;xi;j); ((:))
;
```

```
.qtrees.runRule:[rule;i;j] rule[x i j]
```

在上面的 `applyRule` 中，我们还携带了初始样本数据的索引位图并返回一个字典——这样做允许我们想象每个节点的树结构和内容，使我们每一步都能观察和研究树。

现在我们可以移动到更高层次的函数选择划分并最终生长树：

```
.qtrees.chooseSplitXi:[{yy;y;cbm;bmi;rule;classes;xi]}
// yy 预测变量，所有样本点
// y 节点处的预测变量
// cbm 位图计数：用于预测变量的采样点数
// bmi 位图：指示此节点采样变量的索引
// xi 第 i 个预测变量
```

# 512

# 488

# 机器学习

```
j: asc distinct xi;
info:[[yy;cbm;xi;rule;classes]
split: .qtrees.applyRule[cbm;bmi;xi;rule;j]
  .qtrees.infogain[x where y]]each split;
```

通过遍历所有划分为节点选择最佳划分并找到信息增益最大的划分：

```
-qtrees.growTree:[xy;treeinput]
// treeinput -- 带有划分信息的字典
// xy -- 字典
// 预测 (x) 集合
// 预测 (y) 向量
// k 个分类类的不同向量 (`classes`
// 要采样的预测向量数量 (`m
// 最大树深度 (`maxdepth
:[xy;r]
if[{1]=count distinct xy['y]where r`bitmap
  or xy['maxdepth]<=count r`rulepath;
  ];;
```

```





# 树 489

```

enlist[r],$98<h>type r::quant.trees.growTree[xy;r] raze @[rr;

  where 99h=type each r;enlist];rr

]}each r::quant.trees.chooseSplit[xy;treeinput]

```

我们可以学习一棵树：对于初始划分中的每条记录，我们迭代到纯节点（叶子节点）或达到指定的最大深度（`maxdepth` 键）。当我们到达叶子节点时，返回一个扁平化的结果，然后对下一个划分记录进行递归，直到没有剩余记录为止。扁平化的树应包含所有路径以及一个带有所有索引 $i$ 的父节点的树状结构。提供的函数作为输入，包含预测器的索引、它的索引 $i$ 和 $j$、增益（gain）以及四个传递的四个参数：

```

-quant.trees.learnTree[:params]

// 用于学习树的参数字典

// m 随机选择的特征数量，默认为所有特征

// maxdepth 树的最大深度，如果未达到纯节点，默认

// 100

params[m]: [$m in key params;m;count params`]

params[maxdepth]: [$maxdepth in key params;params`maxdepth;100];

r0: ofinfoains xij`jofain bitmap`X appliedrule`rulepath

classes`m`maxdepth

params,

infoains xij`jofain bitmap`appliedrule`rulepath(!(();ON;0N;0n

  ;count [params`y]wB;::(());));

tree: enlist[r0];

[$98<>type r::quant.trees.growTree;r0:dc`x`y`classes`m

  maxdepth`r

raze @[r,99h=type each r;enlist];

r;

tree: update p:(x'-_l) rulepath from tree;

  :'ip`path xcols update path:(x scan)each till x}p,i:i from tree;

);
```

现在我们将为拟合（或学习）树树所需的参数创建一个字典：

```

dataset!();

daset[x]:value flip delete from iris;

daset[y]:[distinct[x?] iris[`class];

params:dataset,`rule classes!(asc distinct dataset`y);
```

查看您的特征：

```

flip params`x
```

```

5.1 3.5 1.4 0.2

4.9 3 1.4 0.2

4.7 3.2 1.3 0.2

4.6 3.1 1.5 0.2

5 3.6 1.4 0.2

5.4 3.9 1.7 0.4

5 3.4 1.5 0.2

4.4 2.9 1.4 0.2
```

# 490

# 机器学习

```

4.9 3.1 1.5 0.1

5.4 3.7 1.5 0.2

4.8 3.4 1.6 0.2

4.8 3 1.4 0.1

4.3 1.1 0.1

5.8 4 1.2 0.2

5.7 4.4 1.5 0.4

..
```

以及我们预测变量的分类：

```

distinct params`y
0 1 2
```

并以表格形式可视化：

```

flip @[`x`y`params;x;flip]`
```

| x | y |
|---|---|
| 5.1 3.5 1.4 0.2 | |
| 4.9 | 1.4 0.2 | |
| 4.7 3.2 1.3 0.2 | |
| 4.6 3.1 1.5 0.2 | |
| 5 3.6 1.4 0.2 | |
| 5.4 3.9 1.7 0.4 | |
| 5 3.4 1.5 0.2 | |
| 4.4 2.9 1.4 0.2 | |

| 4.9 3.1 1.5 0.1 | |
| 5.4 3.7 1.5 0.2 | |
| 4.8 3.4 1.6 0.2 | |
| 4.8 3 1.4 0.1 | |
| 4.3 1.1 0.1 | |
| 5.8 4 1.2 0.2 | |
| 5.7 4.4 1.5 0.4 | |
..

当我们**生长 (learn)** 一棵树时，我们可以看到返回的 `tree`包含了 `params`，这些是探索每个节点非常有用的中间步骤：

# 492 机器学习

我们可以返回一个只包含叶子节点的子树 $T'$：

```

quant.trees.leaves:[[tree
// tree decision tree
// select from tree where i in til[count p]except p
};
```

其中 $p$ 是该节点的父节点，我们选择所有不是父节点的节点：

```

quant.trees.leaves
```

| i p path | infogains |
|---|---|---|
| | xi | infogain bitma.. |
| 1 0 1 0 | *s0* 0 1 2 3.10.557327 0.267914 0.9182958 0.9182958 2 |
| 5 4 5 32 0 | *s0* 0 1 2 3.10.444276 0.0378185 0.234482 0.146043 3 |
| 6 4 6 3 2 0 | *s0* 0 1 2 3.10.444276 0.0378185 0.234482 0.146043 3 |
| 8 7 7 3 2 0 | *s0* 0 1 2 3.10.191703 0.252692 0.252692 0.459147 3 |
| 10 9 7 3 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 11 9 7 3 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 14 13 14 13 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 15 13 15 12 2 0 | *s0* 0 1 2 3.10.918298 0.252692 0.9182958 0.252692 3 |
| 16 12 16 12 2 0 0 | |

我们可以检查 `tree` 的字段，例如带有关联规则的完整规则路径：

```

select i,p,path,xi,j,rule from tree
x path xi j
-- --
0 0 ()
1 0 1 2 .9
2 0 2 .9
3 2 0 .7
4 4 3 2 .9
5 4 3 2 .6
6 4 3 2 .6
7 7 3 2 .9
8 7 3 2 .5
9 7 3 2 .5
10 9 7 3 2 .6
11 9 7 3 2 .6
12 12 2 0 0 .7
13 13 12 2 0 0 .8
14 13 12 2 0 0 .9
15 13 15 12 2 0 0 .0
16 12 16 12 2 0
```quant.trees.learn

meta tree
| c | t a |
|---|---|
| i | |
| p | |
| path | |

infogains | xi
infogain | f
bitmap | appliedrule
rulepath

# 496 # 机器学习

## 机器学习

分布函数 $G$，即 $\theta = \theta(N, G)$。有两种可能的情况会导致采样分布函数的推断变得复杂：

- $G$ 是已知的，但 $\hat{\theta}(X_1, \dots, X_N)$ 太复杂，无法推导出采样分布 $\theta(N, G)$。
- $G$ 是未知的。

在这两种情况下，$\theta$ 都无法通过解析法推导。让我们强调，渐近理论旨在通过解析法推导该函数并评估其性质。在许多情况下，该函数收敛于方差正比于 $N^{-\alpha}$ 的正态分布。后续段落并非如此。

### $G$ 已知，$\hat{\theta}$ 复杂

由于解析推导可行，我们可以通过数值方法推导 $\hat{\theta}$ 的性质。特别是，我们通过放回采样生成 $B$ 个样本 $X_1^b, \dots, X_N^b$，$b=1, \dots, B$。对于每个样本，我们计算相应的 $\hat{\theta}_b$。

有了 $\hat{\theta}$，我们可以使用观测样本的经验分布函数来估计 $\theta$。评估 $\hat{\theta}$ 的变异性是直观的；我们可以从样本中读取。我们可以对 $\hat{\theta}$ 的值进行假设检验。值得注意的是，我们的数值限制会影响近似的准确性：$B$ 越大，近似就越准确。

### $G$ 未知

我们进一步限制了认知范围，假设我们不知道 $G$。我们对 $G$ 的无知有两个可能的原因。首先，如果我们知道直到参数 $(\vartheta)$ 的 $G$ 的函数形式。如果我们知道该参数，就可以按照上一段中概述的方法进行。然而，在许多情况下，我们可以获得参数 $\vartheta$ 的估计值。在这种情况下，我们可以采用参数自助法（parametric bootstrap），并假设数据来自 $G(\vartheta)$。然后按如下步骤操作：

让我们考虑一个更有趣的情况，即我们对 $G$ 一无所知。关于 $G$，我们唯一知道的信息是样本 $X_1, \dots, X_N$ 中编码的内容。分析 $\hat{\theta}$ 的统计性质是使用非参数自助法（nonparametric bootstrap）。首先，我们从观测样本中构建经验分布 $G_N$。该函数为每个值 $x_i$（$i=1, \dots, N$）分配相同的概率 $1/N$。我们将 $G_N$ 视为 $G$ 的近似。然后按如下步骤操作：从 $G$ 中抽取 $B$ 个大小为 $N$ 的样本。对于每个样本，我们计算 $\hat{\theta}_b^*$。然后，我们根据序列 $\hat{\theta}_b^*$ 导出的分布函数评估 $\hat{\theta}$。例如，$\hat{\theta}$ 的标准差给出：

```
$$\sigma_{\hat{\theta}} = \sqrt{\frac{1}{B} \sum_{b=1}^{B} (\hat{\theta}_b^* - \frac{1}{B} \sum_{b=1}^{B} \hat{\theta}_b)^2}}$$ $$(25.1)$$
```

从 $G_N$ 生成自助样本意味着对 $x_1, \dots, x_N$ 进行放回采样。

# 森林

# 497 # 抛硬币

让我们用一个简单的例子来说明自助法。我们抛一次硬币，用 1 表示正面，0 表示反面。我们对抛 $N$ 次硬币时平均值的估计量的性质感兴趣。抛 $N$ 次硬币等同于记录序列 $x_1, x_2, \dots, x_N$，其中 $x_i = 0$。感兴趣的统计量是：

```
$$\mu_N = \frac{1}{N} \sum_{i=1}^{N} x_i. \quad (25.2)$$
```

为了评估 $\mu_B$ 的统计性质，我们从 $x_1, \dots, x_N$ 中放回抽取 $B$ 个样本。这样的自助样本可能是$B = x_3, x_4, x_1, x_N, x_1, \dots$。我们重复该过程 $B-1$ 次并收集 $\mu_{N,1}, \dots, \mu_{N,B}$。$\mu_{N,b}$（$b=1, \dots, B$）的经验分布函数可以用于近似 $\hat{\mu}_B'$。

我们可以对 $N=10$ 且 $p_{tail}=0.6$ 进行数值说明。我们对该示例估计量的标准差感兴趣。以下代码给出了答案：

```
B:100;
dev (avg ((N:10)?1.0)<0.6) each tail B
0.1527711
```
