

```python
def numerical_gradient(f, params, eps=1e-6):
    numerical_grads = []
    for x in params:
        # x may be a multidimensional array,
        # for each element, calculate its numerical partial derivative
        grad = np.zeros(x.shape)
        it = np.nditer(x, flags=['multi_index'], op_flags=['readwrite'])
        while not it.finished:
            idx = it.multi_index
            old_value = x[idx]
            x[idx] = old_value + eps    # x[idx]+eps
            fx = f()
            x[idx] = old_value - eps    # x[idx] - eps
            fx_ = f()
            grad[idx] = (fx - fx_) / (2*eps)
            x[idx] = old_value    # Note: Be sure to restore the weight parameter to its original value.
            it.iternext()         # Loop through the next element of x

        numerical_grads.append(grad)
    return numerical_grads
```

该函数接受的参数 `f` 表示要求梯度的函数，`params` 表示该函数的参数。因为 `f` 可能有多个参数，所以 `params` 表示这一组多个参数（如 Python 的 `list`、`tuple` 等对象）。为了更通用，假设 `params` 的每个元素 `x` 是一个包含多个元素的多维数组。

在内层循环中，对 `x` 的每个下标 `idx` 所指向的元素 `x[idx]`，分别加上微小增量 `x[idx] + eps` 和 `x[idx] - eps` 并计算对应的函数值 `f()`，然后利用导数的微分近似公式计算出该 `x[idx]` 对应的偏导数并赋值给 `grad[idx]`。注意：每次修改 `x[idx]` 后，必须将其还原为原值，否则会影响其他偏导数的计算，并影响退出该函数后 `params` 的值。

你可以使用这个通用的数值梯度计算函数来计算前面函数的数值梯度：

```python
x = np.array([2., 3.])
param = np.array(x)        # numerical_gradient 的参数 param 必须是 numpy 数组
numerical_grads = numerical_gradient(lambda: f(param), [param], 1e-6)
print(numerical_grads[0])
```

```
[ 0.25 54.00000001]
```

注意 `numerical_gradient` 的第一个参数 `f` 必须指向一个函数对象，而不是函数调用的结果。上面将 `lambda: f(param)` 写成 `f(param)` 是错误的。

对于包含诸如 `param` 等参数的函数 `f`，通常可以使用上述 lambda 表达式或下面的包装函数 `fun` 来返回一个对参数 `param` 进行计算的函数对象。

```python
def fun():
    return f(param)

numerical_grads = numerical_gradient(fun, [param], 1e-6)
print(numerical_grads[0])
```

```
[ 0.25 54.00000001]
```

在后续章节中，将使用这个通用的数值梯度计算函数 `numerical_gradient()` 来计算模型函数的数值梯度。该函数及其他函数包含在本书的源代码文件 `util.py` 中。

## 2.5 分离梯度下降算法与参数优化策略

### 2.5.1 参数优化器

变量（参数）的优化策略在梯度下降算法中是硬编码的。不同优化策略的梯度下降法除参数更新外，具有相同的框架。为了提高代码的复用性和灵活性，可以将参数优化策略从梯度下降算法中分离出来。

可以定义一个表示参数优化策略的类：

```python
class Optimizator:
    def __init__(self, params):
        self.params = params

    def step(self, grads):
        pass

    def parameters(self):
        return self.params
```

`params` 是变量（参数）的列表，`step()` 用于根据梯度 `grads` 更新这些参数 `params`。例如，在该类的基础上可以派生出定义了使用基本梯度下降法的参数优化策略的参数优化器类 `SGD`：

```python
class SGD(Optimizator):
    def __init__(self, params, learning_rate):
        super().__init__(params)
        self.lr = learning_rate

    def step(self, grads):
        for i in range(len(self.params)):
            self.params[i] -= self.lr * grads[i]
        return self.params
```

类似地，可以定义其他参数优化器，如动量法的 `SGD_Momentum`：

```python
class SGD_Momentum(Optimizator):
    def __init__(self, params, learning_rate, gamma):
        super().__init__(params)
        self.lr = learning_rate
        self.gamma = gamma
        self.v = []
        for param in params:
            self.v.append(np.zeros_like(param))

    def step(self, grads):
        for i in range(len(self.params)):
            self.v[i] = self.gamma * self.v[i] + self.lr * grads[i]
            self.params[i] -= self.v[i]
        return self.params
```

### 2.5.2 接受参数优化器的梯度下降法

只要梯度下降算法接受更新参数的参数优化器，就可以根据优化器的优化策略更新参数：

```python
def gradient_descent_(df, optimizator, iterations, epsilon=1e-8):
    x, = optimizator.parameters()
    x = x.copy()
    history = [x]
    for i in range(iterations):
        if np.max(np.abs(df(x))) < epsilon:
            print("The gradient is small enough!")
            break
        grad = df(x)
        x, = optimizator.step([grad])
        x = x.copy()
        history.append(x)
    return history
```

观察一个简单的凸函数曲面，

$$f(x,y) = \frac{1}{16}x^{2} + 9y^{2}$$

这是一个碗状曲面，如图 2-16 所示。其最小值位于碗底，即 `(0,0)` 是整个函数的最小值点，最小值为 0。

![](EPUB/media/file36.png "fig:")

图 2-16 函数 $f(x,y) = \frac{1}{16}x^{2} + 9y^{2}$ 曲面

对该函数应用上述 `SGD` 参数优化器：

```python
df = lambda x: np.array(((1/8)*x[0], 18*x[1]))
x0 = np.array([-2.4, 0.2])

optimizator = SGD([x0], 0.1)
path = gradient_descent_(df, optimizator, 100)
print(path[-1])
path = np.asarray(path)
path = path.transpose()
```

```
[-8.26638332e-06 2.46046384e-98]
```

逼近最优解，切换为 `SGD_Momentum` 优化器：

```python
x0 = np.array([-2.4, 0.2])
optimizator = SGD_Momentum([x0], 0.1, 0.8)
path = gradient_descent_(df, optimizator, 1000)
print(path[-1])
path = np.asarray(path)
path = path.transpose()
```

它也能更好地逼近最优解。

```
The gradient is small enough!
[-1.49829905e-08 -4.74284398e-10]
```

![](EPUB/media/file232.png)

本章介绍三种典型的机器学习技术：线性回归、逻辑回归和 Softmax 回归。它们是基于神经网络的深度学习的基础，其中的数据归一化、模型评估、正则化等概念、技术和方法也常用于深度学习。

## 3.1 线性回归

### 3.1.1 餐车利润问题

Andrew Ng 的深度学习课程中有一个“餐车利润问题”，提供了以下数据集：

```
6.1101,17.592
5.5277,9.1302
8.5186,13.662
7.0032,11.854
5.8598,6.8233
...
```

数据集的第一列是各城市的人口，第二列是该城市餐车的利润，数量单位为万。以下 Python 代码从文本文件读取数据集并输出前 5 行：

```python
x, y = [], []
with open('food_truck_data.txt') as A:
    for eachline in A:
        s = eachline.split(',')
        x.append(float(s[0]))
        y.append(float(s[1]))
for i in range(5):
    print(x[i], y[i])
```
