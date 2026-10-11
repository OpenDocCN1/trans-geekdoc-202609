

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

![](EPUB/media/file69.png)

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

![](EPUB/media/file70.png)

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

