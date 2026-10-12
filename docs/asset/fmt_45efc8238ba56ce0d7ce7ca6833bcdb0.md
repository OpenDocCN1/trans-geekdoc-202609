
假设函数模型 $\hat{f}(x) = b$ 的偏差与方差分别为：`-14.564125266958722` 和 `0.7240080347500965`；假设函数模型 $\hat{f}(x) = wx + b$ 的偏差与方差分别为：`-11.944324952176219` 和 `10.868072850656494`。

简单模型往往不够复杂，无法完全逼近真实函数 $f(x)$，容易欠拟合，其偏差大于复杂模型。虽然复杂模型偏差较小，但因函数变化复杂，其预测值的变化也往往剧烈或发散，即方差较大。

# 偏差与方差

模型预测的偏差和方差可以通过如图 3-33 所示的“靶心图”来说明。靶心是目标的真实值，某个射手则是一个假设函数。训练后，意味着他已经训练好了自己的模型。射击靶心相当于对该样本进行一次预测。每训练一次自己的模型，就射击（预测）一次，最终该假设函数（此人）在不同时间训练出的模型会产生相应的预测值。这些预测值偏离真实值的程度就是他的偏差。左上角的图显示他的偏差非常大，设计技巧仍显不足，模型处于欠拟合状态，即模型无法很好地表达自变量与目标值之间的关系。右侧两列图表明，同一自变量的预测值非常分散，即预测方差大，说明这些不同模型预测的值偏差很大，仿佛此人的射击水平非常不稳定。左侧两列图的预测值相对集中，即预测方差小，说明不同模型的预测结果几乎相同。即此人的射击水平相对稳定。左下角偏差小，方差也小，说明模型拟合效果好（射击精度高）且非常稳定，而右下角偏差相对对称，使得偏差的期望相对较小，响应的预测值始终围绕真实值，看起来拟合得比较准确，但由于方差大，提示可能存在过拟合问题（射击能力不稳定）。

**图 3-33** 偏差与方差

通过训练集和验证集学习曲线的对比，也可以直观地观察到偏差和方差。如果训练集和验证集的误差比较接近，说明对两个不同数据集的预测结果接近，意味着方差比较小（发散程度低）；反之，则说明方差比较大。误差的数值代表了它们偏差的大小。

如图 3-34 所示，当验证误差远大于训练误差（`Jcv >> Jtrain`）且训练误差较小时，说明模型对训练集拟合得很好，但对验证集拟合效果差，表明存在过拟合现象。左侧图中，当验证误差与训练误差相似且两者都较大时，表明可能存在欠拟合。

**图 3-34** 基于训练和验证损失曲线判断欠拟合、过拟合以及偏差和方差

## 3.3 正则化

过拟合（高方差）是由模型过于复杂、自由度过高引起的。解决过拟合的一种方法是增加训练样本数量，但有时很难获得足够的训练样本，或者获取样本耗时费力。

解决过拟合的另一种常用方法是降低模型复杂度。降低模型复杂度的一种途径是选择一个更简单的假设函数来代替复杂的假设函数，例如在前面的例子中使用 3 次多项式代替 9 次多项式作为假设函数。如果不想替换假设函数，可以通过某些技术来限制假设函数的复杂度。这种降低函数复杂度的方法称为**正则化**（Regularization）。

前面提到的**早停法**就是一种正则化方法。通过学习曲线观察模型训练过程中梯度下降法迭代时训练损失和验证损失的变化，即根据训练和验证损失曲线选择合适的迭代次数。使得模型函数不会过于复杂。对于复杂函数，模型参数所有可能取值所表示的假设函数集合可能非常大，但模型训练开始时，参数会被初始化为较小的值（如 0），这些较小模型参数对应的函数集合只是所有可能函数的一小部分，即取值范围较小的模型限制了模型函数的表达能力，降低了模型的复杂度。

给函数模型施加正则化约束的另一种常用方法是在损失函数中添加惩罚项。例如，对于线性回归问题，模型的假设函数 `f(x) = x * w = w[0] + x[1] * w[1] + ... + x[n] * w[n]`，若有 m 个样本 `(x^(i), y^(i))`，描述拟合误差的均方误差损失函数为：

$$L(x; w) = \sum_{i=1}^{m} \parallel x^{(i)}w - y^{(i)} \parallel^{2}$$

### 添加正则项后的损失函数变为

$$L(x; w) = \frac{1}{2m}\sum_{i=1}^{m} \parallel x^{(i)}w - y^{(i)} \parallel^{2} + \lambda \parallel w^{2} \parallel$$

其中：

$$\parallel w^{2} \parallel = w[0]^{2} + w[1]^{2} + \dots + w[n]^{2}$$

该惩罚项（模型参数范数的平方）可以防止模型参数取较大值，因为较大的 `w[i]` 值会导致损失函数值变大，而优化的目标是使损失函数值尽可能小。新损失函数中的 `λ` 是一个需要根据实际问题调整的超参数，它控制拟合误差项与惩罚项之间的重要性。较大的 `λ` 意味着惩罚项占比大，惩罚项效果越强；较小的 `λ` 意味着惩罚项占比小，惩罚项效果越弱。

新损失函数的梯度变为：

$$\nabla L(w) = \frac{1}{m}\sum_{i=1}^{m}(x^{(i)}w - y^{(i)})x^{(i)} + 2\lambda w$$

因此，在使用梯度下降法计算偏导数时，计算偏导数时只需加上后一项的梯度即可。以下是带惩罚项的梯度下降法：

```python
def gradient_descent_reg(X, y, reg, alpha, num_iters, gamma=0.8, epsilon=1e-8):
    w_history = []            # 记录迭代过程中的参数
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X)) # 添加一列特征 1
    num_features = X.shape[1]
    v = np.zeros_like(num_features)
    w = np.zeros(num_features)
    for n in range(num_iters):
        predictions = X @ w            # 求假设函数的预测值，即 f(x)
        errors = predictions - y       # 预测值与真实值的误差
        gradient = X.transpose() @ errors / len(y)     # 计算梯度
        gradient += 2 * reg * w
        if np.max(np.abs(gradient)) < epsilon:
            print("gradient is small enough!")
            print("iterated num is :", n)
            break
        # w -= alpha * gradient # 更新模型参数
        v = gamma * v + alpha * gradient
        w = w - v
        
        w_history.append(w)
    return w_history # 返回优化后的参数和代价历史
```

```python
def loss_reg(w, X, y, reg=0.):
    errors = X @ w[1:] + w[0] - y
    reg_error = reg * np.sum(np.square(w))
    return (errors**2).mean() / 2 + reg_error

def compute_loss_history_reg(X, y, w_history, reg=0.):
    loss_history = []
    for w in w_history:
        loss_history.append(loss_reg(w, X, y, reg))
    return loss_history
```

```python
reg = 0.2
history = gradient_descent_reg(x_train_n, y_train, reg, alpha, iterations)
print("w:", history[-1])
loss_history = compute_loss_history_reg(x_train_n, y_train, history, reg)
plot_history_predict(x_train_n, y_train, history[-1], loss_history)
```

```text
gradient is small enough!
    iterated num is : 184
    w: [8.0125638 5.79344199 3.33539832 3.53746298 2.03218329 2.16210927
     1.23141113 1.33653994 0.72424795]
```

![](img/file69.png)

**图 3-35** 正则化后的训练损失曲线和拟合曲线

修改绘制学习曲线的函数 `learning_curves()`。

```python
def learning_curves(X_train, y_train, X_val, y_val, reg, alpha=0.3, iterations=1000):
    train_err = np.zeros(len(y_train))
    val_err = np.zeros(len(y_train))
    for i in range(1, len(y_train)):
        w_history = gradient_descent_reg(X_train[0:i + 1, :], y_train[0:i + 1], reg, alpha, iterations)
        w = w_history[-1]
        train_err[i] = loss_reg(w, X_train[0:i + 1, :], y_train[0:i + 1], reg)
        val_err[i] = loss_reg(w, X_val, y_val, reg)
    plt.plot(range(2, len(y_train) + 1), train_err[1:], c="r", linewidth=2)
    plt.plot(range(2, len(y_train) + 1), val_err[1:], c="b", linewidth=2)
    plt.xlabel("number of training examples", fontsize=14)
    plt.ylabel("error", fontsize=14)
    plt.legend(["training", "validation"], loc="best")
    plt.axis([2, len(y_train), 0, 100])
    plt.grid()
```

绘制学习曲线。

```python
x_val_n = np.hstack(tuple(x_val**(i+1) for i in range(n)))  # (x_train_1, x_train**2, x_train**3, x_train**4)
x_val_n = (x_val_n - train_means) / train_stdevs

plt.title("Learning Curves for Linear Regression", fontsize=16)
print(x_train_n.shape)
print(w.shape)
print(x_val_n.shape)
reg = 0.2
learning_curves(x_train_n, y_train, x_val_n, y_val, reg, alpha, iterations)
```

```text
(12, 8)
    (9,)
    (21, 8)
    gradient is small enough!
    iterated num is : 158
    ...
```

![](img/file70.png)

**图 3-36** 训练和验证损失曲线

是的，同一个 8 次多项式假设函数，在通过正则化技术惩罚模型参数后，解决了模型的过拟合问题。

## 3.5 逻辑回归

在线性回归问题中，目标值（如餐车的利润和房价）是连续值。而某些问题（如分类问题）的目标值是离散值，即判断一个数据在几个类别中属于哪一类。例如识别一张图片是猫还是狗，从医学图像或其他测量数据判断一个人是否患癌，这些问题都是二分类问题，即需要判断一个数据属于两个类别中的哪一个。**逻辑回归** 是线性回归的延伸，专门用于解决二分类问题。

### 3.5.1 逻辑回归

线性回归能解决二分类问题吗？答案是肯定的，只要设定一个阈值（如 0），线性回归输出值大于阈值 0 的属于一类，小于阈值 0 的属于另一类。线性回归模型函数的输出值范围是 $(-\infty, \infty)$，而逻辑回归进一步利用 sigmoid 函数 $\sigma(x)$（见第 1.3 节）将输出值映射到 $(0, 1)$ 区间。这样，输出值就可以解释为输入变量属于某一类的概率。

使用 sigmoid 函数 $\sigma(x)$ 变换线性回归的预测值，构成了逻辑回归的假设函数：

$$f_{w}(x) = \frac{1}{1 + e^{-x w}} = \sigma(x w) \tag{3-30}$$

利用该假设函数对样本特征及其目标值的关系进行建模，即所谓的**逻辑回归**。逻辑回归的假设函数 $f_{w}(x)$ 取值在 0 和 1 之间，可用来表示 $x$ 属于某一类的概率。如果 $x$ 是医学图像中的肿瘤大小，$f_{w}(x)$ 就可以表示 $x$ 对应的肿瘤是否为恶性的概率。

若分别用 0 和 1 表示两个类别，且用 $f_{w}(x)$ 表示 $x$ 属于类别 1 的概率，则 $x$ 属于类别 0 的概率为 $1 - f_{w}(x)$。

目前：

$$P(y = 1|x) = f_{w}(x) = \frac{1}{1 + e^{-x w}} = \sigma(x w)$$

$$P(y = 0|x) = 1 - f_{w}(x) = 1 - \frac{1}{1 + e^{-x w}} = 1 - \sigma(x w)$$

对于一个样本 $(x, y)$，若 $y=1$，其出现的概率为 $P(y=1|x)$；若 $y=0$，其出现的概率为 $P(y=0|x)$。无论 $y$ 是 1 还是 0，$(x, y)$ 的概率都可以统一表示为 $P(y=1|x)^{y} P(y=0|x)^{1-y}$，即 $f_{w}(x)^{y} (1 - f_{w}(x))^{1-y}$。那么 $m$ 个样本同时出现的概率为：

$$\prod_{i=1}^{m} (f_{w}(x^{i})^{y^{i}} (1 - f_{w}(x^{i}))^{1 - y^{i}})$$

使该概率值最大的 $w$，能使这 $m$ 个样本以最大概率出现。因此，逻辑回归需要使该概率最大化的 $w$。因为乘法会使数值急剧变为无穷大或接近 0，为了使求解算法在数值上稳定且便于求导，通常取该概率值的负对数平均值作为代价函数，即：

$$\mathcal{L}(w) = - \frac{1}{m} \sum_{i=1}^{m} (y^{i} \log(f_{w}(x^{i})) + (1 - y^{i}) \log(1 - f_{w}(x^{i})))$$

$-(y^{i} \log(f_{w}(x^{i})) + (1 - y^{i}) \log(1 - f_{w}(x^{i})))$ 称为样本的**交叉熵损失**。可用 $\mathcal{L}^{(i)}$ 表示，则所有样本的交叉熵损失可表示为：

$$\mathcal{L}(w) = \frac{1}{m} \sum_{i=1}^{m} \mathcal{L}^{(i)}$$

对于样本 $(x^{i}, y^{i})$，若其真实目标值 $y^{i}$ 为 1，且逻辑回归的预测值 $f_{w}(x^{i})$ 也为 1，则 $\mathcal{L}^{(i)} = -(1 \cdot 0 + 0 \cdot \log 0) = 0$；若真实目标值 $y^{i}$ 为 0，且预测值 $f_{w}(x^{i})$ 也为 0，则 $\mathcal{L}^{(i)} = -(0 \cdot \log 0 + 1 \cdot \log 1) = 0$。即当预测值与目标值一致时，该值为 0。若不一致，因为 $y^{i}, 1-y^{i}, f_{w}(x^{i}), 1-f_{w}(x^{i})$ 均为 `(0,1)` 区间内的实数，所以 $\mathcal{L}^{(i)}$ 是大于 0 的正数。因此，只有当预测值与目标值完全一致时，$\mathcal{L}^{(i)}$ 才能达到最小值 0。

逻辑回归的目标是求使该损失（亦称代价）$\mathcal{L}(w)$ 最小的 $w$。其求解算法仍为梯度下降法。为此，需计算 $\mathcal{L}(w)$ 关于 $w$ 的梯度，即对每个 $w[j]$ 的偏导数：

为了更好地求 $L(w)$ 关于 $w = (w[0], w[1], \dots, w[K])^T$ 的偏导数，引入一些辅助符号 $z^{(i)}, f^{(i)}$：

#### 逻辑回归梯度推导

##### 数学公式推导

##### 前向传播

$$z^{(i)} = w^T x^{(i)} = w_1 x_1^{(i)} + w_2 x_2^{(i)} + \dots + w_K x_K^{(i)} + w_0 x_0^{(i)}$$

$$f^{(i)} = \sigma(z^{(i)})$$

###### 损失函数

$$\mathcal{L}^{(i)} = -\left(y^{(i)}\log(f^{(i)}) + (1 - y^{(i)})\log(1 - f^{(i)})\right)$$

$$\mathcal{L}(w) = \frac{1}{m}\sum_{i=1}^{m}\mathcal{L}^{(i)}$$

###### 链式法则求导
