

`r2_train = list()r2_test = list() for i in range(1, 129): X_train_extra = np.column_stack((X_train, np.random.rand(len(X_train), i))) X_test_extra = np.column_stack((X_test, np.random.rand(len(X_test), i))) lr = LinearRegression() lr.fit(X_train_extra, y_train) r2_train.append(lr.score(X_train_extra, y_train)) r2_test.append(lr.score(X_test_extra, y_test))`

在此示例中，代码在波士顿数据集上重新训练线性回归模型，并在训练集和测试集中都添加了一些新的随机特征。该示例记录了随着随机特征数量的增加，两组数据的 R2 值。如果你绘制结果图，你会发现样本内预测能力似乎有所提高，但实际上只是一种幻觉。通过检查测试集，你会发现模型性能实际上已经下降，如 [图 13-1](#c13.xhtml#c13-fig-0001) 所示。

```
import matplotlib.pyplot as plt
fig, ax = plt.subplots(dpi=120)
plt.plot(r2_train, label='train')
plt.plot(r2_test, label='test')
plt.xlabel("additional random features")
plt.ylabel("R2")
plt.show()
```

### 通过贪婪选择解决过拟合问题

不仅不相关的特征（如随机噪声），冗余特征也可能影响模型的预测性能以及你理解线性模型的能力。前面几节承认，线性模型中包含过多信息可能会成为问题：

* 不相关的特征可能会恶化模型的预测能力。

* 多项式扩展可能会产生良好的训练拟合，但测试效果不佳，这是过拟合的信号，因为扩展产生了大量冗余特征。

* 逻辑回归显示，由于 CRIM 与其他一些特征相关，因此其系数具有反直觉性。

![FIGURE 13-1: Adding random features increases in-sample performances but degrades the test results.](images/9781119724018-fg1301.png)

[FIGURE 13-1:](#c13.xhtml#rc13-fig-0001) Adding random features increases in-sample performances but degrades the test results.

作为解决这些问题的方案，可以通过仅选择最具预测能力的特征集来简化训练集。在这样做时，你可以使用交叉验证（可保证你的选择是最优的）以及 Scikit-learn 提供的一系列工具来处理问题。第一个是递归选择，即逐一测试从训练集中删除效果最差的特征。作为一种启发式方法，递归选择使用回归系数的绝对值来逐步消除影响最小的特征。当只剩下少数特征时，算法会回顾其消除过程，并找到能让模型在交叉验证中表现更好的特征集。在此示例中，你从之前的多项式扩展开始，确定是否可以将扩展减少到一个更小、更具预测能力的特征集：

```
from sklearn.feature_selection import RFECV
from sklearn.preprocessing import PolynomialFeatures
pf = PolynomialFeatures(degree=2)
poly_X_train = pf.fit_transform(X_train)
poly_X_test = pf.transform(X_test)
selector = RFECV(estimator=LinearRegression(), step=1, cv=3, scoring='r2')
selector.fit(poly_X_train, y_train)
n_features = selector.n_features_
print(f"Features reduced to {n_features} from " "{poly_X_train.shape[1]}")
```

选择完成后，你可以在训练集和测试集上对其进行测试。注意预测性能提高了多少（现在测试 R² 达到 0.826，而 [图 13-1](#c13.xhtml#c13-fig-0001) 中显示的值约为 0.6）：

```
r2_train = selector.score(poly_X_train, y_train)
print(f"R2 train: {r2_train:0.3}")
r2_test = selector.score(poly_X_test, y_test)
print(f"R2 test: {r2_test:0.3}")
```

### 通过正则化解决过拟合问题

当你拥有许多特征，并希望减少由于预测器之间多重共线性导致的估计方差时，正则化是一种有效、快速且易于实现的解决方案。正则化通过向成本函数添加惩罚项来工作。惩罚项是系数的总和。如果系数被平方（使得正负值无法相互抵消），则为 `L2 regularization`（也称为 `Ridge`）。当你使用系数的绝对值时，则为 `L1 regularization`（也称为 `Lasso`）。

然而，正则化并不总是完美有效。L2 正则化保留模型中的所有特征，并平衡每个特征的贡献。在 L2 解中，如果两个特征高度相关，则每个特征对解决方案的某一部分均等贡献，而如果没有正则化，它们的共享贡献将被不均匀地分配。

或者，L1 通过将高度相关特征的系数设为零，将其从模型中移除，从而在特征之间进行真正的选择。事实上，将系数设为零就像将特征从模型中排除一样。当多重共线性很高时，决定将哪个预测器设为零变得有些随机，你可以得到各种解决方案，其特征被排除的方式不同。这种解决方案的不稳定性可能会带来麻烦，因此当你也希望找出哪些特征对模型很重要时，L1 解更受青睐。

![Tip](images/tip.png)学者们通过基于 L1 正则化创建各种解决方案，然后查看系数在不同解决方案中的表现，找到了一个修复方法。在这种情况下，算法只选择稳定的系数（那些很少被设为零的系数）。你可以在 Scikit-learn 兼容项目网站上阅读更多关于此技术及其细节的内容，网址为 [`https://github.com/scikit-learn-contrib/stability-selection`](https://github.com/scikit-learn-contrib/stability-selection)，以及在博客 [`https://thuijskens.github.io/2018/07/25/stability-selection/`](https://thuijskens.github.io/2018/07/25/stability-selection/) 上阅读。以下示例修改了多项式扩展示例，使用 L2 正则化（岭回归）并减少扩展过程创建的冗余系数的影响。由于正则化程度由 `RidgeCV` alpha 参数控制（alpha 越高，正则化越强），该示例使用内部交叉验证过程验证哪个 alpha 对你的模型更好。你只需提供一组要测试的 alpha 值：

```
from sklearn.linear_model import RidgeCV
l2_lm = RidgeCV(alphas=[0.001, 0.01, 0.1, 1, 10, 100], normalize=True, cv=5, scoring='r2')
l2_lm.fit(X_train, y_train)
best_alpha = l2_lm.alpha_
r2_test = l2_lm.score(X_test, y_test)
print(f"best alpha is: {best_alpha}")
print(f"test R2: {r2_test:0.3}")
```

以下是此代码的输出：

```
best alpha is: 0.1
test R2: 0.753
```

在完成训练数据的拟合并测试预测性能后，你可以查看生成的系数如何变化：

```
for var, coef in zip(X_train.columns, l2_lm.coef_):
    print(f"{var:7} : {coef:+0.3}")
```

由于 L2 倾向于在存在相关特征时降低并重新平衡线性回归模型的系数，因此生成的系数现在更具可解释性，你不应该再发现之前出现的反直觉符号或值：

```
CRIM : -0.438
ZN : +0.546
INDUS : -0.247
CHAS : +0.886
NOX : -1.32
RM : +2.79
AGE : +0.0356
DIS : -2.09
RAD : +1.02
TAX : -0.718
PTRATIO : -1.88
B : +0.943
LSTAT : -3.49
```

下一个示例使用 L1 正则化，当系数冗余时，L1 倾向于将系数带为零（L2 只是将其减小）。在这种情况下，结果与 L2 相差不大。这次，示例使用 Scikit-learn 的 `LassoCV` 类，它类似于 `RidgeCV`，但应用 L1 正则化而不是 L2：

