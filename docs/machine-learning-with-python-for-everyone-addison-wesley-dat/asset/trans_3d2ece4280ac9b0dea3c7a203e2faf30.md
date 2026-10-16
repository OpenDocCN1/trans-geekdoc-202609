
In [12]:

```
# note: we use the squares of the correlations, r^2
corrs = np.corrcoef(diabetes_train_ftrs,
                    diabetes_train_tgt, rowvar=False)[-1, :-1]
cor_order = np.argsort(corrs**2) # r^2 (!)
cor_names = np.array(diabetes.feature_names)[cor_order[::-1]]

# and sklearn's f_regression calculation
f_scores = ftr_sel.f_regression(diabetes_train_ftrs,
                                diabetes_train_tgt)[0]
freg_order = np.argsort(f_scores)
freg_names = np.array(diabetes.feature_names)[freg_order[::-1]]

# numpy arrays don't like comparing strings
print(tuple(cor_names) == tuple(freg_names))
```

True

如果你迷失了大局，这里有一个回顾：

- 方差尚可，但协方差是一个很大的改进。
- 协方差有些粗糙；相关系数 $r$ 很不错；平方相关系数 $r^2$ 更不错。
- sklearn 的 `f_regression` 已为我们按 $r^2$ 排序。

我们可以使用 `f_regression` 按 $r^2$ 排序。

## 13.1.1.3 信息度量

相关性只能直接衡量其输入之间的 *线性关系*。还有许多——甚至无限多种——我们可能关心的其他关系。因此，我们可能会计算列之间其他有用的统计量。从特征和目标之间的关系来看，一个非常通用的方法来自 *编码和信息论* 领域。我们不会深入细节，但让我讲一个简短的故事。

就像许多小孩子一样，我 *爱* 手电筒。我很快就发现摩尔斯电码允许人们用闪烁的手电筒传输信息。然而，年幼的我认为记忆摩尔斯电码是一项不可逾越的任务。相反，我和朋友们为非常具体的场景编造了自己的代码。例如，在玩夺旗游戏时，我们想知道穿过一个场地是否安全。如果只有两个答案，*是* 和 *否*，那么两种简单的闪烁模式就足够了：一次闪烁表示 *否*，两次闪烁表示 *是*。想象一下，大多数时候场地是安全的。那么，大多数时候，我们希望发送一个 *是* 消息。但这样一来，使用两次闪烁表示 *是* 实际上有点浪费。如果我们交换闪烁的含义——一次表示 *是*，两次表示 *否*——我们就能节省一些工作。简而言之，这些就是编码和信息论考虑的思想：如何在考虑我们想要传输的一些消息比其他消息更可能的情况下，高效地通信或传输信息。

现在，如果你没有打瞌睡，你可能想知道这与关联特征和目标有什么关系。想象一下，特征值是一条发送给学习者的消息（图 13.2）。学习者需要解码该消息并将其转化为结果——我们感兴趣的目标。信息论度量将特征视为翻译成一条消息，该消息被解码并导致最终目标。然后，它们量化不同特征传达其信息的程度。信息论中的一个具体度量称为互信息，它以一般意义上捕捉了知道一个结果的值在多大程度上告诉我们另一个值的价值。

![](img/d94e4cd766940d79abed0bc6ba4e4344_446_0.png)

图 13.2 通过手电筒从特征向目标发送消息。

### 一个有用变量和一个随机变量

我们将从一个问题开始，该问题表达起来很简单，但会导致非线性分类问题。

In [13]:
```
xs = np.linspace(-10,10,1000).reshape(-1,1)
data = np.c_[xs, np.random.uniform(-10,10,xs.shape)]
tgt = (np.cos(xs) > 0).flatten()
```

由于这是一个相当不直观的公式，让我们从图形上看它：

In [14]:
```
plt.figure(figsize=(4,3))
plt.scatter(data[:,0], tgt);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_446_1.png)

基本上，我们有一个在规则间隔内打开和关闭（0 和 1）的模式。图并不复杂，但明显是非线性的。在数据中，我们的第一列是均匀间隔的值；第二列是随机值。我们可以查看每个列相对于我们非线性目标的互信息：

In [15]:
```
mi = ftr_sel.mutual_info_classif(data, tgt,
    discrete_features=False)
print(mi)
```

[0.6815 0.0029]

这是一个相当好的迹象：随机列的值很小，几乎为零，而信息列的值较大。我们可以对回归问题使用类似的度量。

In [16]:
```
xs = np.linspace(-10,10,1000).reshape(-1,1)
data = np.c_[xs, np.random.uniform(-10,10,xs.shape)]
tgt = np.cos(xs).flatten()
```

这是第一列与我们目标的图：

In [17]:
```
plt.figure(figsize=(4,3))
plt.plot(data[:,0], tgt);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_447_0.png)

现在我们可以比较 r² 类似和互信息技术：

In [18]:
```
print(ftr_sel.f_regression(data, tgt)[0],
      ftr_sel.mutual_info_regression(data, tgt),
      sep='\n')
```

[0. 0.]
[1.9356 0.  ]

在此示例中，无信息、随机列和信息列与目标的线性关系均为零。然而，查看 mutual_info_regression，我们看到一组合理的值：随机列给出零，信息列给出一个正数。

### 两个预测变量

现在，如果我们有不止一个信息变量会怎样？以下是一些数据：

In [19]:
```
xs, ys = np.mgrid[-2:2:.2, -2:2:.2]
c_tgt = (ys > xs**2).flatten()

# basically, turn r_tgt off if y<x**2
r_tgt = ((xs**2 + ys**2)*(ys>xs**2))

data = np.c_[xs.flat, ys.flat]

# print out a few examples
print(np.c_[data, c_tgt, r_tgt.flat][[np.arange(0,401,66)]])
```

[[-2.  -2.   0.   0. ]
 [-1.4 -0.8 0.   0. ]
 [-0.8  0.4 0.   0. ]
 [-0.2  1.6 1.   2.6]
 [ 0.6 -1.2 0.   0. ]
 [ 1.2  0.   0.   0. ]
 [ 1.8  1.2 0.   0. ]]

这导致了两个不同的问题，一个是分类，一个是回归。

In [20]:
```
fig,axes = plt.subplots(1,2, figsize=(6,3), sharey=True)
axes[0].scatter(xs, ys, c=np.where(c_tgt, 'r', 'b'), marker='.')
axes[0].set_aspect('equal');

bound_xs = np.linspace(-np.sqrt(2), np.sqrt(2), 100)
bound_ys = bound_xs**2
```
```
axes[0].plot(bound_xs, bound_ys, 'k')
axes[0].set_title('Classification')

axes[1].pcolormesh(xs, ys, r_tgt,cmap='binary')
axes[1].set_aspect('equal')
axes[1].set_title('Regression');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_449_0.png)

在这里计算任何统计数据之前，让我们思考一下这个场景一分钟。如果你告诉我 y 的值且它小于零，我就能知道很多关于结果的信息：它总是蓝色（对于分类）或白色（对于回归）。如果 y 大于零，我们的收获就不那么大了，但随着 y 的不断增加，红色（左图）或黑色（右图）的可能性会更高。对于 x，大于零或小于零的值实际上意义不大：事物关于 x 轴完全平衡。

尽管如此，我们可以查看使用 mutual_info_classif 计算的 c_tgt 的基于信息度量：

In [21]:
```
print(ftr_sel.mutual_info_classif(data, c_tgt,
    discrete_features=False, random_state=42))
```

[0.0947 0.1976]

r_tgt 回归问题的相对值与 mutual_info_regression 的值大致相似：

In [22]:
```
print(ftr_sel.mutual_info_regression(data, r_tgt.flat,
    discrete_features=False))
```

[0.0512 0.4861]

这些值与我们的直觉讨论很好地吻合。

## 13.1.1.4 选择顶部特征

实际上，当我们想要应用选择度量时，我们希望对特征进行排名然后挑选。如果我们想要固定数量的特征，SelectKBest 可以轻松实现。我们可以用以下代码取前五名：

In [23]:
```
ftrsel = ftr_sel.SelectKBest(ftr_sel.mutual_info_classif, k=5)
ftrsel.fit_transform(wine_train, wine_train_tgt)

# extract names
keepers_idx = ftrsel.get_support()
print(np.array(wine.feature_names)[keepers_idx])
```

['flavanoids' 'color_intensity' 'hue' 'od280/od315_of_diluted_wines' 'proline']

这使得比较两种不同的特征选择方法变得相对容易。我们看到在 f_classif 和 mutual_info_classif 下，选出的前五个特征大多相同。

In [24]:
```
ftrsel = ftr_sel.SelectKBest(ftr_sel.f_classif, k=5)
ftrsel.fit_transform(wine_train, wine_train_tgt)

keepers_idx = ftrsel.get_support()
print(np.array(wine.feature_names)[keepers_idx])
```

['alcohol' 'flavanoids' 'color_intensity' 'od280/od315_of_diluted_wines' 'proline']

如果我们更喜欢获取特征的某个百分比，我们可以使用 SelectPercentile。将它与 r² 结合，我们得到：

In [25]:
```
ftrsel = ftr_sel.SelectPercentile(ftr_sel.f_regression,
                                  percentile=25)
ftrsel.fit_transform(diabetes_train_ftrs,
                     diabetes_train_tgt)

print(np.array(diabetes.feature_names)[ftrsel.get_support()])
```

['bmi' 'bp' 's5']

要使用互信息，我们可以这样做：

