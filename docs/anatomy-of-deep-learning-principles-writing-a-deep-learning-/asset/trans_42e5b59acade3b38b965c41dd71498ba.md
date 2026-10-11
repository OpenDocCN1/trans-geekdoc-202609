

```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

n_pts = 10
x_train, y_train = sample(n_pts)
x_valid, y_valid = sample(n_pts)
x_test, y_test = sample(n_pts)
```

如果你想选择不同次数的假设函数，例如 `K=0, 1, 2, 3, ... 9`，可以使用这些不同次数的假设函数进行训练，并计算训练误差和验证误差。

```python
def rmse(a, b):
    return np.sqrt(np.mean(np.square(a - b)))

M = 10
errors_train = []
errors_valid = []
for K in range(M):
    X = np.array([np.power(x_train, k) for k in range(K + 1)])
    X = X.transpose()

    # w, history = gradient_descent_vec(X, y, lr, iterations)
    XT = X.transpose()
    XTy = XT @ y_train
    w = np.linalg.inv(XT @ X) @ XTy
    # w = np.linalg.pinv(X) @ y
    # print("w=:", w)

    predict_train = X @ w
    error_train = rmse(y_train, predict_train)

    X_valid = np.array([np.power(x_valid, k) for k in range(K + 1)])
    X_valid = X_valid.transpose()
    predict_valid = X_valid @ w
    error_valid = rmse(y_valid, predict_valid)

    errors_train.append(error_train)
    errors_valid.append(error_valid)

plt.plot(errors_train, 'o-', mfc="none", mec="b", ms=10, c="b", label="Training")
plt.plot(errors_valid, 'o-', mfc="none", mec="r", ms=10, c="r", label="Valid")
plt.legend()
plt.xlabel("degree")
plt.ylabel("RMSE")
plt.ylim(0, 1.5)
plt.show()
```

![](EPUB/media/file57.png)

**图 3-21 训练和测试损失曲线**

可以看出，当多项式次数低于 2 时，训练误差和验证误差都相对较大，说明在训练集和验证集上的拟合效果都不好，即模型处于欠拟合状态。当多项式次数在 3 到 4 左右时，训练误差和验证误差都相对较小。当多项式次数开始大于 5 时，训练误差持续下降，但验证误差反而增加，说明模型的泛化能力开始变差。因此，3 次或 4 次多项式函数是一个较好的假设函数。

训练集、验证集和测试集的适当大小（样本数量）应该是多少？这取决于实际问题。对于某些问题，获取样本的成本较低，样本模型可达数十万甚至数百万。例如，购物网站很容易收集大量用户购物行为数据，训练集样本数据占所有样本数据的比例可以高达 90% 以上，而验证集和测试集占所有样本数据的比例可以低至 5% 左右，因为总样本数非常大，5% 的样本数量已经很大了。对于某些问题，获取样本的成本昂贵，总样本数量相对较少。例如，在医学影像领域，验证集和测试集占总样本数的比例会相对较高，例如高达 20%，自然训练集的比例就会降低。对于一般规模的样本，通常可以将训练集、验证集和测试集的样本数量占所有样本数量的比例设置为 60%、20%、20%。这种比例划分不是绝对的，应根据实际问题确定。

### 3.2.3 学习曲线

狭义上，学习曲线通常指不同数量训练样本的训练误差和验证误差（或得分）。即计算不同数量训练样本的训练误差（或得分）以及验证样本的训练误差（或得分），然后绘制训练误差（或得分）曲线和验证误差（或得分）曲线。通过对比训练曲线和验证曲线，有助于观察训练的过拟合和欠拟合情况。

广义上，任何有助于判断训练情况的曲线都可以称为学习曲线，例如训练损失曲线和准确率曲线。仅训练样本的曲线可用于观察训练是否收敛，但无法判断是欠拟合还是过拟合。只有验证样本的曲线才有助于判断是否过拟合或欠拟合。通常所说的学习曲线是指一条训练曲线和一条验证曲线。

针对前面的问题，可以为特定的假设函数（例如 9 次多项式函数）绘制训练损失曲线和验证损失曲线，观察训练集和验证集的损失（误差）如何随迭代次数变化。

下面的 `loss()` 函数计算模型参数对应的假设函数在样本集（`X`、`y`）上的损失，`learning_curves_trainSize()` 计算不同大小（`trainSize`）训练集的训练损失和验证损失，并绘制训练损失曲线和验证损失曲线。

```python
def loss(w, X, y):
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))  # 添加一列特征 1
    predictions = X @ w
    errors = predictions - y
    return (errors ** 2).mean() / 2

def learning_curves_trainSize(X_train, y_train, X_val, y_val, alpha=0.3, iterations=1000):
    train_err = np.zeros(len(y_train))
    valid_err = np.zeros(len(y_train))
    for i in range(len(y_train)):
        w_history = gradient_descent_vec(X_train[0:i + 1, :], y_train[0:i + 1], alpha, iterations)
        w = w_history[-1]
        train_err[i] = loss(w, X_train[0:i + 1, :], y_train[0:i + 1])
        valid_err[i] = loss(w, X_val, y_val)

    plt.plot(range(1, len(y_train) + 1), train_err, c="r", linewidth=2)
    plt.plot(range(1, len(y_train) + 1), valid_err, c="b", linewidth=2)
    plt.xlabel("number of training examples", fontsize=14)
    plt.ylabel("error", fontsize=14)
    plt.legend(["training", "validation"], loc="best")

    max_err = np.max(np.array([np.max(train_err), np.max(valid_err)]))
    min_err = np.min(np.array([np.min(train_err), np.min(valid_err)]))
    offset = (max_err - min_err) / 10
    plt.axis([1, len(y_train) + 1, min_err - offset, max_err + offset])
    # plt.axis([1, len(y_train) + 1, 0, 100])
    plt.grid()
```

循环中的 `i` 表示每次训练模型的训练集大小，使用 (`X_train`、`y_train`) 的 1、2、... 直到用完所有样本训练模型，计算出的模型参数的训练损失在验证集 (`X_val`、`y_val`) 上求和为验证损失。为正弦波采样一组训练集和验证集，并测试此 `learning_curves_batchSize()`：

```python
np.random.seed(89)
n_pts = 100
x_train, y_train = sample(n_pts)
x_valid, y_valid = sample(n_pts)

# K = 4
K = 2
X_train = np.array([np.power(x_train, k + 1) for k in range(K)]).transpose()
X_valid = np.array([np.power(x_valid, k + 1) for k in range(K)]).transpose()

plt.title("BatchSize Learning Curves for Linear Regression", fontsize=16)

alpha = 0.3
iterations = 50000
learning_curves_trainSize(X_train, y_train, X_valid, y_valid, alpha, iterations)

plt.ylim(-0.5, 20)
plt.show()
```

```
gradient is small enough!
iterated num is : 117
...
```

![](EPUB/media/file58.png "fig:")

**图 3-22 不同大小训练集的训练损失**

可以看出，训练集大小超过 40 后，训练损失和验证误差比较接近。因此，对于 2 次多项式假设函数，训练集的样本数量应大于 40。

对于某个特定的假设函数，也可以通过迭代学习曲线观察多少次迭代是合适的。

