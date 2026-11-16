
In [2]: my_object = PrivateClass()

Snippet [3] 显示我们可以直接访问 `public_data` 属性：

点击此处查看代码图像

```
In [3]: my_object.public_data
Out[3]: 'public'
```

但是，当我们在 snippet [4] 中尝试直接访问 `__private_data` 时，我们会收到一个 `AttributeError`，指出该类没有该名称的属性：

点击此处查看代码图像

```
In [4]: my_object.__private_data
------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-4-d896bdf2053> in <module>()
----> 1 my_object.__private_data

AttributeError: 'PrivateClass' object has no attribute '__private_data'
```

这是因为 Python 更改了属性的名称。不幸的是，属性 `__private_data` 仍然可以间接访问。

## 10.6 案例研究：洗牌和发牌模拟

我们的下一个示例介绍了两个自定义类，您可以使用它们来洗牌和发牌一副牌。类 `Card` 表示一张扑克牌，具有一个面值（`'Ace'`、`'2'`、`'3'`、…、`'Jack'`、`'Queen'`、`'King'`）和一个花色（`'Hearts'`、`'Diamonds'`、`'Clubs'`、`'Spades'`）。类 `DeckOfCards` 表示一副由 `Card` 对象列表组成的 52 张扑克牌。首先，我们将在 IPython 会话中试驾这些类，以演示洗牌和发牌功能以及以文本形式显示卡牌。然后，我们将查看类定义。最后，我们将使用另一个 IPython 会话使用 Matplotlib 将 52 张卡牌显示为图像。我们将向您展示在哪里可以获得外观美观的公共领域卡牌图像。

### 10.6.1 试驾类 `Card` 和 `DeckOfCards`

在查看类 `Card` 和 `DeckOfCards` 之前，让我们使用 IPython 会话来演示它们的功能。

#### 创建、洗牌和发牌

首先，从 `deck.py` 导入类 `DeckOfCards` 并创建该类的一个对象：

```
In [1]: from deck import DeckOfCards

In [2]: deck_of_cards = DeckOfCards()
```

DeckOfCards 方法 `__init__` 按花色顺序以及每种花色内按面值顺序创建 52 个 `Card` 对象。您可以通过打印 `deck_of_cards` 对象来查看此情况，这将调用 DeckOfCards 类的 `__str__` 方法来获取牌组的字符串表示。按从左到右的顺序阅读每一行，以确认所有卡牌均按每种花色（Hearts、Diamonds、Clubs 和 Spades）的顺序显示：

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

接下来，让我们洗牌并再次打印 `deck_of_cards` 对象。我们未指定用于可复现性的种子，因此每次洗牌您都会得到不同的结果：

| 红桃 K | 梅花 Q | 方块 Q | 梅花 10 |
|---|---|---|---|
| 红桃 5 | 红桃 7 | 红桃 4 | 红桃 2 |
| 梅花 5 | 方块 8 | 红桃 3 | 红桃 10 |
| 黑桃 8 | 黑桃 5 | 黑桃 Q | 梅花 A |
| 梅花 8 | 黑桃 7 | 方块 J | 黑桃 10 |
| 方块 4 | 红桃 8 | 黑桃 6 | 黑桃 K |
| 红桃 9 | 黑桃 4 | 梅花 6 | 梅花 K |
| 黑桃 3 | 方块 9 | 梅花 3 | 黑桃 A |
| 红桃 A | 方块 3 | 方块 2 | 红桃 6 |
| 方块 K | 黑桃 J | 梅花 J | 黑桃 2 |
| 方块 5 | 梅花 4 | 红桃 Q | 梅花 9 |
| 方块 10 | 梅花 2 | 方块 A | 方块 7 |
| 黑桃 9 | 红桃 J | 方块 6 | 梅花 7 |

#### 发牌

我们可以通过调用方法 `deal_card` 一次发一张 `Card`。IPython 调用返回的 `Card` 对象的 `__repr__` 方法，以生成在 `Out[]` 提示中显示的字符串输出：

```python
In [6]: deck_of_cards.deal_card()
Out[6]: Card(face='King', suit='Hearts')
```

#### 类 `Card` 的其他功能

为了演示类 `Card` 的 `__str__` 方法，让我们再发一张牌，并将其传递给内置 `str` 函数：

```python
In [7]: card = deck_of_cards.deal_card()

In [8]: str(card)
Out[8]: 'Queen of Clubs'
```

每张 `Card` 都有一个对应的图像文件名，您可以通过 `image_name` 只读属性获取。我们将在不久的将来使用此功能来将 `Cards` 显示为图像：

```python
In [9]: card.image_name
Out[9]: 'Queen_of_Clubs.png'
```

### 10.6.2 类 `Card`——介绍类属性

每个 `Card` 对象包含三个字符串属性，分别表示该 `Card` 的 `face`、`suit` 和 `image_name`（包含相应图像的文件名）。正如您在上一节的 IPython 会话中所见，类 `Card` 还提供用于初始化 `Card` 以及获取各种字符串表示的方法。

#### 类属性 `FACES` 和 `SUITS`

类的每个对象都有类的数据属性的副本。例如，每个 `Account` 对象都有自己的 `name` 和 `balance`。有时，属性应由类的 _所有_ 对象共享。**类属性**（也称为**类变量**）表示 _类范围_ 信息。它属于 _类_，而不属于该类的特定对象。类 `Card` 定义了两个类属性（第 5–7 行）：

- `FACES` 是卡牌面值名称的列表。
- `SUITS` 是卡牌花色名称的列表。

点击此处查看代码图像

```python
# card.py
"""Card class that represents a playing card and its image file name."""

class Card:
    FACES = ['Ace', '2', '3', '4', '5', '6',
             '7', '8', '9', '10', 'Jack', 'Queen', 'King']
    SUITS = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
```

您可以通过在类定义中为其赋值（但不在类的任何方法或属性内赋值，否则它们将是局部变量）来定义类属性。`FACES` 和 `SUITS` 是不打算修改的常量。请回顾，Python 代码风格指南建议使用全大写字母命名常量。4

4 请回顾，Python 没有真正的常量，因此 `FACES` 和 `SUITS` 仍然可以修改。

我们将使用这些列表中的元素来初始化创建的每个 `Card`。但是，我们不需要在每个 `Card` 对象中保留每个列表的单独副本。类属性可以通过类的任何对象访问，但通常通过类的名称访问（例如，`Card.FACES` 或 `Card.SUITS`）。一旦导入类的定义，类属性即存在。

#### `Card` 方法 `__init__`

创建 `Card` 对象时，方法 `__init__` 定义对象的 `_face` 和 `_suit` 数据属性：

```python
def __init__(self, face, suit):
    """Initialize a Card with a face and suit."""
    self._face = face
    self._suit = suit
```

#### 只读属性 `face`、`suit` 和 `image_name`

创建 `Card` 后，其 face、suit 和 image_name 都不会改变，因此我们将这些实现为只读属性（第 14–17 行、19–22 行和 24–27 行）。属性 `face` 和 `suit` 返回相应的数据属性 `_face` 和 `_suit`。属性不要求拥有相应的数据属性。为了演示这一点，`Card` 属性 `image_name` 的值是通过使用 `str(self)` 获取 `Card` 对象的字符串表示、将任何空格替换为下划线并追加 `.png` 文件扩展名而动态创建的。因此，`'Ace of Spades'` 变为 `'Ace_of_Spades.png'`。我们将使用此文件名来加载表示 `Card` 的 PNG 格式图像。PNG（可移植网络图形）是一种用于基于 Web 的图像的流行图像格式。
