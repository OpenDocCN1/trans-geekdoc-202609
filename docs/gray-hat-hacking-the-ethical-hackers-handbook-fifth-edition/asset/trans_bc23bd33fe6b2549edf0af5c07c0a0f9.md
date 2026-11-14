

```
% cat > hello.py
print 'Hello, world!'
^D   # This is simple CTRL+D being pressed to break out
% python hello.py
Hello, world!
```

从 Python 3 开始，print 不再是专门的语句，而是一个真正的函数。2 这是一个必要的更改，要求像普通函数调用一样使用括号。以下是 Python 3.0 中的“Hello, world！”：

```
% python
>>> print ("Hello, world!")
Hello, world!
```

## Python 对象

你真正需要很好理解的主要一点是 Python 可用于存储数据的不同对象类型，以及它如何操作这些数据。我们将介绍五大数据类型：字符串、数字、列表、字典和文件。之后，我们将介绍一些基本语法以及联网方面的最基本知识。

## 字符串

你在“使用 Python 的 Hello, World！”部分已经用过一个字符串对象了。字符串在 Python 中用于存储文本。展示使用和操作字符串有多简单的最佳方法是演示该技术。以下代码适用于 Python 2.7 和 Python 3：

```
% python
>>> string1 = 'Dilbert'
>>> string2 = 'Dogbert'
>>> string1 + string2
'DilbertDogbert'
>>> string1 + " Asok " + string2
'Dilbert Asok Dogbert'
>>> string3 = string1 + string2 + "Wally"
>>> string3
'DilbertDogbertWally'
```

```
>>> string3[2:10] # string 3 from index 2 (0-based) to 10
'lbertDog'
>>> string3[0]
'D'
>>> len(string3)
19
>>> string3[14:] # string3 from index 14 (0-based) to end
'Wally'
>>> string3[-5:] # Start 5 from the end and print the rest
'Wally'
>>> string3.find('Wally') # index (0-based) where string starts
14
>>> string3.find('Alice') # -1 if not found
-1
>>> string3.replace('Dogbert','Alice') # Replace Dogbert with Alice
'DilbertAliceWally'
>>> print('AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA') # 30 A's the hard way
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
>>> print ('A' * 30) # 30 A's the easy way
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

这些是使用简单字符串时会用到的基本字符串操作函数。语法简单直接，正如你从 Python 中会期望的那样。需要立即做出的一个重要区别是：这些字符串（我们将它们命名为 string1、string2 和 string3）仅仅是一个指针——对于熟悉 C 的人来说——或者是内存中某处数据块的一个标签。一个有时会让新程序员感到困惑的概念是：一个标签（或指针）指向另一个标签。以下代码和图 2-1 演示了这个概念：

![](img/5f597c6a70133069118d9e804ace3775_74_0.png)

图 2-1 两个标签指向内存中的同一个字符串

```
>>> label1 = 'Dilbert'
>>> label2 = label1
```

此时，内存中某处存有一个存储了 Python 字符串 'Dilbert' 的数据块。我们还有两个标签指向该内存数据块。如果随后更改 label1 的赋值，label2 则不会改变：

```
... continued from above
>>> label1 = 'Dogbert'
>>> label2
'Dilbert'
```

如图 2-2 所示，label2 并非严格指向 label1。相反，它指向 label1 在被重新赋值之前所指向的同一个对象。

![](img/5f597c6a70133069118d9e804ace3775_75_0.png)

图 2-2 Label1 被重新赋值以指向不同的字符串。

## 数字

与 Python 字符串类似，数字指向一个可以包含任何类型数字的对象。它可以存储小数、大数、复数、负数，以及你能想到的任何其他类型的数字。语法与你预期的一样：

```
>>> n1=5   # Create a Number object with value 5 and label it n1
>>> n2=3
>>> n1 * n2
15
>>> n1 ** n2      # n1 to the power of n2 (5^3)
125
>>> 5 / 3, 5 % 3      # Divide 5 by 3, then 5 modulus 3
(1.6666666666666667, 2)
# In Python 2.7, the above 5 / 3 calculation would not result in a float without
# specifying at least one value as a float.
>>> n3 = 1        # n3 = 0001 (binary)
>>> n3 << 3       # Shift left three times: 1000 binary = 8
8
>>> 5 + 3 * 2      # The order of operations is correct
11
```

现在你已经了解数字的工作原理，我们可以开始组合对象了。当我们计算字符串加数字时会发生什么？

```
>>> s1 = 'abc'
>>> n1 = 12
>>> s1 + n1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Can't convert 'int' object to str implicitly
```

出错了！我们需要帮助 Python 理解我们想要发生什么。在这种情况下，将 'abc' 和 12 组合的唯一方法是将 12 转换为字符串。我们可以即时完成此操作：

```
>>> s1 + str(n1)
'abc12'
>>> s1.replace('c', str(n1))
'ab12'
```

当合理时，不同类型可以一起使用：

```
>>> s1*n1  # Display 'abc' 12 times
'abcabcabcabcabcabcabcabcabcabcabcabc'
```

关于对象还有一点说明——仅仅对对象进行操作通常不会改变对象。只有当你显式地将对象的标签（或指针）设置为新值时，对象本身（数字、字符串或其他）才会通常发生变化，如下所示：

```
>>> n1 = 5
>>> n1 ** 2        # Display value of 5^2
25
>>> n1           # n1, however is still set to 5
5
>>> n1 = n1 ** 2  # Set n1 = 5^2
>>> n1          # Now n1 is set to 25
25
```

## 列表

我们将介绍的下一个内置对象类型是列表。你可以将任何类型的对象放入列表中。列表通常通过在对象或一组对象周围添加 [ 和 ] 来创建。你可以像对字符串那样进行同样的巧妙“切片”操作。切片是指仅返回对象值的子集的技术——例如，使用 label1[5:10] 从第五个值到第十个值。让我们看看列表类型是如何工作的：

```
>>> mylist = [1,2,3]
>>> len(mylist)
3
>>> mylist*4      # Display mylist, mylist, mylist, mylist
[1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
>>> 1 in mylist    # Check for existence of an object
True
>>> 4 in mylist
False
>>> mylist[1:]     # Return slice of list from index 1 and on
[2, 3]
>>> biglist = [['Dilbert', 'Dogbert', 'Catbert'],
...  ['Wally', 'Alice', 'Asok']]   # Set up a two-dimensional list
>>> biglist[1][0]
'Wally'
>>> biglist[0][2]
'Catbert'
>>> biglist[1] = 'Ratbert'       # Replace the second row with 'Ratbert'
>>> biglist
[['Dilbert', 'Dogbert', 'Catbert'], 'Ratbert']
>>> stacklist = biglist[0]       # Set another list = to the first row
>>> stacklist
['Dilbert', 'Dogbert', 'Catbert']
>>> stacklist = stacklist + ['The Boss']
>>> stacklist
['Dilbert', 'Dogbert', 'Catbert', 'The Boss']
>>> stacklist.pop()              # Return and remove the last element
'The Boss'
>>> stacklist.pop()
'Catbert'
>>> stacklist.pop()
'Dogbert'
>>> stacklist
['Dilbert']
>>> stacklist.extend(['Alice', 'Carol', 'Tina'])
>>> stacklist
['Dilbert', 'Alice', 'Carol', 'Tina']
>>> stacklist.reverse()
>>> stacklist
['Tina', 'Carol', 'Alice', 'Dilbert']
>>> del stacklist[1]             # Remove the element at index 1
>>> stacklist
['Tina', 'Alice', 'Dilbert']
```

接下来，我们将快速查看字典和文件，然后将所有元素组合在一起。

## 字典

字典与列表类似，不同之处在于存储在字典中的对象是通过键引用的，而不是通过对象的索引引用的。这证明是一种非常方便的存储和检索数据的机制。字典是通过在键值对周围添加 { 和 } 来创建的，如下所示：

```
>>> d = { 'hero' : 'Dilbert' }
>>> d['hero']
'Dilbert'
>>> 'hero' in d
True
>>> 'Dilbert' in d   # Dictionaries are indexed by key, not value
False
>>> d.keys()    # keys() returns a list of all objects used as keys
dict_keys([['hero']])
>>> d.values()  # values() returns a list of all objects used as values
dict_keys([['Dilbert']])
>>> d['hero'] = 'Dogbert'
>>> d
{'hero': 'Dogbert'}
>>> d['buddy'] = 'Wally'
>>> d['pets'] = 2      # You can store any type of object, not just strings
>>> d
{'hero': 'Dogbert', 'buddy': 'Wally', 'pets': 2}
```

我们在下一节中还将更多地使用字典。字典是存储任何可以与键关联的值的好方法，其中键比列表的索引更有用的方式来获取值。

## Python 中的文件

文件访问与 Python 语言的其他部分一样简单。文件可以打开（用于读取或写入）、写入、读取和关闭。让我们使用本节讨论的几种不同数据类型（包括文件）来组合一个示例。此示例假设我们以一个名为 targets 的文件开始，并将文件内容传输到单独的漏洞目标文件中。（我们能听到你说：“终于，Dilbert 示例结束了！”）请注意块中使用的必要缩进。

