
## 5.5（重采样：从少中获取更多）137

我最后再对重复的训练-测试划分和交叉验证做一个评论。使用 k 折交叉验证，我们会对每个示例都只得到一个、且仅一个预测结果。每个示例恰好位于一个测试子集中。整个数据集的预测结果将汇总自在不同数据集合上训练的 k 个模型。使用重复的训练-测试划分，我们可能会完全忽略对某些示例的训练或预测，而对其他示例进行重复预测，如图 5.8 所示。在重复的训练-测试划分中，一切都取决于我们的选择过程的随机性。

![](img/d94e4cd766940d79abed0bc6ba4e4344_165_0.png)

管理重复循环以进行多次训练-测试划分有点烦人。这并不伤筋动骨，但出错的地方很多。如果有人能把这个过程封装成一个独立的单一函数就好了。幸运的是，sklearn 已经做了这件事。如果我们将 ShuffleSplit 数据分割器传入 cross_val_score 的 cv 参数，我们就能得到与上面手工编码完全相同的算法。

```
In [25]:
linreg = linear_model.LinearRegression()
diabetes = datasets.load_diabetes()

# nondefault cv argument
ss = skms.ShuffleSplit(test_size=.25) # default, 10 splits
scores = skms.cross_val_score(linreg,
diabetes.data, diabetes.target,
cv=ss,
scoring='neg_mean_squared_error')

scores = pd.Series(np.sqrt(-scores))
df = pd.DataFrame({'RMSE': scores})
df.index.name = 'Repeat'
```

```
display(df.describe().T)

ax = sns.swarmplot(y='RMSE', data=df)
ax.set_xlabel('Over Repeated\nTrain-Test Splits');
```

|  | 计数 | 平均值 | 标准差 | 最小值 | 25% | 50% | 75% | 最大值 |
|---|---|---|---|---|---|---|---|---|
| RMSE | 10.000 | 55.439 | 3.587 | 50.190 | 52.966 | 55.397 | 58.391 | 60.543 |

![](img/d94e4cd766940d79abed0bc6ba4e4344_166_0.png)

与我们手动版本之间的细微差异是由于随机选择训练-测试划分造成的。

现在，我想谈谈随机性影响我们这些勇敢的机器学习学习者的另一种方式。这是计算机在我们要求它做随机事情时所使用的那种随机性。这就是 ShuffleSplit 背后发生的事情。别担心，我马上就会解释 random_state。

```
In [26]:

ss = skms.ShuffleSplit(test_size=.25, random_state=42)

train, test = 0, 1
next(ss.split(diabetes.data))[train][:10]
```

Out[26]:

```
array([ 16, 408, 432, 316,  3,  18, 355,  60, 398, 124])
```

顺便说一下，我使用 next 是因为 ShuffleSplit 依赖 Python 生成器来一个接一个地生成划分。说 next 会给我下一个数据划分。获取下一个数据划分后，我挑选出训练数据 [train]，然后是前十个示例 [:10]。够用了。让我们再试一次。

```
In [27]:

ss = skms.ShuffleSplit(test_size=.25, random_state=42)
next(ss.split(diabetes.data))[train][:10]
```

```
Out[27]:

array([ 16, 408, 432, 316,   3,  18, 355,  60, 398, 124])
```

这可不太好。有人叫——有人！我们需要帮助。结果是一样的。这不是 supposed to be 随机的吗？答案是 是的……又不是。计算机上的随机性通常是伪随机的。这是一长串数字，组合在一起时足够随机，可以伪装成随机。我们从该列表中的某一点开始，然后开始取值。对外部观察者来说，它们看起来相当随机。但如果你知道机制，你实际上可以提前知道接下来会有什么值。因此，(1) 我们生成的值看起来大多是随机的，但 (2) 用于生成它们的流程实际上是确定性的。这种确定性有一个很好的副作用，我们可以利用它。如果我们为伪随机数序列指定一个起点，我们就可以获得一个可重复的、并非那么随机的值列表。当我们使用 random_state 时，我们为 ShuffleSplit 在请求随机性时设置一个起点。我们最终会得到相同的输出。可重复的训练-测试划分对于创建可重复的测试用例、与学生分享示例以及在追踪错误时消除一些自由度非常有用。

顺便说一下，这里还有另一个类似问题出现的地方。让我们做两次 KFold 的独立运行。

```
In [28]:

train, test = 0, 1
kf = skms.KFold(5)
next(kf.split(diabetes.data))[train][:10]
```

```
Out[28]:

array([89, 90, 91, 92, 93, 94, 95, 96, 97, 98])
```

```
In [29]:

kf = skms.KFold(5)
next(kf.split(diabetes.data))[train][:10]
```

Out[29]:

```
array([89, 90, 91, 92, 93, 94, 95, 96, 97, 98])
```

在我们希望有随机性的地方缺乏随机性，开始变得有点老套了。这里的问题是 KFold 的默认参数：

```
skms.KFold(n_splits=3, shuffle=False, random_state=None)
```

shuffle=False，默认值，表示我们在将示例分配到不同折之前不会打乱它们。如果我们希望它们被打乱，我们需要明确说明。为了让示例更易读，我们将切换回简单的宠物目标。

In [30]:

```
pet = np.array(['cat', 'dog', 'cat',
    'dog', 'dog', 'dog'])

kf = skms.KFold(3, shuffle=True)

train, test = 0, 1
split_1_group_1 = next(kf.split(pet))[train]
split_2_group_1 = next(kf.split(pet))[train]

print(split_1_group_1,
    split_2_group_1)
```

[0 1 4 5] [0 1 3 5]

如果我们设置 random_state，它会被分割器共享：

In [31]:

```
kf = skms.KFold(3, shuffle=True, random_state=42)

split_1_group_1 = next(kf.split(pet))[train]
split_2_group_1 = next(kf.split(pet))[train]
print(split_1_group_1,
    split_2_group_1)
```

[2 3 4 5] [2 3 4 5]

### 5.5.5 留一交叉验证

我上面提到过，我们可以采取一种极端的方法进行交叉验证，使用与示例数量一样多的交叉验证子集。因此，对于 20 个示例，我们可能进行 20 次训练-测试划分，进行 20 次训练拟合，进行 20 次测试轮次，并得到 20 次
结果评估。这个版本的 CV 称为 *留一交叉验证*（LOOCV），它很有趣，因为我们生成的 *所有* 模型都将 *几乎全部* 共享它们的训练数据。对于 20 个示例，任意两次训练运行之间共享 90% 的数据。你可以参考图 5.7 来直观地看到它。

```
In [32]:
linreg = linear_model.LinearRegression()
diabetes = datasets.load_diabetes()

loo = skms.LeaveOneOut()
scores = skms.cross_val_score(linreg,
    diabetes.data, diabetes.target,
    cv=loo,
    scoring='neg_mean_squared_error')

scores = pd.Series(np.sqrt(-scores))
df = pd.DataFrame({'RMSE':scores})
df.index.name = 'Repeat'

display(df.describe().T)

ax = sns.swarmplot(y='RMSE', data=df)
ax.set_xlabel('Over LOO\nTrain-Test Splits');
```

|  | 计数 | 平均值 | 标准差 | 最小值 | 25% | 50% | 75% | 最大值 |
|---|---|---|---|---|---|---|---|---|
| **RMSE** | 442.000 | 44.356 | 32.197 | 0.208 | 18.482 | 39.547 | 63.973 | 158.236 |

![](img/d94e4cd766940d79abed0bc6ba4e4344_169_0.png)

有趣的是，有三个明显的点具有较高的 RMSE，并且大约有二十个点形成了一个明显的峰值，高于误差主体之上（RMSE > 100）。这意味着大约有二十个点对使用几乎所有数据构建的模型进行预测具有抗性。值得调查这些困难示例中是否存在任何共同因素。

LOOCV 是一种确定性评估方法。选择中没有随机性，因为每次运行 LOOCV 时一切都以相同的方式使用。这种确定性对于比较和测试学习算法的正确性很有用。然而，运行 LOOCV 可能很昂贵，因为我们需要为每个被留出的示例训练一次模型。一些模型具有数学技巧，可以大幅降低重新训练的开销。在评估方面，将大量训练数据（每个 CV 分区中除一个示例外的所有示例）纳入的净效应是，LOOCV 给出了真实错误率的相对无偏估计。因为单示例预测彼此非常相关——大部分训练数据是共享的并输入到相同的学习算法中——因此对新示例的性能误差估计可能差异很大。总体而言，一般建议优先选择 5 折或 10 折 CV 而非 LOOCV。

## 5.6 拆解：把误差分解为偏差和方差

让我们想象一下，我们在一个赛道上，开始进行一些基本测量。我们看到汽车在赛道上飞驰，并测量汽车的位置和速度。假设我们记录了总距离 d = 2 的两圈用时。我们还将记录平均速度 s。如果我有一张这些值的表格，而我不记得任何高中物理，我就可以开始尝试将不同的列联系起来。例如，从两个用时和总用时，我可能会得出 t₁ + t₂ = t_total 的事实。再一次想象，我们忘记了在高中物理或甚至四年级数学中学到的所有东西。

| 驾驶员 | t₁ | t₂ | t_total | s | d |
|---|---|---|---|---|---|
| Mario | 35 | 75 | 110 | .018 | 2 |
| Luigi | 20 | 40 | 60 | .033 | 2 |
| Yoshi | 40 | 50 | 90 | .022 | 2 |

让我们考虑一下尝试关联列的一些变化。首先，测量是完美的，还是我们在记录时存在错误？其次，我允许使用什么关系——什么数学运算——来关联列？为了保持可控，我们将把自己限制在两个简单的运算——加法和乘法——上，看看会发生什么。最后，我们将考虑不同列集合之间作为输入和输出的关系。

在表 5.2 中，我列出了不同的可能性以及它们能多完美地描述数据以及出了什么问题的一些评估。
