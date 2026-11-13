

- 二元运算符：需要两个操作数（值）的运算符。
- 操作数：用于数学表达式的值。
- 一元运算符：只需要一个操作数的运算符。
- 整除：丢弃小数部分的除法。
- 浮点除法：保留小数部分的除法。

算术运算符用于执行加法、乘法、减法等计算。此前介绍的算术运算符都是二元运算符，这意味着它们需要两个操作数（两个值）来应用计算。还有一些一元运算符（只需要一个操作数），例如：

| 一元运算符 | 含义 |
| --- | --- |
| - | 负数 |
| ++ | 将值递增 1 |
| -- | 将值递减 1 |

虽然理解何时使用加法、减法或乘法运算符相当简单，但理解什么是 div 和 mod 运算符可能有点棘手。

## Div：除法运算符

在 Java 和 Python 中，有两种除法：整除和浮点除法。这两种类型在 Java 中都使用相同的符号（正斜杠）。但是，当除以两个整数值时，结果将是一个整数（整除）；当除以两个浮点数或一个小数和一个整数时，结果将是一个小数（浮点除法）。

```java
int no1 = 7;
int no2 = 2;
System.out.println(no1/no2);
```

在上面的示例中，即使结果是 3.5，显示的答案也将是 3，因为这两个数是整数（整型数）。

```java
double no1 = 7.0;
double no2 = 2.0;
System.out.println(no1/no2);
```

但是，在这个示例中，因为两个变量都存储小数，显示的结果也是一个小数（3.5）。

```java
float no1 = 7.0;
int no2 = 2;
System.out.println(no1/no2);
```

在上面的示例中，存储的值是混合数据类型的数字，结果将是一个小数：3.5。

在 Python 中，由于未指定变量类型，因此有不同的运算符来表示不同类型的除法。浮点除法由 /（正斜杠）运算符执行，因此结果将是一个小数。但是，整除使用 //（双斜杠）运算符。// 将返回向下取整除法（这意味着，无论结果如何，它都会始终向下取整——发生的情况是小数部分被截断，或者更简单地说，被忽略或删除）。

```python
no1 = 7
#no1 = 7.0
no2 = 2
print (no1/no2)
```

在这个示例中，输出将是 3.5，无论两个数字的数据类型如何。

```python
no1 = 7
#no1 = 7.0
no2 = 2
print (no1//no2)
```

但是，这次输出将是 3，因为结果被截断，而没有考虑变量的数据类型。

## 编程练习

使用您选择的语言构建代码来解决以下问题。

- 1. 要求用户输入三个数字。输出它们的平均值。例如，如果输入为：3、4 和 5，则输出为 4。
- 2. 要求用户输入姓名和年龄。输出一条包含姓名和用户 10 年后年龄的消息。例如，如果输入是 Bob，15，则输出应为 [Bob，十年后你将年满 25 岁]。
- 3. 要求用户输入一个三位数。输出所有三个数字的总和。例如，如果输入是 125，则输出应为 8。

## 常见错误

编写解决问题的算法需要具体且准确。许多学生因为遗漏小细节而丢分，例如忘记初始化计数器或总计等变量。

## 活动

使用上面编程练习的解答来回答以下问题。

- 1. 问题 1 是否发生了正确的数学运算？
- 2. 你是如何将姓名和年龄拼接以显示问题 2 的输出的？
- 3. 问题 3 是否显示了预期结果？

## 活动

沟通技巧：给予和接受有意义的反馈——成对合作，交换编程练习的解答，并就如何改进或优化所提出的解答互相提供反馈。

## B2.1.2 字符串操作

在编码中，经常需要操作文本。您可能想要显示一些特殊字符，例如双引号 ""、单引号 '' 或反斜杠 \。

由于这些字符在大多数编程语言中已被用于特定目的，因此显示它们可能具有挑战性。同时，程序员可能想要提取字符串的一部分文本，将它们连接在一起，更改或删除它们。这都是如何实现的？

包含转义字符（反斜杠）支持输入语言中通常用于特定目的的特殊字符。例如，单引号用于在 Java 中存储字符，甚至在 Python 中存储字符串；双引号也是如此。因此，当想要在文本中包含单引号或双引号时，必须使用反斜杠：

| 字符 | Java 和 Python |
| :--- | :--- |
| " | \" |
| ' | \' |
| \ | \\ |

### 文本块

在 Java 中，多行字符串可以这样编写：

```java
System.out.println("Write multiple\n"
+ "Lines like this") ;
```

不同行上的文本通过 + 运算符连接在一起。\n 表示换行符，指示新的文本行将显示在下一行。

在 Python 中，可以使用三个双引号编写多行字符串：

```python
print(""" Write multiple
Lines like this
""")
```

编程语言提供了几个可用于操作字符串的内置函数。

在以下示例中，text 是一个存储一段文本的变量，例如："Computer Science is fun！"

### 长度

length 函数返回字符串 text 中存储的值的长度（字符数，包括空格）。在此情况下，x 中存储的值为 24。

```java
x = text.length()
```

```python
x = len(text)
```

**连接：** 将字符串连接在一起。

### 连接

连接是指将两个或多个字符串值连接在一起。Java 和 Python 都允许多种实现连接的方法。其中之一是使用 + 运算符，它将两个字符串连接在一起。

```java
String part1 = "Computer Science is fun";
String part2 = ", isn't it?";
String text = part1 + part2;
System.out.println(text);
```

```python
part1 = "Computer Science is fun"
part2 = ", isn't it?"
text = part1 + part2
print(text)
```

Java 中可用于连接两个字符串的另一个函数是 concat 函数：

```java
String part1 = "Computer Science is fun";
String part2 = ", isn't it?";
String text = part1.concat(part2);
System.out.println(text);
```

请注意，连接是应用于一系列字符串变量的技术，而不是字符串与整数或小数的组合。如果需要连接字符串和整数的组合，可以在 Java 中使用 + 运算符，或在连接之前将整数或小数值转换为字符串。在 Python 中，可以使用插值运算符 (%)、str 函数、str.format 或 f-strings 来实现此目的。

```java
String exam = "Computer Science";
int grade = 9;
System.out.println("Your " + exam + " exam score is " + grade);
```

```python
Python: Use of interpolation operator
exam = "Computer Science"
grade = 9
print ("%s%s%s%s" % ('Your ', exam, " exam score is ", grade))
```

```python
Python: Use of str function
exam = "Computer Science"
grade = 9
print("Your " + exam + " exam score is " + str(grade))
```

```python
Python: Use of str.format
exam = "Computer Science"
grade = 9
print("{} {} {} {}".format('Your ', exam, " exam score is ", grade))
```

```python
Python: Use of f-strings
exam = "Computer Science"
grade = 9
print(f'Your {exam} exam score is {grade}')
```

> **小贴士！**
>
> 在 Python 中，如果您想在不将内容保存到另一个变量的情况下显示两个变量的内容，可以简单地使用 print() 函数，它接受以逗号分隔的多个参数：

```python
part1 = "Computer Science is fun"
part2 = ", isn't it?"
print(part1, part2)
```

### 子字符串

substring 是用于检索字符串一部分的函数，例如，如果您想要提取字符串中的第一个单词或字母，或字符串中特定位置之间的文本。

请注意，字符串中的第一个位置是 0。

在 Java 中，为此目的使用的函数称为 substring：

```java
String text = "Computer Science is fun";
String part = text.substring(8);
System.out.println(part);
```

通过向 substring 函数提供一个参数，它指示要提取的文本的起始索引。在这个示例中，输出将是 "Science is fun"，因为变量 part 将被分配从字符串中从位置 8 开始直到字符串末尾的值，

