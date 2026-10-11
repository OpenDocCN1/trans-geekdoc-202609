
变量名可以随时引用其他对象。变量名不是“一刀切”的，这与 C 等其他语言不同。

```
a = 3.14                        # a 是对象 3.14 的引用
b = a                           # b 和 a 引用同一个对象 3.14
a = "hwdong-net.github.io"      # a 引用新的字符串对象 "hwdong-net.github.io"
print(a)
print(b)
```

```
hwdong-net.github.io
    3.14
```

在这段代码中，变量名 `a` 首先引用对象 `3.14`，然后引用字符串 `"hwdong-net.github.io"`。如图 1-1 所示。

![](EPUB/media/file0.png "fig:")  

图 1-1 左图是执行 `b=a` 后的结果，右图是执行 `a= "hwdong-net.github.io"` 后的结果

#### 6. `input()` 函数

用于接受键盘输入，输入为字符串。`input()` 可以接受一个“提示字符串”。例如：

```
name = input()
print("name: ",name)
score = input("Please enter your score:")
print("Name: ",name,"Score: ",score)
type(score)
```

```
Wang An
    name: Wang An
    Please enter your score: 56.8
    Name: Wang An Score: 56.8

    str
```

`input()` 始终输入 `str` 类型对象，但可以使用类型转换将输入字符串转换为其他基本类型。

```
score = input("Please enter your score:")
print(type(score))
score = float(input("Please enter your score:"))
type(score)
```

```
Please enter your score: 70.5
    <class 'str'>
    Please enter your score: 80.5

    float
```

##### 1.1.3 运算

运算符可用于直接操作（对象）值。不同类型的值支持不同的操作。例如，算术运算 `+`、`-`、`*`、`/`、`%`、`//`、`**` 可用于数值类型（`int`、`float`）。其中，`%`、`//`、`**` 分别代表取余、整除和幂运算。例如：

```
x = 15
y = 2
print('x+y=',x+y)
print('x - y =', x - y)
print('x * y =', x*y)
print('x/y=',x/y)
print('x % y =',x%y)              # 求余数
print('x // y =',x//y)            # 整除
print('x ** y =',x**y)            # 幂运算
```

```
x + y = 17
    x - y = 13
    x * y = 30
    x/y = 7.5
    x % y = 1
    x // y = 7
    x ** y = 225
```

比较运算符 `==`、`!=`、`>`、`<`、`>=`、`<=` 用于比较两个值，分别代表等于、不等于、大于、小于、大于等于、小于等于，比较运算的结果是 `bool` 类型值（`True` 或 `False`）。例如：

```
x = 15
y = 2
print('x > y is',x>y)
print('x < y is',x<y)
print('x == y is',x==y)
print('x != y is',x!=y)
print('x >= y is',x>=y)
print('x <= y is',x<=y)
```

```
x > y is True
    x < y is False
    x == y is False
    x != y is True
    x >= y is True
    x <= y is False
```

逻辑运算符 `and`、`or` 和 `not` 分别代表**逻辑与**、**逻辑或**和**逻辑非**。在逻辑运算中，`True` 或非零或非空对象为真（`True`），而 `False` 或 `0` 或空对象为假（`False`）。运算符的运算规则如下：

*   对于对象 `x`，当 `x` 为真（`True` 或非零或非空）时，`not x` 为 `False`；当 `x` 为假（`False` 或 `0` 或空）时，`not x` 为 `True`（真）。

```
print(not 0,end = ' ')               # print() 默认输出后换行，
                                       # 向 end 参数传递空格 ' '，
                                       # 使其仅输出空格而不换行
print(not "",end = ' ')       
print(not False,end = ' ')
print(not 2,end = ' ')
print(not "hwdong")   
```

```
True True True False False
```

*   对于 2 个对象 `x`、`y`，当 `x` 为真时，`x or y` 的结果为 `x`；当 `x` 为假时，`x or y` 的结果为 `y`。

```
print(3 or 2,end = ' ')            # 因为 3 为真，3 or 2 的结果为 3
print(0 or 2,end = ' ')            # 因为 0 为假，0 or 2 的结果为 2
print(False or True, end = ' ')
print("" or 2)                     # 因为空字符串 "" 为假，"" or 2 的结果为 2
```

```
3 2 True 2
```

*   对于 2 个对象 `x`、`y`，当 `x` 为真时，`x and y` 的结果为 `y`；当 `x` 为假时，`x and y` 的结果为 `x`。

```
print(3 and 2, end = ' ')       # 因为 3 为真，3 and 2 的结果为 2
print(0 and 2, end = ' ')       # 因为 0 为假，0 and 2 的结果为 0
print("" and 2, end = ' ')      # 因为空字符串 "" 为假，
                                #   "" and 2 的结果为 ""，所以无输出
print(False and True)
```

```
2 0 False
```

Python 还有移位运算符（如按位与 `&`、按位或 `|`、异或 `^`、取反 `~`、左移 `<<`、右移 `>>`）和其他运算符。感兴趣的读者可自行查阅相关资料。

运算符 `=` 也可以与其他算术运算符和位运算符结合使用。例如：

`+=` `-=` `*=` `/=` `%=` `**=` `&=` `|=` `^=` `~=` `<<=` `>>=`

```
x = 3
print(id(x))
x+=2 # x = x+2
print(id(x))
```

`x+=2` 等价于 `x = x+2`，意味着将原 `x` 对象加上 `2` 得到一个对象，然后变量名 `x` 引用该加法运算的结果对象。因此，前后的变量名 `x` 代表 2 个不同的对象。

运算符 `in` 和 `not in` 用于判断一个值（对象）是否在容器对象中。例如：

```
print("h"in"hwdong")
print("h"not in"hwdong")
```

```
True
    False
```

#### 下标运算符 `[]`

可以通过给**下标运算符 `[]`** 传递下标来访问容器对象的元素，例如：

```
s = "hwdong"
print(s[0], s[1], s[2], s[3], s[4], s[5])
print(s[-6],s[-5],s[-4],s[-3],s[-2],s[-1])
```

下标从 0 开始，字符串对象 `s` 由一系列字符组成，第一个字符的下标为 0，第二个字符的下标为 1，……，长度为 `n` 的字符串下标为 `0, 1, 2, ..., n-1`。

下标也可以是负整数，其中 `-1` 指最后一个字符，`-n` 指第一个字符。

#### 字符串格式化

使用格式字符 `%` 将某些数据格式化为字符串，创建新字符串。例如：

```
s2 = '%s %s %f' % ("The score", "of LiPing is: ", 78.5)
print(s2)
```

格式字符串 `'%s %s %f'` 中的 `%s` 和 `%f` 分别表示后面三个输出项（`"The score"`、`"of LiPing is: "`、`78.5`）前两个为字符串，最后一个为实数。

使用字符串 `str` 的 `format()` 方法格式化字符串，即依次用 `format()` 方法中的数据替换字符串中的占位符 `{}`。例如：

```
print ("{} {} {}".format("The score", "of LiPing is: ", 78.5)) 
```

### 1.1.4 控制语句

程序通常“自上而下”顺序执行每条语句。有时需要根据某个条件是否满足，决定是否执行某些语句，或重复执行某些语句。Python 的条件语句和循环语句是根据条件决定如何执行某些语句的控制语句。

#### 1. `if` 语句

```
if expression:
      program block
```

表示如果 `if` 关键字后表达式的结果为 `True` 或非零，则执行其中的程序块，例如：

```
score = float(input())
if score>=60:
   print("Congratulations!")
   print("Passed the exam.")
```

```
60.5
    congratulations!
    passed the exam.
```

**注意**：

*   `if` 表达式后必须跟冒号：
*   在 Python 中，**对齐方式** 表示一组语句属于同一个程序块，例如 `if` 程序块中的 2 条语句

Python 中属于同一程序块的代码必须正确缩进，否则 Python 解释器会报错。例如：

```
score = float(input())
if score>=60:
   print("Congratulations!")
 print("Passed the exam.")
```

File "", line 4  

print("Passed the exam.")  

^
