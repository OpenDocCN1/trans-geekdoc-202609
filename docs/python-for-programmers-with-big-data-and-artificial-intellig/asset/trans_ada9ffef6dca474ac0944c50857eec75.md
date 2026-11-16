

7 @dataclass
8 class Card:
```

可选地，@dataclass 装饰器可以指定包含参数的括号，这些参数帮助数据类确定要包含哪些自动生成的方法。例如，装饰器 @dataclass (order=True) 会导致数据类为 <、<=、> 和 >= 自动生成重载的比较运算符方法。例如，如果您需要对数据类对象进行排序，这可能很有用。

## 变量注解：类属性

与常规类不同，数据类在类内部但类方法之外同时声明类属性和数据属性。在常规类中，只有类属性以这种方式声明，而数据属性通常在 __init__ 中创建。数据类需要额外的信息（或提示）来区分类属性和数据属性，这也会影响自动生成方法的实现细节。

第 9–11 行定义并初始化了类属性 FACES 和 SUITS：

点击此处查看代码图像

```
9 FACES: ClassVar[List[str]] = ['Ace', '2', '3', '4', '5', '6', '7',
10 '8', '9', '10', 'Jack', 'Queen', 'King']
11 SUITS: ClassVar[List[str]] = ['Hearts', 'Diamonds', 'Clubs', 'Spades'
12
```

在第 9 行和第 11 行中，注释符号

```
: ClassVar[List[str]]
```

是一个变量注解 3, 4（有时称为类型提示），指定 FACES 是一个类属性（ClassVar），指向字符串列表（List[str]）。SUITS 也是一个类属性，指向字符串列表。

3. https://www.python.org/dev/peps/pep-0526/.

4. 变量注解是最近的语言特性，对常规类来说是可选的。您在大多数旧版 Python 代码中看不到它们。

类变量在其定义中初始化，特定于类，而不是类的单个对象。然而，方法 __init__、__repr__ 和 __eq__ 是用于类对象的。当数据类生成这些方法时，它会检查所有变量注解，并仅将数据属性包含在方法实现中。

## 变量注解：数据属性

通常，我们通过 self.attribute_name = value 形式的赋值，在类的 __init__ 方法（或由 __init__ 调用的方法）中创建对象的数据属性。由于数据类会自动生成其 __init__ 方法，因此我们需要另一种方式来在数据类定义中指定数据属性。我们不能简单地将它们的名称放在类中，这会生成 NameError，如下所示：

点击此处查看代码图像

```
In [1]: from dataclasses import dataclass

In [2]: @dataclass
    ...: class Demo:
    ...:     x # attempting to create a data attribute x
    ...:
--------------------------------------------------------------------------------
NameError                                Traceback (most recent call last)

<ipython-input-2-79ffe37b1ba2> in <module>()
----> 1 @dataclass
      2 class Demo:
      3     x # attempting to create a data attribute x
      4

<ipython-input-2-79ffe37b1ba2> in Demo()
      1 @dataclass
      2 class Demo:
----> 3     x # attempting to create a data attribute x
      4

NameError: name 'x' is not defined
```

与类属性一样，每个数据属性都必须使用变量注解来声明。第 13–14 行定义了数据属性 face 和 suit。变量注解 ": str" 表示每个都应该引用字符串对象：

```
13 face: str
14 suit: str
```

## 定义属性和其他方法

数据类也是类，因此它们可以包含属性和方法并参与类层次结构。对于这个 Card 数据类，我们定义了与本章前面原始 Card 类中相同的只读 image_name 属性和自定义特殊方法 __str__ 和 __format__：

点击此处查看代码图像

```
@property
def image_name(self):
    """Return the Card's image file name."""
    return str(self).replace(', ', '_') + '.png'

def __str__(self):
    """Return string representation for str()."""
    return f'{self.face} of {self.suit}'

def __format__(self, format):
    """Return formatted string representation."""
    return f'{str(self):{format}}'
```

## 变量注解说明

您可以使用内置类型名称（如 str、int 和 float）、类类型或 typing 模块定义的类型（如前面所示的 ClassVar 和 List）来指定变量注解。即使有类型注解，Python 仍然是一种动态类型语言。因此，类型注解在执行时不会被强制执行。因此，尽管 Card 的 face 旨在是字符串，但您可以将任何类型的对象赋值给 face。

## 10.13.2 使用 Card 数据类

让我们演示新的 Card 数据类。首先，创建一个 Card：

点击此处查看代码图像

```
In [1]: from carddataclass import Card

In [2]: c1 = Card(Card.FACES[0], Card.SUITS[3])
```

接下来，让我们使用 Card 的自动生成的 __repr__ 方法来显示 Card：

点击此处查看代码图像

```
In [3]: c1
Out[3]: Card(face='Ace', suit='Spades')
```

我们自定义的 __str__ 方法（当 print 将 Card 对象传递给它时调用）返回形式为 'face of suit' 的字符串：

```
In [4]: print(c1)
Ace of Spades
```

让我们访问我们数据类的属性和只读属性：

点击此处查看代码图像

```
In [5]: c1.face
Out[5]: 'Ace'
In [6]: c1.suit
Out[6]: 'Spades'
In [7]: c1.image_name
Out[7]: 'Ace_of_Spades.png'
```

接下来，让我们演示 Card 对象可以通过自动生成的 == 运算符和继承的 != 运算符进行比较。首先，创建两个额外的 Card 对象——一个与第一个相同，另一个不同：

点击此处查看代码图像

```
In [8]: c2 = Card(Card.FACES[0], Card.SUITS[3])
In [9]: c2
Out[9]: Card(face='Ace', suit='Spades')
In [10]: c3 = Card(Card.FACES[0], Card.SUITS[0])
In [11]: c3
Out[11]: Card(face='Ace', suit='Hearts')
```

现在，使用 == 和 != 比较对象：

```
In [12]: c1 == c2
Out[12]: True
In [13]: c1 == c3
Out[13]: False
In [14]: c1 != c3
Out[14]: True
```

我们的 Card 数据类与本章前面开发的 Card 类可以互换。为了演示这一点，我们创建了 deck2.py 文件，其中包含本章前面的 DeckOfCards 类的副本，并将 Card 数据类导入到该文件中。以下代码片段导入 DeckOfCards 类，创建该类的一个对象并打印它。请回顾，print 隐式调用 DeckOfCards 的 __str__ 方法，该方法将每个 Card 格式化为 19 个字符的字段，从而导致对每个 Card 的 __format__ 方法的调用。请从左到右阅读每一行，以确认所有 Card 都按每种花色（红桃、方块、梅花和黑桃）的顺序显示：

点击此处查看代码图像

```
In [15]: from deck2 import DeckOfCards # uses Card data class
In [16]: deck_of_cards = DeckOfCards()
In [17]: print(deck_of_cards)
```

| 红桃 A | 红桃 2 | 红桃 3 | 红桃 4 |
|---|---|---|---|
| 红桃 5 | 红桃 6 | 红桃 7 | 红桃 8 |
| 红桃 9 | 红桃 10 | 红桃 J | 红桃 Q |
| 红桃 K | 方块 A | 方块 2 | 方块 3 |
| 方块 4 | 方块 5 | 方块 6 | 方块 7 |
| 方块 8 | 方块 9 | 方块 10 | 方块 J |
| 方块 Q | 方块 K | 梅花 A | 梅花 2 |
| 梅花 3 | 梅花 4 | 梅花 5 | 梅花 6 |
| 梅花 7 | 梅花 8 | 梅花 9 | 梅花 10 |
| 梅花 J | 梅花 Q | 梅花 K | 黑桃 A |
| 黑桃 2 | 黑桃 3 | 黑桃 4 | 黑桃 5 |
| 黑桃 6 | 黑桃 7 | 黑桃 8 | 黑桃 9 |
| 黑桃 10 | 黑桃 J | 黑桃 Q | 黑桃 K |

## 10.13.3 数据相对于命名元组的优势

数据相对于命名元组⁵ 提供多项优势：

⁵ https://www.python.org/dev/peps/pep-0526/.

- 尽管每个命名元组在技术上代表不同的类型，但命名元组是一个元组，所有元组都可以相互比较。因此，如果具有相同数量的成员和相同的成员值，不同命名元组类型的对象可能比较为相等。比较不同数据类的对象始终返回 False，将数据类对象与元组对象比较也是如此。

- 如果您有解包元组的代码，向该元组添加更多成员将破坏解包代码。数据类对象不能被解包。因此，您可以向数据类添加更多数据属性，而不会破坏现有代码。

- 数据类可以是继承层次结构中的基类或子类。

## 10.13.4 数据相对于传统类的优势

数据还相对于本章前面您看到的传统 Python 类提供各种优势：

- 数据类会自动生成 `__init__`、`__repr__` 和 `__eq__`，节省您的时间。

- 数据类可以自动生成重载 `<`、`<=`、`>` 和 `>=` 比较运算符的特殊方法。

- 当您更改数据类中定义的数据属性，然后在脚本或交互式会话中使用它时，自动生成的代码会自动更新。因此，您需要维护和调试的代码更少。

- 类属性和数据属性所需的变量注解使您能够利用静态代码分析工具。因此，您可能能够在错误发生在执行时间之前消除其他错误。

