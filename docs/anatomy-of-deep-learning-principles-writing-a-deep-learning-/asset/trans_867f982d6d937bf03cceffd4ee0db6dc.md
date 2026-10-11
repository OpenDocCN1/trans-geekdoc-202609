

```python
def f(x):
    y = 0
    y += x*x
    return y

print(f(2), '\t', f(3))
print(f(3), '\t', f(2))
```

```
4 9
9 4
```

无论是先计算 `f(2)` 再计算 `f(3)`，还是先计算 `f(3)` 再计算 `f(2)`，`f(2)` 和 `f(3)` 的结果仅取决于各自的输入 2 和 3，`f(2)` 和 `f(3)` 的执行顺序无关紧要。

如果使用无环神经网络根据当前词预测下一个词的概率，这种预测也独立于词的处理顺序。如图 7-12 所示，假设语言中只有 "good"、"drink" 和 "wine" 三个词，对于输入词序列 "good drink" 中的每个词，神经网络都输出每个词作为下一个词的概率。

图 7-12 非循环神经网络从词 "good" 预测 "good"、"drink" 和 "wine" 作为下一个词的概率，以及从词 "drink" 预测 "good"、"drink" 和 "wine" 作为下一个词的概率，二者相互独立。无论输入序列是 "good to drink"、"wine is good to drink" 还是 "drink good wine"，从词 "good" 预测 "good"、"drink" 和 "wine" 作为下一个词的概率都是相同的。

无论这三个词在句子中以何种顺序出现，例如 "wine is good" 和 "drinking good wine"，对于每个词，神经网络根据该词预测每个词作为其下一个词的概率，结果都是一样的。用这种神经网络来表示语言模型，每个词的输出值仅取决于它自己，与其他词无关。这显然是不合理的。

不失一般性，如果神经网络只有一层或一层神经元，即：

`y = f(x) = g(xW + b)`

并假设非线性激活函数为 sigmoid 函数，该神经网络可用 Python 代码表示为：

```python
class FNN(x):
    # ...
    def forward(self, x):
        y = sigmoid(np.dot(x, self.W) + self.b)
        return y
```

对于一组数据 `x^((1))`、`x^((3))`、`x^((3))`，FNN 计算这些数据的输出过程如下：

```python
nn = FNN()
y1 = nn.forward(x1)
y2 = nn.forward(x2)
y3 = nn.forward(x3)
```

这三条预测语句的顺序对预测结果 `y1`、`y2`、`y3` 没有影响。

如图 7-12 所示，为了将一个词作为样本输入神经网络，需要对每个词进行量化，即转换为固定长度的向量，因为语言模型只有 3 个词，可以使用长度为 3 的 one-hot 向量来区分这 3 个词，即每个词对应一个不同的 one-hot 向量，例如：good (1,0,0)，drink (0,1,0)，wine (0,0,1)。

## 7.2.2 具有记忆功能的循环神经网络

与无环神经网络不同，循环神经网络是一种具有记忆功能的神经网络，可表示为 `y = f(x, h)`，即除了输入 `x` 外，还有一个隐藏状态变量 `h` 用于记录计算过程的历史。循环神经网络函数类似于编程语言中具有记忆功能的函数或类，例如 C 语言中包含静态局部变量的函数，以及 C++、Java、Python 等语言中的类对象。例如，下面的类 `rf` 使用数据属性 `h` 来记录计算的中间结果（状态）：

```python
class rf():
    def __init__(self):
        self.h = 0
    def forward(self, x):
        self.h += 2*x
        return self.h + x*x
    def __call__(self, x):
        return self.forward(x)

f = rf()
print(f(2), '\t', f(3))
print(f(3), '\t', f(2))
```

```
8 19
25 24
```
