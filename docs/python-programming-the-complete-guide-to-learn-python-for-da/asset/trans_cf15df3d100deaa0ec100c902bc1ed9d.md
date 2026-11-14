

## 2-当某些情况包含其他情况时

Consider a program that asks for a value and tells us:

考虑一个程序，它要求输入一个值并告诉我们：

- if it is a multiple of two,
- 如果它是 2 的倍数，
- if it is a multiple of four (and two)
- 如果它是 4 的倍数（也是 2 的倍数）
- if it is not a multiple of two
- 如果它不是 2 的倍数

Note: The value 0 will be considered a multiple of 4 and 2.

注意：值 0 将被视为 4 和 2 的倍数。

The cases are not mutually exclusive, since the multiples of four are also multiples of two.

这些情况并非互斥，因为 4 的倍数也是 2 的倍数。

The following program would not be correct:

下面的程序是不正确的：

```python
# This program does not work properly
number = int(input("Enter a number:"))
if number % 2 == 0:
    print(f"{number} is a multiple of two")
elif number % 4 == 0:
    print(f"{number} is a multiple of four and two")
else:
    print(f"{number} is not a multiple of two")
```

The error of this program is that if number meets the second condition, it also meets the first. That is, if number is a multiple of four, as it is also a multiple of two, it meets the first condition and the program executes the first block of instructions, without checking the rest of the conditions.

此程序的错误在于，如果 number 满足第二个条件，它也满足第一个条件。也就是说，如果 number 是 4 的倍数，因为它也是 2 的倍数，所以它满足第一个条件，程序将执行第一块指令，而不检查其余条件。

One way to correct that error is to add in the first condition (if) that the number is not a multiple of four.

纠正该错误的一种方法是在第一个条件（if）中添加 number 不是 4 的倍数。

```python
number = int(input("Enter a number:"))
if number % 2 == 0 and number % 4 != 0:
    print(f"{number} is a multiple of two")
elif number % 4 == 0:
    print(f"{number} is a multiple of four and two")
else:
    print(f"{number} is not a multiple of two")
```

The following program could also have been written:

还可以编写以下程序：

```python
number = int(input("Enter a number:"))
if number % 2 == 0 and number % 4 != 0:
    print(f"{number} is a multiple of two")
elif number % 2 == 0:
    print(f"{number} is a multiple of four and two")
else:
    print(f"{number} is not a multiple of two")
```

This program works because the multiples of four are also multiples of two and the program only evaluates the second condition (elif's) if the first one has not been met.

此程序有效，因为 4 的倍数也是 2 的倍数，并且程序仅在第一个条件未满足时才评估第二个条件（elif）。

But we can still simplify the program further, ordering the cases differently:

但我们可以通过以不同顺序排列情况来进一步简化程序：

```python
number = int(input("Enter a number:"))
if number % 4 == 0:
    print(f"{number} is a multiple of four and two")
elif number % 2 == 0:
    print(f"{number} is a multiple of two")
else:
    print(f"{number} is not a multiple of two")
```

This program works correctly because although the second condition (elif's) does not distinguish between multiples of two and four, if number is a multiple of four, the program fails to evaluate the second condition because the first one is met (the one of if).

此程序正确，因为尽管第二个条件（elif）不区分 2 的倍数和 4 的倍数，但如果 number 是 4 的倍数，程序将无法评估第二个条件，因为第一个条件（if 的那个）已满足。

In general, the order that makes it easier to simplify the expressions is usually to consider the particular cases first and then the general cases.

一般来说，使表达式更容易简化的顺序通常是先考虑特殊情况，再考虑一般情况。

If the if ... elif ... conditions cover all possibilities, the else block may not be written:

如果 if ... elif ... 条件涵盖所有可能性，则可以不写 else 块：

```python
number = int(input("Enter a number:"))
if number > 0:
    print("You have written a positive number")
elif number < 0:
    print("You have written a negative number")
```

But it is more common to replace the last elif block ... with an else block:

但更常见的是将最后一个 elif 块 ... 替换为 else 块：

```python
number = int(input("Enter a number:"))
if number > 0:
    print("You have written a positive number")
else:
    print("You have written a negative number")
```

## 非布尔条件

Since any variable can be interpreted as a Boolean variable, if the condition is a comparison with zero, we can skip the comparison.

由于任何变量都可以解释为布尔变量，如果条件是与零的比较，我们可以跳过比较。

For example, the following program:

例如，以下程序：

```python
number = int(input("Enter a number:"))
if number % 2 != 0:
    print(f"{number} is odd")
else:
    print(f"{number} is even")
```

You could write skipping the comparison:

可以跳过比较来编写：

```python
number = int(input("Enter a number:"))
if number % 2:
    print(f"{number} is odd")
else:
    print(f"{number} is even")
```

In this program, if the number is odd, number% 2 results in 1. And since the Boolean value of a nonzero number is True (that is, bool(1) is True), the condition would be met.

在此程序中，如果 number 是奇数，number % 2 的结果为 1。并且由于非零数的布尔值为 True（即 bool(1) 为 True），条件将被满足。

If the comparison is an equality, the not operator can be used. For example, the following program:

如果比较是等式，可以使用 not 运算符。例如，以下程序：

```python
number = int(input("Enter a number:"))
if number % 2 == 0:
    print(f"{number} is even")
else:
    print(f"{number} is odd")
```

You could write skipping the comparison:

可以跳过比较来编写：

```python
number = int(input("Enter a number:"))
if not number % 2:
    print(f"{number} is even")
else:
    print(f"{number} is odd")
```

In this program, if the number is even, number% 2 results in 0. The Boolean value of zero is False (that is, bool(0) is False), but by refusing to not, the condition would be met (already that not False is True.

在此程序中，如果 number 是偶数，number % 2 的结果为 0。零的布尔值为 False（即 bool(0) 为 False），但通过对 not 取反，条件将被满足（因为 not False 为 True。

When learning to program, this notation can be a bit cryptic, so it is recommended to start writing the complete comparisons. Later, when you have become familiar with logical expressions, it will be more natural for you to use it.

学习编程时，这种表示法可能有点晦涩，因此建议从编写完整的比较开始。之后，当你熟悉逻辑表达式后，使用它会更自然。

## Python 中的正则表达式

```python
regex = r '[a-z] + -? [a-z] +'
```

The above expression will consider valid any string that begins with one or more letters ([a-z] +), followed by a hyphen, which is optional, that is, it may or may not appear in the string (-?) Followed again by one or more more character from a to z, in lower case.

上述表达式将视为有效任何以一个或多个字母（[a-z] +）开头，后跟一个连字符（可选，即字符串中可能出现也可能不出现（-?）），然后再跟一个或多个从 a 到 z 的小写字符的字符串。

Some example cases are as follows:

一些示例情况如下：

### 有效示例：

```python
print(re.findall(regex,"well-liked")) == ["well-liked"]
#>>> True
print(re.findall(regex,"html")) == ["html"]
#>>> True
```

### 无效示例：

```python
print(re.findall(regex,"a-b-c")) != ["a-b-c"]
#>>> True
print(re.findall(regex,"a--b")) != ["a--b"]
#>>> True
```

The first expression of the invalid examples is not correct since the second indent is not expected by the regular expression, in the second example, the same occurs.

无效示例中的第一个表达式不正确，因为正则表达式不预期第二个缩进，在第二个示例中，情况相同。

The following example will be used to match strings that represent single parameter mathematical functions:

以下示例将用于匹配表示单参数数学函数的字符串：

```python
regexp = r "[a-z] + (* [0-9] + *)"
```

This will find strings that start with one or more letters ([a-z] +), we have to escape the parentheses to take them as something we want to be part of the string, since the parentheses have a special meaning in regular expressions, we escape them with \\, then we look for zero or more spaces (*) followed by numbers ([0-9] +) and again zero or more spaces.

这将查找以一个或多个字母（[a-z] +）开头的字符串，我们需要转义括号，以便将其视为我们希望作为字符串一部分的内容，因为括号在正则表达式中有特殊含义，我们使用 \\ 转义它们，然后查找零个或多个空格（*），后跟数字（[0-9] +），再后跟零个或多个空格。

### 示例：

```python
print(re.findall(regexp,"cos(0)")) == ["cos(0)"]
#>>> True
print(re.findall(regexp,"sqrt( 2 )")) == ["sqrt( 2 )"]
#>>> True
```

### 无效示例：

```python
print(re.findall(regexp,"cos (0)")) != ["cos (0)"]
#>>> True
print(re.findall(regexp,"sqrt(x)")) != ["sqrt(x)"]
#>>> True
```

As we see, the first invalid example is precisely not valid because we do not allow spaces between the name of the function and the parentheses. The second is wrong because the parameter is a letter instead of a number.

如我们所见，第一个无效示例之所以无效，正是因为我们不允许函数名和括号之间有空格。第二个示例是错误的，因为参数是字母而不是数字。

Let's see another one, this time we want to find strings that contain escape characters () and quotes

让我们看另一个示例，这次我们想要查找包含转义字符（）和引号的字符串

```python
regexp = r """(?:[^\\]|(?:\.))*"""
```

In this case, first we are going to look for chains that are enclosed in quotation marks (r """), what we find, we will find it zero or more times (r ""(? :)*"""), (? :) matches the regular expression in the parentheses. Next, we want anything other than a \\, and note that we must escape it (r "" (?:[^\\") "" *) Or (|) a. followed by any character (r "" (?:[^\\]|(?:.))"" *))

在此示例中，首先我们将查找被引号括起来的字符串（r """"），我们找到的内容将被查找零次或多次（r ""(? :)*""""），(? :) 匹配括号中的正则表达式。接下来，我们想要除 \\ 以外的任何内容，请注意我们必须对其进行转义（r "" (?:[^\\") "" *）或（|）一个 a，后跟任意字符（r "" (?:[^\\]|(?:.))"" *）

```python
regexp = r """(?:[^\\]|(?:\.))*"""
```

### 有效示例：

```python
print(re.findall(regexp,"I say, \"hello.\"")) == ["I say, \"hello.\""]
#>>> True
```

### 无效示例：

```python
print(re.findall(regexp,""")) != ["""]
#>>> True
```

Finally, a regular expression that will match all strings that are in double quotes:

最后，一个将匹配所有位于双引号内的字符串的正则表达式：

```python
regexp = r """[\"^\"]* """
```

With this expression we look for chains that begin and end with (r `"""`), cannot contain any character`"` between the string (r `"""[\"^\"]""`), finally, we will consider the chain that meets this with any character zero or more times (r `"""[\"^\"]* """`).

使用此表达式，我们查找以（r `"""`）开头和结尾的字符串，字符串中间不能包含任何字符 `"`（r `"""[\"^\"]""`），最后，我们将任何字符出现零次或多次的符合此条件的字符串视为匹配（r `"""[\"^\"]* """`）。

### 示例：

### 有效示例：

```python
print(re.findall(regexp,"cuneiform"))
print(re.findall(regexp,"sumerian writing"))
print(re.findall(regexp,""))
```

### 无效示例

```python
print(re.findall(regexp,"esc \"ape\""))
```

