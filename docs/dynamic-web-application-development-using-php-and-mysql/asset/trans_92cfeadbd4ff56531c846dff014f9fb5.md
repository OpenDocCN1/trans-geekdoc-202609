
The above script counts the number of times the submit button has been pressed. It does this by passing a hidden form field with a value set to the number of times the form has been submitted:

```
<p><input type='hidden' name='intCount' value='<?php echo($intCount) ?>' />
```

This form field is hidden from the user but is essential in allowing the PHP script to 'remember' the total number of form submissions. The value of $intCount is incremented at the beginning of the script:

```
if (isset($_POST["submit"]) ) {
$intCount = $_POST["intCount"];
$intCount++;
}
else
$intCount = 1;
```

The output from this script is illustrated in Figure 10.18.

**图 10.18 传递隐藏的表单数据**

![](img/b2471264f405d17994ef173e4b9cec92_326_0.png)

### 练习

- **10.1** 编写一个脚本，其中包含一个表单，包含以下元素：

  - 标题（选择元素）
  - 名字（文本元素）
  - 姓氏（文本元素）
  - 用户名（文本元素）
  - 密码（密码元素）
  - 再次输入密码（密码元素）

- **10.2** 编写一个脚本以修改练习 10.1 的解决方案。你的 PHP 脚本现在应确保所有表单字段都包含数据。

- **10.3** 编写一个脚本以修改练习 10.2 的解决方案。你的 PHP 脚本现在应确保如果检测到任何错误，所有表单字段都会被保留。

- **10.4** 编写一个脚本以修改练习 10.3 的解决方案。你的 PHP 脚本现在应执行以下额外验证：

  - a. 确保两个密码字段相同。
  - b. 确保用户名与名字或姓氏不同。
  - c. 确保密码与名字、姓氏或用户名不同。

- **10.5** 编写一个脚本，使用表单提供你所做的最小硬币数量练习的值（练习 9.3）。

### 摘要

在本章中，我们首先介绍了简单的表单，并说明了用户在表单中输入的数据如何被 PHP 脚本访问。接下来我们考虑 PHP 脚本是否应与表单分开保存，以及如何确保表单始终调用自身，无论其保存的名称是什么。我们详细研究了如何访问不同表单元素的数据。最后，我们通过研究表单验证、数据保留和隐藏数据结束了本章。

### 参考文献和进一步阅读

- Refsnes Data. HTML 表单和输入。 http://www.w3schools.com/html/html_forms.asp
- 万维网联盟。 HTML 文档中的表单。 http://www.w3.org/TR/html4/interact/forms.html
- Wikipedia. Web 表单。 http://en.wikipedia.org/wiki/Form_(web)

我们在本章开始时重新审视字符串，并演示如何操作它们。我们说明如何访问单个字符串的字符、确定字符串的长度以及在字符串中查找和替换字符串。我们研究如何反转字符串、更改其大小写并加密它。

我们介绍了数组的概念并说明如何在 PHP 中创建简单的数组。我们研究 PHP 如何支持可以使用非数字键的数组，以及如何使用‘foreach’循环访问数组的内容。我们研究如何创建多维数组以及它们可用于什么。我们说明了数组必须经过转换过程才能作为表单的一部分传递的方式。最后，我们研究了标准 PHP 库中的一些函数，这些函数使我们能够操作数组，例如计算数组中数据的出现次数、对数组进行排序和实现栈。

### 11.1 字符串 – 复习

我们在之前的示例中大量使用了字符串，但我们想回顾一些关键特性，以防你第一次错过了。字符串是一系列字符，用单引号或双引号括起来以表示字符串的开始和结束，并且可以分配给变量：

```
$strFirstname = "Simon";
$strSurname = 'Stobart';
```

字符串可以使用‘echo’结构输出到浏览器：

```
echo $strFirstname;
```

echo 结构可用于在另一个字符串内输出字符串变量：

```
echo "$strFirstname";
```

在上面的示例中，值‘Simon’被显示。然而，如果变量被单引号括起来，像这样：

```
echo '$strFirstname';
```

那么输出将是 `$strFirstname`，因为显示的是字符串名称而不是其内容。

### 字符串连接

字符串可以使用点运算符连接在一起：

```
$strFirstname . $strSurname;
```

如果上面使用‘echo’结构输出，像这样：

```
echo $strFirstname . $strSurname;
```

```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td>$intLetter</td>";
    echo "</tr>";
    echo "<tr>";
    for ($intLetter=0;$intLetter<13;$intLetter++)
        echo "<td align='center'>" . $strName{$intLetter} . "</td>";
    echo "</tr>";
    echo "</table>";
?>
```

上述脚本使用两个循环输出表格的两行。第一个输出从 0 到 12 的字符偏移量数字：

```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td>$intLetter</td>";
```

第二个输出字符串字符：

```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td align='center'>" . $strName{$intLetter} . "</td>";
```

脚本其余部分主要包含‘echo’语句，这些语句构成 XHTML 表格。考虑‘echo’语句：

```
echo "<td align='center'>" . $strName{$intLetter} . "</td>";
```

我们必须使用点运算符来连接输出，因为字符串字符引用不能在双引号字符串内部自动展开。以下将不起作用：

```
echo "<td align='center'> $strName{$intLetter} </td>";
```

上述脚本的输出如 图 11.2 所示。

**图 11.2 字符串字符输出**

![](img/b2471264f405d17994ef173e4b9cec92_331_0.png)

由于我们事先不知道字符串的长度。为了解决这个问题，PHP 有一个名为‘strlen’（字符串长度）的函数，它返回字符串中的字符数：

```
length = strlen(string);
```

我们将在第 13 章解释如何创建自己的函数，但现在可能值得解释一下 PHP 函数是什么以及如何使用语言提供的一些预写函数。函数是一组相关语句，当调用时执行这些语句。函数可以编写为接收值，然后处理这些值并影响相关语句产生的结果。函数可以返回单个数据，如整数或字符串。图 11.3 以图形方式说明函数可以被视为一个“黑盒子”，数据被发送到它，结果被返回。

> **注意** — 函数在盒子内如何执行其“魔术”对用户来说是未知的。

在‘strlen’函数的情况下，它可以接受单个字符串值并返回字符串的长度。函数的用法在以下脚本中显示：

```
<?php
// File: example11-2.php

$strName = "Simon Stobart";

$intStringLength = strlen($strName);
echo "<p>The string is $intStringLength characters long</p>";
?>
```

在上述脚本中，`$strName` 的值被传递给函数，结果字符串长度存储在变量 `$intStringLength` 中。脚本的输出是：

`The string is 13 characters long`

![](img/b2471264f405d17994ef173e4b9cec92_332_0.png)

### 在字符串中查找字符串

strstr() 函数可用于在另一个字符串内查找字符串的特定部分，函数如下所示：

```
outputString=strstr(searchString, lookingForString)
```

strstr() 函数需要两个参数才能工作。第一个是我们要搜索的字符串，第二个是我们要查找的内容。函数返回从找到我们要查找的内容的那一点开始的输入字符串的剩余部分。考虑以下示例脚本：

```
<?php
// File: example11-3.php

$strName = "Simon Stobart";

$strOutput = strstr($strName, "St");
echo "<p>The result is $strOutput</p>";
?>
```

脚本在变量 `$strName` 中搜索字符串‘St’。上述脚本的输出是：

结果是 Stobart

### 替换字符串的一部分

你可能希望用另一个字符串替换字符串的一部分。str_replace() 函数可以帮助你做到这一点。函数如下所示：

```
outputString=str_replace (lookingForString, replaceString, searchString)
```

以下是函数用法的示例：

```
<?php
// File: example11-4.php

$strSentence = "The use of italics can be useful to highlight certain words";

$strOutput = str_replace("italics", "<i>italics</i>", $strSentence);
echo "<p>The string now looks like: '$strOutput'</p>";
?>
```

上述脚本搜索 `$strSentence` 字符串并将文本‘italics’替换为 `<i>italics</i>`。脚本的输出是：

字符串现在看起来像：'使用斜体可以有助于突出某些单词'

str_replace() 函数用替换字符串替换在搜索字符串中找到的所有要查找的字符串的出现次数。
