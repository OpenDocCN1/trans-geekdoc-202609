

```
"key02": "value02",
"key03": "value03",
}
print (dict)
```

你可以通过在打印命令中引用方括号内的键，从字典中有选择地显示所需的项值，如下所示。

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
X = dict["key02"]
print (X)
OUTPUT - value02
```

你也可以使用“get ( )”方法查看键的值，如下示例所示：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
X = dict.get("key01")
print (X)
```

输出 – value01

在 Python 字典中，你可能需要**更改键的值**。这可以通过引用该项的键并声明新值来完成。让我们看下面的示例：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
```

```
dict["key03"] = "Newvalue"
print (dict)
```

输出 – {"key01": "value01", "key02": "value02", "key03": "Newvalue"}

你也可以使用“len()”函数来确定 Python 字典的**长度**，如下示例所示：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
"key4": "value4",
"key5": "value5"
}
```

```
print (len (dict))
```

输出 – 5

还可以通过**添加**新索引键并为该键赋予新值来更改 Python 字典，如下示例所示：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
```

```
dict ["NEWkey"] = "NEWvalue"
print (dict)
```

输出 – {'key01': 'value01', 'key02': 'value02', 'key03': 'value03', "NEWkey": "NEWvalue"}

有多个内置方法可以从 Python 字典中**删除项目**。

- 要有选择地删除特定项值，可以使用带有指定键名的“pop ()”方法。

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
dict.pop ("key01")
print (dict)
```

输出 – { "key02": "value02", "key03": "value03"}

- 要有选择地删除最后插入的项值，可以使用带有指定键名的“popitem ()”方法。

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
dict.popitem ()
print (dict)
```

输出 – { "key01": "value01", "key02": "value02"}

- 要有选择地删除特定项值，也可以使用带有指定键名的“del”关键字。

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
del dict["key03"]
print (dict)
```

输出 – { "key01": "value01", "key02": "value02"}

- 要彻底删除 Python 字典，也可以使用“del”关键字，如下示例所示：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
del dict
print (dict)
```

输出 – name ‘dict’ is not defined

- 要删除字典中的所有项目而不删除字典本身，可以使用“clear ()”方法，如下所示。

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
dict.clear()
print (dict)
```

输出 - { }

可能有时你需要**复制**现有的 Python 字典。这可以通过使用内置的“copy ()”方法或“dict ()”方法来完成，如下示例所示：

```
dict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
newdict = dict.copy()
print (newdict)
```

```
输出 - {"key01": "value01", "key02": "value02", "key03":
"value03"}
```

```
Odddict = {
"key01": "value01",
"key02": "value02",
"key03": "value03",
}
newdict = dict(Odddict)
print (newdict)
```

```
输出 - {"key01": "value01", "key02": "value02", "key03": "value03"}
```

有一个独特的功能支持将多个 Python 字典**嵌套**在另一个 Python 字典中。你可以创建包含子字典的字典，如下示例所示：

```
McManiaFamilyDict = {
 "burger1" : {
   "name" : "VegWrap",
   "price" : 3.99
 },
 "burger2" : {
   "name" : "Burger",
   "price" : 6
 },
 "burger3" : {
   "name" : "CheeseBurger",
   "price" : 2.99
 }
}
print (McManiaFamilyDict)
```

输出 - {"burger1" : { "name" : "VegWrap", "price" : 3.99}, "burger2" : {"name" : "Burger", "price" : 6}, "burger3" : {"name" : "CheeseBurger", "price" : 2.99}}

或者你可以创建一个包含系统中已存在的其他字典的全新字典，代码如下所示：

```
burgerDict1 : {
	"name" : "VegWrap",
	"price" : 3.99
}
```

```
burgerDict2 : {
	"name" : "Burger",
	"price" : 6
}
```

```
burgerDict3 : {
	"name" : "CheeseBurger",
	"price" : 2.99
}
```

```
McManiaFamilyDict = {
	"burgerDict1" : burgerDict1,
	"burgerDict2" : burgerDict2
	"burgerDict3" : burgerDict3
}
```

```
print (McManiaFamilyDict)
```

输出 - {"burger1" : { "name" : "VegWrap", "price" : 3.99}, "burger2" : { "name" : "Burger", "price" : 6}, "burger3" : { "name" : "CheeseBurger", "price" : 2.99}}

最后，你可以使用“dict ()”函数创建新的 Python 字典。使用此函数为字典创建项时的关键区别在于：1. 使用圆括号代替花括号。2. 使用等号代替分号。让我们看下面的示例：

```
DictwithFunction = dict (key1 = "value1", key2 = "value2", key3 = "value3")
print (DictwithFunction)
```

```
输出 – {"key1": "value1", "key2": "value2", "key3": "value3"}
```

Python 支持大量可用于字典的内置方法。下表包含所有适用方法及其用法。

| 方法 | 描述 |
|---|---|
| clear () | 将从字典中删除所有元素。 |
| copy () | 将返回字典的副本。 |
| fromkeys () | 将返回带有指定键和值的字典。 |
| get () | 将返回指定键的值。 |
| items () | 将返回包含每个键值对元组的列表。 |
| keys () | 将返回包含字典键的列表。 |
| pop () | 将删除带有指定键的元素。 |
| popitem () | 将删除最近添加的键值对。 |
| setdefault () | 将返回指定键的值。如果未找到键，则将添加带有指定值的新键。 |
| update () | 将使用指定的键值对更新字典。 |
| values () | 将返回字典中所有值的列表。 |

### 练习 – 创建一个名为“CoffeeShop”的字典，其中包含键为“type”、“size”和“price”的项，对应值为“cappuccino”、“large”和“5.99”。然后添加一个新项，键为“syrup”，值为“caramel”。

***在此处请自行斟酌，先编写你的代码***

现在，将你的代码与下面的正确代码进行核对：

```python
CoffeeShop = {
"type" : "cappuccino",
"size" : "large",
"price" : 5.99
}
CoffeeShop ["syrup"] = "caramel"
print (CoffeeShop)
```

输出 – {"type" : "cappuccino", "size" : "large", "price" : 5.99, "syrup" : "caramel"}

### 练习 – 创建一个名为“CoffeeShop”的字典，其中包含键为“type”、“size”和“price”的项，对应值为“cappuccino”、“large”和“5.99”。然后使用函数删除最后添加的项。

***在此处请自行斟酌，先编写你的代码***

现在，将你的代码与下面的正确代码进行核对：

```
CoffeeShop = {
  “type” : “cappuccino”,
  “size” : “large”,
  “price” : 5.99
}
CoffeeShop.popitem ( )
print (CoffeeShop)
```

输出 – {"type" : “cappuccino”, “size” : “large”}

### 练习 – 创建一个名为“CoffeeShop”的字典，包含如下列出的嵌套字典：

| 字典名称 | 键 | 值 |
|---|---|---|
| Coffee1 | name | cappuccino |
| | size | xlarge |
| Coffee2 | name | espresso |
| | size | large |

