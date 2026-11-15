

权重初始化方法让我们起步就处于一个更好的区间，这使得我们能够更快地获得良好的结果。如果用100个隐藏神经元来绘制结果，也会观察到同样的现象：

![](img/9499fc06bad8b4a2610710f5e9d6ea39_136_0.png)

在这种情况下，两条曲线并没有完全相交。不过，我的实验表明，只需多训练几个epoch（未显示），准确率就几乎完全一样了。基于这些实验，看起来改进的权重初始化只是加快了学习速度，并没有改变我们网络的最终性能。不过，在第4章中，我们会看到一些神经网络的例子，使用1/√n_in权重初始化后，长期行为会显著更好。因此，不仅是学习速度得到了提升，有时最终性能也会更好。

1/√n_in权重初始化方法有助于改进我们神经网络的学习方式。也有人提出了其他权重初始化技术，其中许多都基于这个基本思想。这里我不会回顾其他方法，因为1/√n_in对我们的目的来说已经足够好。如果你有兴趣进一步了解，我建议查看Yoshua Bengio*2012年论文第14和15页上的讨论，以及其中的参考文献。

> *基于梯度训练深层架构的实用建议，作者：Yoshua Bengio (2012)。

## 问题

- 将正则化与改进的权重初始化方法相关联 L2正则化有时会自动给我们提供一种类似于新权重初始化方法的东西。假设我们使用旧的权重初始化方法。勾勒一个启发式论证：(1) 假设\(\lambda\)不太小，训练的最初几个epoch几乎完全由权重衰减主导；(2) 前提是\(\eta\lambda \ll n\)，权重每个epoch会以\(\exp(-\eta\lambda/m)\)的因子衰减；以及(3) 假设\(\lambda\)不太大，当权重衰减到大约\(1/\sqrt{n}\)的大小时，权重衰减就会趋于平缓，其中\(n\)是网络中权重的总数。论证这些条件在本节绘制的示例中都得到满足。

## 重新审视手写识别：代码

让我们实现本章讨论的想法。我们将开发一个新程序network2.py，它是我们在第1章中开发的程序network.py的改进版本。如果你已经有一段时间没有看network.py了，那么花几分钟快速浏览一下之前的讨论可能会有所帮助。它只有74行代码，而且很容易理解。

与network.py的情况一样，network2.py的明星是Network类，我们使用它来表示神经网络。我们使用网络中各层的大小列表以及要使用的代价函数的选择来初始化Network的一个实例，默认使用交叉熵：

```python
class Network(object):
    def __init__(self, sizes, cost=CrossEntropyCost):
        self.num_layers = len(sizes)
        self.sizes = sizes
        self.default_weight_initializer()
        self.cost=cost
```

__init__方法的前几行与network.py中的相同，而且不言自明。但接下来的两行是新的，我们需要详细了解它们在做什么。

让我们先来看看default_weight_initializer方法。这个方法采用了我们新的改进的权重初始化方法。正如我们所看到的，在这种方法中，输入到神经元的权重被初始化为均值为0、标准差为1除以输入到该神经元的连接数的平方根的高斯随机变量。在该方法中，我们还将使用均值为0、标准差为1的高斯随机变量来初始化偏置。代码如下：

```python
def default_weight_initializer(self):
    self.biases = [np.random.randn(y, 1) for y in self.sizes[1:]]
    self.weights = [np.random.randn(y, x)/np.sqrt(x)
                    for x, y in zip(self.sizes[:-1], self.sizes[1:])]
```

要理解这段代码，回顾一下np是用于线性代数的NumPy库可能会有所帮助。我们将在程序开头导入NumPy。另外，请注意，我们不会为第一层神经元初始化任何偏置。我们避免这样做是因为第一层是输入层，因此任何偏置都不会被使用。在network.py中我们也做了完全相同的事情。

为了补充default_weight_initializer，我们还将包含一个large_weight_initializer方法。该方法使用第1章中的旧方法初始化权重和偏置，权重和偏置都被初始化为均值为0、标准差为1的高斯随机变量。当然，这段代码与default_weight_initializer只有很小的区别：

```python
def large_weight_initializer(self):
    self.biases = [np.random.randn(y, 1) for y in self.sizes[1:]]
    self.weights = [np.random.randn(y, x)
                    for x, y in zip(self.sizes[:-1], self.sizes[1:])]
```

我包含large_weight_initializer方法主要是为了方便，以便更容易地将本章的结果与第1章的结果进行比较！我想不出有多少实际情况会推荐使用它！

Network.__init__方法中的第二个新内容是，我们现在初始化一个cost属性。要了解它的工作原理，让我们看看我们用来表示交叉熵代价*：

```python
class CrossEntropyCost(object):

    @staticmethod
    def fn(a, y):
        return np.sum(np.nan_to_num(-y*np.log(a)-(1-y)*np.log(1-a)))

    @staticmethod
    def delta(z, a, y):
        return (a-y)
```

*如果您不熟悉Python的静态方法装饰器，并且只是将fn和delta视为普通方法。如果您对细节感兴趣，@staticmethod所做的只是告诉Python解释器，随后的方法不以任何方式依赖于对象。这就是为什么self不是作为参数传递给fn和delta方法的原因。*

让我们来拆解一下。首先要注意的是，尽管从数学上讲交叉熵是一个函数，但我们将其实现为一个Python类，而不是Python函数。我之所以这样做是什么原因呢？原因是代价在我们的网络中扮演两个不同的角色。明显的角色是，它是衡量输出激活a与所需输出y匹配程度的指标。这个角色由CrossEntropyCost.fn方法捕获。（顺便说一句，CrossEntropyCost.fn内部的np.nan_to_num调用确保NumPy能正确处理非常接近零的数字的对数。）但代价函数进入我们网络的还有第二种方式。回顾第2章，在运行反向传播算法时，我们需要计算网络的输出误差$\delta^L$。输出误差的形式取决于代价函数的选择：不同的代价函数，输出误差的形式也不同。对于交叉熵，输出误差是，如我们在公式(66)中看到的，

$\delta^L = a^L - y. \quad (99)$

出于这个原因，我们定义了第二个方法CrossEntropyCost.delta，其目的是告诉我们的网络如何计算输出误差。然后，我们将这两个方法打包到一个单一的类中，该类包含我们网络需要知道的关于代价函数的一切内容。

类似地，network2.py还包含一个用于表示二次代价函数的类。这是为了与第1章的结果进行比较而包含的，因为往后我们将主要使用交叉熵。代码如下。QuadraticCost.fn方法是对实际输出a和所需输出y相关的二次代价进行直接计算。QuadraticCost.delta返回的值基于我们在第2章中推导出的二次代价输出误差的表达式(30)。

```python
class QuadraticCost(object):

    @staticmethod
    def fn(a, y):
        return 0.5*np.linalg.norm(a-y)**2

    @staticmethod
    def delta(z, a, y):
        return (a-y) * sigmoid_prime(z)
```

我们现在已经了解了network2.py和network.py之间的主要区别。所有这些都很简单。还有一些较小的更改，我将在下面讨论，包括L2正则化的实现。在讨论那个之前，让我们看看network2.py的完整代码。您不需要详细阅读所有代码，但了解大致情况是值得的。

