

# 列表 2.5 FirstProgram.ipynb (part 5) 输出
```python
aMatrix=np.array([[1,2,3],[4,5,6]])
print(aMatrix)
print(aMatrix[1,2])

[[3]
6]
```

该符号表示法表明，在 Python 语法中，二维数组被视为一维列表的一维维列表。请注意是如何访问单个数组元素的：第一个索引指定列中的位置，第二个索引指定行中的位置。这等同于矩阵的常用数学表示法。通过此，我们可以通过定义一个行向量为如下形式，来修正上述向量的表示法：

# 列表 2.6 FirstProgram.ipynb (part 6) 输出
```python
aVector=np.array([[1,2,3]])
```

然后可以通过转置将其转换为列向量。

# 列表 2.7 FirstProgram.ipynb (part 7) 输出
```python
print(aVector.T)

[[1]
[2]
[3]]
```

在定义了 NumPy 数组之后，我们可以在这些 NumPy 数组上应用数学函数。例如，矩阵上的一些元素级操作如下所示：

# 列表 2.8 FirstProgram.ipynb (part 8) 输出
```python
matrix=np.array([[5,6],[7,8,9]])
result1=aMatrix @ matrix2 #元素级操作
result2 = aMatrix ** 3 #元素级幂运算：
result3 = aMatrix > 3 #找到矩阵大于 3 的索引
print(result1,result2,result3)

[[5 10 9]
[28 40 54]]
[[1 8 27]
[64 125 216]]
[[False False False]
[True True]]
```

基础矩阵乘法（也称为点积或内积）是通过函数 `np.dot(a,b)` 实现的，在 Python 3 中则通过运算符 `@` 实现。

# 列表 2.9 FirstProgram.ipynb (part 9) 输出
```python
result=aMatrix @ matrix2.T
print(result)

[[33 50]
[81 122]]
```

我们借此通过运算符指定 "T" 包含了转置操作。这种运算符指定在面向对象的编程结构中很常见。

我们经常需要访问数组中的子集并合并数组。为了访问数组的子集，我们可以生成下面的索引向量 `idx`，它指定了我们想要作为矩阵 `aMatrix`（前文定义）行的第一个和第二个元素进行处理的索引：

# 列表 2.10 FirstProgram.ipynb (part 10) 输出
```python
idx=[[1],[0,2]]
print(aMatrix[idx])
4 6
```

另一个实用的示例是用列表创建一个向量：

# 列表 2.11 FirstProgram.ipynb (part 11)
```python
x=np.arange(10)
```

这与 `array(range(10))` 相同，以及提取向量的每第二个元素：

# 列表 2.12 FirstProgram.ipynb (part 12) 输出
```python
print(x[::2])
0 2 4 6
```

数组索引与 `x[0:-1:2]` 相同，因为第一个和第二个限制是起始和结束。合并两个数组通过 `concatenate()` 方法完成：

# 列表 2.13 FirstProgram.ipynb (part 13) 输出
```python
result=np.concatenate((aMatrix,matrix2),axis=0)
print(result)
[[1 2 3]
[4 5 6]
[5 6 7 8 9]]
```

一个检查矩阵大小和方向的有用命令是：

# 列表 2.14 FirstProgram.ipynb (part 14) 输出
```python
result.shape
(4, 3)
```

如，第一个索引指定向下，第二个索引指定向右。我们有时需要重新排列数组元素，这可以通过 `reshape` 函数完成：

# 列表 2.15 FirstProgram.ipynb (part 15) 输出
```python
print(result.reshape(2,6))

[[1 2 3 4 5 6]
[7 8 9]]
```

到目前为止，我们讨论了需要的字节数值类型。除了这些数值类型外，当然还有其他的，如字符。文本数据简单地包含在：

# 列表 2.16 FirstProgram.ipynb (part 16) 输出
```python
text='Hello_World!'
print(text)

Hello_World!
```

## 2.2.2 控制流

在下面展示了三种基础编程结构：循环、条件语句和函数。要循环某些代码，可以使用如下：

# 列表 2.17 FirstProgram.ipynb (part 17) 输出
```python
for i in range(4):
    print(i)

0
1
2
3
```

它从 i=0 开始到 i=3。注意 Python 对位置敏感；缩进的代码表示循环内部的语句。条件语句的形式为：

# 列表 2.18 FirstProgram.ipynb (part 18)
```python
if scalar <1:
    print("true")
else:
    print("false")

false
```

再次注意缩进以指定每个条件的代码块。

## 2.2.3 函数

此书尝试使用最小的示例，不需要像面向对象编程那高级代码结构，尽管这些技术在 Python 中是可用的。基础的代码复用技术是定义函数。在 Python 中可以通过如下模板完成。为了更好地组织代码，特别是定义可以重用的代码，我们有定义函数的选项：

# 列表 2.19 FirstProgram.ipynb (part 19)
```python
def func(arg1, arg2=10):
    arg=arg1+arg2
    return arg

a=1
print(func(2), func(a,2))

12

简单变量在 Python 中按值传递，但更复杂的对象可能会通过引用传递。因此在更改调用变量时要小心。函数可以使用参数调用，我们在示例中展示了如何提供默认参数。定义内联函数也有用，例如定义逻辑 sigmoid 函数：

# 列表 2.20 FirstProgram.ipynb (part 20)
```python
sig = lambda x: x / (1 + exp(-x))
```

我们将使用下面这个内联函数来绘制它。

## 2.2.4 绘图

为数据绘制图形是一个实用的科学工具，我们将使用流行的科学库 matplotlib http://matplotlib.org/，特别是 matplotlib 包中提供的稍微简单的接口。我们已经在代码开头导入了这个库。使用该库，在下面的代码中给基础线图示例：

# 列表 2.21 FirstProgram.ipynb (part 21)
```python
#plotting
x=np.arange(100) #相当于 array(range(100))
y=np.sin(0.1+x)
plt.plot(x)
```

在纸上画图时，我们总是需要轴标签来知道画了什么。

# 列表 2.22 FirstProgram.ipynb (part 22)
```python
plt.xlabel("x")
plt.ylabel("y")
```

如果我们想绘制函数，我们需要生成一个数组。

# 列表 2.23 FirstProgram.ipynb (part 23)
```python
x=np.linspace(0,10,100)
```

绘制该函数只需通过以下实现：

# 列表 2.24 FirstProgram.ipynb (part 24)
```python
plt.plot(x,y)
```

现在将这种编程风格称为向量化代码是很常见的的。这种向量化代码并不那么易读，但编写高效代码也是至关重要的。原因在于系统程序员可以非常高效地实现例程，而这与更通用但低效的索引操作相比很难匹配。

为了演示效率问题，让我们测量矩阵乘法操作的时间。我们开始导入标准的 NumPy 和 Mat1 库，并导入一个计时器例程：

# 列表 2.25 FirstProgram.ipynb (part 25) 输出
```python
import time
tic = time.time()
toc = time.time()
print(toc - tic)
2.221487193310176e-05
```

