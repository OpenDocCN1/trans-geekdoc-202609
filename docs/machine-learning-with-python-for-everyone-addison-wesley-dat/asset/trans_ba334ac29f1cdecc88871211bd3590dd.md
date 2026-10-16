
3. SVCs 能很好地泛化到新测试数据，因为它们试图在类别之间尽可能留出缓冲空间——这就是最大间隔原则在发挥作用。

4. 潜在的优化问题——寻找最佳直线——在我们的约束条件下会得到最佳直线。我们不会得到次优的直线。

## 8.3.1 执行 SVC

使用 SVC 时有几个实际细节需要注意：

- SVCs 本身并不适合多类分类。它们通常被封装在“一对一”（OvO）或“一对多”（OvR）系统中。我们在第 6.3.4 节和 6.4 节讨论过这些差异。注意，你不需要为 SVM 添加此功能。它已在幕后为你完成。自 scikit-learn 版本 0.19 起，这些方法都已标准化为使用 OvR。此前，OvO 和 OvR 混用。
- 在 sklearn 中获取 SVC 的方式有四种（实际上更多）：(1) 使用 LinearSVC，(2) 使用线性核的 SVC，(3) 使用 1 次多项式核的 SVC（伪装的直线），(4) 使用线性核的 NuSVC。这四种方法不一定会得到完全相同的结果，因为存在数学、实现和默认参数上的差异。调和这些差异很痛苦；我在本章末尾有一些相关说明。另外，我们尚未讨论核函数，我们将推迟到第 13.2.4 节再讨论。对于现在，请将其视为一个编码细节——尽管它远不止于此。

### 8.3.1.1 事实：运行 SVC

这里，我将只关注这两种 SVC 选项：SVC 和 NuSVC。我马上会讨论 nu 参数，但我选择其值为 .9 以获得接近 SVC 的结果。

```
In [12]:

sv_classifiers = {"SVC(Linear)"  : svm.SVC(kernel='linear'),
                  "NuSVC(Linear)" : svm.NuSVC(kernel='linear', nu=.9)}
```

```
In [13]:

fig, axes = plt.subplots(1,2,figsize=(6,3))
for (name, mod), ax in zip(sv_classifiers.items(), axes.flat):
    plot_boundary(ax, iris.data, iris.target, mod, [0,1])
    ax.set_title(name)
plt.tight_layout()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_282_0.png)

![](img/d94e4cd766940d79abed0bc6ba4e4344_282_1.png)

乍一看，SVC 和 NuSVC 非常相似，但区域边界的确切角度并不完全相同。

### 8.3.1.2 SVC 的参数

SVC 依赖一个主要参数 C 来控制其偏差-方差权衡。C 直接解释起来可能比较困难。NuSVC 解决与 SVC 相同的任务，但依赖不同的数学方法。我们之所以关注它，是因为 NuSVC 的主要参数 ν——读作 new，英文写作 nu——具有简单的含义：至少有 ν% 的数据将被保留为支持向量。它对误差也有影响，但是一种特殊类型的误差：间隔误差。间隔误差是指 (1) 在分隔线错误一侧的点（分类错误）或 (2) 在分隔线正确一侧（分类正确）但位于间隔内的点。因此，ν 的另一个作用是我们容忍训练数据中最多 ν% 的间隔误差。在某些情况下，间隔误差会增加到 ν，而支持向量会减少到 ν。ν 的取值范围在 [0, 1] 之间，我们将其解释为从 0% 到 100% 的百分比。虽然更难解释，但 SVC 相比 NuSVC 具有更好的运行时间特性。

SVC 的参数带有一点神秘性：它们是只有炼金术士才知道的隐藏秘密。事实上，你必须深入研究一些复杂的数学才能理解它们的含义。尽管如此，我们仍可以在一些小例子上探索它们的效果。（我说的是小，不是简单。）让我们看看改变 C 和 ν 如何影响类别之间的边界。

In [14]:

```
def do_linear_svc_separators(svc_maker, pname, params, ax):
    'create svc(params) and draw separation boundary'
    xys = (np.linspace(2,8,100),
          np.linspace(2,8,100))

    for p in params:
```

```
```python
kwargs = {pname: p, 'kernel': 'linear'}
svc = svc_maker(**kwargs).fit(ftrs, tgt)
# plot_separator is in mlwpy.py
plot_separator(svc, *xys,
              '{}={}'.format(pname, p), ax=ax)
```
```

```
```python
In [15]:

ftrs = np.array([[3,3],
                 [3,6],
                 [7,3],
                 [7,6],
                 [6,3]])
tgt = np.array([0,0,1,1,0])
colors = np.array(['r', 'b'])

Cs = [.1, 1.0, 10]
nus = [.3, .4, .5]

fig, axes = plt.subplots(1,3,figsize=(12,4),
                         sharex=True, sharey=True)
for ax in axes:
    ax.scatter(ftrs[:,0], ftrs[:,1], c=colors[tgt])
ax.set_xlim(2,8); ax.set_ylim(2,7)

do_linear_svc_separators(svm.SVC, "C", Cs, axes[1])
do_linear_svc_separators(svm.NuSVC, "nu", nus, axes[2])

axes[0].set_title("No Boundary")
axes[1].set_title("C Boundaries")
axes[2].set_title(r"$\nu$ Boundaries");

# the two right most points are blue
# the remaining three points are red
```
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_283_0.png)

这里有两个要点：

- 1. 更大的 ν 和更小的 C 大致具有相同的效果。然而，ν 和 C 的尺度相当不同。我们在 C 上使用数量级，在 ν 上使用线性、十分之一的步长。
- 2. 更大的 ν 和更小的 C 可以使我们得到一个在某种程度上忽略误分类的 SVC。

## 8.3.2 SVC 中的偏差与方差

这里再做最后一点评论。让我们看看我们的参数——NuSVC 中的 ν 和 SVC 中的 C——如何与偏差和方差相关。我们先从创建一些数据开始：

In [16]:

```
ftrs, tgt = datasets.make_blobs(centers=2,
                                n_features=3,
                                n_samples=200,
                                center_box = [-2.0, 2.0],
                                random_state=1099)

# note: using three features, but graphing only two dimensions
fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.scatter(ftrs[:, 0], ftrs[:, 1],
           marker='o', c=tgt, s=25, edgecolor='k')
ax.axis('off');

# generally the yellow class is on top
# and the purple class is on bottom
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_284_0.png)

现在，我们来看 ν 的影响：

In [17]:

```
nus = np.linspace(0.05, 1.0, 10)
tt = skms.validation_curve(svm.NuSVC(kernel='linear'),
    ftrs, tgt,
    param_name='nu',
    param_range=nus,
    cv=5)

fig,ax = plt.subplots(1,1,figsize=(4,3))
ax = sns.tsplot(np.array(tt).transpose(),
    time=nus,
    condition=['Train', 'Test'],
    interpolate=False)

ax.set_title('5-fold CV Performance for NuSVC')
ax.set_xlabel("\n".join([fr'$\nu$ for $\nu$-SVC']))
ax.set_ylim(.3, 1.01)
ax.legend(loc='lower center');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_285_0.png)

这里我们看到非常大的 ν 基本上对训练和测试都很糟糕。我们无法捕捉到足够的模式来做任何事情——我们偏差过大。在另一端，

这些共同表明，高 C 值会导致过拟合，低 C 值会导致欠拟合。虽然 C 比 ν 更难解释，但它在模型复杂度和我们产生的误差之间进行权衡。更大的 C 意味着我们更关心误差而非复杂度。当 C 非常大时，即使是最小的误差也很重要。因此，我们构建一个复杂度很高的模型来覆盖这些误差。我们将在第 15 章更具体地阐述这种权衡。

## 8.4 逻辑回归

首先，让我们指出房间里的大象。逻辑回归是一种线性分类技术。更糟糕的是，逻辑回归既是一种回归技术，也是一种分类技术。我现在能听到一些同事说，“但是 Mark，它是一种分类技术！”在数学中，所谓的红鲱鱼可能不是红色的，也可能根本不是鱼！撇开这一点不谈，逻辑回归是一种使用回归作为内部组件的分类方法。逻辑回归工作分为两个阶段：(1) 计算与每个目标类别概率密切相关的东西，以及 (2) 用概率最高的类别标记一个例子。第一步是从预测变量到“不完全是概率”的回归。对“不完全是概率”进行阈值处理——或在多个值中取最大值——就给出了一个类别。

我们需要深入一点街头数学来解释发生了什么。一旦我们这样做，你就会看到线性回归和逻辑回归之间非常紧密的关系。连接两者的关键概念叫做对数几率。现在，我们不是在谈论伐木工比赛的结果下注——但我们的故事将从一次赌注开始。对数几率就是我在上一段提到的“不完全是概率”。

### 8.4.1 投注赔率

喜欢赌博的朋友——在地下室打扑克、在赌场、或在赛马场下注——对以赔率思考非常熟悉。我……不是。所以，让我们花几分钟谈谈概率和赔率。这里有一个关于概率和赔率关系的非常简单的例子。假设我们的概率——我们说赢的概率——是 10%。这意味着如果我们玩十次游戏，我们预计赢一次。我们可以换一种方式分解：在十次尝试中，我们预计赢一次，输九次。如果我们创建这两个数字的比率，我们得到 1⁄9 ≈ .1111。这就是赢的赔率。我们也可以把这些赔率写成 1 : 9。请务必非常小心：即使这是赔率并且我们从比率计算而来，这个值并不是赔率比——那是一个不同的概念。

回到赔率：我们如何解释它们？为什么我的赌博朋友喜欢以赔率思考？要回答这个问题，让我们问另一个问题。对于给定的赔率，什么算公平赌注？具体来说，如果赢的赔率是 .1111，参与者需要下注多少钱，才能从长远来看游戏是公平的。为了避免过于抽象，让我们设计一个与 10% 概率——或 1⁄9 赔率——相匹配的游戏。
