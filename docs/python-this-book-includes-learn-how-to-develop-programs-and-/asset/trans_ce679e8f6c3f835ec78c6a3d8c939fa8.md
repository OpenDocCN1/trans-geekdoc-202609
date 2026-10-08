
存储在字符串内部。
你可以使用 `for` 循环分离字符串内部的单个字符。循环中的特征变量将一次假设假设你字符串中的每一个字符。例如：`for c in "Maria":`

```
print (c)
>> M
>> a
>> r
>> i
>> a
```

**利用字符串中的单个字符进行计算**
既然你已经可以对字符串进行迭代，那么很容易想象你将如何分析字符串的细节了。

## 字符串索引 (String Indexing)

索引表示法（Indexing notation）是另一种分析字符串的方法。
索引指的是根据位置引用字符串内部单个元素的方法。
你可以通过在变量后的一对方括号内应用整数值来确定索引：

```
Word = "superman"
Print (word[0])
>> s
```

字符串索引从零开始。

## 遍历字符串与索引

你可以应用 "for" 循环来遍历字符串中的字符。例如：
word = "hello"
for c in word:

print (c)
但是，如果你想通过索引来遍历字符串，那么你需要生成一个与你想要访问的索引相关的数字范围。
例如：
word = "hello"
for i in range(0, 5):

print (word[i])

## 字符串不可变性 (String Immutability)

字符串是不可变数据类型的一个示例。换句话说，它们一旦创建就无法被修改。

背后真正发生的情况是 Python 在计算机内存中定义了一个不同的字符串并引用该字符串而不是之前的那个。

name = 'superman'

![](img/43582740ac1227a817786ef73e0f3772_318_0.png)

name = 'wonder woman'

![](img/43582740ac1227a817786ef73e0f3772_318_1.png)

换句话说，通过表示法无法修改字符串中的单个字符。你可能会触发异常。
word = "Superman"
word[0] = "X"

## 修改字符串 (Changing a String)

要对字符串进行更改，你需要创建一个新的字符串变量。此新变量可以存储修改后的字符串。
例如，让我们来看以下编程挑战：

“编写一个程序，将字符串中所有的元音替换为下划线字符。”

起初，你可能认为可以简单地应用字符串索引来修改相关的字符。例如：
word = "hello"
word[1] = "_"
word[4] = "_"

但字符串是不可变的，这将不起作用！
相反，你需要定义一个新的变量来存储更改，然后应用循环来检查序列中的每个字符以“创建”新字符串。例如：
word = "hello"
newword = ""
for c in word:
if c === 'e' or c == 'o':
newword += "_"
else:
newword += c

## 字符串函数 (String Functions)

到目前为止，你已经知道了几个可以与字符串配合使用的函数。
例如，`len()` 函数可以计算字符串中的字符数量。
此外，当你处理字符串时，还可以应用其他函数来简化你的开发者工作。

## 确定字符串中最大和最小的字符

你可以使用 Python 内置函数来计算字符串内部最大和最小的字符。例如：

```
a = max("python")
b = min("python")
print("max:", a)
print("min:", b)
>> y
>> h
```

## 字符串切片语法 (String Slicing Notation)

为了让 Python 切割字符串，你必须使用括号符号来定义你想要的字符的索引范围。
以下语法的标准表示法包括：
`string[start:end:step]`
对于 Python 切割字符串，你必须使用括号符号来定义你想要的字符的索引范围。
标准语法表示法包括：
字符串的索引。

## 字符串运算符 (String Operators)

现在你已经知道了可以与字符串配合使用的运算符。
`+` 运算符可以连接字符串。
`*` 运算符可以重复字符串。

## 使用 “in” 测试字符串

使用 `in` 和 `not in` 运算符判断子字符串是否存在于字符串中。例如：

```
word = "Jackson Chris"
if "Chris" in word:
    print("found!")
else:
    print("can't find")
```

## 字符串方法 (String Method)

方法是用于处理字符串的函数。标准语法包括：
`stringvariable.method(arguments)`

## 字符串测试 (String Testing)

字符串测试方法允许你确定特定的模式是否在字符串中。例如：

```python
word = "1234"
if word.isdigit():
    print("all chars are digits")
else:
    print("not all chars are digits")
```

## 字符串修改方法 (String Modification)

记住字符串是不可变的，不能直接更改。但它们有返回字符串副本的修改方法。

```python
word = "Craig"
newword = word.lower()
print(newword)
>> craig
```

## 搜索与替换 (Searching and Replacing)

程序通常需要搜索并替换数据，正如搜索和替换功能在你的处理器中存在一样。
字符串可以通过 `find()` 和 `index()` 方法进行搜索。

`find()` 方法在未找到子字符串时返回 -1。
`index()` 方法在未找到时会返回错误。

## 搜索字符串的特定部分 (Searching a Specific Section of a String)

`find()` 和 `index()` 方法可以从字符串开始搜索子字符串。
你还可以定义起始和结束索引来只检查字符串的一部分。

## 如何反向搜索字符串 (How to Search Backwards Through a String)

`rfind()` 和 `rindex()` 方法的工作方式与 `find()` 和 `index()` 相同，区别是从字符串末尾反向搜索。

## 文本居中 (Centering Text)

`s.center(w, [pad])` 将文本在宽度为 `w` 的字段内居中。
可选的 `pad` 字符将位于字符串两侧。

## 第四章：条件执行 (Chapter 4: Conditional Execution)

生活中某些情况下，决定是不可避免的。这与编程没有区别。每个程序都是如此，必须评估相关问题。如果不在流中应用分支，就无法编程。
