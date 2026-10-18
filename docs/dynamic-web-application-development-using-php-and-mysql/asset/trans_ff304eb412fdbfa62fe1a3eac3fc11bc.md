
如你所见，当我们更改变量的值时，这种简写形式只需避免两次写出变量名。变量也可以类似地递减，因此要从‘fltVariable’中减去 4，我们可以写：

```
fltVariable -= 4;
```

表 6.1 显示了所有五个算术运算符的简写表达式示例。

## 运算符优先级

当编写包含多个算术运算符的表达式时，你需要了解‘运算符优先级’，即表达式的哪一部分会先被求值。有一个标准（而且相当大）的表格适用于几乎所有语言，但其中最重要的部分显示在表 6.2 中。

请考虑以下示例：

```
var intVar = 4 + 2 * 3;
```

表 6.1 使用算术运算符的简写表达式

| 通常表达式 | 简写表达式 |
|---|---|
| fltVariable = fltVariable + 5; | fltVariable +=5; |
| fltVariable = fltVariable - 4; | fltVariable -=4; |
| fltVariable = fltVariable * 2; | fltVariable *=2; |
| fltVariable = fltVariable / 3; | fltVariable /=3; |
| fltVariable = fltVariable % 4; | fltVariable %=4; |

表 6.2 运算符优先级表中的一些重要元素

| 优先级 | 符号 | 描述 |
|---|---|---|
| 更高 | () | 括号 |
|  | ++ | 自增和自减运算符 |
|  | -- |  |
|  | * | 乘、除和取模运算符 |
|  | / |  |
|  | % |  |
|  | + | 加法和减法运算符 |
|  | - |  |
|  | *= | 简写赋值表达式 |
|  | /= |  |
|  | += |  |
|  | -= |  |
|  | %= |  |
| 较低 |  |  |

由于乘法先于加法执行，结果将为 10。如果这不是我们想要的，我们可以使用括号来改变表达式各部分求值的顺序。要强制先执行加法，我们可以写

```
var intVar = (4 + 2) * 3;
```

正如你所期望的，这给出的结果是 18，因为加法现在在乘法之前执行。如果同一表达式中出现两个相同优先级的运算符（即加法和减法，或乘法、除法和取余），则它们从左到右求值。例如，在以下表达式中，乘法在除法之前求值，得出答案 15：

```
var intVar = 10 * 3 / 2;
```

## 6.7 使用和创建对象

在第 6.4 节中，我们介绍了与 DOM 相关的一些 JavaScript 对象，例如‘document’和‘window’。在 JavaScript 中还有许多其他类型的对象可供我们使用。其中一些是可直接使用的单个对象，例如‘Math’对象，而另一些是我们可以在需要时创建的类型，例如字符串和日期。在本节中，我们介绍其中一些对象类型并了解它们如何创建和使用。

### Math 对象

算术运算符对于简单计算来说足够了，但有时我们需要能够进行更复杂数学运算的服务。在这些情况下，‘Math’对象提供了对多种数学运算的支持，包括几何方法、幂运算、舍入和随机数生成。以下脚本使用‘random’方法生成介于零和一之间的伪随机数。

```
<!-- File: Example6-5.htm -->
<script type = "text/javascript">
<!--
    document.write("Here is a random number between zero and one: ");
    document.write(Math.random() )
// -->
</script>
```

图 6.6 显示了此脚本的一种可能输出。由于 random 方法生成的数字始终介于零和一之间，推导出其他范围的随机数或随机整数需要进一步的工作。

由于 Math 类的各种方法返回数学运算的值，这些返回值可以分配给变量，例如，

```
var fltRandomNumber = Math.random();
```

Math 类还具有表示常见数学值的一些属性。其中之一是‘PI’。以下脚本元素使用‘Math.PI’，和‘Math.pow’方法，

### 图 6.6 由 Math.random() 方法生成的伪随机数

![](img/b2471264f405d17994ef173e4b9cec92_188_0.png)

### 图 6.7 使用 Math 对象计算得到的圆的面积

![](img/b2471264f405d17994ef173e4b9cec92_188_1.png)

它将第一个参数提高到第二个参数的幂，以计算圆的面积。虽然这是一个简单的示例，但它展示了 Math 类的属性和方法，将结果分配给变量，并使用括号确保计算的各部分按正确顺序进行（即我们在乘以‘PI’之前先平方半径）。

```
<!-- File: Example6-6.htm -->
<script type="text/javascript">
<!--
var intRadius = 10;
var fltArea = Math.PI * (Math.pow(intRadius, 2) );
document.write(fltArea);
// -->
</script>
```

图 6.7 显示了在浏览器中显示的计算结果。

### 字符串

JavaScript 字符串只不过是由单引号或双引号括起来的零个或多个字符的序列。你使用哪一种并不重要，但这种选择确实使你能够在一个引号内包含另一种引号，这在将 JavaScript 与 HTML 结合使用时特别有用。例如，这是一个有效的 JavaScript 字符串，其中包含带有引号属性的 HTML：

```
'<img src = "logo.gif" alt = "logo">'
```

当然，我们也可以交换引号字符：

```
"<img src = 'logo.gif' alt = 'logo'>"
```

字符串的另一个有用方面是它们可以使用‘+’运算符连接（合并）。例如，这里我们通过连接来写出一些文本和文档标题：

```
document.write("Document title is " + document.title);
```

你可以将不同数据类型与字符串连接起来，它们将被视为单个字符串。字符串还具有许多属性和方法。例如，'length'属性返回字符串中的字符数，而'substring'方法返回两个指定字符位置之间的字符串部分。以下脚本同时使用'length'属性和'substring'方法来显示字符串的最后一个字符。请注意，方法返回的子字符串从第一个参数指定的字符位置之后开始，但包含第二个参数指定的位置处的字符：

```
<!-- File: Example6-7.htm -->
<script type = "text/javascript">
<!--
var strFullString = "a string";
var intLength = strFullString.length;
var strSubString = strFullString.substring(intLength-1, intLength);
document.write("Last character is " + strSubString);
// -->
</script>
```

图 6.8 显示了脚本在浏览器中的结果。

### 图 6.8 在浏览器窗口中显示的子字符串

![](img/b2471264f405d17994ef173e4b9cec92_189_0.png)

### 日期对象

与作为浏览器环境一部分的对象以及内置于 JavaScript 中的‘Math’对象不同，表示日期和时间的‘Date’对象需要在需要时创建。能够即时创建‘Date’对象也意味着我们可以创建和操作任意数量的对象。在 JavaScript 中创建对象使用保留字‘new’和构造函数方法，该方法与对象类型同名，并且像其他方法一样后面跟有括号。新建的‘Date’对象可以分配给变量：

```
var dateToday = new Date();
```

我们可以用日期做什么？基本上我们可以使用默认设置，其中包括其创建的日期和时间，或者专门设置其值。如果你简单地将日期对象写入文档，你将获得机器使用的本地时区相对于协调世界时（UTC）的当前日期和时间，UTC 基于格林威治标准时间。你还可以使用‘toUTCString’方法以 UTC 显示当前日期和时间，或使用‘toLocaleString’方法以当前本地时区相对于 UTC 显示时间。在以下脚本中，我们以这三种不同的方式显示同一个日期对象：

```
<!-- File:Example6-8.htm -->
<script type="text/javascript">
<!--
var dateToday = new Date();
document.write("The current date and time is: " + dateToday);
document.write("<br />The date and time in Coordinated Universal Time is: " + dateToday.toUTCString() );
document.write("<br />The date and time using the current locale is: " + dateToday.toLocaleString() );
// -->
</script>
```

不同浏览器显示日期的方式略有不同。图 6.9 显示了这三个版本的日期在 Mozilla Firefox 2 中的显示方式，但其他浏览器在呈现方面会略有不同。

表 6.3 显示了 Date 类的一些其他方法。

### 数组

数组是一组具有相同名称但由索引值标识的值，索引值出现在方括号中。与 Date 对象一样，数组也可以即时创建，我们可以拥有任意数量的数组，因此它们再次使用保留字‘new’创建，例如：

```
var arrMyArray = new Array(size);
```

‘size’参数将是一个指定数组中元素数量的数字。我们可以使用包含索引的方括号设置或检索数组中的值
