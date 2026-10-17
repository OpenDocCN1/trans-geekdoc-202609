
## 继承

它在本质上具有传递性，这意味着如果类 `B` 继承自类 `A`，那么 `B` 的所有子类都将自动继承 `A`。如果没有继承，任何面向对象的语言都不值得关注或使用。继承发明于 1969 年的 Simula 语言。通常，继承是自现有类派生新类的机制。通过这种方式，我们得到了类的层次结构。在大多数基于类的面向对象语言中，通过继承创建的对象（“子对象”）会继承父对象的所有属性和行为——尽管在某些编程语言中存在例外。继承允许程序员在现有类的基础上创建类，这使得通过继承创建的类可以继承父类的属性和方法。这意味着继承支持代码复用性。子类继承的方法或广义地说继承的软件被认为已在子类中使用。通过继承的对象或类之间的关系形成了一个有向图。类所继承的类被称为父类或超类（`super`）。继承超类的类被称为子类或子类（`child`）。超类是祖先。

```python
# 一个演示继承的 Python 程序
# 基类或超类（通常，object 是所有类的祖先）
# 在 Python 3.x 中 "class Person" 等同于 "class Person(object)"
class Person(object):
    # 构造函数
    def __init__(self, name):
        self.name = name
    # 获取名称
    def getName(self):
        return self.name
    # 检查此人是否是员工
    def isEmployee(self):
        return False

# 继承的子类（注意括号中的 Person）
class Employee(Person):
    # 这里返回 true
    def isEmployee(self):
        return True

# 驱动代码
emp = Person("Tech1") # Person 的对象
print(emp.getName(), emp.isEmployee())
emp = Employee("Tech2") # Employee 的对象
print(emp.getName(), emp.isEmployee())

# 输出:
# Tech1 False
# Tech2 True
```

### 继承的不同形式

继承是面向对象范式的一个重要方面。继承为程序提供了代码复用，因为我们可以使用现有类来创建新类，而不是从头开始。在继承中，子类继承属性并访问父类中定义的所有数据成员和函数。子类还可以为父类的函数提供其特定的实现。在教程的这一节中，我们将详细讨论继承。在 Python 中，派生类只需通过在派生类名后的括号中提到基类即可继承基类。考虑以下将基类继承到派生类中的语法。

#### 单继承

当一个子类只继承自一个父类时，它被称为单继承。我们在上面看到过一个例子。

#### 多重继承

当一个子类继承自多个类时，它被称为多重继承。Python 提供了继承多个基类的灵活性。执行多重继承的语法所示。

```python
class Base1:
    pass
class Base2:
    pass
class BaseN:
    pass
class Derived(Base1, Base2, BaseN):
    pass

class Calculation1:
    def Summation(self, a, b):
        return a + b
class Calculation2:
    def Multiplication(self, a, b):
        return a * b
class Derived(Calculation1, Calculation2):
    def Divide(self, a, b):
        return a / b

d = Derived()
print(d.Summation(10, 20))
print(d.Multiplication(10, 20))
print(d.Divide(10, 20))

# 输出:
# 30
# 20
# 0.5
```

#### 多级继承

当我们存在子类和孙类关系时，Python 可以像其他面向对象语言一样实现多级继承。当一个派生类继承另一个派生类时，就实现了多级继承。多级继承实现的层数没有限制。

```python
class class1:
    pass
class class2(class1):
    pass
class class3(class2):
    pass

class Animal:
    def speak(self):
        print("Animal Speaking")
 # 子类 Dog 继承基类 Animal
class Dog(Animal):
    def bark(self):
        print("dog barking")
 # 子类 DogChild 另一个子类 Dog
class DogChild(Dog):
    def eat(self):
        print("Eating bread...")

d = DogChild()
d.bark()
d.speak()
d.eat()

# 输出:
# dog barking
# Animal Speaking
# Eating bread...
```

#### 层次结构继承

从单个基类创建了多个派生类。

#### 混合继承

这种形式结合了多种形式的继承。基本上，它是多种类型继承的混合。

### 我可以重写我的基类吗？

我们可以在子类中为父类方法提供某些特定的实现。当父类方法在子类中带有某些特定实现定义时，该概念被称为方法重写（method overriding）。当子类需要不同的父方法定义时，我们可能需要执行方法重写。考虑以下在 Python 中执行方法重写的示例。

```python
class Animal:
    def speak(self):
        print("speaking")
class Dog(Animal):
    def speak(self):
        print("Barking")

d = Dog()
d.speak()

# 输出:
# Barking
```

在上面的示例中，该方法在两个类中都定义了。发生这种情况时，使用了派生类的方法。通常在重写基方法时，应该扩展定义而不是替换它。更好的选择是使用内置的 `super()`。因此，`super().__init__(3)` 等于 `Parent.__init__(self,3)` 且更优。内置函数 `isinstance()` 和 `issubclass()` 用于检查继承。如果对象是类或其其他派生类的实例，则 `isinstance()` 返回 True。Python 中的每个类都继承自类 `object`。

```python
>>> isinstance(t, Triangle)
True
>>> isinstance(t, Polygon)
True
>>> isinstance(t, int)
False
>>> isinstance(t, object)
True
```

同样，`issubclass()` 用于检查类继承。

```python
>>> issubclass(Polygon, Triangle)
False
>>> issubclass(Triangle, Polygon)
True
>>> issubclass(bool, int)
True
```

#### `issubclass(sub, sup)` 方法

`issubclass(sub, sup)` 方法用于检查指定类之间的关系。如果第一个类是第二个类的子类，则返回 true，否则返回 false。考虑以下示例。

```python
class Calculation1:
    def Summation(self, a, b):
        return a + b
class Calculation2:
    def Multiplication(self, a, b):
        return a * b
class Derived(Calculation1, Calculation2):
    def Divide(self, a, b):
        return a / b

d = Derived()
print(issubclass(Derived, Calculation2))
print(issubclass(Calculation1, Calculation2))

# 输出:
# True
# False
```

# Python 生成器使用指南

生成器是一种可以随时暂停和恢复的函数，它们返回一个可以迭代的对象。与列表不同，生成器是懒惰的（lazy），因此它们一次产生一个项目，并且只在需要时才产生。所以，在处理大型数据集时，它们的内存效率高得多。

## 生成器是如何工作的？

在 Python 中构建一个迭代器有大量的开销；我们必须实现一个带有 `__iter__()` 和 `__next__()` 方法的类，跟踪内部状态，并在没有值可返回时抛出 `StopIteration` 等。这既冗长又不符合直觉。生成器的出现解决了了这种情况。Python 生成器是创建迭代器的简单方法。上述所有开销都由 Python 生成器自动处理。简单来说，生成器是一个返回对象（迭代器）的函数，我们可以对其进行迭代（一次一个值）。

## 为什么在 Python 中使用生成器

有几个原因使得生成器成为非常有吸引力的实现方式。

### 易于实现

与迭代器类相比，生成器可以用更清晰简洁的方式实现。以下是一个使用迭代器类实现 2 的幂序列的示例。

### 内存高效

返回序列的普通函数会在返回结果之前在内存中创建整个序列。如果序列中的项目非常多，这样做就太浪费了。此类序列的生成器实现是内存友好的，并且是首选，因为它一次只产生一个项目。

### 表示无限流

生成器是表示无限数据流的极媒介。无限流无法存储在内存中，由于生成器一次产生一个项目，因此它可以表示无限数据流。

### 生成器的管道操作

生成器可以用于操作管道（piping）。一个示例可以很好地说明这一点。假设我们有一个来自 fast 的日志文件。该日志文件有一列（第 4 列）记录每年的销售数量。字符串和不可用的数字标记为 'N/A'。该文件的生成器如下。

## 如何在 Python 中创建生成器？

在 Python 中创建生成器要简单得多。它就像定义一个使用 `yield` 代替 `return` 的普通函数一样简单。`yield` 会暂停函数并保存所有状态，稍后从那里继续。

## 生成器函数与普通函数的区别

以下是生成器函数与普通函数的区别：

- 生成器函数包含一个或多个 `yield` 语句。
- 被调用时，它返回一个对象（迭代器），而不是立即开始执行。
- `__iter__()` 和 `__next__()` 方法会被自动实现。因此我们可以使用 `next()` 迭代项目。
- 一旦函数执行 `yield`，函数就会暂停，并将控制权转移给调用者。
- 在连续调用之间，局部变量及其状态会被记住。
- 最后，当函数终止时，随后的调用将自动抛出 `StopIteration`。

## Python 生成器表达式

可以使用生成器表达式随地创建简单的生成器。它让生成器像 Python 中列表推导式的 lambda 函数生成器表达式一样简单。列表推导式和生成器表达式的主要区别在于，列表推导式产生整个列表，而生成器一次产生一个项目。它们是“懒惰”的，只在需要时产生项目。因此，生成器表达式比列表高效得多。

## “Yield” 和 “Return” 的区别？

`yield` 暂停函数的执行并将值传回调用者，但返回一个足够的函数以便从离开的地方继续。当恢复时，函数将从上一次 `yield` 之后立即继续执行。这允许其代码随着时间产生的一系列值，而不是像列表那样一次计算并发送它们。`return` 将一个特定值发送给其调用者。`yield` 可以产生一个值的序列。当我们想要迭代序列但不想将整个序列存储在内存中时，我们应该使用 `yield`。`yield` 用于 Python 生成器。生成器函数的定义方式类似于普通函数，但每当它需要生成值时，它使用 `yield` 关键字而不是 `return`。如果 `def` 的体包含 `yield`，该函数会自动变成生成器函数。

## 是否有特定的时刻我应该使用生成器？

生成器为你提供了懒惰求值。当你需要显式使用 'for' 进行迭代，或通过将其传递给任何迭代函数或结构进行隐式迭代时，你应该使用它们。你可以将生成器理解为返回多个项目（就像它们返回列表一样），但不是一次性返回，而是一个接一个地返回，生成器函数会暂停直到请求下一个项目。当你想要处理结果但不想为内存分配所有结果时，你应该使用生成器。另一个时间是用迭代替换调用。生成器方法的方法是：函数（现在是生成器）对调用者一无所知，并且在它想要的任何时候只需 `yield`。调用者不再编写单独的调用，而是在生成器周围的小循环中完成所有的报告。

# 什么是正则表达式？

正则表达式是一种特殊的字符序列，可以帮助你匹配或查找其他字符串或字符串集，它使用存储在模式中的特殊语法。正则表达式在 UNIX 世界中被广泛使用。Python 中的 `re` 模块对类似 Perl 的正则表达式提供了完全支持。如果在编译或使用正则表达式时发生错误，`re` 模块会抛出 `re.error`。正则表达式用于识别在给定的字符序列（字符串）中是否存在某种模式。它们有助于处理文本数据，而这通常是涉及文本挖掘的数据科学项目的先决条件。

你一定遇到过正则表达式的一些应用：它们被用于服务器端验证注册期间的电子邮件地址格式或密码格式，用于解析文本数据文件以查找、替换或删除某些字符串等。

在 Python 中，正则表达式由 `re` 模块支持。这意味着如果你想在 Python 脚本中使用它们，就必须通过 `import` 导入该模块：我们将介绍两个用于处理正则表达式的重要函数。但在那先说一点：有许多字符在用作正则表达式时会具有特殊含义。为了避免在处理正则表达式时产生任何混淆，我们将使用**原始字符串（Raw Strings）**。

## 基础模式

你可以使用字符在 Python 中轻松地创建基础模式。普通字符是最简单的正则表达式。它们本身在表达式中没有特殊含义。例如 `'A'`、`'X'`、`'5'`。普通字符可以用于匹配：

```python
pattern = "C"
sequence = "C"
if match(pattern, sequence):
    print("match!")
else:
    print("Not a match!")
```

如果文本匹配模式，`match()` 函数将返回一个匹配对象；否则它返回 `None`。`re` 模块包含其他函数，你稍后会学习其中一些。现在，让我们关注字符！你注意到模式的开头了吗？这被称为原始字面量（raw literal）。它改变了字符串的解释方式。此类字面量按照它们出现的形式进行存储。例如，当 `\` 前缀的不是 `r` 时，它只是一个反斜杠，而不是被解释为转义字符。你会在特殊字符上看到这意味着什么。有时语法涉及反斜杠转义字符，以防止这些字符被解释为转义，你可以使用 `r` 前缀。在这个示例中你实际上不需要它，但为了保持一致，使用它是一个良好的习惯。

如果你要在序列中查找长模式，重复将变得繁琐。幸运的是，`re` 模块使用以下特殊字符处理重复：

- `+` 检查左侧的一个或多个字符。
- `*` 检查左侧的零个或多个字符。
- `?` 检查左侧恰好为零或一个字符。

如果你想检查序列重复的精确次数怎么办？例如，在应用程序中检查手机号码的有效。`re` 模块使用以下表达式完全处理这种情况：

- `{x}` 严格重复 `x` 次。
- `{x,}` 至少重复 `x` 次。
- `{x,y}` 重复至少 `x` 次但多于 `y` 次。

## 分组

使用正则表达式允许你捕获匹配的一部分。当你验证电子邮件地址并想要单独捕获名称时，这就是正则表达式的分组功能。它允许你捕获匹配文本的部分。被 `match()` 限定的正则表达式部分称为组（groups）。`groups()` 不改变匹配，而是对匹配内部进行分组。不带任何参数的 `group()` 仍然是整个匹配文本。

```python
#!/usr/bin/python
import re
line = "Cats are smarter than dogs"
matchObj = re.match(r'(.*) are (.*?) .*', line, re.M|re.I)
if matchObj:
    print("matchObj.group() : ", matchObj.group())
    print("matchObj.group(1) : ", matchObj.group(1))
    print("matchObj.group(2) : ", matchObj.group(2))
else:
    print("No match!!")
```

当执行上述代码时，它产生以下结果：

- `matchObj.group()` : Cats are smarter than dogs
- `matchObj.group(1)` : Cats
- `matchObj.group(2)` : smarter

### Search

`search` 函数在字符串中搜索模式，并带有可选标志。语法：`re.search(pattern, string, flags=0)`。以下是参数描述：

- `pattern`: 这是要匹配的正则表达式。
- `string`: 这是要搜索的字符串。
- `flags`: 你可以使用按位或 (`|`) 指定不同的标志。这些是修饰符，列在下表中。

`re.search` 函数在成功时返回匹配对象，失败时返回 `None`。使用匹配对象的 `group(num)` 或 `groups()` 函数获取匹配的表达式。

- `group(num=0)`: 此方法返回整个匹配（或特定组 `num`）。
- `groups()`: 此方法以元组形式返回所有匹配子组（如果没有则返回空元组）。
