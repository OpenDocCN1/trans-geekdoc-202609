

你还可以使用“len()”函数来确定 Python 元组的**长度**，如下示例所示：

```python
Tuple = ("string1", "string2", "string3", "string4", "string5", "string6")
print(len(Tuple))
```

输出 - 6

你不能从元组中有选择地删除项目，但可以使用“del”关键字**整个删除元组**，如下示例所示：

```python
Tuple = ("string1", "string2", "string3", "string4")
del Tuple

print(Tuple)
```

输出 - name 'Tuple' is not defined

你可以使用“+”逻辑运算符**连接多个元组**。

```python
Tuple1 = ("string1", "string2", "string3", "string4")
Tuple2 = (101, 202, 303)

Tuple3 = Tuple1 + Tuple2
print(Tuple3)
```

输出 - ("string1", "string2", "string3", "string4", 101, 202, 303)

你还可以使用“tuple()”构造函数创建元组，如下示例所示：

```python
Tuple1 = tuple(("string1", "string2", "string3", "string4"))
print(Tuple1)
```

**练习 – 创建一个名为“X”的元组，字符串数据值为“corn, cilantro, carrot, potato, onion”，并显示位置 -2 处的项目。**

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
X = ("corn", "cilantro", "carrot", "potato", "onion")
print(X[-2])
```

输出 - ("potato")

**练习 – 创建一个名为“X”的元组，字符串数据值为“corn, cilantro, carrot, potato, onion”，并显示从 -1 到 -3 范围内的项目。**

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
X = ("corn", "cilantro", "carrot", "potato", "onion")
print(X[-3:-1])
```

输出 - ("carrot", "potato")

### **练习** – 创建一个名为“X”的元组，字符串数据值为“corn, cilantro, carrot, potato, onion”，并使用列表函数将其中的项目从“potato”更改为“pepper”。

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
X = ("corn", "cilantro", "carrot", "potato", "onion")
Y = list(X)
Y[4] = "pepper"
X = tuple(Y)
print(X)
```

输出 - ("corn", "cilantro", "carrot", "potato", "pepper")

### **练习** – 创建一个名为“X”的元组，字符串数据值为“corn, cilantro, carrot”，以及另一个名为“Y”的元组，数值数据为 (2, 12, 22)，然后将它们连接在一起。

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
X = ("corn", "cilantro", "carrot")
Y = (3, 13, 23)

Z = X + Y
print(Z)
```

输出 - ("corn", "cilantro", "carrot", 3, 13, 23)

## Python 集合

在 Python 中，集合是无法组织和索引的数据类型集合。集合不允许重复项，并且必须写在花括号内，如下语法所示。

```python
set = {"string1", "string2", "string3"}
print(set)
```

与 Python 列表和元组不同，你不能通过引用项目的位置从集合中有选择地显示所需项目，因为 Python 集合没有任何顺序。因此，项目没有任何索引。但是，“for”循环可以用于集合（本章后面将详细介绍此主题）。

与 Python 列表不同，创建后你无法直接**更改 Python 集合的数据值**。但是，你可以使用“add()”方法向集合添加单个项目，并使用“update()”方法向已存在的集合添加一个或多个项目。让我们看下面的示例：

```python
set = {"string1", "string2", "string3"}
set.add("newstring")
print(set)
```

输出 - {"string1", "string2", "string3", "newstring"}

```python
set = {"string1", "string2", "string3"}
set.update(["newstring1", "newstring2", "newstring3"])
print(set)
```

输出 - {"string1", "string2", "string3", "newstring1", "newstring2", "newstring3"}

你还可以使用“len()”函数来确定 Python 集合的**长度**，如下示例所示：

```python
set = {"string1", "string2", "string3", "string4", "string5", "string6",
"string7"}
print(len(set))
```

输出 - 7

要有选择地**从集合中删除特定项目**，可以使用“remove()”方法，如下代码所示：

```python
set = {"string1", "string2", "string3", "string4", "string5"}
set.remove("string4")
print(set)
```

输出 - {"string1", "string2", "string3", "string5"}

你还可以使用“discard()”方法从集合中删除特定项目，如下示例所示：

```python
set = {"string1", "string2", "string3", "string4", "string5"}
set.discard("string3")
print(set)
```

输出 - {"string1", "string2", "string4", "string5"}

“pop()”方法可用于有选择地仅删除集合的最后一个项目。必须注意的是，由于 Python 集合是无序的，系统视为最后一个项目的任何项目都将被删除。因此，此方法的输出将是已删除的项目。

```python
set = {"string1", "string2", "string3", "string4", "string5"}
A = set.pop()
print(A)
print(set)
```

输出 -
"string2"
{"string1", "string3", "string4", "string5"}

要删除整个集合，可以使用“del”关键字，如下所示。

```python
set = {"string1", "string2", "string3", "string4", "string5"}
del set
print(set)
```

输出 - name 'set' is not defined

要删除集合中的所有项目而不删除变量本身，可以使用“clear()”方法，如下所示。

```python
set = {"string1", "string2", "string3", "string4", "string5"}
set.clear()
print(set)
```

输出 - set()

你可以使用“union()”方法**连接多个集合**。此方法的输出将是一个新集合，包含两个集合中的所有项目。你还可以使用“update()”方法将一个集合中的所有项目插入到另一个集合中，而无需创建新集合。

```python
Set1 = {"string1", "string2", "string3", "string4", "string5"}
Set2 = {155, 255, 355, 455, 55}
Set3 = Set1.union(Set2)
print(Set3)
```

输出 - {"string1", 155, "string2", 255, "string3", 355, "string4", 455,
"string5", 55}

```python
Set1 = {"string1", "string2", "string3", "string4", "string5"}
Set2 = {155, 255, 355, 455, 55}
Set1.update(Set2)
print(Set1)
```

输出 - {255, "string1", 155, "string4", 55, "string2", 355, "string3",
455, "string5"}

你还可以使用“set()”构造函数创建集合，如下示例所示：

```python
Set1 = set(("string1", "string2", "string3", "string4", "string5"))
print(Set1)
```

输出 - {"string3", "string5", "string2", "string4", "string1"}

### **练习** – 创建一个名为“Veg”的集合，字符串数据值为“corn, cilantro, carrot, potato, onion”，并向该集合添加新项目“pepper”、“celery”和“avocado”。

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
Veg = {"corn", "cilantro", "carrot", "potato", "onion"}
Veg.update(["pepper", "celery", "avocado"])
print(Veg)
```

输出 - {"corn", "cilantro", "carrot", "potato", "onion", "pepper", "celery", "avocado"}

### **练习** – 创建一个名为“Veg”的集合，字符串数据值为“corn, cilantro, carrot, potato, onion”，然后从该集合中删除最后一个项目。

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
Veg = {"corn", "cilantro", "carrot", "potato", "onion"}
X = Veg.pop()
print(X)
print(Veg)
```

输出 -
onion
{"corn", "cilantro", "carrot", "potato"}

### **练习** – 创建一个名为“Veg”的集合，字符串数据值为“corn, cilantro, carrot, potato, onion”，以及另一个名为“Veg2”的集合，项目为“pepper, eggplant, celery, avocado”。然后将这两个集合合并以创建第三个新集合。

***在此处自行决定并先编写你的代码***

现在，将你的代码与下面的正确代码进行对比：

```python
Veg = {"corn", "cilantro", "carrot", "potato", "onion"}
Veg2 = {"pepper", "eggplant", "celery", "avocado"}

AllVeg = Veg.union(Veg2)      # this Set name may vary as it has not been defined in the exercise

print(AllVeg)
```

输出 - {"pepper", "eggplant", "celery", "avocado", "corn", "cilantro", "carrot", "potato", "onion"}

## Python 字典

在 Python 中，字典是可更改和索引但没有任何顺序的数据类型集合。Python 字典中的每个项目都包含一个键及其值。字典不允许重复项，并且必须写在花括号内，如下语法所示。

```python
dict = {
"key01": "value01",
```

