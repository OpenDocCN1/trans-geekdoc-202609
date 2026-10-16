
![](img/d94e4cd766940d79abed0bc6ba4e4344_461_0.png)

当我们重新构建问题——使用我们在第 10.6.1 节攻击 xor 问题时使用的相同技巧——我们使其可通过线性方法求解。成功。圆中的暗三角形最终位于 SquareSpace 图形的左下角三角形内部。现在，有几个问题。我们所做的工作需要人工干预，而且之所以容易是因为我们知道平方是正确的方向。如果你查看原始目标 tgt = (xs**2 + ys**2 > 1).flatten()，你会看到平方在其中占据了重要地位。如果我们需要对特征进行除法——取比值——那么对值进行平方就不会有帮助了！

因此，我们希望有一种自动化的方式来处理这些问题，并且我们希望自动化方法能为我们尝试构造的特征。自动化这一过程最巧妙且多用途的方法之一是核方法。核方法不能做我们手工能做的所有事情，但在许多场景下它们已经足够。下一步，我们将以一种有些笨拙、手动的方式使用核。但核可以以不需要人工干预的更强大的方式使用。我们——缓慢地，或许是谨慎地——逐步构建起一个自动化系统，用于尝试许多可能的构造特征并使用最好的那些。

## 13.2.2 手动核方法

我还没有定义核。我可以定义，但现在对你来说还没有意义。相反，我将通过演示核的作用以及它与我们构造良好特征的问题的关系来开始。我们将手动应用一个核。警告！通常我们不会这样做。我只是想让你了解核方法内部的情况。) 而不是执行手动数学运算（x², y²），我们将从原始数据过渡到数据的核。在这种情况下，它是一个非常特定的核，捕捉了我们刚刚手工完成的对输入特征进行平方的相同思想。

```
In [44]:

k_data = metrics.pairwise.polynomial_kernel(data, data,
                                            degree=2) # squares
print('first example: ', data[0])

print('# features in original form:', data[0].shape)
print('# features with kernel form:', k_data[0].shape)

print('# examples in both:', len(data), len(k_data))
```

第一个示例： [-2. -2.]
# 原始形式的特征数： (2,)
# 核形式的特征数： (400,)
# 两者的示例数： 400 400

这可能有点令人失望，也可能有点令人困惑。当我们将核应用于 400 个示例时，我们从拥有 2 个特征变成了拥有 400 个特征。为什么？因为核将数据重新描述为示例与每个其他示例之间的关系。对于第一个示例的 400 个特征，描述的是第一个示例与每个其他示例的关系。这使得情况有点难以看清。然而，我们可以让核特征说话。我们将通过将核化数据馈送给预测模型，然后将这些预测绘制回原始数据上来做到这一点。基本上，我们是通过正式名称查找某人的信息——Mark Fenner 住在宾夕法尼亚州——然后将结果与其昵称关联起来——Marco 住在宾夕法尼亚州。

另一个快速说明：如果让你想起了特征对之间的协方差，你也不算太远。然而，核是关于示例之间的关系。协方差是关于特征之间的关系。一个是在列之间；另一个是在行之间。

```
In [45]:

fig, ax = plt.subplots(figsize=(4,3))

# learn from k_data instead of original data
preds = (linear_model.LogisticRegression()
        .fit(k_data, tgt)
        .predict(k_data))

ax.scatter(xs, ys, c=np.where(preds, 'r', 'b'), marker='.')
ax.set_aspect('equal')
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_463_0.png)

这里确实发生了某些事情。在此之前，我们无法成功地将 LogReg 模型应用于圆数据：它在所有地方都产生平坦的蓝色预测。现在，我们似乎得到了完美的预测。我们稍后会更仔细地查看这是如何发生的。但现在，让我们更干净地处理手动核的应用。

手动应用核有点笨拙。我们可以制作一个 sklearn Transformer——参见第 10.6.3 节了解我们第一次接触它们——让我们在学习管道中连接手动核：

In [46]:

```
from sklearn.base import TransformerMixin

class PolyKernel(TransformerMixin):
    def __init__(self, degree):
        self.degree = degree

    def transform(self, ftrs):
        pk = metrics.pairwise.pairwise_kernels
        return pk(ftrs, self.ftrs, metric='poly', degree=self.degree)

    def fit(self, ftrs, tgt=None):
        self.ftrs = ftrs
        return self
```

基本上，我们有一个管道步骤，在将数据发送到下一步之前先将其通过核传递。我们可以将我们手动的 2 次多项式与来自大城市的更花哨的表亲进行比较。我不会详细介绍 Nystroem 核，但我想让你知道它存在有两个原因：

- 1. Nystroem 核——在 sklearn 中的实现——与管道配合良好。我们不必自己将其包装在 Transformer 中。基本上，我们可以为了编程便利而使用它。
- 2. 实际上，Nystroem 核除了使我们的编程稍微容易一些之外，还有一个非常重要的作用。如果我们有一个更大的问题，包含许多示例，那么构造一个将每个示例与每个其他示例进行比较的完整核可能会因为非常大的内存占用而导致问题。Nystroem 通过减少其考虑的示例数量来构造近似核。有效地，它只保留最重要的比较示例。

```
In [47]:

from sklearn import kernel_approximation

kn = kernel_approximation.Nystroem(kernel='polynomial',
                                   degree=2, n_components=6)

LMLR = linear_model.LogisticRegression()
k_logreg1 = pipeline.make_pipeline(kn, LMLR)
k_logreg2 = pipeline.make_pipeline(PolyKernel(2), LMLR)

shootout_fancy = [(k_logreg1, 'Nystroem'),
                  (k_logreg2, 'PolyKernel')]

fig, axes = plt.subplots(1,2,figsize=(6,3), sharey=True)
for (mod, kernel_name), ax in zip(shootout_fancy, axes):
    plot_boundary(ax, data, tgt, mod, [0,1])
    ax.set_title(get_model_name(mod)+" ({})".format(kernel_name))
    ax.set_aspect('equal')
plt.tight_layout()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_464_0.png)

在这里，我们制作了核化逻辑回归的模拟。我们拼凑了一个核方法形式的逻辑回归。我为依赖如此脆弱的代码来做核化逻辑回归而道歉，但我这样做有两个原因。首先，sklearn 的工具箱中没有完整的核化逻辑回归。其次，它给了我一个机会来展示我们如何将 PlainVanillaLearningMethod(Data) 写成 PlainVanillaLearner(KernelOf(Data)) 并实现类似核方法的效果。实际上，我们应该小心地称这种模拟为核方法。它有几个限制，这些限制不影响完整的核方法。我们一会儿会回到这些问题。

我们与原始的全蓝色逻辑回归模型相比取得了实质性进展。但我们仍然在手工做很多事情。让我们去掉训练轮子并完全自动化该过程。

### 13.2.2.1 从手动到自动化的核方法

我们对完全自动化的核方法的首次尝试将使用核化支持向量分类器，即支持向量机（SVM）。我们将 SVM 与我们手工构建的多项式核进行比较。

```
In [48]:

k_logreg = pipeline.make_pipeline(PolyKernel(2),
                                 linear_model.LogisticRegression())

shootout_fancy = [svm.SVC(kernel='poly', degree=2),
                  k_logreg]

fig, axes = plt.subplots(1,2,figsize=(6,3), sharey=True)
for mod, ax in zip(shootout_fancy, axes):
    plot_boundary(ax, data, tgt, mod, [0,1])
    ax.set_title(get_model_name(mod))
plt.tight_layout()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_465_0.png)
