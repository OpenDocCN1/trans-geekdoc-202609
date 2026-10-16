
下面来看看真实值与我们的含噪数据点的对比：

```
In [4]:

fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(x_1, y_true, 'r', label='true')
ax.plot(x_1, y_msr , 'b', label='noisy')
ax.legend();
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_326_0.png)

现在，我要走一条捷径。我不打算经历从数据中拟合和寻找良好参数的过程。我们不会重新运行线性回归来提取`ws`（或`{m,b}`）。但想象一下，我确实这么做了，并得到了完美的参数值——就是上面我们用来生成数据的那些。下面就是我们的误差平方和的样子：

```
In [5]:

def sq_diff(a,b):
    return (a-b)**2
```

```
In [6]:

predictions = rdot(w,x)
np.sum(sq_diff(predictions, y_msr))
```

Out[6]:

5.0

提醒一下，这来自于这个方程：

$loss = \sum_{x,y \in D} (wx - y)^2$

我们需要把我们希望保持权重较小的想法纳入考量。反过来，这个约束是简化（正则化）模型的替代。假设我们不只做预测，而是让模型关联一个总代价。如下：

In [7]:

```
predictions = rdot(w,x)

loss = np.sum(sq_diff(predictions, y_msr))

complexity_1 = np.sum(np.abs(weights))
complexity_2 = np.sum(weights**2) # == np.dot(weights, weights)

cost_1 = loss + complexity_1
cost_2 = loss + complexity_2

print("Sum(abs) complexity:", cost_1)
print("Sum(sqr) complexity:", cost_2)
```

Sum(abs) complexity: 11.3
Sum(sqr) complexity: 22.15

记住，我们这里耍了两个小花招。第一，我们实际上并没有从数据反推权重。相反，我们只是用同一组权重来生成数据，并做出不完全是预测的预测。第二个花招是，我们在两种情况下都使用了相同的权重，所以两种代价中包含了相同的损失。我们是不能比较这两者的：通常，我们只用其中一个来计算代价，从而在一个损失和复杂度的计算方法下找到一组好的权重。

在展示学习中的一个基本关系之前，我还想介绍最后一块内容。一旦我们定义了一个代价，并说我们希望代价很低时，我们实际上就做了另一个权衡。我可以通过减少误差（从而降低损失）或降低复杂度来降低代价。我愿意同等程度地对待这两者，还是认为其中一项更重要？把复杂度减半，值得用两倍的误差来换吗？我们真正的目标是尽量少在将来犯错误。这需要通过现在（在训练数据上）少犯错误，并保持模型低复杂度来实现。

为此，加入一种在减少误差和降低复杂度之间进行权衡的方式是很有价值的。我们这样做：

In [8]:

```
predictions = rdot(w,x)
errors = np.sum(sq_diff(predictions, y_msr))
complexity_1 = np.sum(np.abs(weights))

C = .5
```

```
cost = errors + C * complexity_1
cost
```

Out[8]:

```
8.15
```

这里，我的意思是，就代价而言，复杂度每增加1点，只值损失增加½点。也就是说，损失的代价是复杂度的两倍，或者说损失的重要性是复杂度的两倍。如果我们用C来表示这个权衡，就得到下面这些数学味很浓的方程：

Cost₁ = Σ_{x,y∈D} (wx − y)² + C Σ_j |w_j|
Cost₂ = Σ_{x,y∈D} (wx − y)² + C Σ_j w_j²

用Cost₁找最佳直线称为L₁正则化回归，也叫lasso。用Cost₂找最佳直线称为L₂正则化回归，也叫岭回归（ridge regression）。

## 9.1.1 执行正则化回归

执行正则化线性回归并不比老式（GOF）线性回归更困难。

对于Lasso和Ridge，我们的C（复杂度惩罚的总权重）的默认值都是1.0。在sklearn中，C值由参数alpha设置。所以当C = 2时，我们会调用`linear_model.Lasso(alpha=2.0)`。在正则化的讨论中，你会看到λ、α和C；它们扮演着类似的角色，但你确实需要注意作者在含义上可能存在的细微差别。就我们的目的而言，基本上可以把它们视为一回事。

In [9]:

```
models = [linear_model.Lasso(),           # L1 regularized; C=1.0
          linear_model.Ridge()]            # L2 regularized; C=1.0

for model in models:
    model.fit(diabetes_train_ftrs, diabetes_train_tgt)
    train_preds = model.predict(diabetes_train_ftrs)
    test_preds  = model.predict(diabetes_test_ftrs)
    print(get_model_name(model),
          "\nTrain MSE:", metrics.mean_squared_error(diabetes_train_tgt,
                                                     train_preds),
          "\n Test MSE:", metrics.mean_squared_error(diabetes_test_tgt,
                                                     test_preds))
```

```
Lasso
Train MSE: 3947.899897977698
Test MSE: 3433.1524588051197
Ridge
Train MSE: 3461.739515097773
Test MSE: 3105.468750907886
```

用起来太简单了，我们可能会继续往下走，而不去想什么时候以及为什么使用它们。由于线性回归的默认操作是不带正则化，我们可以轻松切换到正则化版本，看看它是否能改善情况。当我们对某些数据进行训练并看到过拟合失败时，可以试试这个办法。然后，我们可以尝试不同数量的正则化——不同的C值——看看在交叉验证运行中哪种效果最好。我们将在第11.2节讨论帮助我们选择C的工具。

对于含噪很大的数据，我们可能会倾向于构建一个可能过拟合的复杂模型。为了降低复杂度，我们必须在模型中容忍相当多的误差。也就是说，我们为复杂度付更少的代价，而为误差多付一点代价。对于能捕捉线性模式的无噪声数据，我们几乎不需要复杂度控制，使用GOF线性回归就应该能得到不错的结果。

## 9.2 支持向量回归

我们已经介绍了学习中一个基本权衡的思想：我们的代价既来自学习器的错误，也来自其复杂度。支持向量回归（SVR）以一种“同中有异”的方式使用了这一点。我们通过向损失中加入复杂度因子来正则化GOF线性回归。我们可以沿着这条路继续走，对线性回归做进一步调整。我们也可以修改它的损失。记住：代价 = 损失 + 复杂度。线性回归的标准损失是误差平方和，称为平方误差损失。正如我们刚才看到的，这种形式也被称为L2——这里就是L2损失。所以你可能会想：“啊哈！那我们用L1，也就是绝对值之和吧。”你答对了一半。我们要用L1，但会做一些调整。我们的调整是使用L1，但忽略小误差。

### 9.2.1 铰链损失（Hinge Loss）

在8.3节首次接触支持向量分类器（SVC）时，我们没有讨论让SVC实现其神奇功能的底层魔法。事实证明，对于SVC和SVR来说，这种魔法非常相似：两者使用的损失都与线性回归（无论哪种）略有不同。本质上，我们想度量出错时的后果，并且想忽略小误差。把这两点放在一起，就产生了铰链损失（hinge loss）的想法。首先，下面的图显示误差的绝对值的样子：

In [10]:

```
# here, we don't ignore small errors
error = np.linspace(-4, 4, 100)
```

```
loss = np.abs(error)

fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(error, loss)

ax.set_xlabel('Raw Error')
ax.set_ylabel('Abs Loss');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_330_0.png)

我们怎样才能忽略到某个阈值为止的误差呢？例如，让我们编写代码，忽略绝对值小于1.0的误差：

In [11]:

```
an_error = .75
abs_error = abs(an_error)
if abs_error < 1.0:
    the_loss = 0.0
else:
    the_loss = abs_error
print(the_loss)
```

0.0

现在我们要玩点花哨的了。请仔细看。我们可以用一些巧妙的数学来重写这段代码。我们的策略如下：

- 1. 从绝对误差中减去阈值。
- 2. 如果结果大于零，就保留它。否则，用零代替。

