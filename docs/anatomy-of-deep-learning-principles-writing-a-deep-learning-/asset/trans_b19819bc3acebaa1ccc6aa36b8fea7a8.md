

## 函数内部的语句与递归

函数内部可以包含调用其他函数的语句。函数也可以在内部调用自身，这种函数称为**递归函数**。下面是一个计算正整数 `n` 阶乘的函数：当 `n=1` 时直接返回 1，否则将 `n!` 转换为 `n*(n-1)!`。

```python
def fact(n):
    if n == 1:                 # 如果 n 等于 1，直接返回值 1
        return 1
    return n * fact(n - 1)     # 如果 n 大于 1，返回 n 与 fact(n-1) 的乘积

fact(4)                        # 输出: 24
```

```
24
```

当然，也可以使用循环来计算 `n! = 1 * 2 * 3 * ... * n`。

```python
def fact(n):
    ret = 1
    i = 1
    while i <= n:
        ret *= i
        i += 1
    return ret

fact(4)                        # 输出: 24
```

```
24
```

## math 包

许多数学函数库定义在 `math` 包中。要使用该包的函数，需要先导入它（`import`）。

```python
import math
print(math.sqrt(2))
```

```
1.4142135623730951
```

`import... as` 可以为导入的包指定别名，例如：

```python
import math as mt
print(mt.sqrt(2))
print(mt.pow(3.5, 2))
```

```
1.4142135623730951
12.25
```

再看一个例子：

```python
import math             

def circle(r):
    area = math.pi * r ** 2
    perimeter = 2 * math.pi * r
    return area, perimeter    

area, p = circle(2.5)   
print("The area and circumference of a circle with a radius of 2.5 are: %5.2f,%5.2f" % (area, p))
area, p = circle(3.5)
print("The area and circumference of a circle with a radius of 3.5 are: %5.2f,%5.2f" % (area, p))
```

```
The area and circumference of a circle with a radius of 2.5 are: 19.63,15.71
The area and circumference of a circle with a radius of 3.5 are: 38.48,21.99
```

函数可以返回多个值，实际上是作为元组对象返回的。

```python
ret = circle(2.5)  # (area, perimeter) 
print(type(ret))
area, p = ret               
print(area, p)
```

```
<class 'tuple'>
19.634954084936208 15.707963267948966
```

## 全局变量与局部变量

定义在函数外部的变量称为**全局变量**，定义在函数内部的变量称为**局部变量**。全局变量属于全局命名空间，函数的局部变量属于函数的局部命名空间。不同命名空间中可以存在同名变量而互不冲突。函数不能直接访问外部全局变量，例如：

```python
global_x = 6

def f():
    x = 3
    global_x = 5
    print(x, global_x)

f()    
print(global_x)
```

```
3 5
6
```

函数内部的语句 `global_x = 5` 并未修改外部全局变量 `global_x`，而是定义了一个指向对象 5 的局部变量 `global_x`，这对外部全局变量 `global_x` 没有影响。因此，函数 `f()` 执行结束后，内部局部变量被销毁，全局变量 `global_x` 仍为 6。

如果想在函数内部访问并修改全局变量，需要使用关键字 `global` 在函数内部声明该变量为全局变量，例如：

```python
global_x = 6

def f():
    global global_x
    x = 3
    global_x = 5
    print(x, global_x)

f()    
print(global_x)
```

```
3 5
5
```

函数内部的 `global_x` 被声明为外部全局变量 `global_x`。修改它即修改外部全局变量 `global_x`。因此，函数 `f()` 执行后的输出语句打印的是 5 而不是 6。

修改全局变量的另一种方式是将全局变量作为参数传递给函数，但该全局变量必须是非基本类型的对象。因为当基本类型对象作为参数传递时，函数形式参数引用的是实际参数引用对象的副本，而非同一对象。例如：

```python
global_x = 6
a = [1, 2, 3]

def f(y, z):    
    x = 3
    y = 5
    z[0] = 10
    print(y)
    print(z)
    
f(global_x, a)    
print(global_x)
print(a)
```

```
5
[10, 2, 3]
6
[10, 2, 3]
```

如图 1-4 所示，当 `global_x` 传递给 `y` 时，`y` 引用的是 `global_x` 指向对象的副本，而非同一对象；当 `a` 传递给 `z` 时，`z` 与 `a` 引用的是同一对象。

![](EPUB/media/file206.png)

**图 1-4** 函数参数传递时，基本类型参数传递副本对象而非引用

## 匿名函数 / Lambda 函数

对于简短的函数，可以使用关键字 `lambda` 定义一个无函数名的函数，例如：

```python
lambda arguments: expression
```

该函数没有函数名，但有参数 `arguments`。

```python
lambda x: x ** 2
```

通常使用 `=` 运算符给这个 lambda 函数起一个名字，例如：

```python
double = lambda x: x ** 2
```

通过 `double` 引用调用匿名函数：

```python
double(3.5)
```

```
12.25
```

## 嵌套函数与闭包

定义在另一个函数内部的函数称为**嵌套函数**。

```python
def print_msg(msg):      # 外部函数
    def printer():       # 嵌套函数
        print(msg)
    return printer       # 返回嵌套函数

another = print_msg("Hello")
another()
```

```
hello
```

嵌套函数可以访问外层作用域的变量，例如 `printer()` 函数可以访问 `print_msg()` 函数的局部变量（包括参数 `msg`）。

```python
def make_pow(n):
    def pow(x):
        return x ** n  # pow() 可以访问 make_pow() 的变量（即 n）
    return pow
```

`make_pow()` 返回的函数对象 `pow()` 可以访问 `make_pow()` 的变量（即 `n`）。

```python
pow3 = make_pow(3)    # 给返回的嵌套函数 pow() 起名 pow3
                    
pow5 = make_pow(5)    # 给返回的嵌套函数 pow() 起名 pow5

print(pow3(9))
print(pow5(3))
print(pow5(pow3(2)))
```

```
729
243
32768
```

## yield 与生成器

可以通过关键字 `yield` 定义生成器函数，生成器是一个返回迭代器（对象）的函数。

```python
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1
```

生成器函数 `infinite_sequence()` 通过 `yield` 返回一个可迭代对象：

```python
iterator = infinite_sequence()
print(next(iterator))
print(next(iterator))
```

```
0
1
```

使用变量名 `iterator` 引用生成器返回的可迭代对象，可以使用 `next` 函数获取迭代对象的一个值。也可以使用 `for` 遍历该可迭代对象：

```python
for i in infinite_sequence():
    print(i, end=" ")
    if i > 5:
        break
```

```
0 1 2 3 4 5 6
```

# 1.1.7 类与对象

**类**（class）是对抽象概念的描述，它描述了属于同一概念的所有对象的共同属性，这些属性包括：数据属性和方法属性。数据属性描述这类对象的状态，方法属性描述这类对象具有什么功能。类是一种数据类型，它刻画了该类型所有可能值的共同特性，例如 `int` 类型刻画了所有整数的特征。

前面提到的 `str`、`list` 等都是类。通常可以通过类名创建类对象，类对象是一个具体的对象。例如：

