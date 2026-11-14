

Coffee3 name mocha
size small

### 请在此自行判断，先写出您的代码

现在，将您的代码与下面的正确代码核对：

```
CoffeeShop = {
  "coffee1" : {
    "name" : "cappuccino",
    "size" : "xlarge"
  },
  "coffee2" : {
    "name" : "espresso",
    "size" : "large"
  },
  "coffee3" : {
    "name" : "mocha",
    "size" : "small"
  }
}
print(CoffeeShop)
```

输出 - {"coffee1" : { "name" : "cappuccino", "size" : "xlarge"}, "coffee2" : { "name" : "espresso", "size" : "large"}, "coffee3" : { "name" : "mocha", "size" : "small"}})

## 练习 – 使用“dict()”函数创建名为“CoffeeShop”的字典，其中包含键为“type”、“size”和“price”，对应的值为“cappuccino”、“large”和“5.99”。

### 请在此自行判断，先写出您的代码

现在，将您的代码与下面的正确代码核对：

```
CoffeeShop = dict(type = "cappuccino", size = "large", price = 5.99)
print(CoffeeShop)
```

输出 - {"type" : "cappuccino", "size" : "large", "price" : 5.99, "syrup" : "caramel"}

## Python 类与对象

Python 是众多面向对象编程语言之一。Python 中的每个实体都可以被视为对象，并拥有自己的方法和属性。在 Python 中，类用于构建这些对象，充当对象蓝图。

在 Python 中，可以使用关键字“class”以及预定义属性 (p) 来创建类，如下面的语法所示：

```
class ClassName:
    p = 2
```

## 内置函数

实际上，类和对象的创建比上面提供的基本语法复杂得多。这时会使用一个名为“__init__()”的内置函数来创建类。在创建类时，会随之执行这个内置类函数。“__init__()”函数主要用于为对象属性赋值以及执行创建对象所需的其他操作。让我们通过下面的示例来理解这个函数：

```
class Vehicle:
    def __init__(self, name, year):
        self.name = name
        self.year = year

v1 = Vehicle("BMW", 2018)

print(v1.name)
print(v1.year)
```

输出 - BMW 2018

## 对象方法

可以使用 Python 对象创建某些方法。这些方法可以被视为该对象的函数。例如，要创建一个打印有关车辆所有权评论并在对象 v1 上执行的函数，将使用以下命令：

```
class Vehicle:
    def __init__(self, name, year):
        self.name = name
        self.year = year

    def newfunc(ownership):
        print("I am a proud owner of " + self.name)
```

```
v1 = Vehicle("BMW", 2018)
v1.newfunc()
```

输出 - 我是 BMW 的自豪车主

## 引用参数

要引用类的最新实例，使用“self”参数。它允许您访问从类派生的变量。此参数可以根据需要命名，不必命名为“self”。需要牢记的重要一点是，为类定义的第一个参数将成为该类的引用参数，如下面的示例所示：

```
class Vehicle:
    def __init__(refobject, name, year):
        refobject.name = name
        refobject.year = year

    def newfunc(xyz):
        print("I am a proud owner of " + xyz.name)

v1 = Vehicle("BMW", 2018)
v1.newfunc()
```

输出 - 我是 BMW 的自豪车主

在某些情况下，您可能需要更改对象的属性。您可以通过声明对象的新属性轻松完成此操作，如下面的示例所示：

```
class Vehicle:
    def __init__(refobject, name, year):
        refobject.name = name
        refobject.year = year

    def newfunc(xyz):
        print("I am a proud owner of " + xyz.name)

v1 = Vehicle("BMW", 2018)
v1.year = 2019
```

您可以使用“del”关键字有选择地 **删除对象的属性**，如下面的示例所示：

```
class Vehicle:
    def __init__(refobject, name, year):
        refobject.name = name
        refobject.year = year

    def newfunc(xyz):
        print("I am a proud owner of " + xyz.name)

v1 = Vehicle("BMW", 2018)

del v1.year

print(v1.year)
```

输出 - ‘Vehicle’ 对象没有‘year’属性

您还可以使用“del”关键字完全 **删除对象**，如下面的示例所示：

```
class Vehicle:
    def __init__(refobject, name, year):
        refobject.name = name
        refobject.year = year

    def newfunc(xyz):
        print("I am a proud owner of " + xyz.name)

v1 = Vehicle("BMW", 2018)

del v1
```

输出 - NameError: 未定义 'v1'

## “pass” 语句

Python 类的定义必须包含值，否则会报错。但是，在某些情况下，类定义可能没有任何内容。在这种情况下，可以使用“pass”语句来避免报错。请参阅下面的示例：

```
class Vehicle:  # this class definition is empty
    pass       # used to avoid any errors
```

## 练习 – 创建一个名为“CoffeeShop”的类，属性为“type”和“size”，对应的值分别为“cappuccino”和“large”。

### 请在此自行判断，先写出您的代码

现在，将您的代码与下面的正确代码核对：

```
class CoffeeShop:
    def __init__(refobject, type, size):
        refobject.type = type
        refobject.size = size

c1 = CoffeeShop("cappuccino", "large")
print(c1.type)
print(c1.size)
```

输出 - cappuccino   large

**练习 – 创建一个名为“CoffeeShop”的类，属性为“type”和“size”，对应的值分别为“cappuccino”和“large”。** 创建一个新函数“funct1”，它将打印 “I would like to order a” 并在对象上执行。

### 请在此自行判断，先写出您的代码

现在，将您的代码与下面的正确代码核对：

```
class CoffeeShop:
    def __init__(refobject, type, size):
        refobject.type = type
        refobject.size = size

    def funct1(refobject):
        print("I would like to order a " + refobject.type)

c1 = CoffeeShop("cappuccino", "large")
c1.funct1()
```

输出 - 我要点一杯 cappuccino

## Python 运算符

在 Python 中，可以使用各种运算符对 Python 变量及其值执行操作。Python 运算符的不同组别如下：

算术运算符可用于数值，以执行基本数学计算。

| 名称 | 运算符 | 示例 |
|---|---|---|
| 加法 | + | P + Q |
| 减法 | - | P - Q |
| 乘法 | * | P * Q |
| 除法 | / | P / Q |
| 取模 | % | P % Q |
| 幂运算 | ** | P ** Q |
| 整除 | // | P // Q |

赋值运算符可用于将值赋给变量。

| 名称 | 示例 |
|---|---|
| = | P = 5 |
| += | P += 3 |
| -= | P -= 3 |
| *= | P *= 3 |
| /= | P /= 3 |
| %= | P %= 3 |
| //= | P //= 3 |
| **= | P **= 3 |
| &= | P &= 3 |
| |= | P |= 3 |
| ^= | P ^= 3 |
| >>= | P >>= 3 |
| <<= | P <<= 3 |

### 比较运算符

比较运算符可用于比较值。

| 名称 | 运算符 | 示例 |
|---|---|---|
| 相等 | == | P == Q |
| 不相等 | != | P != Q |
| 大于 | > | P > Q |
| 小于 | < | P < Q |
| 大于或等于 | >= | P >= Q |
| 小于或等于 | <= | P <= Q |

### 逻辑运算符

逻辑运算符可用于生成条件语句的组合。

| 运算符 | 用法 | 示例 |
|---|---|---|
| and | 如果两个语句均为真，则返回“真”。 | P < 5 and P < 10 |
| or | 如果其中一个语句为真，则返回“真”。 | P < 5 or P < 4 |
| not | 如果结果为真，则反转结果并返回“假”。 | not(P < 5 and P < 10) |

### 身份运算符

身份运算符可用于比较两个对象，以检查是否多次使用相同的内存位置创建了同一个对象。

