

```
s = str("http://hwdong.net")
print(type(s)) # str
location = s.find("hwdong")       # 通过 str 的 find() 方法查询是否有子串，
                                    # 并返回子串的位置
print(location)
alist = list(range(6))            # [0,1,2,3,4,5] 列表
blist = alist.copy()              # 通过 list 的 copy() 方法创建 alist 的副本列表
blist[2] = 20
print(alist)
print(blist)
```

```
<class 'str'>
7
[0, 1, 2, 3, 4, 5]
[0, 1, 20, 3, 4, 5]
```

正如你所见，可以使用**成员访问运算符 (`.`)** 通过类对象访问**类方法**，以便在此对象上执行某些操作（访问某些信息、修改对象或创建新对象）。例如，`s.find()` 查询 `s` 中是否存在等于字符串 "hwdong" 的子串，并返回子串的位置。而 `alist.copy()` 创建一个内容与 `alist` 相同的列表对象，并使 `blist` 指向新创建的列表对象。

类的方法是属于该类的函数，即类的内部函数，而不是之前的普通外部函数。

在 Python 中使用关键字 `class` 定义类。为了描述所有学生的共同属性，可以定义一个 `Student` 类。

```
class Student:
    def __init__(self, name, score):
        self.name = name
        self.score = score
        
    def print(self):
        print(self.name, ",", self.score)
```

类中的函数称为**方法**。通过类对象调用类的方法，可以在类对象上执行方法中的语句。因为一个类可以有很多对象，所以类的方法必须知道在哪个对象上执行方法的代码。因此，类的方法的第一个参数是 `self`，表示调用该类方法的对象。

以下代码定义了 `Student` 类的两个对象 `s1` 和 `s2`：并通过它们调用 `Student` 类的 `print()` 方法。`Student` 的 `print()` 方法调用内置函数 `print()` 输出 `self` 指向的对象的姓名和分数。

```
s1 = Student("LiPing", 67)
s2 = Student("WangQiang", 83)
s1.print()
s2.print()
```

```
LiPing, 67
Wang Qiang , 83
```

类中的 `__init__()` 方法是一个称为**构造函数**的特殊方法。定义类对象时，会自动调用此构造函数来初始化 `self` 指向的类对象。

上述 `Student` 类的构造函数使用参数 `name` 和 `score` 来初始化 `self` 指向的对象的两个属性 `self.name` 和 `self.score` 的过程。例如，执行语句 `Student("LiPing", 67)` 时，会自动调用此构造函数，并将 "LiPing" 和 67 作为参数 `name` 和 `score` 传递给构造函数以创建一个 `Student` 对象。

每个对象都有自己独立的实例属性，更改一个对象的实例属性不会影响其他对象的实例属性。除了实例属性外，还可以为类定义类属性，这是该类所有对象共享的属性。类属性是在类的方法外部定义的属性。

例如，修改后的 `Student` 类添加了一个类属性 `count`，表示从此类创建了多少个具体的类对象。其初始值为 0。每当创建一个类对象，其计数就会增加。

```
class Student:
    count = 0
    def __init__(self, name, score):
        self.name = name
        self.score = score
        Student.count += 1
        
    def print(self):
        print(self.name, ",", self.score)
```

通常，通过“类名.类属性”来查询或修改类属性，例如 `Student.count`，实例属性也可以通过“实例名.类属性”（包括 `self.类属性`）来查询。如下面的 `s1.count`。

```
print(Student.count)
s1 = Student("LiPing", 67)
print(s1.count)
s2 = Student("WangQiang", 83)
print(Student.count)
```

```
0
1
2
```

## 1.1.8 Matplotlib 入门

Matplotlib 是一个用于 2D 绘图的 Python 包，可用于绘制图形或显示图像。`matplotlib.pyplot` 为 matplotlib 面向对象的绘图库提供了一个方便的类 Matlab 接口函数。可以使用以下代码导入 `matplotlib.pyplot` 模块并将其命名为 `plt`，这样可以避免在代码中编写冗长的 `matplotlib.pyplot`。

```
import matplotlib.pyplot as plt
%matplotlib inline        
```

`%matplotlib inline` 使图形出现在 Jupyter Notebook 中。

`pyplot` 模块的 `plot()` 函数可以直接绘制 2D 数据，例如：

```
y = [i*0.5 for i in range(10)]
print(y)
plt.plot(y)            # 将 y 作为由纵轴坐标点组成的图形绘制
plt.show()             # 调用 plt.show() 显示图形
```

```
[0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5]
```

![](EPUB/media/file1.png)

虽然只给出了纵轴坐标数组 `y`，但 `plot()` 函数会默认自动生成从 0 开始的横轴坐标。当然，也可以传入 2 个数组来分别表示 x 和 y 坐标，例如：

```
x = [i*0.1 for i in range(10)]
y = [xi**2 for xi in x]
print(["{0:0.2f}".format(i) for i in x])
print(["{0:0.2f}".format(i) for i in y])
plt.plot(x, y)                # 绘制由 (x, y) 坐标点组成的图形
plt.show()                    # 调用 plt.show() 显示图形
```

```
['0.00', '0.10', '0.20', '0.30', '0.40', '0.50', '0.60', '0.70', '0.80', '0.90']
['0.00', '0.01', '0.04', '0.09', '0.16', '0.25', '0.36', '0.49', '0.64', '0.81']
```

![](EPUB/media/file2.png)

可以同时绘制多条曲线。

```
x = [i*0.2 for i in range(10)]
y = [xi**2 for xi in x]
y2 = [3*xi-1 for xi in x]

plt.plot(x, y)                         # 绘制由 (x, y) 坐标点组成的图形
plt.plot(x, y2)
plt.ylim(0, 5)
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.title('y=x^2 and y=3x-1')
plt.legend(['y=x^2', 'y=3x-1'])        # 指定图例标签的标签
plt.show()                             # 调用 plt.show() 显示图形
```

![](EPUB/media/file3.png "fig:")  

`pyplot` 模块的 `title()` 函数用于给图形添加标题，而 `legend()` 为每条绘制的曲线命名，`xlim()` 和 `ylim()` 用于限制 x 和 y 坐标的范围，`xlabel()` 和 `ylabel()` 用于给 x 轴和 y 轴添加标签。可以看到不同的图形会自动以不同颜色显示。

`plot()` 函数还可以接受一些参数来自定义绘制图形的样式，例如：

```
import math
x = [i*0.2 for i in range(50)]
y = [math.sin(xi) for xi in x]
y2 = [math.cos(xi) for xi in x]
y3 = [0.2*xi for xi in x]
plt.plot(x, y, 'r-')        
plt.plot(x, y2, 'bo')  
plt.plot(x, y3, 'g:')  
plt.legend(['sin(x)', 'cos(x)', '0.2x'])
plt.show()    
```

![](EPUB/media/file4.png)

其中，`'r-'` 中的 `r` 表示红色，`-` 表示短线，`'bo'` 中的 `b` 表示蓝色，`o` 表示点，`'g:'` 中的 `g` 表示绿色，`:` 表示虚线。

除了可以在 `pyplot` 模块中绘图的 `plot()` 函数外，还有用于绘制其他类型图形的函数，例如用于绘制散点图的 `scatter()`。例如：

```
import math
x = [i*0.2 for i in range(50)]
y = [math.sin(xi) for xi in x]
y2 = [math.cos(xi) for xi in x]
y3 = [0.2*xi for xi in x]
plt.scatter(x, y, c='r', s=6, alpha=0.2)        
plt.scatter(x, y2, c='g', s=18, alpha=0.9)  
plt.scatter(x, y3, c='b', s=3, alpha=0.4)  
plt.legend(['sin(x)', 'cos(x)', '0.2x'])
plt.show() 
```

![](EPUB/media/file5.png)

