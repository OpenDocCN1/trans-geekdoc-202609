
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

![](img/file36.png "fig:")

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

![](img/file232.png)

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

### 3.1.2 机器学习与人工智能

#### 1. 机器学习

“餐车利润问题”是一个经典的机器学习问题。**机器学习**是基于经验数据，发现这些数据中包含的某些统计规律，并利用学到的规律对未来的新数据进行判断或预测。

机器学习可以从这些（城市人口、对应餐车利润）数据中，获得一个反映两者关系或从城市人口到餐车利润的函数关系的数据模型。如果用 `x` 表示城市人口，`y` 表示餐车利润，机器学习就是寻找一个函数 `f(x)`，使得 `y` 满足 `y = f(x)`。求解这种函数关系或模型的过程称为**机器学习**或**模型训练**。有了这个数学（模型）函数 `f(x)`，就可以将新的城市人口 `x` 代入该函数 `f(x)` 中，以预测该城市的餐车利润。

在机器学习中，用于训练模型的数据称为**样本数据**、**样本集**或**训练集**。样本集包含多个样本，每个样本由**样本特征**（如城市人口）和**样本标签**（如餐车利润）组成，它们分别对应学习函数 `y = f(x)` 的自变量 `x` 和因变量 `y`。样本标签通常也被称为“**真实值**”或“**目标值**”。学习模型的最终目标是根据该模型，从样本特征预测其目标值或标签。

通常，模型的预测值 `f(x)` 不可能完全等于真实值，模型训练通常是寻找某种最优意义（如预测值 `f(x)` 与真实值 `y` 某种误差最小化）的数学函数。

#### 2. 机器学习与人工智能的关系

机器学习是人工智能领域的一个研究方向。人工智能不同于普通计算机程序。普通计算机程序基于已知的数学模型进行计算，每个计算步骤都按照确定的计算公式执行。例如，根据圆面积 A 与半径 r 之间众所周知的公式 $A = \frac{1}{2}\pi r^{2}$ 计算某个半径圆的面积。

但对于许多实际问题，无法找到确定的数学模型来表示数据之间的关系或规律。例如，“房价预测问题”希望根据房屋的特征信息（如房屋面积等）预测房价，但没有现成的数学模型告诉我们如何从房屋的特征信息计算房价。

类似的问题还有很多，例如：“预测股票价格”、“识别人脸照片中是谁”、“确定一段语音对应的文本”、“判断邮件是否为垃圾邮件”、“下棋时在棋盘状态下如何走子”、“电商网站的推荐系统如何推荐用户可能感兴趣的商品”、“自动驾驶汽车”等。

这些问题要求计算机具备与人类相同的智能。人类之所以能轻松识别图像中是否包含猫或狗，是因为他们以前见过许多此类图像，并在大脑中形成了某种模型，从而能轻松完成这一识别任务；但对于计算机来说，所有图像都是数字矩阵（数组），没有明确的公式来表达图像与其类别之间的关系。

如何让计算机拥有人类智能？这是计算机科学研究领域人工智能的目标。人工智能并不神秘。例如，20 世纪 80 年代出现的专家系统将特定领域专家的经验转化为一些规则，然后基于逻辑推理和规则匹配等方法解决特定问题。例如，如果一个人发烧，意味着此人可能生病了；如果红细胞很少，意味着可能患有某种缺血或失血性疾病。然而，专家系统存在耗时、费力、昂贵等问题，且针对某一问题的专家规则无法用于其他问题。此外，图像和语音识别等一些问题难以定义规则。

与基于逻辑推理的传统人工智能不同，作为现代人工智能的机器学习不需要专家的领域知识。它只需要大量数据，并可以使用统计方法对数据进行建模和统计学习。

例如，购物网站的推荐系统可以根据用户的购物和网站浏览记录预测用户的爱好，从而向他们发送相应的推荐商品。同样，如果有大量房屋特征及其价格的数据，机器学习可以找到一个反映两者关系的合理数学模型，并基于该数学模型从房屋的特征信息预测价格。

#### 3. 机器学习的分类

机器学习主要分为三类：监督学习、无监督学习和强化学习。

所谓**监督学习**，是指用于学习的数据不仅知道其数据特征，还知道其目标值，例如餐车的利润。对于一个样本，不仅知道城市人口，还知道该城市餐车的利润。如果假设样本特征 x 和目标值 y 之间满足函数关系 `y = f(x)`，则可以从多个已知数据特征 `x` 和目标值 `y` 的数据样本 `(x^(i), y^(i))` 中找出这个假设函数，使它们尽可能满足 `y^(i) = f(x^(i))`。这种基于多个已知数据特征 `x` 和目标值 `y` 的数据样本 `(x^(i), y^(i))` 求解最佳假设函数的机器学习称为**监督学习**。这也是目前应用最广泛的机器学习方法。

因此，监督学习是基于许多已知自变量（也称为特征）及其对应的因变量（也称为标签或目标）的样本，学习自变量（特征）与因变量（目标）之间的函数关系。一旦知道了这个函数，就可以为新的样本特征预测其目标值。

### 3.1.3 什么是线性回归？

如图 3-2 所示，可以训练（学习）一个用于手写数字识别的函数模型 `f`。该函数接受一个输入数字图像，并输出 0 到 9 中的某个数字。也可以训练语音识别模型，从语音输入生成相应的文本。或者训练一个围棋人工智能程序，根据输入的棋局输出落子位置。

**图 3-2** 监督学习是学习一个将输入（数据特征）转换为输出（目标值）的函数。

自变量和因变量之间存在无穷多种各式各样的函数关系，例如线性函数、二次函数、三角函数等。监督学习应根据具体问题和数据集的特点，选择一个合适的函数来表示数据特征 `x` 和目标值 `y`。例如，针对餐车利润问题，根据对数据的观察，可以认为城市人口与利润之间似乎存在线性关系，那么可以使用 `f(x) = wx + b` 这样的线性函数作为 `x` 和 `y` 之间的函数模型。函数 `f(x) = wx + b` 称为**假设函数**。当然，不同的参数 `w`、`b` 代表不同的线性关系。模型训练是基于真实值 `y^(i)` 和假设函数的预测值 `f(x^(i)) = wx^(i) + b` 的某种误差，求解出一组最优参数 `w`、`b`。一旦 `w`、`b` 确定为模型函数 `f`，对于新的输入 `x[*]`, 只需代入该函数 `f` 即可得到预测值 `f(x^(*)) = wx^(*) + b`。

监督学习目前是人工智能中应用最广泛、最成功的机器学习方法。例如，图像分类识别利用大量已知图像类别的图像来识别新图像属于哪个类别。信件邮政编码识别系统可以自动识别手写邮政编码。还有击败人类围棋冠军的 AlphaGo，以及击败所有人类专家、根据基因序列成功预测蛋白质 3D 结构的 AlphaFold 等。

监督学习主要包括以下步骤（任务）：

1.  需要一组训练样本；
2.  设计一个能很好描述样本特征与目标值关系的假设函数；
3.  选择一个合理的损失函数来描述预测值与真实值之间的误差；
4.  训练模型；
5.  使用模型进行预测。
