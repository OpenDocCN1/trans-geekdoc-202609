
是其中之一。如果没有元素等于 V，该方法将抛出一个 `ValueError` 异常。

```
>>> menu1
['beans', 'kale', 'spam', 'spam', 'spam', 'tofu', 'trifle', 'sardines']
>>> menu1.remove('spam')
>>> menu1
['beans', 'kale', 'spam', 'spam', 'tofu', 'trifle', 'sardines']
>>> menu1.remove('spam')
>>> menu1
['beans', 'kale', 'spam', 'tofu', 'trifle', 'sardines']
```

Traceback (most recent call last):
File "stdin>", line 1, in ?
ValueError: list.remove(x): x is not in list
``` `list.sort()` 方法将列表的元素按升序排序。

```
>>> menu1
['beans', 'kale', 'spam', 'tofu', 'trifle', 'sardines']
>>> menu1.sort()
>>> menu1
['beans', 'kale', 'sardines', 'spam', 'tofu', 'trifle']
```

注意，`.sort()` 方法本身不返回任何值；它是在原地对列表的值进行排序。类似的方法是 `.reverse()`，它可以原地反转元素：

```
>>> menu1
['beans', 'kale', 'sardines', 'spam', 'tofu', 'trifle']
>>> menu1.reverse()
>>> menu1
['trifle', 'tofu', 'spam', 'sardines', 'kale', 'beans']
```

## `range()` 函数：创建等差数列

等差数列一术是指一个数字序列，其中任意两个相邻元素之间的差都是相同的。例如：[1, 2, 3, 4, 5]；[10, 20, 30, 40]；[88, 77, 66, 55, 44, 33]。

Python 内置的 `range(n)` 函数返回一个包含等差数列的列表。调用此函数有不同的方式。

要生成序列 `[0, 1, 2, ..., n-1]`，请使用形式 `range(n)`。

```
>>> range(6)
[0, 1, 2, 3, 4, 5]
>>> range(2)
[0, 1]
>>> range(0)
[]
```

注意，该序列永远不会包含参数 `n` 的值；它会提前一个值停止。

要生成序列 `[i, i+1, i+2, ..., n-1]`，请使用形式 `range(i, n)`：

```
>>> range(5,11)
[5, 6, 7, 8, 9, 10]
>>> range(1,5)
[1, 2, 3, 4]
```

要生成相邻值之间差值为 `d` 的等差数列，请使用三参数形式 `range(i, n, d)`。生成的序列将为 `[i, i+d, i+2d, ...]`，并在达到等于 `n` 的值之前停止。

```
>>> range( 10, 100, 10 )
[10, 20, 30, 40, 50, 60, 70, 80, 90]
>>> range( 100, 0, -10 )
[100, 90, 80, 70, 60, 50, 40, 30, 20, 10]
>>> range( 8, -1, -1 )
[8, 7, 6, 5, 4, 3, 2, 1, 0]
```

## 一个值可以有多个名称

在修改可变值（如列表）时，必须小心，因为可能有一个多个名称绑定到该值。这里有一个演示。

我们创建一个包含两个字符串的列表并为其绑定两个名称。

```
>>> menu1 = menu2 = ['kale', 'tofu']
```

```
>>> menu1
['kale', 'tofu']
>>> menu2
['kale', 'tofu']
```

然后我们使用切片选择 `menu1` 的所有元素创建一个新列表：

```
>>> menu3 = menu1[:]
>>> menu3
['kale', 'tofu']
```

现在看一看当我们修改 `menu1` 的列表时发生了什么：

```
>>> menu1.append('sardines')
>>> menu1
['kale', 'tofu', 'sardines']
>>> menu2
['kale', 'tofu']
>>> menu3
['kale', 'tofu']
```

如果我们向 `menu1` 添加了第三个字符串，为什么它也出现在 `menu2` 中呢？答案在于 Python 的赋值语句：评估形式为 `menu1 = menu2 = expr` 的赋值，其中 `menu1` 是变量，`expr` 是某个表达式，首先将 `expr` 还原为单个值，然后将每个名称绑定到该值。让我们按照示例一步步操作，查看每一步后的全局命名空间。首先我们创建一个列表并绑定两个名称：

```
>>> menu1=menu2=['kale', 'tofu']

| 名称 | 值 |
|---|---|
| menu1 | ['kale', 'tofu'] |
| menu2 | |

两个不同的名称 `menu1` 和 `menu2` 指向同一个列表。接下来，我们创建该列表的元素拷贝并将名称 `menu3` 绑定到拷贝上。

```
>>> menu3 = menu1[:]
>>> menu3
['kale', 'tofu']
```

| 名称 | 值 |
|---|---|
| menu1 | ['kale', 'tofu'] |
| menu2 | |
| menu3 | |

所以，当我们向 `menu1` 的列表添加第三个字符串时，名称 `menu2` 仍然绑定到同一个列表。

```
>>> menu1.append('sardines')
>>> menu1
['kale', 'tofu', 'sardines']
>>> menu2
['kale', 'tofu', 'sardines']
```

| 名称 | 值 |
|---|---|
| menu1 | ['kale', 'tofu', 'sardines'] |
| menu2 | |
| menu3 | |

这种行为在实践中很少成为问题，但重要的是两个或多个名称可以绑定到同一个值。如果你担心在其他名称绑定到同一个列表时修改它，始终可以使用切片表达式 `L[:]` 创建一个拷贝。

```
>>> L1 = ['bat', 'cat']
>>> L2 = L1
>>> L3 = L1[:]
>>> L1.append('hat')
>>> L2
['bat', 'cat', 'hat']
>>> L3
['bat', 'cat']
```

## 字典 (DICTIONARIES)

Python 的字典类型适用于许多查找应用。在数学术语中：Python 字典是零或多个有序对 (键, 值) 的集合，满足：

- 值可以是任何类型。
- 每个键在字典中只出现一次。
- 键不可变变的。特别是，键可以是列表或字典，或者包含列表或字典的元组等。

## 字典操作

这种思想是将值存储与某些键关联的字典中，以便以后可以使用键检索关联的值。

在 Python 中创建新字典的通用形式如下：`{k_j: v_j, k_l: v_l, ...}`。

要从字典 `d` 中检索与键 `k` 关联的值，使用这种形式的表达式：`d[k]`。

是一些交互示例：

```
>>> numberNames = {0:'zero', 1:'one', 10:'ten', 5:'five'}
>>> numberNames[10]
'ten'
>>> numberNames[0]
'zero'
>>> numberNames[999]
Traceback (most recent call last):
File "<stdin>", line 1, in =
KeyError: 999
```

注意，当你尝试检索字典中不存在的键的值时，Python 会抛出一个 `KeyError` 异常。

要为字典 `d` 中的键 `k` 添加或替换值，请使用使用这种形式的赋值语句：`d[k] = v`。

```
>>> numberNames[2] = "two"
>>> numberNames[2]
'two'
>>> numberNames
{0:'zero', 1:'one', 10:'ten', 2:'two', 5:'five'}
```

## 注意

字典内部对的顺序是未定义的。注意在上面的示例中，这些对出现的顺序并不是它们被添加的顺序。

可以使用字符串以及许多其他值作为键：

你可以使用 "in" 运算符测试键 `k` 是否存在字典 `d` 中，如下所示：

```
k in d
```

如果 `k` 是字典 `d` 中的键，则此操作返回 `True`，否则返回 `False`。
"k not in d" 结构是反向测试：如果 `k` 不是字典 `d` 中的键，则返回 `True`，如果是则返回 `False`。

```
>>> 1 in numberNames
True
>>> 99 in numberNames
False
```

```
>>> "forty-leven" in numberNames
True
>>> "elevenleven" in numberNames
False
```

```
>>> "forty-leven" not in numberNames
False
>>> "elevenleven" not in numberNames
True
```

Python 的 `del`（删除）语句可以从字典中移除键值对。

```
>>> numberNames
{0:'zero', 1:'one', 10:'ten', 2:'two', 5:'five'}
>>> del numberNames[10]
>>> numberNames
{0:'zero', 1:'one', 2:'two', 5:'five'}
```

```
>>> numberNames[10]
```

Traceback (most recent call last):
File "<stdin>", line 1, in ?
KeyError: 10
```

## 字典方法

任何 Python 字典都定义了一些有用的方法。要测试键 `k` 是否存在字典 `d` 中，使用此方法：

```
d.has_key(k)
```

这等同于表达式 "k in d"：如果键在字典中，则返回 `True`，否则返回 `False`。

```
>>> numberNames
{0:'zero', 1:'one', 2:'two', 5:'five'}
>>> numberNames.has_key(2)
True
```

```
>>> numberNames.has_key(10)
False
```

要获取字典 `d` 中所有键的列表，使用此表达式：
`d.keys()`

要获取字典 `d` 中所有值的列表，使用此表达式：
`d.values()`

可以使用此表达式同时获取所有的键和值，它返回一个包含二元素元组的列表，每个元组包含键和一个值，格式为 `(k, v)`。
`d.items()`

示例：

```
>>> numberNames
{0:'zero', 1:'one', 2:'two', 5:'five'}
>>> numberNames.keys()
[0, 1, 2, 5]
>>> numberNames.values()
['zero', 'one', 'two', 'five']
>>> numberNames.items()
```

