

>>> s = 'wooden house'
>>> sM = s.upper() # converts the letters to uppercase
>>> sM
'WOODEN HOUSE'
>>> sM.lower() # converts the letters to lowercase
'wooden house'
>>> s.capitalize() # first letter of the string in uppercase
'Wooden house'
>>> s.title() # first letter of each string word in uppercase
'Wooden House'
>>> i = s.find('e') # searches the index (position) of the first string 'e'
>>> i # if it doesn't find the string it returns -1
5
>>> s.count('a') # count how many times the element or string appears
0
>>> s.replace('o', 'e') # replace the first string with the second
'weeden heuse'
>>> s.split() # split s using the string " producing list
['wooden', 'house']
>>> s1 = 'Hello'
>>> s1.isupper() # True if all characters in S are uppercase
False # False otherwise
>>> s1[0].isupper()
True
>>> s1.islower() # True if all characters in S are lowercase
False # False otherwise
>>> s1[1].islower()
True

上表展示了字符串值的一组典型方法。我们使用 capitalize() 方法解决了首字母大写的问题。split 方法根据用作参数的分隔符将字符串分成若干段，此处的分隔符是空格。参数 "" 是默认参数，因此可以使用 s.split() 来拆分文本中的单词。生成的子字符串（在此例中为单词）作为列表返回，子字符串作为元素。

## 示例

我们将展示在字符串中进行遍历或搜索的几个示例，以 (i) 统计 'to' 的数量，(ii) 统计给定字符或子字符串 'c1' 的数量，并搜索字符或子字符串。

```python
def count(s):
    """Count letter a in a string
    >>> countLetter('hot potato', 'a')
    1
    >>> countLetter('Esplugues', 'a')
    0
    """
    n = 0
    for c in s:
        if c == 'a':
            n = n + 1
    return n
```

### 使用 s.count() 方法

```python
def count(s):
    return s.count('a')
```

```python
def count(s, c1):
    """Count letter or sub-string c1 in string s
    Examples:
    >>> count('hot potato', 'a')
    1
    >>> count('potato', 'u')
    0
    """
    n = 0
    for c in s:
        if c == c1:
            n = n + 1
    return n
```

在字符串中查找字符或子字符串可以使用 for、while 结构，也可以直接使用字符串的某些方法。让我们先看看使用 for 和 while 的经典查找选项。

```python
def search(s, c1):
    """search for letter c1 in string s
    Examples:
    >>> search('hot potato', 'a')
    True
    >>> search('potato', 'u')
    False
    """
    OK = False
    for c in s:
        if c == c1:
            OK = True
            break
    return OK
```

```python
def search(s, c1):
    """search for letter c1 in string s
    Examples:
    >>> search('hot potato', 'a')
    True
    >>> search('potato', 'u')
    False
    """
    OK = False
    N = len(s)
    i = 0
    while i < N and not OK:
        if s[i] == c1:
            OK = True
            i += 1
    return OK
```

在 Python 中，可以在循环内退出函数，因此查找可以写为：

```python
def search(s, c1):
    """search for letter c1 in string s
    Examples:
    >>> search('hot potato', 'a')
    True
    >>> search('potato', 'u')
    False
    """
    for c in s:
        if c == c1:
            return True
    return False
```

但此查找也可以使用 count()、find() 方法，或者直接使用布尔运算符 in 来完成：

```python
def search(s, c1):
    """search for letter c1 in string s
    Examples:
    >>> search('hot potato', 'a')
    True
    >>> search('potato', 'u')
    False
    """
    return c1 in s
# return s.count(c1) > 0
# return s.find(c1) >= 0
```

## 元组

元组与字符串一样，是排列在 Python 对象中的元素序列。与字符串（元素为字符）不同，元组可以包含任何类型的元素，包括不同类型的元素。元素的索引方式与字符串相同，通过整数进行索引。元组的语法是逗号分隔的值序列。虽然并非必需，但通常会用括号将其括起来，

```python
# Example of tuples
>>> a = 1, 2, 3
>>> a
(1, 2, 3)
>>> b = (3, 4, 5, 'a')
>>> b
(3, 4, 5, 'a')
>>> type(a)
<class 'tuple'>
>>> type(b)
<class 'tuple'>
```

赋给变量 a 和 b 的对象是元组类型。关键是在元素之间包含逗号。例如，

```python
>>> t = 'k',
>>> t
('k',)
>>> type(t)
<class 'tuple'>
>>> t2 = 'k'
>>> t2
'k'
>>> type(t2)
<class 'str'>
```

对象 'k' 是一个元组，然而 'k' 是一个字符串。可以使用不包含任何内容的括号创建一个空元组：()。我们还可以使用内置的 tuple() 函数将可迭代序列（例如字符串或列表）转换为元组，或创建一个空元组：

```python
>>> tuple('Hello')
('H', 'e', 'l', 'l', 'o')
>>> tuple([1, 2])
(1, 2)
>>> tuple()
()
```

## 索引、切片及其他元组操作

访问元组元素、提取元素和操作与字符串类似。让我们看几个例子：

```python
>>> b = (3, 4, 5, 'a')
>>> b[0]
3
>>> b[-1]
'a'
>>> b[0:3]
(3, 4, 5)
>>> t = ('the', 'tuples', 'are', 'immutable')
>>> t[0]
'the'
>>> t[1] = 'lists'
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

元组的静态或不可变特性与字符串一样可见。我们可以将元组嵌套于元组中，并像对待字符串一样对它们进行连接和重复，

```python
>>> b = (3, 4, 5, 'a')
>>> c = (b, 2)
>>> b + c
(3, 4, 5, 'a', (3, 4, 5, 'a'), 2)
>>> 3*b
(3, 4, 5, 'a', 3, 4, 5, 'a', 3, 4, 5, 'a')
```

Python 的 for-in 迭代结构可以用于任何可迭代序列，包括元组：

```python
>>> games = ('tennis', 'baseball', 'football', 'volleyball', 'swimming')
>>> for sport in games:
... print(sport)
tennis
```

- 棒球
- 足球
- 排球
- 游泳

同样，如同字符串序列一样，在元组中，你可以使用连接 (+) 和重复 (*) 操作对元组进行操作，以及使用 `in` 和 `not in` 运算符来检查元素在元组中的成员关系。

## 多重赋值和带有多个返回值的函数

Python 允许通过元组赋值进行多重赋值。这些操作允许将赋值右侧的一个值元组赋给左侧的一个变量元组。必须满足的条件是：变量元组中的变量数量等于值元组中的元素数量。此外，多次赋给变量元组的对象可以是字符串或列表，只要字符数或元素数等于接收值的元组中的变量数量。让我们看一些示例：

```python
>>> a, b, c = (1, 2, 3)
>>> a
1
>>> type(a)
<class 'int'>
>>> d, e, f = 'xyz'
>>> d
'x'
>>> type(d)
<class 'str'>
```

在第一个变量元组 (a, b, c) 中，变量接收整数值。虽然该对象是结构化类型（元组），但其元素是整数类型的变量。同样，变量元组 (d, e, f) 中的每个变量接收字符串类型的值，其变量类型也为字符串。

元组赋值的这一特性使得解决变量交换这一典型问题变得简单，而不需要辅助变量。例如，如果我们想交换变量 x = 5 和 y = 7 的值，在经典语言中会这样做：

```python
>>> x = 5
>>> y = 7
>>> temp = x # use of auxiliary (temporary) variable temp
>>> x = y
>>> y = temp
>>> print(x, y)
7   5
```

使用元组的多重赋值，解决方案是直接的：

```python
>>> x = 5
>>> y = 7
>>> x, y = y, x
>>> print(x, y)
7   5
```

在函数的情况下，它们也可以返回多个结果，这些结果可以使用元组赋给多个变量。严格来说，函数只返回一个结果。但如果该值是一个元组，那么它可以赋给一个变量元组。元素数量必须匹配。让我们看下面的函数示例：

```python
def myFunction(x):
    """
    Returns 2 values: x increased and decreased by 1
    """
    return x + 1, x - 1

a, b = myFunction(10)
print(a, b)
print(myFunction(20))
```

