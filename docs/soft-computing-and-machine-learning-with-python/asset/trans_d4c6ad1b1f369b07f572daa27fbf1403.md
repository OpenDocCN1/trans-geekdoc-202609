

```python
>>> >>> treeFile.open('trees')
>>> for treeLine in treeFile:
...
    print treeLine.rstrip()
...
```

yew
oak
alligator juniper

与 `.readline()` 方法一样，当你以这种方式迭代文件的行时，这些行将包含换行符。如果上面的示例没有使用 `.strip()` 来修剪这些行，那么每行输出后面都会跟着一个空行，因为 `print` 语句会添加一个换行。

### 随机访问设备的文件定位

对于磁盘文件等随机访问设备，有一些方法可以让你找到文件中的当前位置，并移动到不同的位置。

- * `F.tell()` 返回你在文件 F 中的当前位置。

例如，`F.seek(80, 1)` 将文件位置移动到文件起始之后 80 个字符处。

- * `F.seek(N, 2)` 移动到相对于文件末尾 N 个字符的位置。例如，`F.seek(0, 2)` 将移动到文件末尾；`F.seek(-200, 2)` 将你的位置移动到文件末尾前 200 字节处。

```python
>>> treeFile = open ("trees")
>>> treeFile.tell()
0L
>>> treeFile.read(6)
'yew'noa'
>>> treeFile.tell()
6L
>>> treeFile.seek(1)
>>> treeFile.tell()
```

```python
1L
>>> treeFile.read(5)
'ew\noa'
>>> treeFile.tell()
6L
>>> treeFile.seek(1, 1)
>>> treeFile.tell()
7L
>>> treeFile.seek(-3, 1)
>>> treeFile.tell()
4L
>>> treeFile.seek(0, 2)
>>> treeFile.tell()
26L
>>> treeFile.seek(-3, 2)
>>> treeFile.tell()
23L
>>> treeFile.read()
'er\n'
```

# 写入文件

要创建一个磁盘文件，使用如下通用形式的语句打开文件：

```python
F = open (filename, "w")
```

第二个参数 `"w"` 指定写入权限。如果可能，Python 将创建一个同名的空文件。如果已存在同名文件，且你对它有写入权限，则现有文件将被删除。

要向你创建的文件写入内容，请使用此方法：

```python
F.write(s)
```

其中 `s` 是任何字符串表达式。

# 警告

你通过 `.write()` 方法发送到文件的数据在通过调用文件对象的 `.close()` 方法关闭它之前，可能不会真正出现在磁盘文件中。

这是由于一种名为“缓冲”（buffering）的机制。Python 会累积你发送到文件的数据，直到达到一定的数量，然后它会通过写入操作将这些数据“刷新”（flush）到物理文件中。Python 在你关闭文件时也会将数据刷新到文件。

如果你想确保写入到文件的数据在不关闭文件的情况下物理上确实存在于文件中，请对文件对象调用 `.flush()` 方法。

```python
>>> sports = open ("sportfile", "w")
>>> sports.write ( ('tennis\nrugby\nquoits\n')
>>> sports.close()
>>> sportFile = open ("sportfile")
>>> sportFile.readline()
'tennis\n'
>>> sportFile.readline()
'rugby\n'
>>> sportFile.readline()
'quoits\n'
','
```

这是一个演示 `.flush()` 方法作用的详细示例。

```python
>>> sporting = open('sports', 'w')
>>> sporting.write('golf\n')
>>> echo = open('sports')
>>> echo.read()
''
>>> echo.close()
>>> sporting.flush()
>>> echo = open('sports')
>>> echo.read()
'golf\n'
>>> echo.close()
>>> sporting.write('soccer')
>>> sporting.close()
>>> open('sports').read()
'golf\nsoccer'
```

# 面向对象编程

到为止，我们已经使用了 Python 的一些内置类型，如 `int`、`float`、`list` 和 `file`。

现在是时候探索 Python 更强大的功能了：创建你自己的类型。

这是一个大步，让我们从回顾编程语言的一些特性开始。

# 蜗牛赛技术简史

企业家 Malek 想要开发一种服务来帮助非营利组织筹资金。以下是蜗牛赛设计的方案：

![](img/e1ab17402154bec3fa9783fe234_0.png)

在比赛开始时，蜗牛们背上用可降解墨水写着的名字被放在起线上，Malek 开始计时。当每只蜗牛越过终点时，Malek 记录它们的时间。

Malek 想编写一个 Python 程序来打印比赛结果。我们将回顾 1960 年左右的编程。

# 标量变量

1960 年左右的语言是 FORTRAN。很多工作是使用标量变量完成的，即每个变量持有一个数字。假设我们刚刚进行了蜗牛赛，Judy 用了 87.3 分钟，而 Kyle 用了 96.6 分钟。我们可以用这些值创建 Python 变量：

```python
judy = 87.3
kyle = 96.6
```

为了找到胜利者，可以使用语句：

```python
>>> if judy < kyle:
...     print "Judy wins with a time of", Judy
... elif kyle > judy:
...     print "Kyle wins with a time of", kyle
... else:
...     print "Judy and Kyle are tied with a time of", Judy
```

如果 Judy 和 Kyle 是两只蜗牛，这个程序将正常运行。Malek 将此放入脚本。在每次比赛后，他更改给出完成时间的两个行代码，然后运行脚本。这可行，但有很多问题：

- 准备比赛结果的人必须知道如何编辑脚本。
- 它并没有真正节省劳动。任何学生都可以查看时间并判断谁赢。
- 蜗牛的名字是程序的一部分，如果使用了不同的蜗牛，我们必须编写新程序。
- 如果有三只蜗牛怎么办？还有更多情况：三胜、三平和三并。如果 Malek 想同时赛十只蜗牛怎么办？太复杂了！

# 面向对象的数据结构：列表

让我们考虑涉及任意数量蜗牛比赛的通用问题。Malek 考虑到比赛中可能有数千名参赛者。此外，为了让运行成为可能，让我们编写一个通用脚本来读取每个人的结果。我们将使用非常简单的文本格式来编码比赛结果。这里有一个 Judy 和 Kyle 比赛的示例文件：

87.3 Judy
96.6 Kyle

这里有一个将处理该文件并报告胜利时间的脚本。脚本名为 `snailist.py`。首先读取名为 `results` 的结果文件并将其存储在列表中`.split()` 方法用于将每行拆分为部分，第一部分包含经过的时间。

```python
#!/usr/local/bin/python
################################=====
# snailist.py: 结果脚本。
----------------------------------------------------
# 创建一个空列表来存储完成时间。
timeList = []

# 打开包含结果的文件。
resultsFile = open ('results')

# 遍历文件的行，存储每个完成时间。
for resultsLine in resultsFile:
    # 创建行的字段列表，例如 ['87.3', 'Judy\n']
    fieldList = resultsLine.split()

    # 将完成时间转换为浮点数并添加到 timeList。
    timeList.append(float(fieldList[0]))
```

此时，`timeList` 是一个浮点数列表。我们使用 `.sort()` 方法将列表按升序排序，这样胜利时间将位于第一个元素。

```python
# 将 timeList 按升序排序，然后将 ‘winningTime’ 设置为
# 最佳时间。
timeList.sort()
```

print "The winning time is", timeList[0]

尝试自己构建结果文件和脚本以验证它们是否工作。尝试一些有平局的情况。
这个脚本到目前为止是还可以的。然而，它有一个主要的缺点：它没有告诉你谁赢了！

# 面向对象的数据结构：元组列表

为了改进上面的脚本，让我们修改脚本，将每只蜗牛的时间和名称组合在一个双元素元组中，例如 `(87.3, 'Judy')`。

在改进后的脚本中，`timeList` 是元组列表，而不仅仅是时间列表。然后我们可以利用元组的一个有趣属性对列表进行排序。如果你比较两个元组，且它们的第一个元素不相等，则结果与比较它们的第一个元素的结果相同。然而，如果第一个元素相等，Python 会比较每个元组的第二个元素，依此类推，直到找到不相等的值，或发现所有元素都相等。

这是一个示例。记得 `cmp(a, b)` 函数比较任意值，如果 a 在 b 之前则返回负数，如果 a 在 b 之后则返回正数，如果它们被视为相等则返回零：

```python
>>> cmp(50,30)
1
>>> cmp(30,50)
-1
>>> cmp(50,50)
0
>>>
```

如果你比较两个元组且第一个元素不相等，则结果与比较它们前两个元素相同。例如：

```python
>>> cmp ( (50,30,30), (80,10,10) )
```

