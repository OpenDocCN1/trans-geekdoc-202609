# Web 专业人士 PHP 高级指南





## 第 1 章 PHP 复习
### 概述](#)
- PHP 语法
- 变量
- 运算符
- 数组
- If/Then 语句
- Switch 语句
- For 循环
- Foreach 循环
- While 循环
- Do While 循环
- 自定义函数
- PHP 面向对象编程
- `phpinfo()`
- 其他资源

## 第 2 章 会话管理
### PHP4 会话管理简介
- 初始化
- 启动会话
- 会话文件的内容
- 会话期间的跨页面变量跟踪
- 注销会话变量
- 销毁会话
- 简单的基于会话的购物车
- DBX：PHP 对多数据库的支持
- 创建自己的多数据库支持
- 使用 Pear::DB

## 第 4 章 更好的表单处理
### Better 表单简介
- Post 和 Get
- 脚本解析（Souping）
- 表单字段检查
- 使用 `$HTTP_GET` 和 `$HTTP_POST`
- 变量变量

## 第 5 章 运用所学：简单的购物车
### 简介](#
- 购物车的功能
- 设置
- 代码

## 第 6 章 文件操作
### 概述](#)
- 打开与关闭文件
- 实际应用
- 数据挖掘
- 解析大文件

## 第 7 章 PHP 身份验证
### 用户身份验证概述
- 生成密码
- 基于文本文件的用户身份验证

## 第 9 章 运用所学：会议跟踪器
### 简介](#
- [设置](#
- [代码](#

## 第 10 章 PHP 与 XML
### 概述](#
- [创建 XML 解析器](#
- [解析与转换 XML 文档](#
- [将数据库内容导出到 XML 文件](#

## 第 11 章 使用 PHP 生成动态图形
### 概述](#
- [GD 库](#
- [启用 GD 支持](#
- [使用 GD 生成图形](#

## 第 12 章 PHPGTK
### PHPGTK 简介
- [安装 PHPGTK](#
- [创建基础 GTK 对象](#
- [汇总](#
- [简单的 PHPGTK 应用](#

---

作者：Christopher Cosentino

在这本简明且实战的教程中，PHP 专家 Christopher Cosentino 提供了数十种用于构建严肃 Web 应用的强大新技术。通过其六年来 PHP 开发的经验总结的专业级示例，Cosentino 将引导你构建更易用、更友好的网站；改进用户身份验证；生成动态图形；解析 XML 文档；构建与数据库无关的 Web 应用以及更多内容！





### PHP4 会话管理简介
### 会话管理的初始 `php.ini` 设置
## 启动会话
## 会话文件的内容
### 会话期间跨页面的变量跟踪
### 注销会话变量
### 销毁会话
### 基于会话的简单购物车

## 第 3 章 多数据库交互
### PHP4 中的高级数据库交互
### PHP 中的特定数据库函数
## DBX—PHP 对多数据库的支持
### 创建自己的多数据库支持
### 使用 `Pear::DB`

## 第 4 章 更好的表单处理
### 更好的表单简介
### Post 和 Get
### 增强脚本
### 表单字段
### 使用 `$_GET` 和 `$_POST`
### 整合在一起
### 变量

## 第 5 章 运用所学——购物车
### 简介
### 购物车的功能
### 配置
### 代码实现

## 第 6 章文件操作
### 概述
### 打开与关闭文件
### 实际应用
### 数据
### 解析大型文件

## 第 7 章 PHP 身份验证方案
### 用户验证概述
### 生成密码
### 通过文本文件进行用户验证
### 通过 IP 地址进行用户验证
### 使用 HTTP 身份验证进行用户验证
### 通过数据库查询进行用户验证

## 第 8 章 错误管理
### 概述
### 错误报告

## 第 9 章 运用所学——会议跟踪应用
### 简介
### 配置
### 代码实现

## 第 10 章 PHP 与 XML
### 概述
### 创建 XML 解析器
### 解析与转换文档
### 将数据库内容导出到 XML 文件

## 第 11 章 使用 PHP 生成图形
### 概述
### GD 库
### GD 支持
### 使用 GD 画图形

## 第 12 章 PHP
### PHP 简介
### 安装 PHP
### 创建基础对象
### 整合在一起
### 简单的 PHP 



### 致谢
- 编辑/制作监督：Kathleen M. Caren
- 高级执行编辑：John Neidhart
- 封面设计总：Jerry Votta
- 封面设计：Talar A. Booruy
- 生产经理：Alexis R. Heydt-Long
- 市场经理：Bryan Gambrel
- 编辑助理：Brandt Kenna
- 系列设计：Gail Cocker-Bogusz







### 本书目标

本书的目标是帮助你更好地掌握 PHP，学习一些不常使用的特性，并帮助你构建一些在你的工作或爱好中有帮助的应用程序。我希望它能为你提供一些思路，让你自己开发的应用程序更易于编码、更易使用。

### 本书目标读者

本书适用于那些已经进行过基础 PHP 编程，并希望学习一些更高级的技术以使应用程序更易用、更易编程的人。。

我收到了许多来自各地读者的邮件，他们是我的第一本书——`Essential PHP for Web Professionals`（同样由 Prentice Hall 出版）的读者，他们非常喜欢我提供的简洁风格和丰富的示例。我甚至收到了几十封邮件，发件人说他们虽然读过其他的 PHP 编程书籍，但在读我的书之前，并没有真正理解 PHP 的工作原理。我无法言形容这让我感到多么高兴。我希望这本书也能达到同样的效果。

这本书写给那些准备好更进一步、学习更多 PHP 知识的你。这本书并不是参考书，也没有涵盖 PHP 的每一个高级方面。然而，它确实超出了基础范围，介绍了一些有助于你进行 PHP 编程的概念。

### 获取代码

本书所有的代码都可以在 `www.phptr.com/advancedweb/php` 的高级 Web 页面获取。你可以从该页面下载每个章节的所有示例。该网页还将包含任何更新或勘误说明，以及常见问题的解答。如果你在阅读本书时遇到任何真正的困难，请随时发送邮件到 `cosentino@digital-salage.net` 与我联系。我在书中之所以提到这一点，是因为我收到了大量寻求 PHP 帮助的邮件。如果是简单的问题，我通常可以回答任何问题，但最近邮件邮件让我有些应接不来，可能无法回答所有问题。请注意，我不能总是立即回答你的问题。我会尽快回答，但有时可能需要几天时间。

### 致谢

我由衷感谢该项目的编辑 `Karen McLean` 和 `John Neidhart`，感谢他们的支持与耐心。我还想非常感谢 `Jan Schwartz` 在我第一本书制作中出的工作。感谢 `Micah Brown` 对本书以及 Prentice Hall 出版的 `Advanced Series of Web design` 系列书籍所付出的工作。我还要感谢 `Leon Atkinson` 对本书草稿提出的细致评论，并感谢他编写了我购买的第一本书——`Core PHP Programming`。它帮助我开启了 PHP 编程的大门。诚挚 `Allan Brumer` 在 BSD 上对代码提供的帮助评论和测试。感谢你的帮助，Allan！我非常愿意再次与你合作其他项目。特别感谢马萨诸塞大学的 `Professor John R. Nelson, Jr. 教授`，感谢他的帮助、指导和智慧，并帮助我起步。谢谢你，约翰叔！当然，还要向亲爱的 `Sarah` 表示最诚挚的感谢和无限的爱，感谢她在写书期间对我坐在电脑前度过又几个小时时的耐心支持。最后，感谢那些发邮件告诉我我的第一本书对他们有帮助的读者。谢谢你们！我希望这本书也能帮到你们。


以下内容来自 GNU 网站 `http://www.gnu.org/`。



```






```





























*   如果您希望将程序的某些部分整合到分发条件不同的自由程序中，请写信向作者寻求许可。对于由自由软件基金会版权的软件，请写信给自由软件基金会；我们有时会为此类情况提供特例。我们的决策将受到两个目标的指引，即维护我们所有自由软件衍生品的自由状态，以及促进软件的的共享和重用。




![](img/15011533.htm)

* * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#fmlev1sec4.htm) ![下一节](img/#ch01_split_000.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#copyrightpg_split_000.htm) ![下一节](img/#pref02_split_000.htm) |
| --- |

* * *

## Prentice Hall PTR 高级 Web 开发系列

*   高级 JavaScript：洞察与创新技术，Livingston
*   高级 Macromedia Flash MX：实战 ActionScript，第二版，Livingston and Justiniano
*   Web 专业人士的高级 PHP，Cosentino
*   Web 开发的高级 SOAP，Livingston
*   开发基于 SVG 的 Web 应用程序，Pearlman and House

![](img/15011533.htm)

* * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#copyrightpg_split_000.htm) ![下一节](img/#pref02_split_000.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#pref01_split_00.htm) ![下一节](img/#pref03_split_000.htm) |
| --- |

* * *

## 关于 Prentice Hall 专业技术参考

Prentice Hall Professional Technical Reference (PH PTR) 的起源可以追溯到 20 世纪 60 年代第一个计算机科学出版计划，如今已发展成为全球领先的技术书籍供应商。我们的品牌于 1986 年正式作为独立品牌推出，现在我们的编辑每年出版超过 200 本书籍，其作者来自计算、工程和商业领域的领军人物。我们的根基深植于孕育技术的土壤之中：Kernighan 和 Ritchie 的 C 语言、Nemeth 的系统管理、Horstmann 的 Core Java。PH PTR 在展望未来的同时铭记起点。我们通过提供今天的解决方案不断演进和突破。![graphics/prenticehall.gif)| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#copyrightpg_split_000.htm) ![下一节](img/#pref02_split_000.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#pref01_split_000.htm) ![下一节](img/#pref03_split_000.htm) |
| --- |

* * *

## 第 1 章.PHP 复习

*   概述
*   PHP 语法
*   变量
*   运算符
*   数组
*   If/Then 语句
*   Switch 语句
*   For 循环
*   Foreach 循环
*   While 循环
*   Do While 循环
*   自定义函数
*   使用 PHP 进行对象编程
*   phpinfo
*   其他资源

### 概述

PHP 是一种设计为易于嵌入 HTML 页面的语言（尽管你不必这样做）。大多数 PHP 页面都是 PHP 代码和 HTML 混合的。当 Web 服务器读取 PHP 页面时，它会寻找两个标记来告知它应该以 PHP 而不是 HTML 启动页面，即 PHP 的起始和结束标记：`<?php` 和 `?>`。

如果你配置了 `php.ini` 文件以接受“短标签”（默认启用），那么你可以使用 `<?` 和 `?>` 代替。此外，你还可以配置 `php.ini` 文件使其接受 ASP 风格标签 `<%` 和 `%>`。此功能默认关闭，其唯一的真实目的似乎允许某些 HTML 编辑器将中间的代码识别为 HTML 之外的内容，这样编辑器就不会通过强加自身的一套 HTML 语法规则来破坏代码。

嵌入 HTML 的 PHP 简短示例：

```
<h1>Welcome To The Web Site Of <? echo $company; ?>!</h1
```

上述代码通过 Web 服务器查看时，简单地在 PHP 代码位置打印出公司名称。

通常，单行 PHP 代码应该以分号结束，但如果使用了起始或结束括号，则没有需要使用分号（这在看 if/then 语句时就能理解了）。

例如：

```php
<? 
echo "<p>a line of code";
echo "<p>another line of code;
?>
```

### PHP 语法

本书假设你已经有一定的 PHP 经验。这本书并不是一本入门读物，而是一本为那些可能需要快速复习或已经熟悉类似语言（如 PERL）的人提供的更高级用法的书籍。

尽管如此，我仍然提供了关于 PHP 的简短介绍。例如：

```php
<? 
echo "<p>a line of code";
echo "<p>another line of code;
?>
```





| ![](img/#index.htm)   ![Previous section](img/#ch01lev1sec1.htm)   ![Next section](img/#ch01lev1sec3.htm) |
| Top |
| --- |
| ![](img/#index.htm)   ![Previous section](img/#ch01lev1sec2.htm)   ![Next section](img/#ch01lev1sec4.htm) |
| --- |

* * *

### 变量

你也可以轻松地将小的 PHP 代码嵌入到 HTML 中，例如打印变量的值时：

```php
<h1>Today's Date is <?= $date ?>.</h1> 
```

PHP 中的 `<?=` 语法在后跟变量时，用作 `echo()` 函数的简写。

你可以在 PHP 脚本中包含注释。Web 服务器会忽略注释，PHP 代码中的任何注释都不会发送到浏览器。注释有三种形式：

*   `#`—用法与在 PERL 中相同；注释 `#` 符号之后行的剩余部分。
*   `//`—用法与在 JavaScript 中相同；注释 `//` 符号之后行的剩余部分。
*   `/*` 和 `*/`—注释掉两组符号之间的任何内容。这与 C 语言中注释代码的语法相同。

PHP 代码中的注释示例：

```php
<? 
echo "Hello"; #打印出 "Hello"
echo "Hello"; //打印出 "Hello"
/* The following
prints out "Hello" */
echo "Hello";
?>
```

你经常看到使用 `//` 字符或 `/*` 和 `*/` 字符表示的注释。`#` 字符很少见，尽管它仍然有效。

PHP 变量由 `$` 表示。要给变量 `$a` 赋值 "Hello World"，你只需在代码中调用它：

```php
$a = "Hello World"; 
```

字符串必须用引号包含，但它们本身可以包含变量：

```php
$a = 4; 
$string = "The value of a is $a";
// $string = "The Value of a is 4";
```

PHP 变量不需要预先声明，也不需要定义类型。注意，如果你尝试在给变量赋值之前使用，可能会收到关于使用未声明变量的警告（取决于你在 `php.ini` 中如何设置错误报告，请参阅[第 8 章]）。例如：

```php
$a = 4; 
$c = $a + $b;
// $c = 4, 但会出现警告 "Warning: Undefined variable.."
```

警告不会阻止脚本继续。如果你忘记在某行的末尾添加分号，你将得到解析错误（Parser error），这将阻止脚本运行。

由于 PHP 变量不是强类型的，你不需要担心像在 C 语言中那样在错误的类型上进行数学运算。例如：

```php
$a = 4; 
$b = "5";
$c = $a + $b;
// $c = 9;
```

PHP 还支持布尔变量，可以赋值 1 或 0，或者 true 或 false 单词：

```php
$a = true; 
$b = 1;
//$a = $b
$c = false;
$d = 0;
//$c = $d
```

* * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm)   ![Previous section](img/#ch01lev1sec2.htm)   ![Next section](img/#ch01lev1sec4.htm) |
| Top |
| --- |
| ![](img/#index.htm)   ![Previous section](img/#ch01lev1sec3.htm)   ![Next section](img/#ch01lev1sec5.htm) |
| --- |

* * *

### 运算符

PHP 对运算符的支持包括以下内容：

#### 算术运算符

PHP 支持标准的数学运算符：

```php
$a = 4; 
$b = 2;
//加法: $a + b = 6
//减法: $a - $b = 2
//乘法: $a * $b = 8
//除法 :$a / $b = 2
//取模 ($a / $b 的余数): $a % $b = 0
//自增: $a++ (由于 $a = 4，将等于 5)
```

#### 赋值运算符

PHP 中两个主要的赋值运算符是 `=` 和 `.`。等号显而易见，它为变量赋值：

```php
$a = 4; 
$b = $a;
// $b = 4
```

#### 比较运算符

PHP 支持标准的比较运算符，如[表 1-1]所示：

| 运算符 | 描述 |
| --- | --- |
| `$a == $b` | 测试两个值是否相等 |
| `$a != $b` | 测试两个值是否不相等 |
| `$a < $b` | 测试第一个值是否小于第二个值 |
| `$a > $b` | 测试第一个值是否大于第二个值 |
| `$a <= $b` | 测试第一个值是否小于或等于第二个值 |
| `$a >= $b` | 测试第一个值是否大于或等于第二个值 |

PHP 还支持自增和自减运算符：

```php
$a = 4; 
$a++; // $a = 5
$b = 5;
$b--; // $b = 4
```

#### 字符串拼接

`.` 运算符连接两个值：

```php
$a = "The ";
$b = "fox";
$c = $a . $b;
// $c = "The fox"
```

* * *

### 数组

PHP 支持数值数组（按顺序索引）以及关联数组（按键索引）。

```php
$fruits = array("apple", "banana", "cherry");
$age = array("Ben"=>"35", "Peter"=>"37", "Joe"=>"43");
```

* * *

### if/then 语句

你常见的语言结构之一是 if/then 语句。if/then 语句允许你评估一个表达式并根据其真假采取行动。例如：

```php
$a = 1;
if($a) {
  echo "True!";
}
```

由于 `$a = 1`，PHP 在 if 语句上下文中将其解释为布尔类型。由于 1 为真，if 语句输出了消息。另一个例子，这次带有 "else" 子句：

```php
$a = 5;
$b = "10";
if($a > $b) {
    echo "$a is greater than $b";
} else {
    echo "$a is not greater than $b";
}
```

PHP 不关心 `$a` 是整数而 `$b` 是字符串。它意识到 $b 也是一个很好的整数。它然后评估表达式：“如果 $a 大于 $b$，则打印 $a$ 大于 $b$；如果不是（else），则打印 $a$ 不大于 $b$。”同样重要的是，你没有说 "$a 小于 $b$”，因为 $a$ 可能等于 $b$。如果是这种情况，那么表达式的后半部分即 else 语句就是执行的部分。

注意使用括号来包裹操作。同样注意在括号使用的地方没有分号。

最后一个例子是 if/elseif/else 语句：

```php
if($a == $b) { 
    // 执行某些操作
} elseif ($a > $b) {
    // 执行其他操作
} elseif($a < $b) {
    // 执行再次其他操作
} else  {
    // 如果其他都不符合，我们执行这个...
}
```





在 C 语言中，`switch` 语句的出现是为了在进行 `if/then` 类型的计算时需要一些额外的支持。使用 `if/then` 语句时，你被限制在单一条件下。`switch` 语句允许对数据进行额外的评估，即使其中一个 `case` 已经满足。`switch` 语句还可以避免你编写大量的 `if/elseif/elseif/…` 语句。PHP 遵循了 C 对 `switch` 语句的使用。

```php
$a = "100"; 
switch($a) {
    case(10):
      echo "The value is 10";
      break;
    case (100):
      echo "The value is 100<br>";
    case (1000):
      echo "The value is 1000";
      break;
    default:
      echo "<p>Are you sure you entered a number?";
}
```

如你所示，`switch` 语句包含四个基本部分：

- **switch**: `switch` 识别在每个 `case` 中将要评估的值或表达式。在上面的示例中，你告诉 `switch` 语句你将在后续的情况下中评估变量 `$a`。
- **case**: `case` 语句评估你从 `switch` 命令传递的变量。你可以像使用 `if` 语句一样使用 `case()`。如果 `case` 为真，则执行 `case` 语句之后的所有内容，直到解析器遇到 `break` 命令，此时执行停止并退出 `switch`。
- **Breakpoints（断点/跳出）**: 由 `break` 命令定义，使解析器退出 `switch`。断点通常放在满足 `case()` 时执行的语句之后。
- **Default（默认值）**: `default` 是一种特殊的 `case`。如果 `switch` 中没有其他 `case` 语句被执行，则会执行它。

### For 循环 (For Loops)

For 循环是遍历有限数据集合的有用结构，例如数组中的数据：

```php
for($i = 0; $i < sizeof($array); $i++) { 
    //对 array[$i] 进行某些操作
}
```

For 循环在定义时需要三个要素：

- **Counter（计数器）**: 在上面的示例中为 `$i = 0`。你可以传递一个已经赋值的变量，或者在 `for` 语句中为变量赋值。
- **condition（条件）**: 继续 `for` 循环所需的条件：在上面的示例中，只要 `$i` 小于 `$array` 的大小，`for` 循环就会继续执行。
- **statement（语句）**: 在每次循环中修改计数器的语句：在上面的示例中，`$i++` 在每次循环后增加计数器。

### Foreach 循环 (Foreach Loops)

Foreach 循环允许你快速遍历数组。

```php
$array = array("name" => "Jet", "occupation" => "Bounty Hunter" ); 
foreach ($array as $val) {
    echo "<P>$val";
}
```
输出：
<P>Jet
<P>Bounty Hunter

你也可以使用 `foreach` 循环获取数组中值的键（key）：

```php
foreach ($array as $key => $val) { 
    echo "<P>$key : $val";
}
```
输出：
<P>name : Jet
<P>occupation : Bounty Hunter

### While 循环 (While Loops)

`while` 循环是另一种有用的结构。`while` 循环持续持续直到循环中的表达式为假。`while` 循环的一个常见用途是从结果集中返回行：

```php
while($row = fetch_array(result)) {
    // 某些操作
}
```

你还可以使用 `continue` 来跳过当前迭代，例如：

```php
while($row = fetch_array(result)) {
    if($row['name'] != "Jet") {
        continue;
    }
    // 执行某些操作
}
```

### Do While 循环 (Do While Loops)

`do while` 循环的工作原理与 `while` 循环完全相同，但 `do while` 循环在循环完成后评估表达式，而不是像 `while` 循环那样在循环之前。`do while` 循环至少执行一次：

```php
$i = 0;
do {
   print $i;
} while ($i>0);
```

而以下代码可能完全不会执行：

```php
$i = 0;
while($i > 0) {
   print $i;
}
```

### 自定义函数 (User-Defined Functions)

除了 PHP 的内置函数外，你还可以创建自己的函数。记住，如果你想使用函数外部存在的变量，必须将它们声明为全局变量，或者将它们作为参数传递给函数。

```php
function check_age($age) { 
    if ($age > 21) {
        return 1;
    } else {
        return 0;
    }
}
// 使用：
if(check_age($age)) {
    echo "You may enter!";
} else {
    echo "Access Not Allowed!";
    exit;
}
```

函数将在你的脚本内部适当时间通过以下语法被调用：

```php
$age = 10; 
check_age($age);
// 在屏幕上打印 "Access Not Allowed!"
```

### PHP 面向对象编程 (Object Oriented Programming with PHP)

PHP 以类的形式支持面向对象编程 (OOP)。就像在其他 OOP 语言中一样，可以扩展类以实现代码的更高重用。

创建一个包含人的姓、名和电话号码的地址条目类：





```php
class address_book_entry { 
    var $first;
    var $last;
    var $number;
    function set_name($first, $last) {
      $this->first = $first;
      $this->last = $last;
    }
    function set_number($number) {
      $this->number = $number;
    }
    function display_entry() {
      echo "<p>Name: " . $this->first . " " . $this->last;
      echo "<br>Number: " . $this->number;
    }
}
// Usage:
$entry = &new address_book_entry;
$entry->set_name("Jane","Smith");
$entry->set_number("555-555-5555");
$entry->display_entry();
// 显示:
Name: Jane Smith
Number: 555-555-5555
```

此外，你可以扩展现有类来创建一个新类，该类将具有旧类相同的功能，加上你添加的任何新功能：

```php
class address_book_entry2 extends address_book_entry { 
var $email;
function set_email($email) {
       $this->email = $email;
    }
    function display_entry2() {
      echo "<p>Name: " . $this->first . " " . $this->last;
      echo "<br>Number: " . $this->number;
      echo "<br>Email: " . $this->email;
    }
}
// Usage:
$entry = &new address_book_entry2;
$entry->set_name("Jane","Smith");
$entry->set_number("555-555-5555");
$entry->set_email("jsmith@com.com");
$entry->display_entry();
// 显示:
Name: Jane Smith
Number: 555-555-5555
Email: smith@com.com
```

* * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch01lev1sec12.htm) ![下一节](img/#ch01lev1sec14.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch01lev1sec13.htm) ![下一节](img/#ch01lev1sec15.htm) |
| --- |

* * *

### phpinfo( )

`phpinfo()` 是一个非常有用的函数，它允许你查看你的 Web 服务器上运行的是哪个版本的 PHP，以及该版本中启用的所有特定设置。

在本书中，会有一些章节要求你验证自己的设置。实现这一点的一种方法是创建一个仅包含以下内容的脚本：

```php
<? 
    phpinfo();
?>
```

执行该脚本后，浏览器将显示当前的 PHP 设置。如果你正在他人的服务器上工作，并且不确定它的功能，那么这个函数将特别有用。

* * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch01lev1sec13.htm) ![下一节](img/#ch01lev1sec15.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch01lev1sec13.htm) ![下一节](img/#ch01lev1sec15.htm) |
| --- |

## 第 2 章 Session 管理

### 2.1 Session 简介
本章向你介绍如何使用 PHP 管理 Session。Session 允许你在页面之间存储信息。

Session 是通过一个唯一的 ID 来标识的。这个 ID 通常存储在浏览器的 Cookie 中，但如果禁用了 Cookie，Session ID 可以在 URL 中传递。在本章，你将学习如何启动、使用和销毁 Session。

### 2.2 启动 Session
要启动 Session，必须调用 `session_start()` 函数。这应该在脚本的最开始部分，在任何输出到浏览器之前完成。

```php
<?php
session_start();
```

### 2.3 Session 内容
一旦启动了 Session，你就可以使用 `$_SESSION` 全局变量存储数据。

```php
<?php
session_start();
$_SESSION["username"] = "John";
$_SESSION["role"] = "admin";
?>
```

### 2.4 销毁 Session
要销毁 Session，可以使用 `session_destroy()` 函数。

```php
<?php
session_start();
session_destroy();
?>
```

### 2.5 配置
在本章开始之前，你可能需要对 php.ini 文件进行一些微调，以便 Session 正常工作。

#### Windows
如果你使用的是 Windows 版本的 PHP，第一件事是编辑 php.ini 文件。php.ini 中的默认 Session 设置在 Windows 下无法正常工作。

用文本编辑器打开 php.ini 文件（位于 `c:\windows` 或 `c:\winnt`），并搜索以下行：

```ini
session.save_path = /tmp
```

将其更改为你存放临时文件的目录，例如：

```ini
session.save_path = C:/temp
```

你也可以保留该值为 /tmp，并在你的 Web 服务器所在的磁盘根目录下创建一个 "tmp" 的目录。例如，如果你的 Web 服务器位于 D:/apache/bin，那么你可以创建 d:/tmp，而无需更改 php.ini 中的 session.save\_path 设置。

在 Windows 上，session.save\_path 设置错误的良好迹是：当你尝试加载启用 Session 的页面时，Apache 会崩溃。

#### Linux
如果你使用的是 Linux，你需要确保 /tmp 目录可以由运行 Web 服务的用户写入。这通常是 nobody 用户，大多数系统默认都允许 nobody 用户写入 /tmp 目录。

其余的默认 Session 设置在本章的示例中应该都能正常工作。

### 更多资源
如果你还需要更多关于 Session 的信息，可以参考以下书籍：

*   PHP Programming to Build Dynamic Websites (2nd Edition) by Atkinson
*   Essential PHP for Web by Cosentino
*   Core PHP: Using PHP by Prentice Hall





你不应该将会话文件（session files）存储在任何从 Web 服务器可见的目录中。如果你使用的是 `Apache`，那么任何 `htdocs` 目录下的目录都是如此。你不希望将会话文件放置在 Web 服务器可见的目录中的，是因为恶意用户可能会打开这些文件并查看单个会话数据，甚至通过这种方式劫持用户会话。

## 启动会话

除非你在每个想要使用或更改变量的页面上启动会话，否则你无法跨用户会话跟踪变量。启动会话使用 `session_start()` 函数：

```
session_start(); 
```

`session_start()` 不接受任何参数。如果你正在启动一个新的会话，该函数将初始化会话并创建必要的临时文件来跟踪会话。如果函数通过 cookie 或 `GET` 变量发现了 `$PHPSESSID`，则函数将恢复当前会话，页面将可以任何已注册到会话的变量。

一旦你启动了会话，你就需要向会话注册一些变量。在通过 `session_register()` 函数注册变量之前，会话不会跟踪这些变量：

```
session_register(STRING); 
```

`session_register()` 的 `STRING` 参数应该是你想注册到会话的变量名称，以便可以在任何启用会话的页面上访问它。

一旦你启动了会话并注册了一个或多个变量，你就可以在网站的任何启用会话的页面使用这些变量。脚本 2-1 `session.php` 提供了一个启动会话和注册变量的简单示例。

### 脚本 2-1 session.php

```
1.  <?
 2.  session_start();
 3.  if(!isset($count)) {
 4.    session_register("count");
 5.    $count = 1;
 6.  }
 7.  ?>
 8.  You have been to this page <?=$count?> times.
 9.  <?
10.  $count++;
11.  ?>
```

### 脚本 2-1 session.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2 | 启动会话或继续已有的会话。 |
| 3 | `if` 语句检查 `$count` 变量是否已设置。如果 `$count` 变量已设置，则脚本假设这是会话的延续，不采取任何操作，并继续到第 7 行。 |
| 4 | 如果 `$count` 变量未设置，则脚本假设这是一个新会话的开始，并注册变量 `$count`。 |
| 5 | 由于脚本在上一行刚刚注册了变量 `$count`，因此它使用此行为 `$count` 分配一个默认值 1。 |
| 8 | 显示一行文本，说明页面被访问的次数。 |
| 10 | 将 `$count` 变量加 1。 |

运行此脚本并多次点击刷新按钮。注意，每次你刷新页面时，页面访问次数都会增加 1。图 2-1 显示了这种示例。关闭浏览器然后在新浏览器中重新加载页面会将 `$count` 重置为 '1'，因为关闭浏览器实际上结束了会话。

### 图 2-1 session.php

![graphics/02fig01.jpg)

## 会话文件的内容

你可以通过查看 `php.ini` 文件中 `session.save_path` 设置指定的目录来查看会话变量的实际内容。在该目录下，你应该能看到一个类似于 "sess_c4a972c1745304544dc5cc1" 的文件。重要部分是文件名是以 `sess_` 开头的。之后的随机字符串是 PHP 分配给每个会话的唯一标识符。如果你在一个共享站点上或过去运行过任何会话，可能会有几个看起来像 PHP true 的文件。尝试找到时间戳与你访问示例时最接近的一个，但打开任何一个文件都会让你对会话变量是如何存储的。。在文本编辑器中打开文件将显示以下内容：

```
count|i:6;
```

文件中显示的实际数字将有所不同，取决于你重新加载页面的次数。文件内容显示变量名，后面是一个管道符号 `|`，然后是变量类型标识符——在这种情况下 "i" 代表整数——最后是变量的值，后跟分号。如果你在会话中注册了多个变量，它们将按照注册的顺序列出，大多数情况下用分号分隔。例如，如果你在会话中注册了两个整数变量 `$count` 和 `$day`，它们将如下所示：

```
count|i:6;day|i:7;
```

表 2-1 详细列出了你在典型会话文件中可能会看到的常见变量类型。

### 表 2-1 会话文件中的变量类型标识符

| 符号 | 变量类型 |
| --- | --- |
| i | 整数 (Integer) |
| s | 字符串 (String) |
| b | 布尔 (Boolean) |
| d | 浮点数 (Float) |
| a | 数组 (Array) |
| O | 对象 (Object) |
| N | NULL |

## 会话期间跨页面跟踪变量

现在你已经如何启动会话并跟踪某些变量，如何利用这些呢？会话有无数用途，但会话真正的益处是减少你和 Web 服务器的工作量。考虑一个拥有注册用户的典型站点。该站点可能有论坛、用户可以回应的故事，以及用户可以选择启用或禁用的各种功能。

通常，你会将这些偏好存储在某些数据库中，并在用户登录站点时加载。你需要一种方法在用户查看的每个页面上记住这些值。如果用户不想在某个页面上看到投票功能，那么可以假设他们也不想在其他页面上看到它。你可以在用户每次加载页面时查询数据库以查看应该启用哪些功能，或者可以将这些信息存储在 cookie 中，但每种方法都有缺点。对于大型站点，每次加载页面都查询数据库会导致严重的服务器资源问题。





这正是会话（sessions）大显用场。你可以存储可以在多个页面访问的值。通过在会话开始时加载用户偏好，你可以将数据库查询减少到最低，并且只需要担心在用户的浏览器上存储一个 cookie，从而消除了对任何网站在浏览器上存储的 cookie 数量有限的顾虑。如果你使用 `PHP` 的会话链接重写功能，你甚至不需要担心这一个 cookie！

在接下来的示例中，你将把一些默认变量加载到会话中，就像它们来自数据库查询一样，然后将在脚本 2-3 `track_prefs2.php` 中验证会话变量是否有效。结果将显示在图 2-2 中。

#### 脚本 2-2 track_prefs1.php

```
1.  <?
 2.  session_start();
 3.  session_register("first");
 4.  session_register("last");
 5.  session_register("email");
 6.  session_register("news_prefs");
 7.  ?>
 8.  <html>
 9.  <head>
10.  <title>Welcome</title>
11.  <style type="text/css">
12.    p, ul, h3 {font-family: verdana, helvetica, sans-serif;}
13.    .enabled {font-weight: bold; color: green;}
14.    .disabled {font-weight: bold; color: red;}
15.  </style>
16.  </head>
17.  <<body>
18.  <?
19.  function load_user_data(){
20.    global $first, $last, $email, $news_prefs;
21.    $first = "Faye";
22.    $last = "Valentine";
23.    $email = "faye@bebop.com";
24.    $news_prefs = array(
25.      "Local" => 0,
26.      "Nation" => 1,
27.      "World" => 1,
28.      "Comics" => 0,
29.      );
30.  }
31.  load_user_data();
32.  ?>
33.  <h3>Welcome</h3>
34.  <p>Welcome back <b><?=$first?></b>
35.  <p>Your settings have been loaded.
36.  <p><a href=track_prefs2.php>View Your Settings</a>.
37.  </</body>>
38.  </html>
```

#### 图 2-2. track_prefs2.php

![graphics/02fig02.jpg](img/02fig02.jpg)

#### 脚本 2-2. track_prefs1.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有的会话。 |
| 3–6 | 注册在整个会话期间使用的会话变量。 |
| 8–17 | 打印 HTML 页面的开头。 |
| 19 | 声明一个新函数 `load_user_data()`。 |
| 20 | 允许函数使用并修改脚本全局范围内的变量。这些变量对应于脚本之前注册的会话变量。 |
| 21–23 | 给会话变量分配一些字符串。 |
| 24 | 将数组赋值给会话变量 `$news_prefs`。 |
| 25–29 | 为数组分配项。 |
| 31 | 运行 `load_user_data()` 函数。 |
| 33–36 | 通知用户其设置已加载，并提供查看设置的链接。 |
| 37–38 | 关闭页面的 HTML 标签。 |

#### 脚本 2-3 track_prefs2.php

```
1.  <?
 2.    session_start();
 3.  ?>
 4.  <<html>
 5.  <head>
 6.  <title>View Settings</title>
 7.  <style type="text/css">
 8.    p, ul, h3 {font-family: verdana, helvetica, sans-serif;}
 9.    .enabled {font-weight: bold; color: green;}
10.    .disabled {font-weight: bold; color: red;}
11.  </style>
12.  </head>
13.  <<body>
14.  <h3>View Your Settings</h3>
15.  <p>Hello <b><?=$first?> <?=$last?></b>,
16.  <p>Email: <?=$email?>
17.  <p>Your settings:<<ul>>
18.  <?
19.  while(list($key,$value) = each($news_prefs)) {
20.    if($value) {
21.      $value = "Enabled";
22.    } else {
23.      $value = "Disabled";
24.    }
25.    print("<li class=$value>$key: $value</li>");
26.  }
27.  ?>
28.  </ul>
29.  </body>>
30.  </html>
```

#### 脚本 2-3 track_prefs2.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有的会话。 |
| 4–13 | 打印 HTML 页面的开头。 |
| 14–17 | 欢迎用户并显示其姓名、邮箱和设置列表开头。 |
| 19–26 | 遍历 `$news_prefs` 数组。如果值为真，则将其设为“Enabled（已启用）”，否则设为“Disabled（已禁用）”。打印每个键值值。 |
| 27–30 | 关闭页面的 HTML 标签。 |




如果你一直在查看 `session.save_path` 目录下的会话文件内容，你可能会注意到那里堆积了一些文件，这取决于你打开了多少个会话示例。这些文件在用户关闭浏览器结束会话时仍然存在未被删除，是因为我们没有去销毁会话。你必须显式地销毁会话，会话文件才会被删除。之所以这样做，是因为你无法判断用户会在会话中持续多久。用户启动会话后，回家过完晚上（甚至过一个漫长的周末！），第二天回来时浏览器仍然打开在桌面上，这是完全可能的。如果用户一直在购物，由于上述原因，你肯定不想在一段固定的有限时间后删除他们的会话。

有两种方法可以应对临时目录中文件的堆积，且在大多数情况下不会对用户的会话产生不利影响。

第一种是使用 `session_destroy()` 函数：

```
session_destroy(); 
```

`session_destroy()` 不接受参数。`session_destroy()` 会注销与用户会话关联的所有会话变量，并删除会话创建的任何会话文件。请记住，即使变量从会话中被注销，该变量仍然存在于当前页面且其值保持不变。

接下来的脚本演示了 `session_destroy()` 函数的使用。

### 脚本 2-4 session2.php

```
1.  <?
 2.  session_start();
 3.  if(isset($destroy)) {
 4.    session_destroy();
 5.    unset($name);
 6.  } else {
 7.    if(!session_is_registered("name")) {
 8.      session_register("name");
 9.      $name = "Spike";
10.      }
11.  }
12.  ?>
13.  <p>SESSID: <?=$PHPSESSID?>
14.  <p>Name: <?=$name?>
15.  <form action=session2.php method=post>
16.  <input type="submit" name="reload" value="Reload Session"><br>
17.  <input type="submit" name="destroy" value="Destroy Session">
18.  </form>
```

### 脚本 2-4. session2.php 逐行解释

| 行 |  |
| --- | --- |
| 2 | 启动会话或继续现有会话。 |
| 3–5 | 检查 `$destroy` 变量是否设置。如果设置了，说明用户点击了“Destroy”（销毁）按钮。 |
| 6–10 | 如果未设置 `$destroy`，则注册名为 `$name` 的会话变量并将该变量赋值为 "Spike"。 |
| 13–14 | 打印当前会话 ID 和 `$name` 变量的值。 |
| 15–18 | 向用户显示表单，允许其刷新当前页面或销毁与当前会话关联的会话变量。如果用户刷新页面（通过点击“Reload”或使用浏览器的刷新按钮），会话变量将重置并显示会话 ID 值。如果用户点击“Destroy”按钮，则与页面相关的会话文件将被删除，从而删除会话变量的值。 |

在点击“Reload Session”和“Destroy Session”按钮时，注意你临时目录中的文件。每次你点击“Destroy Session”，注意具有相应会话 ID 的会话文件会从你的 `session.save_path` 目录中删除。每次点击“Reload Session”都会在该目录中重新创建文件。

管理孤立会话文件的另一种方法是利用 PHP 对这些会话文件的自动“垃圾”清理。用文本编辑器打开你的 `php.ini` 文件并滚动到 `[session]` 设置。查找以下两个设置：

```
; 每次会话初始化时启动“垃圾回收”过程的百分比概率。
session.gc_probability = 1
; 在此秒数之后，存储的数据将被视为“垃圾”，并由垃圾回收过程
; 进行清理。
session.gc_maxlifetime = 1440
```

第一个设置 `session.gc_probability` 设置了被识别为垃圾文件的删除百分比概率。默认值“1”意味着每次启动会话时有 1% 的概率。

第二个设置 `session.gc_maxlifetime` 设置了会话在标记为垃圾之前可以存在的寿命（秒为单位）。默认值“1440”意味着超过 24 分钟的每个会话都被视为垃圾。




```php
1.  <?
 2.  session_start();
 3.  $inventory = array(
 4.      "001" => "Tooth Paste",
 5.      "002" => "Facial Tissue",
 6.      "003" => "Cotton Swabs",
 7.      "004" => "Shampoo",
 8.      "005" => "Conditioner",
 9.      "006" => "Deodorant"
10.      );
11.  function populate_cart() {
12.    global $name, $email, $items;
13.    $items = array(0, 0, 0, 0, 0, 0);
14.    session_register("name");
15.    session_register("email");
16.    session_register("items");
17.  }
18.  function get_user_info() {
19.    ?>
20.    <<h3>在继续之前请向我们提供以下信息：</h3>
21.    <form action=session_cart.php method=post>
22.    <p>姓名: <input type="text" name="name">
23.    <br>邮箱: <input type="text" name="email">
24.    <p><input type="submit" name="infosubmit" value="提交">
25.    </form>
26.    <?
27.  }
28.  function shop() {
29.    global $name, $email, $items, $inventory;
30.    ?>
31.    <p>在下方购物：
32.    <form action=session_cart.php method=post><p>
33.    ?>
34.    $total = 0;
35.    for($i = 0; $i < sizeof($inventory); $i++) {
36.      ?>
37.      商品 ID: <b><?=key($inventory);?></b> 描述: <b><?=$inventory[key(
$inventory)]?</b></b>
38.      数量: <input type="text" name="items_in[<?=$i?>]" value="<?=$items[$i]?>" size="2" 
maxlength="2"><br>
39.      ?>
40.      next($inventory);
41.      $total = $total + $items[$i];
42.    }
43.    ?>
44.    <p>您的购物车中有 <?=$total?> 件商品。
45.    <p><input type="submit" name="additems">
46.    </form>
47.    ?>
48.    if($total > 0) {
49.      ?>
50.      <form action=session_cart_checkout.php>
51.      <input type="submit" name="checkout" value="结算!">
52.    </form>
53.      ?>
54.    }
55.  }
56.  /* 主程序 */
57.  if(isset($additems)) {
58.      ?>
59.    $items = $items_in;
60.    echo("<h3>购物车已更新！</h3>");
61.    shop();
62.  }elseif(!isset($name)) {
63.    get_user_info();
64.  } elseif(isset($infosubmit)) {
65.    populate_cart();
66.    shop();
67.  } else {
68.    shop();
69.  }
70.  ?>
```

### Script 2-5. session_cart.php 逐行说明

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有会话。 |
| 3–10 | 创建一个数组作为商店中的可用商品。 |
| 11 | 声明一个新函数 `populate_cart()`。该函数初始化用户的购物车。 |
| 12 | 为用户声明一些全局变量。`$items` 是购物车中的商品。 |
| 13 | 将用户购物车中的商品清零。 |
| 14–16 | 将已声明的变量注册到会话中。 |
| 18–27 | 当用户首次到达购物车时，声明函数 `get_user_info()`。该函数要求输入姓名和邮箱。 |
| 28 | 声明 `shop` 函数。该函数负责在用户的购物车中添加和删除商品。 |
| 29 | 允许函数访问并修改 `$name`、`$email`、`$items` 和 `$inventory`。 |
| 32 | 创建购物表单。 |
| 34 | 给变量 `$total` 赋值 0。该变量用于显示购物车中的商品总数，在用户添加或移除商品时进行计算。 |
| 35 | 遍历 `$inventory` 数组。 |
| 37–38 | 显示商店库存中每个商品的 ID (`key`) 和描述 (`value`)。同时，在文本输入框中显示用户购物车中的商品数量。如果用户未向购物车添加任何商品，所有值读取为 0，这是用于初始化购物车的值。 |
| 40 | 使用 `next()` 函数，以便在下次循环执行时可以使用下一个键。 |
| 41 | 将用户购物车当前的商品总数累加到循环计数中。 |
| 42 | 退出 `for` 循环。 |
| 44 | 显示当前总数。 |
| 45 | 显示“添加商品”按钮。用于执行主程序中的 `additems` 子句。 |
| 48–54 | 如果购物车中至少有一个商品，则显示“结算”按钮，将用户引导至 `session_cart_checkout.php`。 |
| 55 | 函数结束。 |
| 56 | 开始主程序。 |
| 57–59 | 检查是否点击了“添加商品”按钮。如果是，向用户显示购物车已更新（`items` 已更新）。 |
| 58 | 如果点击了“添加商品”按钮，用表单中的 `$items_in` 替换会话变量 `$items`。在提交表单变量时，会话变量不会自动更新，需要显式赋值新值。 |
| 59 | 向用户显示购物车已更新。 |
| 60 | 运行 `shop()` 函数，以便用户可以添加或移除商品。 |
| 61 | 如果未点击“添加商品”按钮且 `$name` 变量未设置，则执行 `get_user_info()` 函数，因为这是用户首次访问页面。 |
| 63–65 | 如果上述条件均不成立但 `$infosubmit` 变量已设置，说明用户刚刚输入了信息。执行 `populate_cart()` 初始化购物车。 |
| 66–68 | 如果没有发生其他情况，直接执行 `shop` 函数。此时用户已输入信息且购物车已初始化，但尚未添加商品。 |

### Script 2-6. session_cart_checkout.php 全宽视图

```php
1.  <?
 2.  session_start();
 3.  $inventory = array(
 4.      "001" => "牙膏",
 5.      "002" => "纸巾",
 6.      "003" => "棉签",
 7.      "004" => "洗发水",
 8.      "005" => "护发素",
 9.      "006" => "去味剂"
10.      );
11.  if(!isset($name)) {
12.    ?>
13.    <h2>抱歉，您需要先 <a href=session_cart.php>添加商品</a>才能结算。</h2>
14.    <?
15.  }elseif(isset($finish)) {
16.    ?>
17.    <h3>订单完成！</h3>
18.    <?
19.    // 发送邮件确认...
20.    // 将订单发送到处理脚本...
21.    session_unset();
22.    session_destroy();
23.  } else {
24.    ?>
25.    <h2>结算</h2>
26.    <p>感谢 <?=$name?> 的购物，您的订单如下：
27.    <p><table border=1>
28.    ?>
29.    $total = 0;
30.    for($i = 0; $i < sizeof($inventory); $i++) {
31.      ?>
32.      <td>商品 ID: b><?=key($inventory);?></b></td>
33.      <td>描述: <b><?=$inventory[key(
$inventory)]?</b></td>
34.      <td>数量: <?=$items[$i]></td></tr>
35.      ?>
36.      next($inventory);
37.      $total = $total + $items[$i];
38.    }
39.    ?>
40.    <tr><td colspan=3 align=right>总计: <?=$total?></td></tr>
41.    </table>
42.    <p>在您完成订单后，订单确认信息将发送至邮箱地址：<b>><?=$email?></b>。
43.    <p>
44.    <form action=session_cart.php>
45.      <input type="submit" name="continue" value="继续添加商品">
46.    </form>
47.    <form action=session_cart_checkout.php>
48.      <input type="submit" name="finish" value="完成订单">
49.    </form>
50.    ?>
51.  }
52.  ?>
```

##### Script 2-6. session_cart_checkout.php 逐行说明

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有会话。 |
| 3–10 | 创建一个数组作为商店中的可用商品。 |
| 11 | 检查 `$name` 是否设置。如果是，说明已有会话数据。 |
| 12–14 | 如果 `$name` 未设置，说明没有会话数据或订单未完成。重回到购物车页面以便用户注册姓名和邮箱并添加商品。 |
| 15 | 如果 `$finish` 变量已设置，显示订单完成消息。 |
| 19 | 发送邮件确认的占位符。 |
| 20 | 将订单发送到处理脚本的占位符。 |
| 21 | `session_unset()`。 |
| 22 | `session_destroy()`。 |
| 24 | 否则，显示结算标题。 |
| 26 | 显示“感谢 $name$ 的购物，您的订单如下：”。
| 27 | 开启表格。 |
| 29 | 初始化 `$total` 为 0。 |
| 30 | 遍历 `$inventory` 数组。 |
| 32–34 | 在表格行中显示每个商品的 ID、描述和数量。 |
| 36 | 使用 `next()` 到下一个键。 |
| 37 | 将当前商品数量累加到 `$total`。 |
| 40 | 在表格行中显示最终总计。 |
| 41 | 关闭表格。 |
| 42–43 | 在用户完成订单后，订单确认信息将发送至邮箱：$email$。 |
| 44–46 | 提供一个继续添加商品的表单。 |
| 47–49 | 提供一个完成订单的表单。 |





| 15 || 检查是否已点击了“完成订单”。 |

| 16–20 || 如果点击了“完成订单”按钮，则通知用户订单已完成。然后执行任何必要的处理，例如发送电子邮件或将订单发送到订单处理脚本。 |

| 21 || 删除所有会话变量，因为我们不再需要这些数据了。 |

| 22 || 销毁会话以从服务器磁盘上移除会话文件。这样做的额外好处是，防止用户点击“刷新”或“后退”按钮，从而避免为同一件物品产生多个订单。 |

| 23 || 如果订单尚未确定，且我们知道会话中已设置 `$name` 变量，则执行脚本的剩余部分。 |

| 25–41 || 使用来自 `$inventory` 数组和用户购物车 `$items` 中的数据显示表格。此表格与 `session_cart.php` 脚本中显示购物表单的表格类似，不同之处在于字段是编辑的。 |

| 42 || 显示一条消息，向用户说明点击“完成订单”按钮后会发生什么详情。 |

| 43–46 || 提供一个按钮，让用户可以返回并编辑购物车中的项目。 |

| 47–49 || 显示“完成订单”按钮，以便用户确认他们的订单。 |

| 51 || 关闭第 11 行开始的 if/elseif/else 语句。 |

***

## 第 3 章 多数据库交互

### 本章内容

*   PHP4 中的高级数据库交互
*   PHP 中的特定数据库函数
*   DBX—PHP 对多数据库的支持
*   创建你自己的多数据库支持
*   使用 `PEAR::DB`

### PHP4 中的高级数据库交互

如果你已经接触了 PHP 一段时间，你很可能已经注意到它对连接 MySQL 数据库的卓越支持。市面上大多数 PHP 书籍只描述了 PHP 对 MySQL 的数据库支持。但 PHP 支持更多的数据库，且提供的支持程度几乎与 MySQL 相同。从 4.1 版本开始，PHP 以后各种形式支持以下数据库：

*   MySQL— [www.mysql.com](http://www.mysql.com)
*   mSQL— [www.hughes.com.au](http://www.hughes.com.au)
*   MS SQL (Microsoft SQL server；仅限 Win32 系统)
*   filePro (只读)— [www.fptech.com](http://www.fptech.com)
*   Informix—（来自 IBM） [www.informix.com](http://www.informix.com)
*   InterBase— [www.interbase.com](http://www.interbase.com)
*   Oracle— [www.oracle.com](http://www.oracle.com)
*   Ovrimos— [www.ovrimos.com](http://www.ovrimos.com)
*   Sybase— [www.sybase.com](http://www.sybase.com)
*   DB++—实验性— [www.concept-asa.de](http://www.concept-asa.de)
*   DBM—适用于多种版本 *nix* 的扁平文件数据库
*   PostgreSQL— [www.pgsql.com](http://www.pgsql.com)
*   Frontbase— [www.frontbase.com](http://www.frontbase.com)

基本上，PHP 已经拥有足够的内置支持来满足你的大多数数据库需求，特别是因为它包含了对 Oracle、Sybase、Informix 和微软等商业巨头的支持。

遗憾的是，每个被支持的数据库都有不同的函数来完成相同的操作。例如，连接到 MySQL 数据库使用 `mysql_connect` 函数，而连接到 MS SQL 服务器则使用 `mssql_connect`。这两个函数几乎完全相同，但名称不同。





使用上述所有信息并无妨，但如果主机是 `localhost`，端口是默认端口 `5432`，且该用户没有关联密码，那么你可以直接使用：

```
pg_connect("dbname=test user=username"); 
```

请参阅特定的 PostgreSQL 实现文档以获取相关信息。本章中的示例假设你正在默认端口 `5432` 上运行 PostgreSQL 服务器，因此 `pg_connect` 示例中未包含端口号。

## 选择合适的数据库

一旦你成功连接到数据库服务器，接你就需要选择要在哪个数据库上执行查询。

在 PostgreSQL 的情况下，你已经在 `pg_connect()` 函数中选择了数据库，因此没有选择数据库的函数。

然而，在使用 MS SQL 或 MySQL 时，你仍然需要使用相应的函数来选择数据库：

```
mysql_select_db(STRING) 
```

或者

```
mssql_select_db(STRING) 
```

在每情况下，`STRING` 指向你正在连接的数据库名称。

## 查询数据库以插入、读取或删除数据

一旦连接到数据库服务器并选择了数据库，接下来的逻辑步骤是以查询的形式对数据进行某些操作。大多数数据库接受查询中的任何标准 SQL 命令，也接受它们自己的特定数据库命令。

示例中使用的三个数据库都使用相同的语法：

*   `mysql_query(STRING);`
*   `mssql_query(STRING);`
*   `pg_query(STRING);`

其中 `STRING` 是一个 SQL 语句，例如 `"SELECT name FROM phonebook WHERE name = 'Sarah'."`。

## 获取查询结果并展示给用户

一旦你完成了查询，你需要获取结果并将其显示给用户，或者对其进行某些其他处理。实现这一点的简单方法之一是使用大多数支持 PHP 的数据库包含的 `fetch_array` 函数。

*   `mysql_fetch_array(RESULT);`
*   `mssql_fetch_array(RESULT);`
*   `pg_fetch_array(RESULT);`

结果中的数据被加载到数组的字段中（既是关联又是索引）。结果中的每一列都被加载到数组的字段中。数组的键与返回数据的列名对应。

***

## DBX—PHP 对多数据库的支持

对于不需要复杂的特定数据库查询应用程序，可以使用 PHP 内置的 DBX 函数。

在使用 DBX 函数之前，如果你使用的是 Linux，则必须在编译时启用支持；如果你使用的是 Windows，则需要启用 DBX 模块。

### 在 Linux 中启用 DBX

如果你使用 Apache 的 APXS 功能编译 PHP（`compile --with-apxs=/path/to/apache/bin/apxs`），那么为 PHP 模块添加功能将轻而易举。

在重新编译 PHP 之前，我建议你先删除 `config.cache` 文件并清理上次编译留下的文件。可以这样操作：

```
cd /path/to/php/source 
rm config.cache
make clean
```

在执行 `make clean` 命令后，你会注意到有很多文件被删除了。不用担心，`make` 程序只是在清理它在重新编译时不需要的文件。如果不运行 `make clean` 命令，你可能会遇到一些问题。如果你一直没有问题地编译 PHP，但突然它无法正确编译了，即使你没有更改任何内容，那么 `make clean` 命令很可能解决你的问题。

一旦你清理了上次编译留下的混乱，就可以开始新的编译了。

要编译编译启用了 DBX 支持的 PHP，请从 shell 提示符执行以下命令（根据需要替换特定安装的路径）：

```
./compile --with-apxs=/usr/local/apache/bin/apxs \ 
--enable-dbx \
```

你还应该启用你任何想要使用的数据库的支持——例如：

```
--with-mssql 
```

在运行 `configure` 之后，执行命令：

```
make 
```

假设没有发生错误，你就可以执行命令：

```
make install 
```

最后一条命令将 `libphp4.so` 库文件复制到 `/path/to/apache/libexec/`。

重启 Apache 以加载新库：

```
/path/to/apache/bin/apachectl restart 
```

你可以通过使用 `phpinfo()` 函数并验证 DBX 是否列在配置部分下，来确认 DBX 已正确安装。

### 在 Windows 中启用 DBX

在 Windows 上启用 DBX 支持非常简单，因为 DLL 文件已经预编译并包含在基础 PHP 安装中。打开你的 `php.ini` 文件并搜索如下行：

```
extension_dir = 
```

此行应指向扩展所在的位置。如果你没有将扩展移动到与 `php.ini` 文件相同的目录，你需要编辑该行，例如：

```
extension_dir = C:\Apache\php\
```

接下来，在 `php.ini` 中找到以下部分，取消（删除行开头的分号）包含 DBX 库的行：

```

```

取消该行的注释后，保存文件并重启 Apache 服务器。你可以通过使用 `phpinfo()` 函数并验证 DBX 是否列在配置部分下，来确认 DBX 已正确安装。

### DBX 函数

DBX 函数是一组单一函数，允许你访问多个数据库而无需编写自己的封装函数。

从 4.1 版本开始，PHP DBX 支持以下数据库：

*   mysql
*   odbc
*   pgsql
*   mssql
*   fbs

DBX 可用函数如下：

#### dbx_close(CONNECTION)

`dbx_close()` 函数接受一个参数 `CONNECTION`。`CONNECTION` 是在你调用 `dbx_connect()` 时创建的标识符。

#### dbx_connect(MODULE, HOST, DATABASE, USER, PASSWORD, PERSISTENT)

`dbx_connect()` 函数用于与数据库服务器建立连接，并指定使用的数据库。`dbx_connect` 返回一个包含连接句柄以及其所连接数据库名称的对象。详情见示例。`dbx_connect` 函数接受六个参数：

*   `MODULE`——你想要为此连接使用的数据库模块。该模块本质上是你尝试连接的数据库类型。值可以是：
    *   `DBX_MYSQL`——用于 MySQL 数据库。
    *   `DBX_ODBC`——用于支持 ODBC 连接的任何数据库。
    *   `DBX_PGSQL`——用于 PostgreSQL 数据库。
    *   `DBX_MSSQL`——用于 MS SQL 数据库。
    *   `DBX_FBSQL`——用于 Frontbase 数据库。
*   `HOST`——数据库服务器的主机或 IP 地址。
*   `DATABASE`——数据库服务器上的数据库名称。
*   `USER`——用户名。
*   `PASSWORD`——用户密码。
*   `PERSISTENT`——是否建立持久连接。如果你希望连接持久，请在此处放置 `DBX_PERSISTENT`。否则，此参数不是必需的。

示例：[/



```
$module = DBX_MYSQL; //注意这里没有引号！ 
$dbconn = dbx_connect($module, "192.168.0.5", "php", "mysqluser", "password") or DIE (
"无法连接");
//$dbconn->database = "php"
//$dbconn->handle 是一个资源标识符
```

### `dbx_error(CONNECTION)`

`dbx_error` 函数返回对模块上一次函数调用的错误信息。参数 `CONNECTION` 是你在调用 `dbx_connect()` 时定义的连接标识符。

示例：

```
$result = dbx_query($dbconn, "select something from non_existing_table"); 
if ($result == 0) {echo dbx_error($dbconn); }
//响应：Table 'php.non_existing_table' 不存在
```

### `dbx_query(CONNECTION, SQL STATEMENT, FLAGS)`

`dbx_query` 函数允许你向数据库发送 SQL 查询。如果查询没有失败且返回了一行或多行，则它返回一个对象。返回零行的查询不会返回对象。相反，它返回 1，表示查询成功但没有返回数据，例如从一个没有数据的表中进行 **select *** 操作。其参数为：

*   `CONNECTION`—当调用 `dbx_connect()` 函数时创建的连接标识符。
*   `SQL STATEMENT`—一个标准的 SQL 语句。
*   `FLAGS`—你可以通过指定以下一个或多个标志来规定查询返回的信息量。默认情况下，所有标志都是开启的。在指定标志时，必须使用 `|` 符号分隔它们——例如 "DBX_RESULT_INDEX | DBX_RESULT_INFO"。这些标志包括：
    *   `DBX_RESULT_INDEX`—始终返回。结果数组中的所有结果都通过数字索引，例如 `$result[0]`、`$result[1]` 等。
    *   `DBX_RESULT_INFO`—返回关于所返回列的信息，例如字段名和字段类型。
    *   `DBX_RESULT_ASSOC`—将返回的数组的键设置为为列名。

`dbx_query` 返回的对象包含以下属性：

*   `handle`—与 `$dbconn->handle` 相同的句柄。通过 `$result->handle` 访问。
*   `cols`—结果集中的列数。通过 `$result->col` 访问。
*   `rows`—结果集中的行数。通过 `$result->rows` 访问。
*   `info`—仅在标志位参数中指定了 `DBX_RESULT_INFO` 或 `DBX_RESULT_ASSOC` 时才会返回。提供一个包含列名及其类型的二维数组。通过 `$result['info'][$x]` 和 `$result['name'][$x]` 访问，其中 `$x` 是特定行的索引。
*   `data`—包含来自结果的实际数据。通过 `$result->data[$x]['field name']` 访问，其中 `$x` 是特定行的索引。

示例：

```
$result = dbx_query($dbconn, "select something from 
some_table", DBX_RESULT_INFO);
```

### `dbx_sort(RESULT, SORT FUNCTION)`

`dbx_sort` 函数允许你使用自定义的排序函数对查询结果进行排序。然而，在 SQL 语句中使用 "ORDER BY" 子句会更高效。`dbx_sort` 接受的参数为：

*   `RESULT`—上一个 `dbx_query` 语句的结果。
*   `SORT FUNCTION`—你的自定义排序函数。

示例：

```
function my_sort { 
       //你的自定义排序定义
}
dbx_sort($result, "my_sort");
//$result 现在已根据 my_sort() 完成了排序
```

### `dbx_compare(ROW1, ROW2, COLUMN KEY, FLAGS)`

`dbx_compare` 函数允许你比较两个结果集，`ROW1` 和 `ROW2`。如果 `ROW1 = ROW2`，则 `dbx_compare` 返回 0。如果 `ROW1 > ROW2`，则 `dbx_compare` 返回 1。如果 `ROW1 < ROW2`，则 `dbx_compare` 返回 -1。`dbx_compare` 接受的参数为：

*   `ROW1`—来自 `dbx_query` 函数调用的结果。
*   `ROW2`—来自 `dbx_query` 函数调用的结果。
*   `COLUMN KEY`—应进行比较的列名。
*   `FLAGS`—你可以指定多个标志来按升序或降序比较行，并规定进行何种类型的比较。用管道符分隔任何类型的顺序。
    *   `DBX_CMP_ASC`—（默认）按升序比较。
    *   `DBX_CMP_DESC`—按降序比较。
    *   `DBX_CMP_NATIVE`—（默认）“原样”比较项目。
    *   `DBX_CMP_TEXT`—作为字符串比较项目。
    *   `DBX_CMP_NUMBER`—作为数字比较项目。

示例：

```
$comp = dbx_compare ($r1, $r2, "income"); 
//$如果 $r1 = $r2 则 $comp = 0
```





- 19: 定义数据库服务器的主机名或 IP。
- 20: 定义数据库用户的用户名。
- 21: 定义数据库用户的密码。
- 22: 在数据库服务器上定义数据库名称。
- 24: 定义一个函数来查询数据库并返回数据库中的 URL。
- 25: 执行查询。注意调用 `dbx_query()` 函数之前有一个 `"@"` 符号。`"@"` 符号会抑制函数在出现问题（例如数据库宕机）时可能发出的任何警告。有关处理这些错误的更多信息，请参阅第 8 章。
- 26: 如果 `$result == 0`，则发生了错误，因为在成功时，`dbx_query` 应该返回一个对象。
- 27: 如果第 26 行为真，则打印错误。
- 28–30: 如果没有错误，则返回结果对象。
- 30: 结束函数声明。
- 32: 定义一个名为 `url()` 的函数，用于从数据库中添加或删除 URL。该函数接受以下参数：
    - `$action`——"add" 或 "delete"
    - `$dbconn`——到数据库的连接链接
    - `$url`——要添加或删除的 URL
    - `$description`——URL 的描述
- 33: 如果参数 `$action` 为 `"add"`，则表示我们正在添加 URL。
- 34: 生成添加 URL 的 SQL 语句。
- 35: 如果 `$action` 不是 `"add"`，则检查它是否为 `"delete"`。
- 36: 解码编码的 URL。
- 37: 生成删除 URL 的 SQL 语句。
- 38: 结束第 33 行开始的 if/else 语句。
- 39: 使用生成的 SQL 查询数据库。
- 40: 如果 `$result == 0`，则发生了错误，因为在成功时，`dbx_query` 应该返回一个对象。
- 41: 向用户显示错误，包括特定的 DBX 错误消息。
- 42–44: 如果查询数据库时没有错误，则向用户显示成功消息。
- 45: 结束函数。
- 46: 开始主程序。
- 47: 使用脚本开头定义的变量生成数据库连接字符串。
- 49–53: 打印显示标题的页面 HTML 以及添加 URL 的表单。
- 55–57: 如果点击了 "Add URL!" 按钮，则运行 `url()` 函数。
- 58–60: 如果点击了任何 URL 旁边的 "Delete"链接，则运行 `url()` 函数。
- 61: 生成获取 URL 的 SQL 语句。
- 62: 使用上述生成的 SQL 运行 `get_url()` 函数从数据库中获取 URL。
- 63: 检查 `get_urls()` 函数返回的结果集中是否有数据。如果没有数据，则说明数据库为空。
- 65: 向用户显示数据库为空的消息。
- 67: 如果数据库不为空，则执行脚本的剩余部分。
- 70–71: 创建一个显示 URL 的表格。
- 73: 启动 for 循环，遍历从 `get_url()` 函数返回的数据。
- 75: 将 URL 打印到表格中，并包含该 URL 的超链接。
- 76: 在表格中打印 URL 的描述。
- 77: 为该 URL 打印删除链接。
- 79: 结束 for 循环。
- 81: 结束第 63 行开始的 if/else 语句。
- 83–84: 关闭页面的 HTML。

### 为多个数据库创建你自己的支持支持

如果你有一个不需要复杂的数据库交互的简单应用程序，但你仍然希望它支持多个数据库，那么你可以创建自己的一套数据库包装函数。

你必须考虑到可能出现的不同特定特定限制，并针对最低共同标准进行编码。也就是说，如果你还想支持 MS SQL 或 PostgreSQL 数据库，就不能使用 MySQL 支持的有用 `"AUTO_INCREMENT"` 列功能，因为它们没有实现该功能。同样，MySQL 不支持辅助键，因此你不能使用该约定。下一个示例提供了一个支持 MySQL、MS SQL 和 PostgreSQL 的示例数据库包装器。它被称为 `DBlib`，包含了表 3-1 中列出的函数：

##### 表 3-1. DBlib.php 函数

| 函数 | 描述 |
| --- | --- |
| `connectDB(DB_ID)` | 连接到数据库服务器并返回 `DB_CONNECTION`。 |
| `selectDB(DB_ID)` | 选择在服务器上哪个数据库。 |
| `queryDB(DB_ID, QUERY)` | 向数据库发送 SQL 查询。返回 `RESULT` 集合。 |
| `returnDBarray(DB_ID, RESULT)` | 返回 `RESULT` 集中行的数组。 |
| `numrowsDB(DB_ID, RESULT)` | 返回上次查询受影响的行数。 |
| `closeDB(DB_ID, DB_CONNECTION)` | 关闭与数据库的连接。 |

示例的第一部分是 `DBlib.php` 文件，将其包含在你自己的应用程序中。

##### 脚本 3–2 DBlib.php





```php
<?
  function connectDB($db) {
  global $host, $database, $username, $password;
  switch($db) {
    case ("psql"):
      $conn_string = "host=" . $host . " dbname=" . $database . " user=" . $username . " password=" . $password;
      $dbconn = pg_connect($conn_string) or die ("Error Connecting to PostgreSQL DB");
      return $dbconn;
      break;
    case ("mysql"):
      $dbconn = mysql_connect($host, $username, $password) or die ("Error Connecting to MySQL DB");
      return $dbconn;
      break;
    case("mssql"):
      $dbconn = mssql_connect($host, $username, $password) or die ("Error Connecting to MS SQL DB");
      return $dbconn;
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function selectDB($db) {
  global $database;
    switch($db) {
    case ("psql"):
      return 1;
      break;
    case ("mysql"):
      mysql_select_db($database) or die ("Error Connecting to MySQL DB");
      return 1;
      break;
    case("mssql"):
      mssql_select_db($database) or die ("Error Connecting to MS SQL DB");
      return 1;
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function queryDB($db, $query) {
    switch($db) {
    case ("psql"):
      if(!$result = @pg_exec($query)){
        $result = 0;
      }
      break;
    case ("mysql"):
      if(!$result = @mysql_query($query)){
        $result = 0;
      }
      break;
    case("mssql"):
      if(!$result = @mssql_query($query)){
        $result = 0;
      }
      break;
    default;
      echo "<P>Invalid Database: $db";
      $result = 0;
    }
    return $result;
  }

  function returnDBarray($db, $result) {
  if($result != "error") {
    switch($db) {
      case ("psql"):
        if(!$array = @pg_fetch_array($result)){
          $array = 0;
        }
        break;
      case ("mysql"):
        if(!$array = @mysql_fetch_array($result)){
          $array = 0;
        }
        break;
      case("mssql"):
        if(!$array = @mssql_fetch_array($result)){
          $array = 0;
        }
        break;
      default;
        echo "<P>Invalid Database: $db";
        $array = 0;
    }
    return $array;
  }
  }

  function closeDB($db,$dbconn) {
    switch($db) {
    case ("psql"):
      if(!@pg_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    case ("mysql"):
      if(!@mysql_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    case("mssql"):
      if(!@mssql_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function numrowsDB($db, $result) {
    switch($db) {
    case ("psql"):
      if(!$rows = @pg_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    case ("mysql"):
      if(!$rows = @mysql_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    case("mssql"):
      if(!$rows = @mssql_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    default:
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }
?>
```

### 脚本 dbib.php 逐行解释

#### 1. connectDB 函数
`connectDB($db)` 函数初始化数据库连接。
- **第 2-3 行**: 定义全局变量 `$host`、`$database`、`$username` 和 `$password`。
- **第 4 行**: 根据 `$db` 类型开始一个 switch 语句。
- **第 5-9 行 (psql)**: 构建 `$conn_string`，使用 `pg_connect()` 连接到 PostgreSQL 并返回 `$dbconn`。
- **第 10-13 行 (mysql)**: 使用 `mysql_connect()` 连接到 MySQL 并返回 `$dbconn`。
- **第 14-17 行 (mssql)**: 使用 `mssql_connect()` 连接到 MS SQL 并返回 `$dbconn`。
- **第 18-21 行 (default)**: 如果无效，则输出错误并返回 0。

#### 2. selectDB 函数
`selectDB($db)` 函数选择数据库。
- **第 24-25 行**: 访问全局变量 `$database`。
- **第 26-29 行 (psql)**: 返回 1。
- **第 30-33 行 (mysql)**: 执行 `mysql_select_db($database)` 并返回 1。
- **第 34-37 行 (mssql)**: 执行 `mssql_select_db($database)` 并返回 1。
- **第 38-41 行 (default)**: 如果无效，则输出错误并返回 0。

#### 3. queryDB 函数
`queryDB($db, $query)` 函数执行查询。
- **第 44-50 行 (psql)**: 使用 `@pg_exec($query)`，如果失败则将 `$result` 设置为 0。
- **第 51-55 行 (mysql)**: 使用 `@mysql_query($query)`，如果失败则将 `$result` 设置为 0。
- **第 56-60 行 (mssql)**: 使用 `@mssql_query($query)`，如果失败则将 `$result` 设置为 0。
- **第 61-66 行 (default)**: 如果无效，则输出错误并返回 0。

#### 4. returnDBarray 函数
`returnDBarray($db, $result)` 函数将结果以数组返回。
- **第 69 行**: 检查 `$result` 是否为 "error"。
- **第 71-75 行 (psql)**: 使用 `@pg_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 76-80 行 (mysql)**: 使用 `@mysql_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 81-85 行 (mssql)**: 使用 `@mssql_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 90 行**: 返回数组 `$array`。

#### 5. closeDB 函数
`closeDB($db, $dbconn)` 函数关闭数据库连接。
- **第 95-102 行 (psql)**: 使用 `@pg_close($dbconn)`，成功返回 1，失败返回 0。
- **第 103-109 行 (mysql)**: 使用 `@mysql_close($dbconn)`，成功返回 1，失败返回 0。
- **第 110-116 行 (mssql)**: 使用 `@mssql_close($dbconn)`，返回状态。

#### 6. numrowsDB 函数
`numrowsDB($db, $result)` 函数返回结果集的行数。
- **第 124-131 行 (psql)**: 使用 `@pg_numrows($result)`，返回行数或 0。
- **第 132-138 行 (mysql)**: 使用 `@mysql_numrows($result)`，返回行数或 0。
- **第 139-146 行 (mssql)**: 使用 `@mssql_numrows($result)`，返回行数或 0。
- **第 147-151 行 (default)**: 数据库类型无效时输出错误并返回 0。





- 38–39: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 40: 返回 `0` (false)，这样任何调用该函数的都会知道函数执行失败。
- 41: 结束 `switch` 语句。
- 42: 结束函数声明。
- 44: 声明 `queryDB` 函数。该函数需要数据库类型 (`$db`) 和 SQL 查询 (`$query`) 作为参数。
- 45: 开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- 46: 如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- 47: 使用 `pg_exec()` 执行查询并检查是否存在错误。
- 48: 如果有错误，将 `$result` 设置为 `0`。
- 49: 结束 `if` 语句。
- 50: 跳出 `switch` 语句，因为分支已经满足。
- 51: 如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- 52: 使用 `mysql_query()` 执行查询并检查是否存在错误。
- 53: 如果有错误，将 `$result` 设置为 `0`。
- 54: 结束 `if` 语句。
- 55: 跳出 `switch` 语句，因为分支已经满足。
- 56: 如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- 57: 使用 `mssql_query()` 执行查询并检查是否存在错误。
- 58: 如果有错误，将 `$result` 设置为 `0`。
- 59: 结束 `if` 语句。
- 60: 跳出 `switch` 语句，因为分支已经满足。
- 61–62: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 63: 返回 `0` (false)，这样任何调用该函数的都会知道函数执行失败。
- 64: 结束 `switch` 语句。
- 65: 将 `$result` 的值返回给调用该函数的函数。如果 `$result = 0`，则调用函数知道发生了错误。
- 66: 结束函数声明。
- 68: 声明 `returnDBarray` 函数。该函数需要数据库类型 (`$db`) 和上一个查询的结果集 (`$result`) 作为参数。
- 69: 验证结果不等于 `0`。如果等于，说明上一个查询出错。如果没有错误，则继续。
- 70: 开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- 71: 如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- 72: 使用 `pg_fetch_array()` 获取数组并检查是否存在错误。
- 73: 如果有错误，将 `$array` 设置为 `0`。
- 74: 结束 `if` 语句。
- 75: 跳出 `switch` 语句，因为分支已经满足。
- 76: 如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- 77: 使用 `mysql_fetch_array()` 获取数组并检查是否存在错误。
- 78: 如果有错误，将 `$array` 设置为 `0`。
- 79: 结束 `if` 语句。
- 80: 跳出 `switch` 语句，因为分支已经满足。
- 81: 如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- 82: 使用 `mssql_fetch_array()` 获取数组并检查是否存在错误。
- 83: 如果有错误，将 `$array` 设置为 `0`。
- 84: 结束 `if` 语句。
- 85: 跳出 `switch` 语句，因为分支已经满足。
- 86–87: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 88: 将 `$array` 设置为 `0`，这样任何调用该函数的都会知道函数失败。
- 89: 结束 `switch` 语句。
- 90: 将 `$result` 的值返回给调用该函数的函数。如果 `$result = 0`，则调用函数知道发生了错误。
- 91: 结束检查 `$result` 不等于 `0` 的 `if` 语句。
- 92: 结束函数声明。
- 94: 声明 `closeDB` 函数。该函数需要数据库类型 (`$db`) 和数据库连接 (`$dbconn`) 作为参数。
- 95: 开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- 96: 如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- 97:  `pg_close()` 并检查是否存在错误。
- 98: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 99–100: 如果错误，通知调用函数关闭成功。
- 101: 结束 `if` 语句。
- 102: 跳出 `switch` 语句，因为分支已经满足。
- 103: 如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- 104:  `mysql_close()` 并检查是否存在错误。
- 105: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 106–107: 如果错误，通知调用函数关闭成功。
- 108: 结束 `if` 语句。
- 109: 跳出 `switch` 语句，因为分支已经满足。
- 110: 如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- 111:  `mssql_close()` 并检查是否存在错误。
- 112: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 113–114: 如果错误，通知调用函数关闭成功。
- 115: 结束 `if` 语句。
- 116: 跳出 `switch` 语句，因为分支已经满足。
- 117–118: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 119: 返回 `0` 通知调用函数函数失败。
- 120: 结束 `switch` 语句。
- 121: 结束函数声明。
- 123: 声明 `numrowsDB` 函数。该函数需要数据库类型 (`$db`) 和上一个查询的结果集 (`$result`) 作为参数。
- 124: 开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- 125: 如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- 126:  `pg_numrows()` 并检查是否存在错误。
- 127: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 128–129: 如果错误，通知调用函数关闭成功。
- 130: 结束 `if` 语句。
- 131: 跳出 `switch` 语句，因为分支已经满足。
- 132: 如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- 133:  `mysql_num_rows()` 并检查是否存在错误。
- 134: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 135–136: 如果错误，通知调用函数关闭成功。
- 137: 结束 `if` 语句。
- 138: 跳出 `switch` 语句，因为分支已经满足。
- 139: 如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- 140:  `mssql_num_rows()` 并检查是否存在错误。
- 141: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 142–143: 如果错误，通知调用函数关闭成功。
- 144: 结束 `if` 语句。
- 145: 跳出 `switch` 语句，因为分支已经满足。
- 146–147: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 148: 返回 `0` 通知调用函数函数失败。
- 149: 结束 `switch` 语句。
- 150: 结束函数声明。

示例的下一个部分是为示例应用程序创建表所需的 SQL：





### 脚本 3–3 addressbook.sql

```sql
1.  CREATE TABLE addressbook (
2.  first VARCHAR(32),
3.  last VARCHAR(32),
4.  home VARCHAR(16),
5.  cell VARCHAR(16),
6.  work VARCHAR(16));
```

最后一部分是示例应用程序，它使用 `DBlib.php` 文件作为其数据库封装，允许应用程序在无需更改任何代码的情况下与三种不同的数据库后端配合。关于该脚本产生的输出，请参阅图 3-2。

### 脚本 3–4 customDB.php

```php
1.  <?
 2.  $page = "customDB.php";
 3.
4.  require_once("DBlib.php");
 5.  /* DBlib.php 必要条件 */
 6.//$db = "psql"; //PostgreSQL 数据库
 7.//$db = "mysql"; //MySQL 数据库
 8.  $db = "mssql"; // MS SQL 数据库
 9.  $host = "192.168.0.1";
10.  $database = "php";
11.  $username = "mssqluser";
12.  $password = "password";
13.  /**************************/
 14.
15.  function display_addresses ($db) {
16.    global $dbconn;
17.    selectDB($db, $dbconn);
18.    $sql = "select * from addressbook";
19.    if(!$result = queryDB($db, $sql)) {
20.      echo "<P>Error with query!";
21.    }
22.    $rows = numrowsDB($db, $result);
23.    if($rows == 0) {
24.      echo "您的通讯录中没有条目.";
25.    } else {
26.    ?><table border=1><?
 27.      while($row = returnDBarray($db, $result)) {
 28.        ?>
 29.        <tr><td colspan=2><b><?=$row['first'];?> <?=$row['last'];?></b></td></tr>
 30.        <tr><td>家庭: </td><td><?=$row['home'];?></td></tr>
 31.        <tr><td>手机: </td><td><?=$row['cell'];?></td></tr>
 32.        <tr><td>工作: </td><td><?=$row['work'];?></td></tr>
 33.        ?>
 34.      }
 35.    ?></table><?
 36.    }
 37.  }
 38.
39.  function add_address($db, $HTTP_POST_VARS) {
40.    global $dbconn;
41.    selectDB($db, $dbconn);
42.    $query = "insert into addressbook values ('" .
 43.      $HTTP_POST_VARS['first'] . "','" .
 44.      $HTTP_POST_VARS['last'] . "','" .
 45.      $HTTP_POST_VARS['home'] . "','" .
 46.      $HTTP_POST_VARS['cell'] . "','" .
 47.      $HTTP_POST_VARS['work'] . "')";
48.    if(!queryDB($db, $query)) {
49.      echo $query;
50.      return 0;
51.    } else {
52.      return 1;
53.    }
54.  }
 55.
56.  function add_address_form(){
57.    global $page;
 58.    ?>
 59.    <h3>添加地址：h3>
60.    <form action=<?=$page?> method=post>
61.    <p>名: <input type="text" name="first">
62.    <br>姓: <input type="text" name="last">
63.    <br>家庭: <input type="text" name="home">
64.    <br>手机: <input type="text" name="cell">
65.    <br>工作: <input type="text" name="work">
66.    <p><input type="submit" name="add_address" value="添加条目!">
67.    </form>
 68.    ?>
69.  }
70.  /***** 主程序 *****/
71.  ?>
72.  <h3>通讯录</h3>
73.  <p><a href=<?=$page?>?action=add>添加条目</a>
74.  <p>
 75.  <?
76.  $dbconn = connectDB($db);
 77.  if(isset($add_address)) {
 78.    if(!add_address($db, $HTTP_POST_VARS)) {
79.      echo "<h3>添加条目出错!</h3>";
80.    } else {
81.      echo "<h3>条目已添加!</h3>";
82.    }
83.  }
```




PEAR 是一个“用于可复 PHP 组件的框架和发行系统”。PEAR 提供了类似于 PERL CPAN 模块集的“模块”。可以将这些模块想象成预构建组件的库，通过它们你可以让你的 PHP 编码变得更容易。PEAR 目前处于测试阶段并正在热热开发中，但它已经包含了许多你可以在自己的项目使用的有用模块。PEAR 提供了开源模块、这些模块的发行和维护，并为这些模块制定了编码标准。

> [1] 取自 PEAR 网站：[pear.php.net](http://pear.php.net)。

PEAR 随 PHP 一起发行。如果你最近安装了 PHP，可能会注意到 `pear` 目录及其包含的许多文件。由于 PEAR 仍处于测试阶段，它尚未被广泛宣传，但它已经开始受到 PHP 者的者的关注，特别是那些一直使用诸如 PHPLIB 和 ADOdb 等第三方库的开发者。虽然已经有很多良好的第三方库可用，但在编码指南、发行和维护方面还没有统一的标准。PEAR 看起来是解决这个问题的方案。

开始变得非常的模块之一是 PEAR DB，它是“访问 SQL 数据库的统一 API”。PEAR DB 的功能大大超过了 DBX 库，并且几乎是纯面向对象的。PEAR DB 支持 PHP 核心支持的数据库的子集，并正在扩展以支持更多数据库。PEAR DB 是编写与数据库无关的 PHP 应用程序的工具。

### 下载 PEAR

你可以从 PEAR 网站 [pear.php.net](http://pear.php.net) 下载 PEAR 的最新版本。在网站右上角的“搜索”框中输入“DB”。

点击出现的第一个搜索结果“DB”，然后从发布列表中下载最新的稳定版本。

### 从并发版本系统 (CVS) 下载 PEAR

尽管 PEAR 包含在所有最新版本的 PHP 中，并且你可以从 PEAR 网站下载较晚的稳定版本，但包含最新功能的、最先进且最强大的 PEAR 版本可能仍然停留在 CVS 仓库中。请注意，你不应该在生产网站上使用 CVS 版本！如果你有权访问 CVS ([www.cvshome.org](http://www.cvshome.org))，那么你应该利用这一机会，从 PHP CVS 仓库下载最新的 PEAR 源码。你可以在 [`cvs.php.net/`](http://cvs.php.net/) 找到 PHP CVS 仓库的所有详细信息。

下载最新的 PEAR 源码：

1. 切换到你想要放置源码的位置（或一个方便拷贝文件的地方）。
2. 执行命令：
   ```bash
   cvs -d :pserver:cvsread@cvs .php.net:/repository login
   ```
   系统会提示输入密码。输入 "phpfi"。
3. 执行命令：
   ```bash
   cvs -d :pserver:cvsread@cvs .php.net:/repository export -D "last week" php4/pear
   ```
   PEAR DB 文档的主要贡献者之一 Thomas V. V. Cox 建议使用 "last week" 标记。有时候最新版本会有小 bug，但大多数时候没有。

### 安装 PEAR

将 PEAR 文件夹复制到你的 Web 目录。完成后，你需要在你的脚本中包含 `pear.php` 文件。

```php
require_once('pear.php');
$dsn = "mysql://user:password@host/database";
$dbconn = DB::connect($dsn);

if (DB::isError($dbconn)) {
    die($dbconn->getMessage());
}
```

### 回归基础

现在你已经建立好了连接，并有了在连接失败时捕获错误的方法，接下来你需要学会的是向数据库发送查询。这是通过 `query()` 方法实现的。

```php
$result = $dbconn->query(QUERY);
```

`query()` 接受一个参数 QUERY，它是一个 SQL 语句。你将查询结果赋值给一个变量（例如 `$result`），这是一个结果对象。

一旦你获得了一个有效的结果对象，就可以使用“fetch”方法之一来从结果中获取数据，然后将其格式化并显示给用户，或者对其进行一些其他处理。你可以使用两种 fetch 方法：`fetchRow()` 和 `fetchInto()`。

```php
$row = $result->fetchRow();
```

以及

```php
$result->fetchInto($row);
```

这两种方法产生的结果完全相同：一个名为 `$row` 的变量，其中包含了结果中的当前行数据。




* `DB_FETCHMODE_ASSOC`— 数据被格式化为关联数组。
* `DB_FETCHMODE_OBJECT`— 数据被格式化为对象，其中列名为属性。

例如，假设你有一个名为“crew”的表格（表 3-2），其中包含以下信息：

### 表 3-2. 示例数据

| ID | NAME | ORIGIN |
| --- | --- | --- |
| 0 | Spike | MA |
| 1 | Jett | AZ |
| 2 | Faye | FL |
| 3 | Ed | NM |
| 4 | Ein | CO |

你查询数据库并获得结果：

```php
$sql = "select name, origin from crew"; 
$result = $dbconn->query($slq);
```

这三种格式将是：

```php
// 使用默认的 DB_FETCHMODE_ORDERED 格式 
$row = $result->fetchRow();
$name = $row[0]; // $name = "Spike";
$origin = $row[1]; //$origin = "MA";

// 使用关联数组作为格式
$row = $result->fetchRow(DB_FETCHMODE_ASSOC);
$name = $row['name']; // $name = "Spike";
$origin = $row['origin']; //origin = "MA";

// 使用对象作为格式
$result->fetchInto($row, DB_FETCHMODE_OBJECT);
$name = $row->name; // $name = "Spike";
$origin = $row->origin; //origin = "MA";
```

这些格式提供了极大的灵活性。另外注意，不同的 fetch 方法会产生相同的预期结果。

由于在脚本的为每个 fetch 方法都手动输入 `DB_FETCHMODE_ASSOC` 或 `DB_FETCHMODE_OBJECT` 作为参数可能会非常麻烦（如果你选择使用这些格式），PEAR DB 提供了一个名为 `setFetchMode()` 的巧妙方法。

```php
$dbconn->setFetchMode(MODE); 
```

`setFetchMode` 是连接对象的一个方法，用于设置所有 fetch 函数的默认抓取模式。参数 `MODE` 可以是之前指定的三个抓取模式中的任何一个。注意，如果你还没有将抓取模式设置为其他值之一，那么将抓取模式设置为 `DB_FETCHMODE_ORDERED` 是没有意义的，因为已经是默认值。一旦你使用此方法，你调用的所有 fetch 方法都会使用 `setFetchMode()`指定的模式，除非你在 fetch 方法本身中指定了不同的抓取模式。

你还应该使用检查连接错误的相同方法来检查结果是否存在错误。如果 `query()` 产生错误，它将返回一个错误对象：

```php
$result = $dbconn->query($sql); 
if (DB::isError($result)) { die ($result->getMessage());}
```

在你完成结果集后，应该使用 `free()` 方法释放结果对象。这将“释放”与结果集相关的内存并减少对 Web 服务器的负载：

```php
$result->free(); 
```

最后，当你完成脚本后，应该关闭与服务器的连接。这是通过连接对象的 `disconnect` 方法实现的：

```php
$dbconn->disconnect(); 
```

你现在拥有了创建简单脚本的构建模块。接下来的脚本将说明不同的 fetch 方法和错误处理。

### 脚本 3–5 peardb1.php

```php
1.  <?
 2.  ini_set("include_path", "/path/to/php/pear");
 3.  require_once('DB.php');
 4.  $type = "mssql";
 5.  $user = "mssqluser";
 6.  $pass = "password";
 7.  $host = "192.168.0.1";
 8.  $database = "php";
 9.  $dsn = "$type://$user:$pass@$database";
10.  $dbconn = DB::connect($dsn);
11.  if (DB::isError($dbconn)) { die ($dbconn->getMessage()); }
12.  /*
13.  create table bebop (
14.      id INT,
15.      name VARCHAR(8),
16.      origin CHAR(2);
17.  */
18.  $values = array (
19.      "insert into bebop values ('0','Spike','MA')",
20.      "insert into bebop values ('1','Jett','AZ')",
21.      "insert into bebop values ('2','Faye','FL')",
22.      "insert into bebop values ('3','Ed','NM')",
23.      "insert into bebop values ('4','Ein','CO')"
24.  );
25.
26.  $result = $dbconn->query("select * from bebop");
27.  if(DB::isError($result)) { die ($result->getMessage());}
28.  if($result->numRows() == 0) {
29.      echo "<P>Populating the DB!<p>";
30.      for($i = 0; $i < sizeof($values); $i++) {
31.        $result2 = $dbconn->query($values[$i]);
32.        if (DB::isError($result2)) { die ($result2->getMessage());}
33.      }
34.      echo "<P>Done the DB! Reload Page<p>";
35.  } else {
36.      $result = $dbconn->query("select name, origin from bebop");
37.      if (DB::isError($result)) { die ($result->getMessage());}
38.      echo "<P>Default Fetch Mode (DB_FETCHMODE_ORDERED):";
39.      while($result->fetchinto($row)){
40.        echo "<br>" . $row[0] . " " . $row[1];
41.      }
42.      $result = $dbconn->query("select name, origin from bebop");
43.      $dbconn->setFetchMode(DB_FETCHMODE_ASSOC);
44.      echo "<HR>DB_FETCHMODE_ASSOC Fetch Mode:";
45.      while($row = $result->fetchRow()){
46.        echo "<br>" . $row['name'] . " " . $row['origin'];
47.      }
48.      $result = $dbconn->query("select name, origin from bebop");
49.      $dbconn->setFetchMode(DB_FETCHMODE_OBJECT);
50.      echo "<HR>DB_FETCHMODE_OBJECT Fetch Mode:";
51.      while($row = $result->fetchinto($row)){
52.        echo "<br>" . $row->name . " " . $row->origin;
53.      }
54.  }
55.  $result->free();
56.  $dbconn->disconnect();
57.  ?>
```

### 脚本 3-5. peardb1.php 逐行说明

| 行 | 描述 |
| --- | --- |
| 2 | 设置包含路径，以便脚本可以使用 PEAR 库。 |
| 3 | 引入发行的 `DB.php` 库。 |
| 4–8 | 定义连接属性，以便脚本连接数据库。 |
| 9 | 使用上述属性构建 DSN。 |
| 10 | 建立到数据库服务器的连接。 |
| 11 | 如果连接数据库出错，则终止脚本并显示与错误相关的消息。 |
| 13–16 | 定义创建示例用表所需的 SQL 语句。 |
| 18–24 | 创建一个用于在数据库中创建条目的 SQL 语句数组。 |
| 26 | 查询数据库检查表中是否存在内容。 |
| 27 | 检查第 26 行的查询是否出错。如果是，终止脚本并向用户显示错误消息。 |
| 28 | 如果结果集返回的行数为 0，则执行第 29–34 行。 |
| 29 | 通知用户脚本正在填充数据库。 |
| 30 | 启动 for 循环以遍历 `$values` 数组中的项。 |
| 31 | 为 `$values` 数组中的每个项执行查询。 |
| 32 | 如果查询出错，则终止脚本并显示任何错误消息。 |
| 34 | 如果没有发生错误，通知用户数据库已填充，他们应该刷新页面。 |
| 35 | 如果表中有行（已在第 28 行中检查），则执行脚本的剩余部分。 |
| 36–37 | 查询数据库。如果查询出错，则终止脚本并显示任何错误消息。 |
| 38–41 | 使用 `DB_FETCHMODE_ORDERED`模式显示结果。注意结果在第 40 行显示。 |
| 42 | 查询数据库。 |
| 43 | 设置抓取模式。 |
| 44–47 | 使用 `DB_FETCHMODE_ASSOC`模式显示结果。注意结果在第 46 行显示。 |
| 48 | 查询数据库。 |
| 49 | 设置抓取模式。 |
| 50–52 | 使用 `DB_FETCHMODE_OBJECT`模式显示结果。注意结果在第 52 行显示。 |
| 54 | 结束第 28 行开始的 if 语句。 |
| 55 | 释放结果。 |
| 56 | 关闭数据库连接。 |





# 优化脚本
- 表单字段检查
- 使用 `$HTTP_GET_VARS` 和 `$HTTP_POST_VARS`
- 整合一切
- 变量变量

### 更好的表单简介

本章介绍了表单。表单是用户交互的最基本的方法。用户必须通过表单向网站输入信息。想一下，每一个公告板、购物车、反馈表单和投票都是表单的一种类型。如果没有表单，Web 仅仅是那些能够将 Web 页面 `FTP` 到服务器的人的发布媒介。

由于表单是你网站上大部分用户交互的基础，因此你有必要让用户输入信息变得更加容易。你曾多少次填写了一个长表单，结果却被你某项填写错误并要求你点击“返回”来修复？当你点击“返回”按钮后，你会发现整个表单变空了，迫使你重新填写所有信息！或者，有些表单提示你填写有误，但仔细检查后你发现不出哪里错了，而且脚本没有提供任何额外的线索。如果不需要重新输入所有信息，并且你填写错误的字段能以某种方式突出显示，以便你轻松进行修正，难道不是更好吗？

你可以使用 `JavaScript` 在表单提交之前检查数据，但并非所有浏览器对 JavaScript 的处理方式相同，因此你可能会遇到某些浏览器的兼容性问题。使用 `PHP`，你可以确保只向浏览器发送纯 HTML，从而减少跨浏览器兼容性错误。取决于代码的复杂程度，使用 `PHP` 而非 `JavaScript` 来检查错误会略微增加服务器的负载。

### Post 和 Get

在 HTML 中创建表单时，可以使用两种方法。它们是 `post` 和 `get`，例如：

```html
<form action=submit.php method=post>
```

或者：

```html
<form action=submit.php method=get>
```

如果你不指定方法，Web 服务器将假设你使用的是 `get` 方法。那么这到底回事？它们的作用是一样的对吧？嗯，几乎如此。你可能已经注意到，在提交使用 `get` 方法的表单后，URL 看起来长了很多。例如，你可能会看到：

```text
http://web.com/form.php?name=fred&age=20&comments=This+site+rocks
```

这是因为 `get` 方法将表单内容直接放在 URL 中。这有几个缺点。首先，取决于你的 Web 服务器操作系统和软件，通过 `get` 方法通过表单发送的数据量是有限制的。在许多系统中，这个限制是 256 个字符。此外，单个 `get` 查询可能会存储在你的 Web 服务器日志中。如果你在共享服务器上使用空间，其他人可能会解析它。

`post` 方法的数据不会出现在 URL 中，这使得它更安全，并允许传输大量数据。

## 让表单更加友好

第一个脚本 `form1.php` 展示了如何通过突出显示用户填写错误的字段来让表单更加用户友好。

```php
<?php
$page = "form1.php";
?>
<<html>
<head>
<style type="text/css">
.error { color:red; }
</style>
</head>
<body>
<form action="<?php echo $page; ?>" method="post">
<table border="0">
<?php error_flag($error, "first"); ?>First Name: <input type="text" name="first" value="<?php echo $first; ?>"></td>
<?php error_flag($error, "last"); ?>Last Name: <input type="text" name="last" value="<?php echo $last; ?>"></td>
<td colspan="2" align="center"><input type="submit" name="submit" value="Submit"></td>
</table>
</form>
<?php
function error_flag($error, $field) {
  if ($error[$field]) {
    echo "<td class='error'>";
  } else {
    echo "td>";
  }
}

function check_form() {
  global $error, $print_again, $first, $last;
  $error['first'] = false;
  $error['last'] = false;
  $print_again = false;
  if ($first == "") {
    $error['first'] = true;
    $print_again = true;
  }
  if ($last == "") {
    $error['last'] = true;
    $print_again = true;
  }
  if ($print_again) {
    print_form();
  } else {
    echo "<h3>Thank you for completing the form!</h3>";
  }
} // end function check_form

function print_form() {
  // ... 打印表单的逻辑
}

***** MAIN *****/
if(isset($submit)) {
  check_form();
} else {
  print_form();
}
?>
</body>
</html>
```

注：由于原始文本在结尾处大量重复且损坏，我已根据提供的代码片段重构了逻辑流，并提供了清理后的版本。





* `$error`— 一个从 `check_form()` 函数返回的错误数组（如果有）。
* `$print_again`— 从 `check_from()` 函数返回的布尔值变量。
* `$first` 和 `$last`— 从此字段中的表单返回的变量。
* `$page`—我们在表单的 `action=…` 行中使用了这个变量。这样做的好处是我们可以轻松更改页面名称，而不必担心破坏脚本。

如果这是第一次运行此脚本，所有这些变量都为空。 |

| | |
| :--- | :--- |
| 22–24 | 打印表单标签。注意我们包含了 `$page` 变量。还要注意 post 方法。 |
| 25–30 | `if/then/else` 语句检查 `$print_again` 变量是否被设置为 `true`。如果是的话，我们就打印一条消息，说明之前遗漏了一些字段。如果 `$print_again` 变量没有被设置，那么我们只打印一条消息让用户填写表单。 |
| 31–40 | 打印表单字段。这是一个非常标准的表单，但有两个不同点：1. 每个字段标签之前跟的是函数 `error_flag` 而不是普通的 `<td>` 标签。这是因为我们想检查用户之前在向此字段输入信息时是否出错。如果他们出错了（而且他们总会在某个时候出错），那么 `error_flag()` 函数将打印 `<td class=error>` 而不是 `<td>`。错误级样式表 (CSS) 类只需将该单元格中的文本变为红色。每个文本输入都有一个关联的值——例如，`value="<?=$first ?>`。如果用户是第一次填写表单，那么这些值是空的。但是，如果用户之前犯了错误，并且这是他们第二次或后续填写表单，那么之前输入的值将显示在表单中。这样，用户就不需要重新向表单输入信息了。 |
| 41 | 结束 `print_form()` 函数。 |
| 43 | 定义 `check_form()` 函数。 |
| 44 | 允许函数使用列出的全局变量。注意这些与 `print_form()` 函数使用的变量相同。 |
| 47 | 将 `$print_again` 变量初始化为 `false`。假设用户输入的数据无误，那么它应该保持为 `false`。 |
| 48–51 | 检查 `$first` 变量（代表用户的名字）以查看用户是否输入了值。如果他们没有在该字段中输入任何内容，我们通过将 `$error` 数组的第一个元素设置为 `true` 并同时将 `$print_again` 变量设置为 `true` 来生成一个错误。 |
| 52–55 | 这三行的作用与 48–51 行相同，不同的是这次我们正在检查 `$last` 变量（代表用户的姓）。 |
| 56–60 | 如果遇到错误且 `$print_again` 变量被设置为 1 (true)，则再次打印表单，否则向用户打印一条消息。 |
| 61 | 结束 `check_form()` 函数。 |
| 64–65 | 如果点击了提交（Submit）按钮，则执行 `check_form()` 函数。 |
| 66–68 | 如果没有点击提交按钮，则执行 `print_form()` 函数。 |
| 70–71 | 关闭 HTML 页面。 |

***

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch04lev1sec1.htm) ![下一节](img/#ch04lev1sec3.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch04lev1sec2.htm) ![下一节](img/#ch04lev1sec4.htm) |

***

### 增强脚本

你可以增强此脚本使其变得更智能：

#### 检查空格

该脚本目前的这种写法，如果用户只是在每个字段中都输入空格，它就很容易被欺骗。在第 46 行和第 50 行的 `check_form` 脚本中，我们检查用户是否输入了内容。这包括空格。如果我们想确保用户输入的是字符（而不只是空格），我们可以这样检查：

```
if(ereg("^ +", $last)) { 
    $error[last] = true;
    $print_again = true;
}
```

基本上，`ereg()` 函数正在检查 `$last` 变量查看是否以一个或多个空格开头。我们将在本章的稍后部分详细查看 `ereg()` 函数。

#### 检查最小字符数

有时你可能想确保用户输入了最小数量的字符。通过使用 HTML 输入标签上的 `maxlength` 属性，强制限制用户输入的最大字符数是很容易的——例如 `<input type="text" maxlength="24">`。

```
if(strlen($first) < 3) { 
      $error[first] = true;
      $print_again = true;
  }
```

在这里我们使用 `strlen()` 函数（字符串长度）来查看 `$first` 变量是否包含至少三个字符。如果它有零、一个或两个字符，那么我们就抛出一个错误。

#### 添加更多错误信息

添加一些额外的错误信息也是很有用的。我们可以稍微修改上面的示例：

```
  if(strlen($first) < 3) { 
      $error['first'] = "请在此字段中输入两个以上的字符。 ";
      $print_again = true;
  }
  if(ereg("^ +", $last)) {
      $error['last'] = "请在此字段中输入字符，而不是空格。 ";
      $print_again = true;
  }
```

在这里，我们不再给 `$error` 变量赋值 `true` 值，而是可以添加错误的简短描述。然后如果我们按照如下方式修改我们的 `error_flag` 函数，就可以在再次向用户显示表单时，向他们打印这条消息：

```
function error_flag($error, $field) { 
      if($error[$field]) {
        print("<td class=error>");
      } else {
         print("<td>");
      }
} //end error_flag
```

***

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch04lev1sec1.htm) ![下一节](img/#ch04lev1sec3.htm) |

***

### 字段检查

如你所见，要让表单对用户更友好并不难。但为了你自己自己，你应该检查输入表单的数据是否真的有用。仅仅检查他们是否填写了字段并不总是够的。

这就是 `ereg()` 的用处。`ereg()` 是一个内置 PHP 函数，意思是评估正则表达式。还有一个与 `ereg()` 工作相同（可能更快）的 Perl 兼容叫做 `preg_match()`。这两个函数的语法非常相似，在大多数情况下完全相同。语法如下：

```
ereg(search, string)
```

其中 `search` 是正则表达式搜索标准，`string` 是你要搜索的字符串。`ereg` 函数返回布尔值（真或假）。如果搜索标准匹配字符串，则 `ereg()` 返回 `true`；否则返回 `false`。

现在，正则表达式是所有经常处理文本的程序员都应该真正了解的东西之一。正则表达式中使用的不同搜索标准可能很晦涩，但它们确实非常有效。

看看我们之前使用的示例：

```
  if(ereg("^ +", $last)) { 
      $error['last'] = true;
      $print_again = true;
  }
```

搜索标准 `"^ +"` 字面上意思是“以空格开头并在后面跟着零或多个空格的字符串”。我们搜索这个是因为我们不希望用户通过为姓输入空格而不是字符来欺骗表单被接受。

然而，我们可以使用其他的正则表达式运算符更详细地分析输入到表单的数据。常见的正则表达式运算符列表可以在 表 4-1 中找到。

##### 表 4-1. 常见的正则表达式运算符





| 符号 | 描述 | 示例 |
| --- | --- | --- |
| `*` | 匹配 0 次或多次出现。 | 就像 UNIX 通配符符号一样，`*` 匹配所有内容。用此匹配符号组。 |
| `+` | 匹配 1 次或多次出现。 | `"e+"` 匹配一个包含一个或多个字符 `"e"` 的字符串。 |
| `^` | 位于字符串开头，匹配该字符串的起始位置。 | `"^Hello"` 匹配任何以单词 `"Hello"` 开头的字符串。 |
| `$` | 位于字符串末尾，匹配该字符串的结尾。 | `"$goodbye!"` 匹配任何以 `"goodbye!"` 结尾的字符串。 |
| `|` | 用于分隔搜索项。 | `"a|b"` 匹配包含字符 `"a"` 或字符 `"b"` 的字符串。 |
| `[]` | 匹配字符范围。 | `"\[a-z\]"` 匹配包含从 a 到 z 小写字母的字符串。`"\[A-D\]"` 匹配包含从 A 到 D 大写字母的字符串。`"\[0-9\]"` 匹配包含 0 到 9 数字的字符串。`"\[1-5\]"` 匹配包含 1 到 5 数字的字符串。 |
| `()` | 序列中的分组操作符。 | 括号的作用与大多数编程操作中的类似。你可以将项组合在一起。例如，`(5\[0-9\]+)` 匹配一个包含数字 5 后跟一个或多个数字的字符串。`"5"` 不匹配，而 `"55"` 匹配。 |
| `.` | 匹配任意单个字符。 | `"\[0-9\].\[0-9\]"` 匹配一个包含数字、后跟任意其他字符、再跟数字的字符串。 |
| `\\` | 转义操作符使其按字面意思处理。 | 如果你想字面搜索特定的操作符，必须转义以下操作符：`[*\+?{}.]` |

#### 检查有效的邮箱地址

用户在表单中输入的最常见内容之一是邮箱地址。拥有用户的邮箱地址可以让你执行诸如在他们忘记密码时发送密码等操作。这不仅节省了用户在你的网站上创建新账户的麻烦，也节省了你的数据库空间。

但有时用户会填写表单但没有输入有效的邮箱地址。你是否收到过邮箱字段中为类似 "qwert" 内容的表单提交？使用正则表达式匹配，你至少可以检查用户输入的邮箱地址以判断其在技术上是否有效。

一个技术上有效的邮箱地址由用户名、@` 符号和服务器名称组成。有效的用户名可以包含字母、数字、下划线 (`_`)、减号 (`-`) 和点 (`.`)。有效的服务器名称几乎相同，但服务器名称不能包含下划线。最后，域名结尾必须包含一个 `.`，后面跟两个或更多字母，例如 `.com`、`.it` 或 `.info`。使用我们在表 4-1 中的正则表达式操作符，我们可以构建一个匹配有效邮箱地址的正则表达式。

假设一个有效的用户名必须以至少一个字母或数字开头：

```
^[a-z0-9]+ 
```

后面跟着零个或多个字母、数字、下划线 `_` 或减号 `-`：

```
[a-z0-9_-]* 
```

然后可以是零个或一个 `.`，后面跟任意数量的字母、数字、下划线 `_` 或减号 `-`：

```
(\.[a-z0-9_-]+)* 
```

紧接着是 `@` 符号：

```
@ 
```

之后至少跟跟一个字母或数字：

```
[a-z0-9]+ 
```

然后可以是零个或一个 `.`，后面跟任意数量的字母、数字、下划线 `_` 或减号 `-`：

```
(\.[a-z0-9_-]+)* 
```

最后，可以再跟另一个 `.`，然后是两个或更多字母（域名的结尾），最后邮箱字符串必须结束：

```
\.([a-z]+){2,}$ 
```

将它们整合在一起，你得到：

```
^[a-z0-9]+(\.[a-z0-9_-]+)*@[a-z0-9_-]+(\.[a-z0-9-]+)*\.([a-z]+){2,}$ 
```

但我们还没有考虑到字母的大小！上面的表达式只允许邮箱地址中出现小写字母，但大写字母也是有效的。为了节省时间，我们没有在表达式中包含 "A–Z" 范围，因为我们可以使用略有不同的 `ereg()` 形式，它被称为 `eregi()`。`eregi()` 的工作方式与 `ereg()` 完全相同，不同之处在于它不区分大小写。这样你就不需要在表达式中使用 `[a-zA-Z]` 语法同时搜索大写和小写字符了。你只需要使用 `[a-z]`。

我们的 `eregi()` 函数现在看起来像这样：

```
eregi("^[a-z0-9]+[a-z0-9_-]*(\.[a-z0-9_-]+)*@[a-z0- 
9_-]+(\.[a-z0-9_-]+)*\.([a-z]+){2,}$", $email);
```

这是一个演示如何检查有效邮箱的短脚本（Script 4-2）：

```php
<?php
$emails = array("test@example.com", "invalid", "user@domain.uk");
foreach ($emails as $email) {
    if (eregi("^[a-z0-9]+[a-z0-9_-]*(\.[a-z0-9_-]+)*@[a-z0- 
9_-]+(\.[a-z0-9_-]+)*\.([a-z]+){2,}$", $email)) {
        echo "$email is valid.\n";
    } else {
        echo "$email is not valid.\n";
    }
}
?>
```

虽然这种写法很丑，但它在检查邮箱方面非常好。这里还有你可以在 `ereg()` 和 `eregi()` 中使用的语法：

##### 表 4-2 可移植式正则表达式

| 符号 | 描述 |
| --- | --- |
| `[:alpha:]` | 等于 `[a-zA-Z]` |
| `[:alnum:]` | 等于 `[a-zA-Z0-9]` |
| `[:digit:]` | 等于 `[0-9]` |
| `[:lower:]` | 等于 `[a-z]` |
| `[:upper:]` | 等于 `[A-Z]` |
| `[:space:]` | 等于空白空格 (" ") |
| `[:print:]` | 匹配任意打印字符，但 `/n`（换行）和 `/t`（制表符）不匹配 |
| `[:graph:]` | 匹配除空格外的任何图形字符 |
| `[:xdigit:]` | 十进制，等于 `[a-f-F0-9]` |
| `[:punct:]` | 匹配包含任何标点符号的字符串 |





PHP 会自动将从表单传递的任何变量注册到 `$HTTP_GET_VARS` 或 `$HTTP_POST_VARS` 数组中。如果使用 post 方法提交表单，则表单中的任何值将被赋值给 `$HTTP_POST_VARS` 数组。如果使用 get 方法提交表单（在未指定方法时的默认方法），则表单的值将被赋值给 `$HTTP_GET_VARS` 数组。

> [1] 如果你正在使用 PHP 4.0.3 或更高版本，你的 `php.ini` 文件将自动启用此功能。如果没有开启，则你必须编辑 `php.ini` 中的 `track_vars` 行并将其设置为 `true`。

例如，当将以下表单提交到 PHP 脚本时：

```
<form action=script.php method=post> 
<input type=hidden name=firstname value="Edward">
<input type=hidden name=occupation value="Computer Specialist">
</form>
```

PHP 自动创建一个可以通过关联方式访问的数组：

```
$PHP_POST_VARS['name'] = "Edward"; 
$PHP_POST_VARS['occupation'] = "Computer Specialist";
```

此功能使得创建和管理表单函数变得更容易，因为你不需要将每个变量变为全局变量，也不需要在调用表单处理函数时列出每个变量。

如果你有一个需要输入 15 个独立字段的表单且未使用 `$HTTP_POST_VARS` 或 `$HTTP_GET_VARS`，那么你的函数定义可能像这样：

```
function my_form_handler($var1, $var2, $var3, $var4, 
..., $var19, $var 20){
```

或者：

```
function my_form_handler(){ 
  global $var1, $var2, $var3, $var4, ..., $var19, $var 20;
```

使用 `$HTTP_POST_VARS` 或 `$HTTP_GET_VARS`，你的代码将更易维护：

```
function my_form_handler($HTTP_POST_VARS) { 
```

或者：

```
function my_form_hander() { 
global $HTTP_POST_VARS;
```

这使得更容易向表单中添加（或删减）额外的字段，而无需在代码中搜索处理表单的函数调用以及向函数调用行添加额外的变量。

### 脚本 4-3 form2.php

```
1.  <?
 2.  function print_form() {
 3.    ?>
 4.    <form action="form2.php" method=post>
 5.    <p>First Name: <input type="text" name="first">
 6.    <br>Last Name: <input type="text" name="last">
 7.    <br>Number: <input type="text" name="number">
 8.    <br><input type="submit" name="submit" value="Submit">
 9.    </form>
10.    <?
11.  }
12.
13.  function form_handler($first, $last, $number) {
14.    $sql = "insert into phonelist values ('$first', '$last', '$number')";
15.    echo "<P>$sql";
16.  }
17.
18.  function form_handler2($HTTP_POST_VARS) {
19.    $sql = "insert into phonelist values('" . $HTTP_POST_VARS['first'] .
20.                        "','" . $HTTP_POST_VARS['last'] .
21.                        "','" . $HTTP_POST_VARS['number'] . "')";
22.    echo "<P>$sql";
23.  }
24.
25.  if(isset($submit)) {
26.    form_handler($first, $last, $number);
27.    form_handler2($HTTP_POST_VARS);
28.  } else {
29.    print_form();
30.  }
31.  ?>
```

### 脚本 4-3. form2.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2–11 | 声明一个函数 `print_form()`。该函数仅打印一个表单，使用户可以输入名、姓和电话号码。 |
| 13 | 声明一个函数 `form_hander()`，它需要三个参数，即用户从 `print_form()` 函数提交表单时返回的项目。 |
| 14 | 使用用户提供的值生成 SQL。 |
| 15 | 打印生成的 SQL。 |
| 16 | 结束函数。 |
| 18 | 声明一个函数 `form_handler2()`，它只需要一个参数 `$HTTP_POST_VARS`。 |
| 19–21 | 使用用户提供的值生成 SQL。 |
| 22 | 打印生成的 SQL。 |
| 23 | 结束函数。 |
| 25 | 如果用户点击了“提交”按钮，则执行脚本到第 27 行。 |
| 26 | 使用三个必需变量调用 `form_handler()` 函数。 |
| 27 | 使用 `$HTTP_POST_VARS` 调用 `form_handler2()` 函数。 |
| 28–30 | 如果没有按下“提交”按钮，则执行 `print_form()` 函数。 |

### 整合一切

现在我们已经有了构建智能、友好且易于处理表单的组件，让我们来看一个真实的示例。该示例所示图 4-1，提供了用户为典型的社区网站注册的方法。

### 图 4-1. register.php

![graphics/04fig01.jpg](img/04fig01.jpg)

某些字段是必填的，某些不是。如果字段名以 `_required` 结尾，脚本将认为该字段是必填的。

脚本还会检查输入了有效的电子邮件地址，并且用户输入了两个相同的密码。

### 脚本 4-4 register.php





```php
1. <html>
  2. <head>
  3.   <title>注册</title>
  4. <style type="text/css">
  5.   .error {color:red; font-weight: bold;}
6. </style>
  7. </head>
  8. <body>
  9. <?php
10. $page = "register.php";
11.
12. function print_form() {
13.   global $page, $error, $print_again, $HTTP_POST_VARS;
14.   $fields = array("first" => "text",
15.            "last" => "text",
16.            "age" => "text",
17.            "email_required" => "text",
18.            "login_required" => "text",
19.            "password1_required" => "password",
20.            "password2_required" => "password");
21.   $labels = array("first" => "名字",
22.            "last" => "姓",
23.            "age" => "年龄",
24.            "email_required" => "邮箱",
25.            "login_required" => "期望用户名",
26.            "password1_required" => "密码",
27.            "password2_required" => "确认密码");
28.   ?>
29.   <form action="<?php echo $page ?>" method="post">
30.   <?php
31.   if($print_again) {
32.     ?><<h3>您遗漏或错误输入了某些字段。请修正<span 
class=error>红色</span></span>字段。密码必须一致。</h3><?php
33.   } else {
34.     ?><<h3>请填写以下字段。</h3><?php
35.   }
36.   ?>
37.   <table border="0">
38.   <?php
39.   foreach($fields as $key => $value) {
40.     ?>
41.     <tr><td <?php error_flag($error, $key); ?>><?php echo $labels[$key];?>: </td>
42.       <td><input type="<?php echo $value;?>" name="<?php echo $key;?>" value="<?php @print(
$HTTP_POST_VARS[$key])?>"></td></td></tr>
43.     <?php
44.   }
45.   ?>
46.   <tr><td colspan="2"><input type="submit" name="submit" value="提交"></td></tr>
47.   </table>
48.   </form>
49.   <?php
50. } // end function print_form
51.
52. function error_flag($error, $field) {
53.   if($error[$field]) {
54.     print("<td class=error>");
55.   } else {
56.     print("<td>");
57.   }
58. } //end function error_flag
59.
60. function check_form() {
61.   global $error, $print_again, $HTTP_POST_VARS;
62.   $print_again = false;
63.   //Check Required Fields Have Been Entered
64.   foreach($HTTP_POST_VARS as $key => $value) {
65.     if(($value == "") && eregi("_required$", $key)){
66.       $error[$key] = true;
67.       $print_again = true;
68.     } else {




| ![](img/#index.htm)   ![上一节](img/#ch04lev1sec6.htm)   ![下一节](img/#ch05_split_000.htm) |

| --- |

* * *

### 变量变量

我在某些基于表单的应用程序中发现了一个非常有用的技巧，那就是“变量变量”（variable variables）。变量变量允许你为变量使用变量名。通过这种方式，你可以根据脚本所需的任何目的动态生成变量名。

示例：

```
$name =  "integer"; 
$$name = 10;
//结果为 $integer = 10;
```

注意，当你将这些值 `echo` 到屏幕上时，得到的结果与你可能预期的不同。在上面的示例中，如果你想将该值打印到屏幕上，你不能像通常那样的那样将变量变量名括在引号中：

```
echo "<p>$$name"; 
// 结果是在屏幕上打印 "$integer"
echo "<p>" . $$name;
// 结果是在屏幕上打印 "10"
```

变量名也可以通过如下表达式来创建：

```
$name = "integer"; 
${$name . "_1"} = 10;
// 结果为 $integer_1 = 10;
```

与 `for` 循环结合使用，这有助于创建动态表单，可以轻松更改以包含更多或更少的字段。

下面的示例（图 4-2 所示）允许你将文件上传到服务器。你只需要指定想要上传的文件数量，脚本会自动创建必要的变量。

#### 脚本 4-5 upload.php

[\[查看全宽\]](&r=noccc&xmlid=0-13-008539-1/ch04lev1sec7#PLID3) 

```
1.  <?
 2.  $page = "upload.php";
 3.  ?>
 4.  <html><html>
 5.  <head>
 6.    <title>Upload Files</title>
 7.  </head>
 8.  <body>
 9.  <?
10.
11.  function specify_number() {
12.    global $page;
 13.    ?>
 14.    <form action=<?=$page?> method=post>
 15.    Enter number of fields to display for upload and press Enter: <input type="text" 
name="fields" size="2" maxlength="2">
 16.    </form>
 17.    <?
 18.  }
 19.
20.  function print_form($fields) {
 21.    global $page
 22.    ?>
 23.    <form action=<?=$page; ?> method=post enctype="multipart/form-data">
 24.    <table border=1>
 25.    <?
 26.    for($i = 0; $i < $fields; $i++) {
 27.    ?>
 28.    <<tr><td>File:</td>
 29.    <td>
 30.     <input type="hidden" name="MAX_SIZE" value="102400">
 31.     <input type="file" name="file<?=$i?>">
 32.    </</td>></tr>
 33.    <?
 34.    ?>
 35.    </table>
 36.     <input type="hidden" name="fields" value="<?fields?>">
 37.     <input type="submit" name="submit" value="Upload!">
 38.    </form>
 39.    <?
 40.  } // end print_form
 41.
 42.  $uploaddr = "/tmp/"; //请确保包含末尾的斜杠。
 43.  if(isset($submit)) {
 44.    for($i = 0; $i < $fields; $i++) {
 45.      if(is_uploaded_file(${"file".$i})) {
 46.        $newfile = $uploaddr . $_FILES['file_' . $i]['name'];
 47.        if(!@copy(${"file".$i}, $newfile)) {
 48.          echo "<p>Error Uploading " . $_FILES['file_' . $i]['name'] . "</p>";
 49.        } else {
 50.          echo "<p>Upload OK for " . $_FILES['file_' . $i]['name'] . "</p>";
 51.        }
 52.      }
 53.    }
 54.  } elseif(isset($fields)) {
 55.    print_form($fields);
 56.  } else {
 57.    specify_number();
 58.  }
 59.  ?>
 60. </body>
 61. </html>
```

#### 图 4-2. upload.php

![graphics/04fig02.jpg](img/04fig02.jpg)

#### 脚本 4-5. upload.php 逐行解析

| 行号 | 描述 |
| --- | --- |
| 2 | 定义 $page 变量。 |
| 4 | 开始 HTML 标签。 |
| 11 | 定义 specify_number() 函数。 |
| 12 | 声明全局变量 $page。 |
| 14 | 创建表单，动作指向 $page，方法为 post。 |
| 15 | 提示用户输入要上传的显示字段数量并按回车。 |
| 20 | 定义 print_form($fields) 函数。 |
| 21 | 声明全局 $page。 |
| 23 | 创建表单，动作指向 $page，方法为 post，编码为 multipart/form-data。 |
| 24 | 创建一个边框为 1 的表格。 |
| 26 | 循环从 0 到 $fields-1。 |
| 28 | 创建表格行，单元格显示 "File:"。 |
| 30 | 创建一个隐藏输入框，MAX_SIZE 值为 102400。 |
| 31 | 创建文件输入框，名称为 file 加上索引。 |
| 36 | 创建一个隐藏输入框，fields 值为 ?fields。 |
| 37 | 创建提交按钮，显示为 "Upload!"。 |
| 42 | 设置上传目录 $uploaddr（确保包含末尾斜杠）。 |
| 43 | 如果设置了 $submit。 |
| 44 | 循环从 0 到 $fields-1。 |
| 45 | 检查该变量是否为已上传的文件。 |
| 46 | 构造新文件的路径，拼接目录和原始文件名。 |
| 47 | 尝试将上传的文件复制到新路径。 |
| 48 | 如果复制失败，打印错误信息。 |
| 50 | 如果复制成功，打印成功信息。 |
| 54 | 如果如果设置了 $fields。 |
| 55 | 调用 print_form($fields)。 |
| 57 | 否则，调用 specify_number()。 |
| 61 | 结束 HTML 标签。 |





此购物车为用户提供了一个简单的界面，如图 5-1 所示。用户只需点击鼠标，即可浏览不同类别的商品。所有类别都可以页面顶部的下拉菜单访问。

### 图 5-1. 购物界面

![graphics/05fig01.jpg](img/05fig01.jpg)

当用户选择一个类别时，该类别下的所有商品都会显示在页面上。如果他们知道自己想要，只需点击 `Add` 按钮即可将商品添加到购物车。每点击一次 `Add` 按钮就会添加一个商品；多次点击意味着添加了多个商品。

如果用户想了解某个特定商品的更多信息，可以点击商品名称。这将向用户展示该商品的更详细的视图，如果提供了商品图片，还会显示图片供用户查看。

同样，他们可以点击 `Add` 按钮将一个或多个商品添加到购物车；多次点击意味着添加多个商品。

用户还会看到一个链接，可以返回他们刚才浏览的类别，也可以从页面顶部的下拉列表中选择新类别。

另一个让购物车变得简单的特性是购物车界面。用户在购物的每个页面上都能看到自己的购物车以及其中包含的商品。页面还会显示购买费用的累计总额。

用户可以选择点击商品旁边的 `Remove` 按钮从购物车中移除商品。每次点击会移除一个商品单位，直到没有商品为止。

用户还可以选择通过点击购物车中的批量修改链接来修改购物车中商品的 `bulk` 数量。这会在每个商品旁边显示出文本输入字段，用户可以使用这些字段来指定购物车中某件商品的精确数量。这样，当用户想要 50 件特定商品时，就不需要点击 50 次 `Add` 按钮了。

最后，当用户的购物车中有商品时，就会出现一个 `Check Out` 链接。点击 `Check Out` 将用户引导到标准的结账表单，在那里输入 `Name`、`Address`、`Credit Card Information` 等。

### 简单的管理和维护界面

购物车还带有简单的管理和维护界面。一个接口用于管理商店的类别和库存（参见图 5-2），另一个用于管理订单（参见图 5-3）。

### 图 5-2. 类别和库存管理界面

![graphics/05fig02.jpg](img/05fig02.jpg)

### 图 5-3. 订单管理界面

![graphics/05fig03.jpg](img/05fig03.jpg)

要管理商店的类别和库存，你需要使用 `dbmanage.php` 脚本。该脚本包含了管理这些实体的逻辑。





```sql
1.  create table customers (
 2.  id INT NOT NULL,
 3.  first VARCHAR(32),
 4.  mi CHAR(2),
 5.  last VARCHAR(32),
 6.  address1 VARCHAR(64),
 7.  address2 VARCHAR(64),
 8.  city VARCHAR(32),
 9.  state CHAR(2),
10.  zip VARCHAR(10),
11.  country VARCHAR(32),
12.  shiptobilling VARCHAR(5),
13.  ship_address1 VARCHAR(64),
14.  ship_address2 VARCHAR(64),
15.  ship_city VARCHAR(32),
16.  ship_state CHAR(2),
17.  ship_zip VARCHAR(10),
18.  ship_country VARCHAR(32),
19.  ship_phone VARCHAR(32),
20.  email VARCHAR(128),
21.  PRIMARY KEY(id));
22.
23.  create table order_details (
 24.  id int not null,
 25.  orderid INT,
 26.  code VARCHAR(32),
 27.  qty INT,
 28.  PRIMARY KEY(id));
29.
30.  create table orders (
 31.  id INT not null,
 32.  customer INT,
 33.  status VARCHAR(16),
 34.  tracking_number VARCHAR(128),
 35.  PRIMARY KEY(id));
36.
37.  create table inventory (
 38.  id INT not null,
 39.  name VARCHAR(32),
 40.  category INT,
 41.  code VARCHAR(32),
 42.  description TEXT,
 43.  price VARCHAR(8),
 44.  picture VARCHAR(128),
 45.  qty INT,
 46.  PRIMARY KEY(id));
47.
48.  create table category (
 49.  id INT not null,
 50.  name VARCHAR(128),
 51.  description TEXT,
 52.  PRIMARY KEY(id));
```

##### 脚本 5-1. cart.sql 逐行解释

| 行 | 描述 |
| --- | --- |
| 1-21 | 创建一个表来存储客户数据。 |
| 23-28 | 创建一个表来存储订单详情。订单中的每个项目在该表中都有单独的一行。`orderid` 列作为指向 `orders` 表的外键键。 |
| 30-35 | 创建一个表来存储订单。此表引用 `customer` 表获取客户信息，并持有订单的状态和跟踪信息。 |
| 37-46 | 创建一个表来存储库存中每个项目的数据。`category` 列作为指向 `category` 表的外键键。 |
| 48-52 | 创建一个表来存储分类信息。 |

#### cart.php

`cart.php` 是应用程序的主脚本。它引用了 `cart_inc.php` 来使用一些额外的共享函数。

##### 脚本 5-2 cart.php

```php
1.  <?
 2.  require_once("include/cart_inc.php");
 3.  session_start();
 4.  session_register("items");
 5.  session_register("category_choice");
 6.  session_register("total");
 7.
 8.  if(!isset($items)) {
 9.    $items = array();
10.  }
11.  if(!isset($category_choice)) {
12.    $category_choice=1;
13.  }
14.
15.  /*************** MAIN ***************/
16.  head();
 17.  $dbconn = connect();
18.  select_cat();
19.  $status = "shopping";
20.
21.  ?>
22.  <table width="58%" border="1" cellspacing="10" cellpadding="10" height="371" 
bordercolor="#0000FF" bgcolor="#999999">
23.  <tr align="left" valign="top">
24.  <td bgcolor="#CCCCCC" bordercolor="#0000FF">
25.  <table border="0" cellpadding="10"><tr><td valign=top>
 26.  <?
 27.  if(isset($category_choice_in)) {
 28.    $category_choice = $category_choice_in;
 29.  }
30.
31.  if(isset($update_cart)) {
 32.    foreach($items_in as $cat => $val) {
 33.      foreach($items_in[$cat] as $id => $qty) {
 34.        if($qty < 1) {
 35.          unset($items_in[$cat][$id]);
 36.        }
 37.      }
 38.    }
 39.  }
40.    $items = $items_in;
41.  }
42.  if(isset($item_view)) {
 43.    full_item($item_view);
44.  } else {
 45.    display_cart($category_choice);
46.  }
47.
48.  if(isset($action)) {
 49.    alter_cart($items, $category_choice, $action);
50.  }
51.
52.  ?>
53.  </td><td valign=top>
54.  <h3>您的购物车:</h3>
55.  <?
56.  if(isset($modify)) {
57.    edit_cart($items);
58.  } else {
59.    display_cart($items);
60.  }
61.  ?>
62.  <p>
63.  <?
64.  if(sizeof($items) > 0) {
65.    $total = calculate_total($items);
66.    //print_r($items);
67.    ?>
68.    <p>您想 <a href="checkout.php">结账</a> 吗？
69.    <?
70.  }
71.  ?>
72.  </td>
73.  </tr>
74.  </table>
75.  </div>
76.  </body>
77.  </html>
78.
79.
```

##### 脚本 5-2 cart.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2 | 引入 `cart_inc.php` 来使用所有的工作函数。 |
| 3 | 会话。 |
| 4-6 | 注册会话变量以存储项目、分类选择和总金额。 |
| 8-10 | 如果 `$items` 未设置，则将其初始化为空数组。 |
| 11-13 | 如果未设置 `$category_choice`，则默认设置为 1。 |
| 16 | 调用 `head()` 函数显示页面的开启 HTML。我们现在这样做是为了让会话变量正确注册。 |
| 17 | 建立数据库连接。 |
| 18 | 执行 `cart_inc.php` 中的 `select_cat()` 函数。该函数列出了所有可用分类。 |
| 19 | 将 `$status` 设置为 shopping。稍后我们会更改。 |
| 22-25 | 打印一个包含项目和购物车的表格。 |
| 27-29 | 更新会话变量 `$category_choice` 为用户当前浏览的分类。 |
| 31-40 | 如果用户更新了购物车，则对 `$items_in` 数组进行增加或减少操作。然后用购物车中的项目更新会话变量 `$items`。 |
| 42-46 | 如果用户点击了项目列表中的项目，则使用 `cart_inc.php` 中的 `full_item()` 函数显示该项目的详细信息。否则，使用 `display_cart()` 显示分类项目。 |
| 48-50 | 如果执行了某些操作（添加或删除项目），则执行 `cart_inc.php` 中的 `alter_cart()` 函数。 |
| 54 | 打印购物车标题。 |
| 56-60 | 如果用户点击了购物车上的批量修改链接，则执行 `cart_inc.php` 中的 `edit_cart()` 函数，否则使用 `display_cart()` 显示购物车。 |
| 65-71 | 如果购物车中有一个或多个项目，通过调用 `cart_inc.php` 中的 `calculate_total()` 函数计算总额。同时也提供一个指向结账的链接。为了测试，可以取消第 67 行的注释来查看数组中存储了哪些项目。 |
| 73-79 | 关闭表格并结束页面的 HTML。 |





```php
<?
define(SECURE_URL, "http://localhost/advancedphp/chapter05/");
define(IMAGE_URL, "http://localhost/advancedphp/chapter05/images/");
define(SHIPPING_COST, "7.00");
define(COMPANY_NAME, "Widget Industrial Inc.");
define(CREDIT_AUTH_URL, "finishorder.php");
define(COMPANY_EMAIL, "company@example.com");

function connect() {
  ini_set("include_path", "G:\apache\Apache\php\pear");
  require_once("DB.php");
  $type = "mysql";
  $username = "php";
  $password = "password";
  $host = "localhost";
  $database = "cart";
  $dsn = $type . "://" . $username . ":" . $password . "@" . $host . "/" . $database;
  $dbconn = DB::connect($dsn);
  errortrap($dbconn);
  $dbconn->setFetchMode(DB_FETCHMODE_ASSOC);
  return $dbconn;
} //end connect

function errortrap($result) {
  if(DB::isError($result)) {
    ?><<h3>发生了错误！</h3>><?
    die($result->getMessage());
  }
} //end errortrap

function alter_cart($cat, $items, $item, $action) {
  global $dbconn;
  $sql = "select * from inventory where id = '$item' AND category =  '$cat'";
  $result = $dbconn->query($sql);
  errortrap($result);
  if($result->numRows() > 0) {
    switch($action) {
      case("add"):
        if(!isset($items[$cat][$item])) {
          $items[$cat][$item] = 0;
        }
        $items[$cat][$item]++;
        break;
      case("remove"):
        if(isset($items[$cat][$item])) {
          $items[$cat][$item]--;
        }
        if($items[$cat][$item] < 1) {
          unset($items[$cat][$item]);
        }
        break;
      default:
        break;
    }
  }
  return $items;
} //end alter_cart

function full_item($item, $items) {
  global $dbconn;
  $sql = "select * from inventory where id = $item";
  $result = $dbconn->query($sql);
  errortrap($result);
  $result->fetchinto($r);
  ?>
  <table border=1 cellpadding=5 cellspacing=0>
    <tr><td class=tablehead><?=$r["name"]?></td></tr>
    <tr><td><?=$r["name"]?><br><?=$r["description"]?>
    <br><b>价格：</b>: <?=$r["price"]?>
    <p>
    <?
    if($r["picture"] != "") {
      ?><div align="center"><img src="<? echo IMAGE_URL . $r["picture"]?>"></div><?
    }
    if($r["qty"] > 1) {
      ?>
      <p><div align=center><a href="<?=SECURE_URL?>cart.php?cat=<?=$r["category"]?>&item=<?=$item?>&itemview=<?=$item?>&action=add"><img 
      src="<?=IMAGE_URL?>add.gif" border=0></a>
      <?
    } else {
      ?>
      <p>抱歉，缺货</p>
      <?
    }
    ?>
    <br><a href="<?=SECURE_URL?>cart.php">返回此类别的商品列表</a></a>/</div></td>td></tr>
  </table>
  <?
} //end full_item

function build_menu ($ref, $table) {
  global $dbconn;
  $sql = "select * from $table order by id";
  $result = $dbconn->query($sql);
  errortrap($result);
  if($result->numRows() > 0) {
    $x = 0;
    while($result->fetchInto($r)){
      if($x == 0) {
        echo '<option value="' . $r["id"] . '" selected>' . $r[$ref] . '</option>';
        $x++;
      } else {
        echo '<option value="' . $r["id"] . '">' . $r[$ref] . '</option>';
      }
    }
  } else {
    echo '<option value="">未定义分类</option>';
  }
} //end build_menu

function head() {
  ?>
  <html>
  <head>
  <style type=text/css>
    h, h2, h3, p, td {font-family: verdana, sans-serif; }
    .tablehead {font-size: 12pt; color: #FFFFFF; background-color: #00009; }
    .required {font-weight: bold; color: red; }
    .small {font-size: 8pt; font-style: italic;}
  </style>
  </head>
  <body bgcolor="#FFFFFF">
  <div align=center>
    <table width="74%" border="0" cellspacing="0" cellpadding="0" height="128" 
    bgcolor="#FFFFFF">
    <tr>
    <td height="134" align="center"><h1>简单购物车</h1></td>
    </tr>
  </table>
  <?
} //head

function calculate_total($items) {
  global $dbconn;
  $shipping = SHIPPING_COST;
  $total = 0;
  foreach($items as $key => $val) {
    foreach($items[$key] as $key2 => $val2) {
      $sql = "select * from inventory where id = '$key2'";
      $result = $dbconn->query($sql);
      errortrap($result);
      $result->fetchinto($r);
      $total+= ($r["price"] * $val2);
    }
  }
  if($total != 0) {
    $total = $shipping;
  }
  return $total;
}

function display_cart($items) {
  global $dbconn;
  global $items, $status;
  $shipping = SHIPPING_COST;
  $count = 0;
  ?>
  <table border=1 cellpadding=5 cellspacing=0>
    <tr><td class=tablehead>商品名称</td><td class=tablehead>数量</td><td
    class=tablehead>单价</td><td class=tablehead>&nbsp;</td></tr>
    <?
    foreach($items as $cat => $val) {
      foreach($items[$cat] as $item => $qty) {
        $sql = "select * from inventory where id = '$item'";
        $result = $dbconn->query($sql);
        errortrap($result);
        $result->fetchinto($r);
        ?>
        <tr><td>$=$r["name"]?</td><td>$=$qty?</td><td>$=$r["price"]?</td>
        <?
        if($status == "checkout") {
          echo "<td>&nbsp;</td>";
        } else {
          ?>
          <td><a href="<?=SECURE_URL?>cart.php?cat==$r["category"]?>&item==$r["id"]?>&action=remove">
          <img src="<?=IMAGE_URL?>remove.gif" border=0></a></td>
          <?
        }
        ?>
        </tr>
        <?
        $count++;
      }
    }
    if($count == 0) {
      $items= array();
      ?>
      <tr><td colspan=4><h3>购物车是空的！</h3></tr>
      <?
    }
    $total = calculate_total($items);
    ?>
    <tr><td colspan=3>运费及手续费</td><td>$=$shipping?</td></tr>
    <tr><td class=small>
    <?
    if($status != "checkout") {
      if($count > 0) {
        ?>点击 <a href<?=SECURE_URL?>cart.php?modify=bulk">这里</a> 来修改
    购物车中的数量。<?
      }
    }
    ?>
    &nbsp;</td><td colspan="2" align="right">总计：</td><td>
    <?
    printf("%.2f", $total);
    ?></</td></td></tr></table>
} //end display_cart

function cart2($items) {
  foreach($items as $cat => $val) {
    foreach($val as $item => $qty) {
      ?>
      <input type="hidden" name="cart[<?=$cat?>][<?=$item?>]" value="<?=$qty; ?>" 
    size="3">
      <?
    }
  }
} //end cart2

function display_items($cat, $items) {
  global $dbconn;
  $sql = "select * from inventory where category = '$cat'";
  $result = $dbconn->query($sql);
  errortrap($result);
  if($result->numRows() > 0) {
    ?>
    <h2>此分类下的可用商品：</h2>
    <table border=1 cellpadding=5 cellspacing=0>
      <tr><td class=tablehead>商品名称 <div class=small>点击名称查看详情</div></td><td
      class=tablehead>价格</td><td class=tablehead>&nbsp;</td></tr>
      <?
      while($result->fetchinto($r)) {
        ?>
        <tr><td><a href="<?=SECURE_URL?>cart.php?itemview==$r["id"]?>"><?=$r["name"]?</a></td><td>$=$r["price"]?</td></td></td><td>
        <?
        if($r["qty"] > 1) {
          ?>
          <a href="<?=SECURE_URL?>cart.php?cat==$r["category"]?>&item==$r["id"]?>&action=add"><img src="<?=IMAGE_URL?>add
      gif" border=0></a>
          <?
        } else {
          ?>
          缺货
          <?
        }
        ?>
        </td></td></tr>
        <?
      }
      ?>
      </table>
      <?
    } else {
      echo "<h3>请在上方选择一个分类</h3>";
    }
} //end display_items

function edit_cart($items) {
  global $dbconn;
  ?>
  <form action=cart.php method=post>
    <table border=1 cellpadding=5 cellspacing=0>
      <tr><td class=tablehead>商品名称</td><td class=tablehead>单价</td><td
      class=tablehead>数量</td></tr>
      <?
      foreach($items as $cat => $val) {
        foreach($items[$cat] as $item => $qty) {
          $sql = "select * from inventory where id = '$item'";
          $result = $dbconn->query($sql);
          errortrap($result);
          $result->fetchinto($r);
          ?>
          <tr><td>$=$r["name"]?</td><td>$=$r["price"]?</td><td><td>
          <input type="text" name="items_in[<?=$cat?>][<?=$item?>]" value="<?=$qty?>" 
    size="3">
          </td></td></tr>
          <?
        }
      }
    }
    ?>
    </table>
    <input type="submit" name="update_cart" value="更新购物车">
  </form>
  <?
} //end edit_cart

function select_cat() {
  ?>
  <form action=cart.php method=post>
    <p>选择购物分类：<select name="category_choice_in">
    <? build_menu("name","category"); ?>
    </select>
    <input type="submit" name="submit" value="提交">
  </form>
  <?
} //end select_cat
?>
```





### 脚本 5-3. cart_inc.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2-7 | 创建一些常量。根据你网站的实际情况填写值。由于此购物车假设采用固定运费，我在这里也指定了运费，以便于修改。 |
| 9-22 | 使用 PEAR DB 连接函数创建与数据库的连接。 |
| 24-29 | 创建一个短的错误捕获函数，用于在每次查询后检查 PEAR DB 错误。可以根据你的报告需求对其进行自定义。错误报告将在第 8 章中进行详细介绍。 |
| 31-57 | 定义一个函数 `alter_cart()`，用于从用户的购物车中添加和移除项目。`items` 数组实际上是一个二维数组。`items` 数组中的每个元素本身也是数组。顶层数组是类别。它们内部的数组是项目数组。结构如下：<br>* `items[category[cat1], category[cat2], category[cat3]]` <br>* `cat1[item1[qty], item2[qty], item3[qty]]` <br>* `cat2[item1[qty], item2[qty], item3[qty]]` <br>* `cat3[item1[qty], item2[qty], item3[qty]]` |
| 59-88 | 定义一个函数 `full_item()`，用于显示项目的完整描述和选项图片。用户在查看完整描述时也可以将项目添加到购物车。 |
| 90-108 | 定义一个函数 `$build_menu` 作为“辅助函数”。该函数仅简单地创建一个供其他函数使用的下拉菜单。 |
| 110-129 | 定义一个函数 `head()`，用于显示页面的起始 HTML 标签。 |
| 131-141 | 定义一个函数 `calculate_total()`，用于确定购物车中项目的总费用。 |
| 150-204 | 定义一个函数 `$display_cart()`，向用户显示购物车中的项目。该函数有几个作用：首先，用户可以轻松地看到购物车中有哪些项目；其次，用户可以点击按钮轻松地移除项目。 |
| 206-214 | 定义一个函数 `cart2form()`，提取用户购物车中的项目并将其放在隐藏表单字段中。这被用于 `checkout.php` 页面。 |
| 216-252 | 定义一个函数 `display_items()`，用于显示给定类别下的项目列表。除了显示项目，该函数还提供了一个将项目添加到用户购物车的按钮，以及一个查看项目完整描述的链接。 |
| 254-280 | 定义一个函数 `edit_cart()`，允许用户通过指定数量来“批量修改”购物车中的项目，而无需多次点击“添加”按钮。 |
| 282-291 | 定义一个函数 `select_cat()`，打印一个短表单，以便用户选择一个类别进行浏览。 |
| 292 | 结束页面的 PHP 代码。 |

#### dbmanage.php

`dbmanage.php` 用于管理库存中的类别和项目。

### 脚本 5-4 dbmanage.php

查看全宽





```php
<?
  require_once("../include/cart_inc.php");

function add($item, $HTTP_POST_VARS) {
  global $dbconn;
  if($item == "cat") {
    $id = $dbconn->nextID('category',true);
    $sql = "insert into category values ('$id', '" . $HTTP_POST_VARS["name"] . "','" . $HTTP_POST_VARS["description"] . "')";
  } elseif($item == "item") {
    $id = $dbconn->nextID('inventory',true);
    $sql = "insert into inventory VALUES('$id', '" . $HTTP_POST_VARS["name"] . "','" . $HTTP_POST_VARS["category"] . "','" . $HTTP_POST_VARS["code"] . "','" . $HTTP_POST_VARS["description"] . "','" . $HTTP_POST_VARS["price"] . "','" . $HTTP_POST_VARS["picture"] . "','" . $HTTP_POST_VARS["qty"] . "')";
  } else {
    return 0;
  }
  $result = $dbconn->query($sql);
  errortrap($result);
  return 1;
} //end add

function display($item, $cat) {
  global $dbconn;
  if($item == "cat") {
    $sql = "select * from categories order by name";
  } elseif($item == "item") {
    $sql = "select * from inventory order by category, name";
  } else {
    return 0;
  }
  $result = $dbconn->query($sql);
  errortrap($result);
  ?>
  <p>
  <table border=1 cellpadding=5>
  <?
  if($item == "item") {
    ?><tr class=tablehead><td>Name</td><td>Code</td><td>Description</td><td>Price</td><td>Picture</td><td>Qty</td></tr><?
  } else {
    ?><tr class=tablehead><td>Name</td><td>Description</td></tr><?
  }
  while($result->fetchinto($r)) {
    if($item == "cat") {
      ?><</td>$r["name"]??td><tdrr["description"]??td>
         elseif elseif($item == "item") {
                        rr["name"]???</td>tdrr["code"]???><tdrr["r"]??td

      tdtdrr[""]???tdtdtdrrpicture"]?&nbsp;
      <td<?=$r["qty"]?</td>
      

            

    

  

  ?table
} // end display

function item_edit($cat, $limit) {
  global $dbconn;
  $sql = "select * from inventory where category = '$cat' order by id $limit,20";
  $result = $dbconn->query($sql);
  errortrap($result);
  if($result->numRows() > 0) {
    ?>
    <p>Viewing inventory items <?=limit+=20) ?>.
    <form action=dbmanage.php method=post>
    <input type=hidden name="category" value="<?cat?>
    <input type=hidden name=limit value="<?limit ?>">
    <input type="submit" name="choose_cat" value="View Next 20">
    </form>
    <table><table>
      <tr class=tablehead><td>Name</td>td><td>Category</td>td><td>Code</td>td><td>Description</td>td><td>Price</td>td><td>Picture</td>td><td>Qty</td>td><td>Action</td>td>
      <?
      while($result->fetchinto($r)){
        ?>
        <form action=dbmanage.php method=post>
          <input type=hidden name=id value="<?r["id"]?>
          <input type=hidden name=limit value="<?limit ?>">
          <tr>
            <td><input type=text name=name value="<?r["name"]?>></td>
            <td>
              <select name="category">
                <? build_menu("name","category"); ?>
              </select>
            </td>
            <td><input type=text name=code value="<?r["code"]?>></td>
            <td><textarea name=description cols=15 rows=2><?r["description"]></textarea></td>
            <td><input type=text name=price value="<?r["price"]?>></td>
            <td><input type=text name=picture value="<?r["picture"]?>></td>
            <td><input type=text name=qty value="<?r["qty"]?>></td>
            <td><input type="submit" name="submit" value="Update"><input type="submit" name="submit" value="Delete"></td>
          </tr>
        </form>
        <?
      }
      ?></table>
  } else {
    ?>
    <h2>There are more items in this category</h2>
    <?
  }
} //end item_edit

function process_item_edit ($HTTP_POST_VARS) {
  global $dbconn;
  $delete_cat_items = "false";
  if($HTTP_POST_VARS["submit"] == "Delete Item") {
    $sql = "delete from inventory where id = '" . $HTTP_POST_VARS["id"] . "'";
  } elseif($HTTP_POST_VARS["submit"] == "Update Item") {
    $sql = "update inventory set name='" . $HTTP_POST_VARS["name"] . "', category=' .$HTTP_POST_VARS["category"] . "', code='" . $HTTP_POST_VARS["code"] . "', description='" . $HTTP_POST_VARS["description"] . "', price='" . $HTTP_POST_VARS["price"] . "', picture =' . $HTTP_POST_VARS["picture"] . "', qty='" . $HTTP_POST_VARS["qty"] . "' where id='" . $HTTP_POST_VARS["id"] . "'";
  } elseif($HTTP_POST_VARS["submit"] == "Delete Category") {
    $sql = "delete from category where id = '" . $HTTP_POST_VARS["id"] . "'";
    $delete_cat_items = "true";
  } elseif($HTTP_POST_VARS["submit"] == "Update Category") {
    $sql = "update category set name='" . $HTTP_POST_VARS["name"] . "', description='" . $HTTP_POST_VARS["description"] . "' where id='" . $HTTP_POST_VARS["id"] . "'";
  }
  $result = $dbconn->query($sql);
  errortrap($result);
  echo "<h2>" . $HTTP_POST_VARS["submit"] . " Successful!</h2>\n";
  if($delete_cat_items == "true") {
    $sql2 = "delete from inventory where category = '" . $HTTP_POST_VARS["id"] . "'";
    $result = $dbconn->query($sql2);
    errortrap($result);
  }
} //end process_item_edit

function cat_edit() {
  global $dbconn;
  $sql = "select * from category order by id ";
  $result = $dbconn->query($sql);
  errortrap($result);
  if($result->numRows() > 0) {
    ?>
    <p>Viewing Categories:
    <table>
      <tr class=tablehead><td>Name</td><td>Description</td><td>Action</td></tr>
      <? // while($r = mysql_fetch_array($result))
      while($result->fetchinto($r)) {
        ?>
        <form action=dbmanage.php method=post>
          <input type=hidden name=id value="<?r["id"]?>
          <tr>
            <td><input type=text name=name value="<?r["name"]?>></td>
            <td><textarea name=description cols=25 rows=5><?r["description"]></textarea></td>
            <td><input type="submit" name="submit" value="Update"><input type="submit" name="submit" value="Delete"></td>
          </tr>
        </form>
        <?
      }
      ?></table>
  } else {
    ?>
    <h2>There are no categories to edit!</h2>
    <?
  }
} //end cat_edit

function add_cat_form() {
  ?>
  <form action=dbmanage.php method=post>
    <table border="1" cellspacing="0" cellpadding="5">
      <tr class=tablehead<td colspan="2"><h2>Add Category</h2></tr>
      <tr><td><input type="text" name="name" size="32" maxlength="32"></td></tr>
      <tr><td><textarea name="description cols=30 rows=5></textarea></td></tr>
      <tr><td colspan="2"><input type="submit" name="add_cat" value="Add Category"></td></tr>
    </table>
  </form>
  ?>
} //end add_cat_form

function add_item_form() {
  ?>
  <form action=dbmanage.php method=post>
    <table border="1" cellspacing="0" cellpadding="5">
      <tr class=tablehead<td colspan="2"><h2>Add Inventory Item</h2></tr>
      <tr><td><input type="text" name="name" size="32" maxlength="32"></td></tr>
      <tr><td>Category</td><td><select name="category">
        <? build_menu("name","category"); ?>
        </select></td></tr>
      <tr><td>Code</td><td><input type="text" name="code" size="32" maxlength="32"></td></tr>
      <tr><td>Description</td><td><textarea name="description" cols=30 rows=5></textarea></td></tr>
      <tr><td>Price</td><td><input type="text" name="price" size="8" maxlength="8"></td></tr>
      <tr><td>Picture</td><td><input type="text" name="picture"></td></tr>
      <tr><td>Qty In Stock</td><td><input type="text" name="qty" size="5"></td></tr>
      <tr><td colspan="2"><input type="submit" name="add_item" value="Add Item"></td></tr>
    </table>
  </form>
  ?>
} //end add_item_form

function choose_cat_form() {
  ?>
  <form action=dbmanage.php method=post>
    <select name="category">
      <? build_menu("name","category"); ?>
    </select>
    <input type="submit" name="choose_cat" value="Edit Items In This Category">
  </form>
  ?>
} //end choose_cat_from

function edit_cats_form() {
  ?>
  <form action=dbmanage.php method=post>
    <input type="submit" name="edit_cat" value="Edit All Categories">
  </form>
  ?>
}

function choices() {
  ?>
  <table border=1 cellpadding=5 cellspacing=0>
    <tr valign="middle">
      <td><a href=dbmanage.php?action=addcat>Add A Category</a></td>
      <td><a href=dbmanage.php?action=additem>Add An Item</a></td>
      <td><a href=dbmanage.php?action=display>Display Inventory</a></td>
    </tr>
    <?=choose_cat_form()?>
    <?=edit_cats_form()?>
  </table>
  ?>
} //end_choices

***** MAIN *****
head();
$dbconn = connect();
if(isset($submit)) {
  process_item_edit($HTTP_POST_VARS);
}
if(isset($choose_cat)) {
  if(!isset($HTTP_POST_VARS["limit"])) {
    $HTTP_POST_VARS["limit"] = 0;
  }
  item_edit($category, $HTTP_POST_VARS["limit"]);
}
if(isset($edit_cat)) {
  cat_edit();
}
choices();
if(isset($action)) {
  if($action == "addcat") {
    add_cat_form();
  } elseif($action == "additem") {
    add_item_form();
  } elseif($action == "display") {
    display("item","1");
  }
}
?>
</body>
</html>
```





### 脚本 5-4. dbmanage.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2 | 引入 `cart_inc.php`，因为它包含了此脚本使用的一些函数。 |
| 4-25 | 定义函数 `add()`，用于向库存中添加分类或项目。该函数使用 PEAR DB 的函数 `nextID()` 来生成自增 ID： |
```php
$dbconn->nextID($table, $create);
```
`nextID` 接受两个参数：<br>* `$table`: 要生成 ID 的表。<br>* `$create`: 一个布尔值，如果不存在 ID 序列，则将其设置为 true 以启动该序列。|`nextID()` 函数解决了我们这些人的问题：我们喜欢在 MySQL 中使用 `auto_increment` 功能来创建 ID，但与此我们也希望应用程序能够运行在不同的数据库上（其中某些数据库并不使用 `auto_increment` 功能来处理 ID）。 |
| 27-62 | 定义函数 `display()`，用于显示库存中的项目。 |
| 64-107 | 定义函数 `item_edit()`，用于打印表单以编辑库存中的现有项目。该函数一次显示多个项目，每次 20 个。 |
| 109-136 | 定义函数 `process_item_edit()`，用于处理通过 `item_edit()` 函数所做的更改。如果删除了某个分类，那么与该分类相关的所有项目也会被删除。 |
| 138-167 | 定义函数 `cat_edit()`，用于打印表单以编辑现有的分类。 |
| 169-180 | 定义函数 `add_cat_form`，用于打印添加新分类的表单。 |
| 182-198 | 定义函数 `add_item_form()`，用于打印添加新项目的表单。 |
| 200-218 | 定义函数 `choose_cat_form()`，用于打印表单允许用户选择一个要编辑的分类。 |
| 221-228 | 定义函数 `choices()`，显示用户管理库存可以采取的不同操作。 |
| 230 | 开始主程序。 |
| 231 | 使用 `head()` 函数打印页面的起始 HTML 头部。 |
| 232 | 建立数据库连接。 |
| 233-235 | 如果点击了“提交”按钮，则执行 `process_item_edit()` 函数。`$submit` 按钮映射到此页面所有的编辑功能。 |
| 236-242 | 如果设置了 `$add_item` 变量，则尝试添加新项目。如果发生错误，则在屏幕上打印消息（脚本可能在此之前就会停止，因为错误捕获机制应该捕获它）。如果没有错误，则通知用户新项目已添加。 |
| 243-249 | 如果设置了 `$add_cat` 变量，则尝试添加新分类。如果发生错误，则在屏幕上打印消息（脚本可能在此之前就会停止，因为错误捕获机制应该捕获它）。如果没有错误，则通知用户新分类已添加。 |
| 250 | 执行 `choices()` 函数向用户显示这些功能。 |
| 251-259 | 如果设置了 `$action` 变量，我们知道用户点击了 `choices()` 函数中定义的“添加分类”、“添加项目”或“显示所有项目”按钮之一。执行点击的按钮（或链接）对应的函数。 |
| 260-265 | 如果设置了 `$choose_cat` 变量，我们知道用户想要查看或编辑特定分类的项目。显示该分类中的项目。`Limit` 用于每次查看 20 个项目。如果未设置 `$limit`，我们知道用户处于第一页，因此将 `$limit` 设置为 0。`item_edit()` 函数会在每次查看子集时增加 `limit`。 |
| 266-268 | 如果设置了 `$edit_cat` 变量，我们知道用户想要编辑分类，因此执行 `cat_edit()` 函数。 |
| 269 | 关闭页面的 PHP 和 HTML。 |

### admin.php

`admin.php` 用于管理已提交的订单。

### 脚本 5-5 admin.php

全屏查看





```php
1
function display_orders($mode) {
  global $dbconn;
  switch($mode) {
    case("all"):
      $sql = "select * from orders order by id";
      break;
    case("open"):
      $sql = "select * from orders where status = 'open' order by id";
      break;
    case("shipped"):
      $sql = "select * from orders where status = 'shipped' order by id";
      break;
    case("backorder"):
      $sql = "select * from orders where status = 'backorder' order by id";
      break;
    case("hold"):
      $sql = "select * from orders where status = 'hold' order by id";
      break;
    default:
      $sql = "select * from orders order by id";
      break;
  }
  $result = $dbconn->query($sql);
  errortrap($result);
?>
  <h3>订单列表</h3>
  <table border=1 cellpadding=10 cellspacing=0>
    <tr><td colspan=5><a href="admin.php?view=all">查看所有订单</a> | <a href="admin.php?view=open">查看待处理订单</a> | <a href="admin.php?view=shipped">查看已发货订单</a> | <a href="admin.php?view=backorder">查看缺货订单订单</a> | <a href="admin.php?view=hold">查看暂留订单</a></td></tr>
    <tr><td>订单编号</td><td>客户</td><td>状态</td><td>物流单号</td>&nbsp;</td></tr>
<?
while($result->fetchinto($r)) {
  $r2 = get_customer($r["customer"]);
?>
  <tr>
    <td><a href="admin.php?display=orderdetails&id=<?=$r["id"]?>"><?=$$r["id"]?></a></td>
    <td><a href="admin.php?display=customer&id=<?=$r2["id"]?>"><?=$$r2["last"]?>, <?=$r2["first"]?></a></td>
    <td><?=$r["status"]?></td>
    <td><?=$r["tracking_number"]?> &nbsp;</td>
    <td><a href="admin.php?display=update&id=<?=$r["id"]?>">更新订单状态</a></td>
  </tr>
<?
}
?>
  </table>
<?
} //结束 display_orders 结束

function display_order_details($id) {
  global $dbconn;
  $sql = "select * from order_details where orderid = '$id'";
  $result = $dbconn->query($sql);
  errortrap($result);
?>
  <h2>订单 <?=$id???> 的订单详情</h2>
  <h3>订单中的商品</h3>
  <table border=1 cellpadding=10 cellspacing=0>
    <tr><td>数量</td><td>描述</td></tr>
<?
while($result->fetchinto($r)) {
?>
  <tr>
    <td><?=$r["qty"]?> &nbsp;</td>
    <?
      $sql2 = "select * from inventory where id='" . $r["code"] . "'";
      $result2 = $dbconn->query($sql2);
      errortrap($result2);
      $result2->fetchinto($r2);
?>
    <td>
      名称: <?=$r2["name"]?>
      <br>代码: <?=$r2["code"]?>
      <br>描述: <?=$r2["description"]?>
      <br>价格: <?=$r2["price"]?>
    </td>
  </tr>
<?
}
?>
  </table>
<?
  $sql = "select customer from orders where id = '$id'";
  $result = $dbconn->query($sql);
  errortrap($result);
  $result->fetchinto($r);
  $cust = get_customer($r["customer"]);
  display_customer($cust);
} //结束 display_order_details

function update_order_status($id) {
  global $dbconn;
  $sql = "select * from orders where id = '$id'";
  $result = $dbconn->query($sql);
  errortrap($result);
  $result->fetchinto($r);
?>
  <form action=admin.php method=post>
    <p>当状态更改为“已发货”时，可以包含一个可选的物流单号发送给客户。</p>
    <table border=1 cellpadding=5 cellspacing=0>
      <tr><td>订单 ID</td><td><?=$r["id"]?></td></tr>
      <tr><td>状态（当前状态为 <b><?=$r["status"]?></b>）</td>
      <td>
        <select name="status">
          <option value="open">开启</option>
          <option value="shipped">已发货</option>
          <option value="backorder">缺货</option>
          <option value="hold">暂留</option>
        </select>
      </td>
      </tr>
      <tr><td>物流单号</td><td><input type="text" name="tracking" value="<?=$r["tracking"]?>"></td></tr>
      <input type="hidden" name="id" value="<?=$r["id"]?>">
      <input type="hidden" name="customer" value="<?=$r["customer"]?>">
      <tr><td colspan=2><input type="submit" name="update" value="更新订单!"></td></tr>
    </table>
  </form>
<?
} //结束 update_order

function update_order_process($HTTP_POST_VARS) {
  global $dbconn;
  $sql = "update orders set status='" . $HTTP_POST_VARS["status"] . "', tracking_number='" . $HTTP_POST_VARS["tracking"] ."' where id='" . $HTTP_POST_VARS["id"] . "'";
  $result = $dbconn->query($sql);
  errortrap($result);
  $message = "来自 " . COMPANY_NAME . " 的订单已处理。当前状态为：\n";
  $message .= "状态: " . $HTTP_POST_VARS["status"] . "\n";
  if($HTTP_POST_VARS["tracking"] != "") {
    $message .= "您的物流单号为 " . $HTTP_POST_VARS["tracking"] . "\n";
  }
  $r_cust = get_customer($HTTP_POST_VARS["customer"]);
  $to = $r_cust["email"];
  mail($to, COMPANY_NAME . " 订单!", $message, "From: " . COMPANY_NAME . " <" . COMPANY_EMAIL . ">");
?>
  <h3>状态已更改！</h3>
  <p>状态已更新，邮件已发送给客户。</p>
  <p>点击<a href="admin.php">这里</a>返回管理页面。</p>
<?
} //结束 update_order_process

function get_customer($id) {
  global $dbconn;
  $sql = "select * from customers id = '$id'";
  $result = $dbconn->query($sql);
  errortrap($result);
  $result->fetchinto($row);
  return $row;
} //结束 get_customer

function display_customer($r_cust) {
?>
  <h3>客户详情</h3>
  <table border=1 cellpadding=5 cellspacing=0>
    <tr><td>客户 ID</td><td><?=$r_cust["id"]?></td></tr>
    <tr><td>名字</td><td><?=$r_cust["first"]?></td></tr>
    <tr><td>中间名首字母</td><td><?=$r_cust["mi"]?></td></tr>
    <tr><td>姓</td><td><?=$r_cust["last"]?></td></tr>
    <tr><td>地址</td><td><?=$r_cust["address1"]?></td></tr>
    <tr><td>地址 2</td><td><?=$r_cust["address2"]?></td></tr>
    <tr><td>城市</td><td><?=$r_cust["city"]?></td></tr>
    <tr><td>州/省</td><td><?=$r_cust["state"]?></td></tr>
    <tr><td>邮政编码</td><td><?=$r_cust["zip"]?></td></tr>
    <tr><td>国家</td><td><?=$r_cust["country"]?></td></tr>
    <tr><td>电话</td><td><?=$r_cust["phone"]?></td></tr>
    <tr><td>邮箱</td><td><?=$r_cust["email"]?></td></tr>
  </table>
<?
} //结束 display_customer

***** MAIN *****/
require_once("../include/cart_inc.php");
$dbconn = connect();
head();

if(isset($view)) {
  display_orders($view);
} elseif(isset($update)) {
  update_order_process($HTTP_POST_VARS);
} elseif(isset($display)) {
  switch($display) {
    case("orderdetails"):
      display_order_details($id);
      break;
    case("customer"):
      $r_cust = get_customer($id);
      display_customer($r_cust);
      break;
    case("update"):
      update_order_status($id);
      break;
    default;
      break;
  }
} else {
  display_orders("all");
}
?>
```



` 标签中似乎不完整（在开头中断了），我根据您提供的结构为您翻译了已有的部分。

[content]

### 脚本 5-5. admin.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 2-47 | 定义函数 `display_orders()`，根据所选的模式显示订单。模式有：<br>* 全部（无论状态显示每个订单）<br>* 待处理 (Open)<br>* 已发货 (Shipped)<br>* 缺货订单 (Backorder)<br>* 挂起 (Hold) |
| 49-88 | 定义函数 `display_order_details()`，显示特定订单的详情。当用户点击订单号时调用此函数。显示以下信息：<br>* 订购商品<br>* 商品数量<br>* 客户信息 |
| 90-137 | 定义函数 `update_order_status()`，允许管理员更改订单状态。向客户发送电子邮件通知其状态变更。 |
| 139-146 | 定义函数 `get_customer()`，用于获取客户信息并将其返回给调用函数进行显示。 |
| 148-173 | 定义函数 `display_customer()`，显示从 `get_customer()` 返回的信息。这两个函数都是在 `get_order_details()` 中使用的辅助函数。 |
| 175 | 开始主程序。 |
| 176 | 引入 `cart_inc.php` 脚本，以便此脚本可以使用 `cart_inc.php` 中定义的函数。 |
| 177 | 建立数据库连接。 |
| 178 | 打印页面的起始 HTML。 |
| 180-181 | 如果设置了变量 `$view`，则根据 `$view` 变量显示订单——例如 `$view = "open"`。 |
| 182-183 | 如果设置了变量 `$update`，则使用 `update_order_process()` 函数处理更新。 |
| 184-198 | 如果设置了变量 `$display`，则根据 `$display` 的内容切换到相应的函数。 |
| 199-201 | 如果没有设置其他内容，则显示所有订单。 |
| 202 | 结束页面的 PHP 代码。 |

#### checkout.php

`checkout.php` 用于收集客户详情并将所有信息发送到信用卡授权服务。在这种情况下，它直接将信息发送到 `finishorder.php`。通常情况下，您会将此页面提交给授权服务，然后由授权服务重定向到 `finishorder.php`。图 5-4 显示了结账屏幕。

##### 脚本 5-6 checkout.php

全屏查看 

```php
1. <?
  2. require_once("include/cart_inc.php");
  3. session_start();
  4. head();
  5. $dbconn = connect();
  6. $response = "1";
  7. //$response = "2"; // 信用卡被拒绝
  8. //$response = "3"; // 通用错误
  9.
10. if(sizeof($items) == 0) {
 11.   ?>
 12.   <h3>购物车中没有商品！请点击浏览器的后退按钮并向购物车添加一些 
商品。</<h3>>
 13.   <?
 14. } else {
 15. ?>
 16. <h2>这里是您订购的商品：</h2>
 17. <?
 18. $status = "checkout";
 19. display_cart($items);
 20. ?>
 21. <p>请填写以下信息以继续。</p>
 22.   <FORM METHOD=POST ACTION="<?=CREDIT_AUTH_URL?>">
 23.     <INPUT TYPE=HIDDEN NAME="Amount" VALUE="<?=$total?>">
 24.     <INPUT TYPE=HIDDEN NAME="x_Description" VALUE="来自 <?=COMPANY_NAME?> 的订单">
 25.     <INPUT TYPE=HIDDEN NAME="x_Invoice_Num" VALUE="<?=time()?>">
 26.     <INPUT TYPE=HIDDEN NAME="x_response_code" VALUE="<?response?>">
 27.   <?cartform($items);?>
 28.     <table border="1" cellspacing="1" cellpadding="5">
 29.     <tr>
 30.       <td colspan="2" class="tablehead"><b>账单地址</b></td></td>>
 31.     </tr>
 32.     <tr>
 33.       <td>信用卡号<span class="required">*</span></span></td>
 34.       <td>
 35.         <input type="text" name="x_card_num">
 36.       </td>
 37.     </tr>
 38.     <tr>
 39.       <td>有效期<span class="required">* <br>
 40.         (MMYY - 例如 2002 年 4 月写为 0402)</td>
 41.       <td>
 42.         <input type="text" name="x_exp_date" maxlength="4" size="4">
 43.       </td>
 44.     </tr>
 45.     <tr>
 46.       <td>名<span class="required">*</span></span></td>
 47.       <td>
 48.         <input type="text" name="x_first_name">
 49.       </td>
 50.     </tr>
 51.     <tr>
 52.       <td>中间首字母</td>
 53.       <td>
 54.         <input type="text" name="x_mi">
 55.       </td>
 56.     </tr>
 57.     <tr>
 58.       <td>姓<span class="required">*</span></span></td>
 59.       <td>
 60.         <input type="text" name="x_last_name">
 61.       </td>
 62.     </tr>
 63.     <tr>
 64.       <td>地址行 1:<span class="required">*</span></span></td>
 65.       <td>
 66.         <input type="text" name="x_address">
 67.       </td>
 68.     </tr>
 69.     <tr>
 70.       <td>地址行 2:</td>
 71.       <td>
 72.         <input type="text" name="x_address_2">
 73.       </td>
 74.     </tr>
 75.     <tr>
 76.       <td>城市<span class="required">*</span></span></td>
 77.       <td>
 78.         <input type="text" name="x_city">
 79.       </td>
 80.     </tr>
 81.     <tr>
 82.       <td>州/省（两个字母缩写）<span class="required">*</span></span></td>
 83.       <td>
 84.         <input type="text" name="x_state" size="2" maxlength="2">
 85.       </td>
 86.     </tr>
 87.     <tr>
 88.       <td>邮政编码<span class="required">*</span></span></td>
 89.       <td>
 90.         <input type="text" name="x_zip" size="10" maxlength="10">
 91.       </td>
 92.     </tr>
 93.     <tr>
 94.       <td>国家<span class="required">*</span></span></td>
 95.       <td>
 96.         <select name=x_country>
 97.           <option>加拿大
 98.           <option>英国
 99.           <option selected>美国
 100.         </select>
 101.       </td>
 102.     </tr>
 103.     <tr>
 104.       <td>白天电话</td>
 105.       <td>
 106.         <input type="text" name="x_phone">
 107.       </td>
 108.     </tr>
 109.     <tr>
 110.       <td>电子邮件<span class="required">*</span></span></td>
 111.       <td>
 112.         <input type="text" name="x_email">
 113.       </td>
 114.     </tr>
 115.     <tr>
 116.       <td>收货地址与账单地址一致：</td></td>
 117.       <td>
 118.         <input type="checkbox" name="shiptobilling" value="true">
 119.         <br>
 120.         <font size="-2"> (勾选寄送至账单地址)</font></td>
 121.     </tr>
 122.     <tr>
 123.       <td colspan="2" class="tablehead">
 124.         <p><b>收货地址 </b><br>
 125.           （如果您的收货地址与账单地址不同，请填写此处）
 126.           地址）：</p>
 127.       </td>
 128.     </tr>
 129.     <tr>
 130.       <td>地址行 1:</td></td>
 131.       <td>
 132.         <input type="text" name="x_ship_to_address">
 133.       </td>
 134.     </tr>
 135.     <tr>
 136.       <td>地址行 2:</td></td>
 137.       <td>
 138.         <input type="text" name="x_ship_to_address">
 139.       </td>
 140.     </tr>
 141.     <tr>
 142.       <td>城市</td></td>
 143.       <td>
 144.         <input type="text" name="x_ship_to_city">
 145.       </td>
 146.     </tr>
 147.     <tr>
 148.       <td>州/省（两个字母缩写）<span class="required">*</span></span></td>
 149.       <td>
 150.         <input type="text" name="x_ship_to_state" size="2" maxlength="2">
 151.       </td>
 152.     </tr>
 153.     <tr>
 154.       <td>邮编</td></td>
 155.       <td>
 156.         <input type="text" name="x_ship_to_zip" size="10" maxlength="10">
 157.       </td>
 158.     </tr>
 159.     <tr>
 160.       <td>国家<span class="required">*</span></span></td>
 161.       <td>
 162.         <select name=x_ship_to_country>
 163.           <option>加拿大
 164.           <option>英国
 165.           <option selected>美国
 166.         </select>
 167.       </td>
 168.     </tr>
 169.   </</table>
 170.   <p>
 171.     <INPUT TYPE=SUBMIT VALUE="提交订单">
 172.   </p>
 173.</FORM>
```





- 2: 需要 `cart_inc.php`（我们需要 `define` 语句中包含的信息）。
- 3: 启动会话。我们将使用 `$items` 会话变量中的信息。
- 4: 打印页面的起始 HTML 代码。
- 5: 建立与数据库的连接。
- 6-8: 正常情况下，这些是由授权服务发送的。取消其中之一的注释以便在 `finishorder.php` 脚本中查看结果。
- 10-14: 检查购物车中是否有内容。如果没有，则没有必要显示此页面。
- 15-20: 打印一个短表格，显示已订单的项目。将 `$status` 变量设置为 `$checkout`。
- 21-173: 向用户显示表单。
- 174-176: 取消会话变量并销毁会话。
- 177: 结束第 10 行开始的 `if` 语句。
- 178: 结束该页面的 PHP 代码。

## finishorder.php

`finishorder.php` 用于将授权后的订单存入数据库。如果订单未通过服务器授权（由授权服务发送的响应码定义），则将向用户显示一条消息，通知他们存在问题。

如果订单通过，`order`、`customer` 和 `order_details` 表将更新新的订单信息，并向客户发送确认电子邮件。

### 脚本 5-7 finishorder.php

查看全屏 

```php
1.  <?
 2.  require_once("include/cart_inc.php");
 3.  head();
 4.  $dbconn = connect();
 5.
6.  switch($x_response_code) {
 7.    case("1"):
 8.      if(!isset($shiptobilling)) {
 9.        $shiptobilling = "false";
10.      }
11.      $id = $dbconn->nextID('customers',true);
12.      $sql = "insert into customers values ('$id', '$x_first_name', '$x_mi', 
'$x_last_name', '$x_address', '$x_address_2', '$x_city', '$x_state', '$x_zip', 
'$x_country', '$shiptobilling', '$x_ship_to_address', '$x_ship_to_address2', 
'$x_ship_to_city', '$x_ship_to_state', '$x_ship_to_zip', '$x_ship_to_country', '$x_phone',
 '$x_email')";
13.      $result = $dbconn->query($sql);
14.      errortrap($result);
15.      $id2 = $dbconn->nextID('orders',true);
16.      $sql = "insert into orders values ('$id2', '$id', 'open', NULL)";
17.      $result = $dbconn->query($sql);
18.      errortrap($result);
19.      foreach($cart as $code => $qty) {
20.        $id3 = $dbconn->nextID('order_details',true);
21.        $sql = "insert into order_details values ('$id3', '$id2', '$code', '$qty')";
22.        $result = $dbconn->query($sql);
23.        errortrap($result);
24.        $sql2 = "update inventory set qty = qty-'$qty' where id = $'";
25.        $result2 = $dbconn->query($sql2);
26.        errortrap($result2);
27.      }
28.      $mail = "Thank you for your order!\n";
29.      $mail .= "We have received your order and we will notify you when it ships.";
30.      mail($x_email, "Your order from COMPANY_NAME", $mail);
31.      ?>
32.      <h2>Thank you!</h2>
33.      <p>Your order has been accepted. You should receive a receipt in a few minutes.</p>
34.      break;
35.    case("2"):
36.      ?>
37.      <h2>Credit Card Denied</h2>
38.      <p>The reason was: $x_response_code</p>
39.      break;
40.    case("3"):
41.      ?>
42.      <h2>Unspecified Error</h2>
43.      <p>The reason was: $x_response_code</p>
44.      break;
45.    default:
46.      ?>
47.      <h2>Error Processing Request</h2>
48.      <p>The reason was: $x_response_code</p>
49.      break;
50.  }
51.?>
```

## 第 6 章 处理文件

本章内容
* 概述
* 打开和关闭文件
* 使用方法
* 数据挖掘
* 解析大文件

### 概述

PHP 是处理文件的非常有用的语言。虽然在解析文件方面可能不如 `PERL` 那样健壮，但在处理文本文件时，它仍然提供了强大的灵活性。

本章涵盖了读取、操作和写入文本文件。你可以使用本章的功能，从文件（本地或通过 HTTP、FTP）读取数据，并根据你的需求处理这些数据。

### 打开和关闭文件

#### 打开文件

在用 PHP 读取文件之前，必须先将其打开。要打开文件，你需要使用 `fopen()` 函数。

```php
$file_handler = fopen($file, $mode)
```

你必须将函数结果赋值给变量，如上所示。这被称为文件指针。你在整个脚本中使用该指针来引用打开的文件。

`fopen()` 函数有两个参数：

* `$file` 是文件名（如果需要，包含路径）。
* `$mode` 是可用模式之一：
    * `r`—— 只读模式打开文件。你不能向文件中写入任何内容。读取从文件开头开始。
    * `r+` —— 以读写模式打开文件。读写都从文件开头开始。如果你在将内部指针移动到文件末尾之前进行写入，将删除现有内容。
    * `w`—— 只写模式打开文件。你不能从文件中读取数据。写入从文件开头开始。如果指定的 `$file` 参数的文件不存在，则 PHP 会尝试创建该文件。请确保你的权限设置正确！





* `w+` — 与上述相同，但也可以读取文件。
* `a`— 这种模式与 'w' 模式相同，区别在于内部指针被置于文件末尾。除非你将内部指针重置到文件开头，否则现有内容不会被覆盖。
* `a+` — 与上述相同，但也可以读取文件。

此外，如果文件是二进制文件，且你的操作系统是 Windows，则必须在模式中包含一个 `"b"`。本章仅处理 ASCII 文本文件，因此在接下来的示例中不需要 `"b"` 模式。如果你确实需要打开二进制文件，例如所示：

```
$file_handle = fopen($filename, "rb+") 
```

请注意 `"w"` 和 `"a"` 模式之间的区别。使用 `"w"` 打开文件会有效删除文件内容，而使用 `"a"` 模式则保留文件内容并允许你向文件末尾追加额外数据。

一旦打开了文件，你就可以从中读取或写入文件。

### 读取文件

有多个函数可以从文件中读取内容。

你可以使用 `fread()` 函数从文件中读取数据：

```
$file_contents = fread($file_pointer, $length_to_read); 
```

你必须将 `fread()` 的赋值赋值一个变量，该变量将包含读取到的数据。`fread()` 函数接受两个参数：

* `$file_pointer` 是你从 `fopen()` 函数中赋值的值的文件指针。
* `$length` 是你想要读取的字节数。

在使用 `fread()` 读取文件时，你可以读取整个文件。要做到这一点，你需要知道文件的字节大小。你可以使用 `filesize()` 函数轻松找到文件的总字节大小：

```
$bytes = filesize($filename); 
```

以下脚本演示了如何打开一个短文本文件并显示其内容：

```
$file = "/path/to/text.txt"; 
$filepointer = fopen($file, "r");
$contents = fread($filepointer, filesize($file));
echo "<pre>" . htmlentities($contents) . "</pre>";
```

在从互联网读取文件时，存在一个轻微的问题：你无法轻易确定文件的大小，因为文件不在本地服务器上。一个简单的解决办法是尝试读取比你认为文件中存在的字节得多的字节。由于 `fread()` 在到达文件末尾 (EOF) 时会停止，因此无需担心 PHP 为你在 `fread()` 的 `$length` 参数中指定的额外字节浪费处理资源。例如：

```
$file = "http://www.example.com/text.txt"; 
$filepointer = fopen($file, "r");
$contents = fread($filepointer, 9999999);
```

### 关闭文件

当你完成对使用 `fopen()` 函数打开的文件的读取或写入后，应该始终使用 `fclose()` 函数将其关闭：

```
fclose($filepointer); 
```

关闭文件允许你清理打开该文件时使用的任何内存，并防止文件在保持打开状态时有时（极少情况下）可能的文件损坏。

 * *

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch06lev1sec1.htm) ![下一节](img/#ch06lev1sec3.htm) |
| 顶部 |
| --- |
| ![](img/#index.htm) ![上一节](img/#ch06lev1sec2.htm) ![下一节](img/#ch06lev1sec4.htm) |

 * *

### 实际应用

接下来的脚本展示了如何从互联网打开文件并将其显示在页面上，如图 6-1 所示。美国海洋和大气管理局（NOAA）提供了各种用途的数据。

```php
<?php
// 1.php
?>
<html
<head>
<title>METAR-1.php</title>
</head>
<body bgcolor="#FFFFFF">
<!-- 2.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 3.php -->
<title>METAR-1.php</title>
</head>
<body
<!-- 4.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 5.php -->
<title>METAR-1.php</title>
</head>
<body
<!-- 6.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 7.php -->
<title>METAR-1.php</title>
</head>
<body
<!-- 8.php -->
<title>METAR-1.php</title>
</head>
<body
<!-- 9.php -->
<title>METAR-1.php</title>
</head>
<body
<!-- 10.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 11.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 12.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 13.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 14.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 15.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 16.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 17.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 18.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 19.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 20.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 21.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 22.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 23.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 24.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 25.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 26.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 27.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 28.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 29.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 30.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 31.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 32.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 33.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 34.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 35.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 36.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 37.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 38.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 39.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 40.php -->
<title>METAR-1.php</title>
</head>
<<body>
<!-- 41.php -->
<title>METAR-1.php</title>
</head>
</body>
</html>
```




| 23 | 与上述相同，只是这次打开数据的编码版本并将其赋值给 `$file2` 变量。 |
| 24–25 | 尝试打开 NOAA 服务器上的文件。如果无法打开该文件，则向 `connect_error()` 函数抛出错误以通知用户。 |
| 26 | 如果打开文件时没有错误，则执行第 27–30 行。 |
| 27 | 读取文件的全部内容（我们假设它小于 9,999,999 字节）并将其赋值给 `$decoded` 变量。 |
| 28 | 将数据打印到页面。我们使用 `htmlentities()` 将任何可能被识别为 HTML 代码的数据转换为该数据的 HTML 代码。 |
| 29 | 使用 `fclose()` 函数关闭文件。 |
| 30 | 关闭第 26 行开始的 `if` 语句。 |
| 31–32 | 尝试打开 NOAA 服务器上的另一个文件。如果无法打开该文件，则向 `connect_error()` 函数抛出错误以通知用户。 |
| 33 | 如果打开文件时没有错误，则执行第 34–37 行。 |
| 34 | 读取文件的全部内容（我们假设它小于 9,999,999 字节）并将其赋值给 `$decoded` 变量。 |
| 35 | 将数据打印到页面。我们使用 `htmlentities()` 将任何可能被识别为 HTML 代码的数据转换为该数据的 HTML 代码。 |
| 36 | 使用 `fclose()` 函数关闭文件。 |
| 37 | 关闭第 33 行开始的 `if` 语句。 |
| 38 | 关闭第 31 行开始的 `if` 语句。 |
| 39–41 | 结束脚本的 PHP 和 HTML。 |

***

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm) ...（省略了导航链接） |

***

### 数据挖掘

许多 Web 页面都提供了大量的有用信息。有时，你需要的信息被许多你不需要或不的其他信息包围。使用 PHP，可以读取 Web 上的页面并提取你需要的信息。

从其他网站提取信息时，重要的是记住另一个网站上的任何数据都可能受版权保护。在没有数据所有者明确许可的情况下，不要为了自己的目的使用他人的数据。

接下来的示例详细介绍了如何从路透社新闻服务（Reuters News Service）网页检索股票报价。这仅仅是一个示例，除非你获得路透社关于使用其数据的书面许可，否则应在你自己的网站上使用。

HTML 是一种指定页面包含数据类型相当糟糕的语言。它在格式化数据方面很好，但在查找你需要的数据方面，你有时需要一点想象力。

在提取所需数据之前，你必须以其“自然”状态查看数据。在下面的示例中，在你搜索报价后，数据是从 [www.reuters.com/quote.jhtml](http://www.reuters.com/quote.jhtml) 的路透社页面获取的。查看页面的 HTML，你会发现报价在“Bid”（买入）和“Ask”（卖出）行下方，这些行是页面上唯一的。因此，你可以通过搜索唯一文本来提取价格。

此脚本使用了另一种读取文件的方法，称为 `file()` 函数：

```php
$file = "/home/me/myfile.txt"; 
$filearray = file($file);
```

`file()` 函数打开文件，将文件内容读入数组，文件中的每行对应数组中的一个元素，然后关闭文件。`file()` 接受一个参数，即要打开的文件名，如果适用，则包含路径。

再次提醒，在使用用于挖掘 Web 页面数据的脚本时，务必尊重版权声明！此脚本的结果可以在 图 6-2 中看到。

##### 脚本 6–2 stockquote.php

```php
1.  <html>
 2.  <head><title>Stock Quote Mining</title></head>
 3.  <body><body>
 4.  <form action="stockquote.php">
 5.  <p>Enter Symbol For Quote: <input type="text" name="symbol">
 6.  <br><input type="submit" name="submit" value="Fetch Quote">
 7.  </form>
 8.  <hr noshade>
 9.  <?
10.  if(isset($symbol)) {
11.    $file = "http://www.reuters.com/quote.jhtml?ticker=";
12.    $contents = file($file . $symbol);
13.    $size = sizeof($contents);
14.    echo "<h3>Quote for $symbol</h3>";
15.    for($i = 0; $i < $size; $i++) {
16.      $data = strip_tags($contents[$i]);
17.      if(trim($data) == "Ask") {
18.        $quote = strip_tags($contents[$i+1]);
19.        echo "<p>Ask: $quote</p>";
20.      }
21.      if(trim($data) == "Bid") {
22.        $quote = strip_tags($contents[$i+1]);
23.        echo "<p>Bid: $quote</p>";
24.      }
25.    }
26.  }
27.  ?>
28.  </body>
29. </html>
```

##### 图 6-2 stockquote.php

![graphics/06fig02.jpg](img/06fig02.jpg)

##### 脚本 6-2 stockquote.php 逐行解释

| 行 | 说明 |
| --- | --- |
| 1–8 | 输出页面的起始 HTML 以及请求代码的表单 |
| 9 | 开始页面的 PHP |
| 10 | 检查 `$symbol` 是否设置 |
| 11 | 将 URL 赋值给 `$file` |
| 12 | 将从文件读取的内容赋值给 `$contents` |
| 13 | 获取 `$contents` 数组的大小 |
| 14 | 输出标题 |
| 15–25 | 使用 `for` 循环遍历数组中的每个记录 |
| 16 | 从获取的记录中提取 HTML 标签并将此值赋值给 `$data` |
| 17–20 | 如果裁剪 `$data` 后结果为 "Ask"，那么在分析我们要挖掘的页面后，我们我们需要的数据在下一行。执行第 18–20 行。 |
| 18 | 从数组的下一行（`$contents[$i+1]`）获取 "Ask" 报价 |
| 19 | 向页面输出 "Ask" 报价 |
| 21–24 | 如果裁剪 `$data` 后结果为 "Bid"，那么在分析我们要挖掘的页面后，我们我们需要的数据在下一行。执行第 22–24 行。 |
| 22 | 从数组的下一行（`$contents[$i+1]`）获取 "Bid" 报价 |
| 23 | 向页面输出 "Bid" 报价 |
| 25 | 关闭第 15 行开始的 `for` 循环 |
| 26 | 关闭第 10 行开始的 `if` 语句 |
| 27–29 | 结束页面的 PHP 和 HTML |

***

### 解析大文件

上面的方法对于相对简单的文件效果良好，但如果你需要解析一个结构基本但有细细微差异的大文件呢？一种方法是使用 `ereg()` 函数^([\[1\]](#ch06lev1sec5.htm#ch06fn01)) 来寻找数据模式。

> ^(\[1\]) 有关 `ereg()` 函数的细节请参阅 第 4 章。




接下来的脚本将解析大型文本文件并将其内容存入数据库。该文件包含 789 道多选题，见于美国联邦航空管理局（FAA）私人飞行员笔试。

> [2] 这些问题不受版权保护，可以免费获取。

该文档遵循基本结构，即带有编号的问题，后跟着三个可能的答案。某些问题引用了图表，而另一些问题引用了多个图表。脚本的目标是解析文本文件并将每个问题放入 `MySQL` 数据库，同时包含相应的答案选项。如果问题引用了某个或多张图表，脚本也会将其放入数据库。

该文档可以在互联网上找到 [av-info.faa.gov/data/airmanknowledge/par.txt](http://av-info.faa.gov/data/airmanknowledge/par.txt)。该文档非常大，且某些问题的结构略有不同，特别是当提到引用的图表时。

该脚本获取问题并将所有信息放入数据库，以便更于管理数据并将其转换为其他应用程序可格式。

此脚本使用了另一个名为 `preg_split()` 的正则表达式函数。`preg_split()` 能够将字符串拆分为数组，类似于常用的 `explode()` 函数。它不是根据某个字符拆分字符串，而是根据正则表达式匹配来拆分字符串。

在阅读脚本描述之前，请查看 [av-info.faa.gov/data/airmanknowledge/par.txt](http://av-info.faa.gov/data/airmanknowledge/par.txt) 中的文件，以熟悉数据的通用结构。这样一切都会变得清晰得多。

脚本由三个文件组成：

*   `parsefile.sql`—— 创建和设置数据库所需的 SQL 语句。
*   `parsefile.php`—— 解析文本文件并将数据放入数据库的 PHP 脚本。
*   `displaydata.php`—— 从数据库读取数据并向用户显示数据的 PHP 脚本。此脚本仅是关于数据放入数据库后你可以进行操作的一个示例。

### 脚本 6–3 parsefile.sql

```
1.  //mysqladmin create faa
 2.
3.  grant ALL on faa.* to php@localhost identified by "password";
 4.
5.  create table questions(
 6.    id INT NOT NULL,
 7.    code varchar(8),
 8.    question TEXT,
 9.    primary key(id));
10.
11.  create table answers(
 12.    question INT NOT NULL,
 13.    letter CHAR(1),
 14.    answer TEXT);
 15.
16.  create table figures(
 17.    question INT NOT NULL,
 18.    figure VARCHAR(3),
 19.    additional VARCHAR(24));
 20.
21.  create table info(
 22.    id INT NOT NULL,
 23.    version VARCHAR(8),
 24.    date VARCHAR(10),
 25.    bank VARCHAR(16));
```

### 脚本 6-3. parsefile.sql 逐行解释

| 行 | 描述 |
| --- | --- |
| 1 | 使用 `mysqladmin` 命令行程序创建一个名为 "faa" 的数据库。 |
| 3 | 授予所需的权限，以便用户可以使用用户名 "php" 和密码 "password" 访问数据库。 |
| 5–9 | 创建一个存储问题文本的表。 |
| 11–14 | 创建一个存储答案的表。每个问题有三个答案。 |
| 16–19 | 创建一个存储问题中任何图表引用的表。 |
| 21–25 | 创建一个存储题库版本和日期信息的表。 |

### 脚本 6–4 parsefile.php

查看全屏





```php
1. <?
  2. function connect() {
  3.   if(!mysql_connect("localhost","php","password")) {
  4.     die("<h1>Could Not Connect To MySQL Server</h1>");
  5.   } elseif(!mysql_select_db("faa")) {
  6.     die("<h1>Could Not Access DB</h1>");
  7.   }
  8.   return 1;
  9. }
 10.
11. function parse($data) {
 12.   global $question_num;
 13.   // 如果引用图表，考虑到 FAA 标记这些图表的方式不一致
 14.   if(ereg("(\(Refer to figure )([0-9]+)(\.\)|(\)\.))", $data, $regs)) {
 15.     $data2 = preg_split("/(\(Refer to figure )([0-9]+)(\.\)|(\)\.))/", $data);
 16.     sql_query("insert into figures values('$question_num','" . $regs[2] . "', NULL)");
 17.     return trim($data2[1]);
 18.   // 如果引用多个图表，考虑到 FAA 标记这些图表的方式不一致
 19.   } elseif (ereg("(\(Refer to figures |\(Refer to figure )([0-9]+|[0-9]+) (, and |and 
...figure )([0-9]+)(\.)(\))", $data, $regs)) {
 20.     $data2 = preg_split("/(\(Refer to figures |\(Refer to figure )([0-9]+|[0-9]+) (, and 
...||and figure )([0-9]+)(\.)(\))/", $data);
 21.     sql_query("insert into figures values('$question_num','" . $regs[2] . "', NULL)");
 22.     sql_query("insert into figures values('$question_num','" . $regs[4] . "', NULL)");
 23.     return trim($data2[1]);
 24.   // 如果引用带有区域的图表，考虑到 FAA 标记这些图表的方式不一致
 25.   } elseif(ereg("(\(Refer to figure )([0-9]+)(, | )([a-zA-Z]+)( [ a-zA-Z0-9]+)(\.)(\))", 
...data, $regs)) {
 26.     $data2 = preg_split("/(\(Refer to figure )([0-9]+)(, | )([a-zA-Z]+)( [ a-zA-Z0-9]+)(\.)(\
......))/", $data);
 27.     sql_query("insert into figures values('$question_num','" . $regs[2] . "', 'area " . 
...regs[5] . "')");
 28.     return trim($data2[1]);
 29.   // 奇葩的分号和多个图表区域搞乱了一切...
 30.   } elseif(ereg("(\(Refer to figure )([0-9]+)(, | )([a-zA-Z]+)( [ a-zA-Z0-9]+)(; and 
...figure )([0-9]+)(\.)(\))", $data, $regs)) {
 31.     $data2 = preg_split("/(\(Refer to figure )([0-9]+)(, | )([a-zA-Z]+)( [ a-zA-Z0-9]+)(; 
...and figure )([0-9]+)(\.)(\))/", $data);
 32.     sql_query("insert into figures values('$question_num','" . $regs[2] . "', 'area " . 
...regs[5] . "')");
 33.     sql_query("insert into figures values('$question_num','" . $regs[7] . "', NULL)");
 34.     return trim($data2[1]);
 35.   // 其他所有情况
 36.   } else {
 37.     return $data;;
 38.   }
 39. }
 40.
41. function sql_query($query){
 42.   if(!mysql_query($query)) {
 43.     die("<h1>Error with QUERY: $query</h1>");
 44.   }
 45.   //echo "<P>$query";
 46. }
 47.
 48. /***** MAIN *****/
 49. //$file = "http://av-info.faa.gov/data/airmanknowledge/par.txt";
 50. $file = "par.txt";
 51. $contents = file($file);
 52. $size = sizeof($contents);
 53. $questions = "not started";
 54.
 55. $answer_let = "A";
 56. $question = "";
 57.
 58. connect();
 59. mysql_query("delete from questions");
 60. mysql_query("delete from answers");
 61. mysql_query("delete from figures");
 62. mysql_query("delete from info");
 63. insert into info values ('1',NULL,NULL,NULL);
 64. for($i = 0; $i < $size; $i++) {
 65.   if(trim($contents[$i]) != ""){
 66.     $data = $contents[$i];
 67.     if(ereg("^Version", $data)) {
 68.       $versioninfo = explode(":", $data);
 69.       $version = trim($versioninfo[1]);
 70.       sql_query("update info set version = '$version' where id = '1'");
 71.     } elseif(ereg("[0-9]+/[0-9]+/[0-9]+", $data)) {
 72.       $date = trim($data);
 73.       sql_query("update info set date = '$date' where id = '1'");
 74.     } elseif(ereg("^Bank", $data)) {
 75.       $bankinfo = explode(":", $data);
 76.       $bank = trim($bankinfo[1]);
 77.       sql_query("update info set bank = '$bank' where id = '1'");
 78.     } elseif(ereg("[0-9]+/[0-9]+/[0-9]+", $data)) {
... (根据格式规则截断)
```

##### 脚本 4. parse.php 逐行解析

| 行号 | 说明 |
| :--- | :--- |
| 2–9 | 定义 `connect()`，建立数据库连接。 |
| 11–39 | 定义 `parse()`，解析数据。 |
| 12 | 允许变量 `$question_num` 使用。 |
| 13 | 提供关于后续情况的注释。 |
| 14 | 如果 `$data` 匹配 `ereg()` 表达式，则执行 15–17。 |
| 15 | 在 14 行匹配 `ereg()`，此行将图表引用与实际问题分离。 |
| 16 | 使用 `$question_num` 变量作为伪外键将图表引用存入数据库。 |
| 17 | 将实际问题返回主程序（不含图表引用）。 |
| 18 | 提供关于后续情况的注释。 |
| 19 | 如果不是，跳转到第 19 行。 |
| 20 | 由于文中标记图表的方式不一致，我们需要使用考虑到文本中差异的正则表达式。 |
| 21–22 | 使用 `$question_num` 变量作为伪外键将图表引用存入数据库。 |
| 23 | 将实际问题返回主程序（不含图表引用）。 |
| 24 | 提供关于后续情况的注释。 |
| 25 | 如果 `$data` 匹配 `ereg()` 表达式，则执行 26–28。 |
| 27 | 使用 `$question_num` 变量作为伪外键将图表引用存入数据库。 |
| 28 | 将实际问题返回主程序（不含图表引用）。 |
| 29 | 提供关于后续情况的注释。 |
| 30 | 如果 `$data` 匹配 `ereg()` 表达式，则执行 31–34。 |
| 32–33 | 使用 `$question_num` 变量作为伪外键将图表引用存入数据库。 |
| 34 | 将实际问题返回主程序（不含图表引用）。 |
| 35 | 提供关于后续情况的注释。 |
| 41 | 定义 `sql_query()`，执行查询。 |
| 42 | 如果 `mysql_query()` 失败，则执行 43。 |
| 48–57 | 主部分逻辑。 |
| 50 | 将 `$file` 设置为 "par.txt"。 |
| 51 | 读取文件到 `$contents` 数组。 |
| 52 | 获取 `$contents` 的 `size()`。 |
| 53 | 初始化 `$questions` 为 "not started"。 |
| 55–56 | 初始化 `$answer_let` 和 `$question`。 |
| 58 | 调用 `connect()`。 |
| 59–62 | 清空表中的现有数据。 |
| 63 | 在 `info` 表中插入初始记录。 |
| 64 | 遍历 `$contents` 的每一行。 |
| 65 | 如果行不空，则： |
| 66 | 将行赋值给 `$data`。 |
| 67 | 如果 `$data` 以 "Version" 开，则执行 68–70。 |
| 70 | 提取版本并更新 `info` 表。 |
| 71 | 如果 `$data` 匹配日期模式，则执行 72–73。 |
| 73 | 提取日期并更新 `info` 表。 |
| 74 | 如果 `$data` 以 "Bank" 开始，则执行 75–77。 |
| 77 | 提取银行并更新 `info` 表。 |
| 78 | 如果 `$data` 匹配图表模式，则执行 79–81。 |
| 79 | 如果 `$questions` 为 "started"，则： |
| 80 | 使用 `preg_split()` 将 `$data` 拆分为部分。 |
| 81 | 将版本存入 `info` 表。 |
| 82 | 将 `$questions` 设置为 "started"。 |
| 83 | 初始化 `$question` 为空字符串。 |





### 19
此用例与之前的相似，只是它尝试匹配具有多个图表引用的问题，例如：
* (参见图 # 和图 #)
* (参见图 # 和图 #)
* (参见图 #，和 #)

由于文本中每个问题最多包含两个图，我们需要提取出两个图表编号并将它们存入数据库中。我们再次使用 `$regs` 参数传递给 `ereg()`，通过用括号对正则表达式进行细致分组，我们知道图表编号将位于第二个和第四个分组，即 `$regs[2]` 和 `$regs[4]`。

### 20
与之前一样，我们需要分割文本，以从实际问题中移除图表引用，并使用与上一行相同的正则表达式进行 `split` 操作。

### 21–22
将多个图表引用存入数据库中。

### 23
将数据的实际问题部分返回给主程序进行进一步处理。

### 24
提供一个注释来解释接下来的用例。

### 25
如果你查看过文本文件，可能会注意到某些带有图表引用的问题还提到了图表的特定区域。此 `ereg()` 函数已经考虑了这些区域引用。

### 26
分割文本以提取实际问题部分。

### 27
将图表引用连同对图表的区域引用一起存入数据库。

### 28
将问题返回给主程序。

### 29
提供一个彩色的注释来解释接下来的用例。

### 30
最后，我们考虑了包含区域的多个图表，并为了以防万一插入了奇数的分号或逗号。此 `ereg()` 函数匹配如下文本：
* (参见图 #，区域 A；和图 #)
* (参见图 # 区域 #，和图 #)
* (参见图 # 区域 A，和 #)

### 31
再次分割文本以提取实际问题。

### 32–33
将图表/区域引用存入数据库中。

### 34
将实际问题返回给主程序。

### 35
提供一个注释来解释接下来的用例。

### 36–38
如果没有图表引用，那么我们假设剩余数据只是问题的行，并将其返回给主程序，以附加到已经发送的问题的其他部分之后。

### 39
结束函数声明。

### 41–46
定义一个函数 `sql_query()`，尝试将查询发送到数据库。如果发生错误，脚本将终止。有一行被注释掉的 `echo`。如果你想在浏览器中打印查询语句，请取消该行的注释。

### 48
开始主程序。

### 49–50
定义用于打开文件的 `$file` 变量。这些行中的每一行的作用都是相同的。如果你将文件复制到了本地机器，请取消第 50 行的注释并注释第 49 行。如果你有快速的互联网连接，则执行相反操作。

### 51
使用 `file()` 函数将 `$file` 的内容读取到数组中。

### 52
通过查看数组中的记录数量来确定文件中有多少行。

### 53
定义变量 `$questions` 并给它赋值为 "not started"（未开始）。这样做是因为文件开头有一些额外信息，在我们开始解析问题本身之前，必须对这些信息进行解析。

### 55
定义变量 `$answer_let` 并赋值赋值为 "A"。这用于跟踪当前答案的字母（A、B 或 C）。

### 56
定义变量 `$question` 并给它一个空值。这将用于在从文件中读取问题片段时保存并追加它们。

### 58
使用 `connect()` 函数建立数据库连接。

### 59–62
执行查询以删除数据库内容。由于数据库设计为一次只存储一个版本的问题，你必须确保数据库中没有现有数据。

### 63
在 `info` 表中插入一条“default”（默认）行作为占位符。

### 64–102
遍历文本文件的每一行并对其进行解析。

### 65
如果该行为空，则继续。否则，跳转到第 101 行。

### 66
将当前行的值（`$contents[$i]`）赋值给 `$data` 变量以减少打字量。

### 67–70
如果行以 "Version" 开头，则根据 ":" 字符分割该行，去除任何空格，并通过将 SQL 发送给 `sql_query()` 函数将题库的版本号存入数据库。

### 71–73
如果行包含日期格式——例如 "6/11/2002"——则去除文本周围的空格并将其放入数据库。

### 74–77
如果行以 "Bank" 开头，则根据 ":" 字符分割该行，去除任何空格，并将库信息存入数据库。

### 78
如果行以数字紧跟一个点号开头，那么通过研究文本，我们知道这是一个题号。继续执行到第 87 行。

### 79–82
如果 `$question` 变量已被设置，说明我们已经收集了一些问题数据。将该问题存入数据库并清空 `$question` 变量，因为我们将一个新的问题。

### 83
将 `$questions` 变量设置为已（如果这是遇到的第一个问题，它可能还没有被设置）。

### 84
根据任何空格分割当前行。问题的初始行如下：
`"1. || A01 || PVT"`
会将行分为三个数组元素并赋值给 `$data2` 变量。

### 85
从 `$data2` 数组获取题号，去掉末尾的点号，并赋值给 `$question_num` 变量。

### 86
从 `$data2` 变量获取问题代码并赋值给 `$code` 变量。

### 87
将题号和代码插入数据库。我们暂时不放入实际问题，在该处仅一个 `NULL`。稍后我们会放入完整的问题。

### 88
如果行以 "A."、“B." 或 "C." 开头，我们知道这是问题的答案之一。跳转到第 95 行。

### 89
使用 `preg_split()` 函数将字母与实际答案分离。

### 90
使用题号作为外键将答案插入数据库。使用 `$answer_let` 变量作为答案字母。

### 91
增加 `$answer_let` 变量，因为我们知道下一个字母比当前的大一个。

### 92–94
如果 `$answer_let` 变量为 "D"，将其重置为 "A"，因为我们知道每个问题有三个可能的答案：A、B 或 C。

### 95–99
如果上述均未匹配，那么我们知道获得了一个实际问题，因为前面没有上述任何匹配。将此部分文本发送给 `parse()` 函数进行解析。

### 100
结束从第 65 行开始的 `if` 语句。

### 101
结束从第 64 行开始的 `for` 循环。

### 102
如果脚本运行到这里没有崩溃，说明没有发生任何错误。打印一条消息告诉你自己！

### 103
结束脚本的 PHP 代码。现在运行 `displaydata.php` 查看结果。

接下来的脚本（如图 6-3 所示）仅仅显示我们放入数据库中的内容。这只是一个快速的示例，向你展示了 `parsefile.php` 是如何彻底解析该大型文本文档的。

##### 脚本 6–5 displaydata.php





```php
1.  <html>
2.  <head><title>Display Parsed File From Database</title>
3.  <style type=text/css>
4.  h1, h2, h3, p, td, a {font-family: verdana, arial, helvetica, sans-serif;}
5.  .navy {color: navy; }
6.  </style>
7.  </head>
8.  <body>
9.  <?
10.
11.    function connect() {
12.      if(!mysql_connect("localhost","php","password")) {
13.        die("<h1>Could not connect to MySQL Server</h1>");
14.      } elseif(!mysql_select_db("faa")) {
15.        die("<h1>Could Not Access DB</h1>");
16.      }
17.    return 1;
18.  }
19.
20.  function display($sql) {
21.    $color = "#FFFFFF";
22.    connect();
23.    $result = mysql_query($sql);
24.    while($row = mysql_fetch_array($result)) {
25.      $question_num = $row['id'];
26.      echo "<tr bgcolor=\"$color\"><td class=navy>" . $question_num . "</td><td><pre>" . 
stripslashes($row['question'] . "</pre>");
27.      $sql2 = "select * from figures where question = '$question_num' order by figure";
28.      $result2 = mysql_query($sql2);
29.      if(mysql_num_rows($result2) > 0) {
30.        while($row2 = mysql_fetch_array($result2)) {
31.          echo "<br>See Figure: " . $row2['figure'] . " " . $row2['additional'];
32.        }
33.      }
34.      echo "</td></tr></tr>>";
35.      $sql3 = "select * from answers where question = '$question_num' order by letter";
36.      $result3 = mysql_query($sql3);
37.      while($row3 = mysql_fetch_array($result3)) {
38.        echo "<tr bgcolor=\"$color\"><td colspan=2>";
39.        echo $row3['letter'] . ". " . stripslashes($row3['answer']);
40.        echo "</td></tr>";
41.      }
42.      if($color == "#FFFFFF") {
43.        $color = "#FFFF80";
44.      } else {
45.        $color= "#FFFFFF";
46.      }
47.      echo "</td></tr>";
48.      flush();
49.    }
50.  }
51.  ?>
52.  <table border=1 cellspacing=0 cellpadding=5>
53.  <?
54.  if(!isset($next)) {
55.    $sql = "select * from questions limit 0, 200";
56.    $next = 0;
57.  } else {
58.    $sql = "select * from questions order by id limit $next, 200";
59.  }
60.  display($sql);
61.  $next += 200;
62.  ?>
63.  </table>
64.  <p><a href="displaydata.php?next=<?=$next?>">下 200 个问题</a></p>
65. </body>
66. </html>
```

##### 图 6-3. displaydata.php

![graphics/06fig03.jpg](img/06fig03.jpg)

### 脚本 6-5. displaydata.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 1–9 | 打印脚本的起始 HTML 部分，包括一些样式表格式。 |
| 11–18 | 定义一个函数 `connect()`，用于连接数据库。 |
| 20–50 | 定义一个函数 `display($sql)`，用于连接数据库。`display()` 函数接收一个参数 `$sql`，即 SQL 语句。 |
| 21 | 初始化 `$color`。`$color` 用于为每行交替颜色。 |
| 22 | 调用 `connect()` 连接数据库。 |
| 23 | 使用传递函数的 `$sql` 生成 `$result`。 |
| 24–34 | 显示问题以及与其相关的插图。 |
| 35–41 | 显示与问题相关的答案。 |
| 42–46 | 更改 `$color` 使其与当前颜色相反。 |
| 47 | 将内容刷新到浏览器。 |
| 49 | 结束循环。 |
| 50 | 结束函数。 |
| 52 | 打印表格的起始部分。 |
| 53 | 回到 PHP 模式。 |
| 54–59 | 如果 `$next` 未设置，则创建一个 SQL 语句来显示前 200 个问题。如果 `$next` 已设置，则使用它显示后续 200 个。 |
| 60 | 使用生成的 SQL 执行 `display($sql)`。 |
| 61 | 将 `$next` 增。 |
| 63 | 关闭表格。 |
| 64 | 打印指向下 200 个问题的链接。 |
| 65–66 | 关闭 HTML 标签。 |





这些身份验证方法适用于临时网站。它们不应被用于保护敏感信息，例如社会安全号码、信用卡号，或任何你不会随手丢在街角的物品。有很多方法可以绕过这些手段，无论是通过黑客攻击、IP 伪装还是传统的暴力破解。然而，对于需要基本身份验证且耗费数小时尝试破解所能获得的益处也微乎其微的社区网站来说，这些方法是行有效的。当涉及到信用卡时，恶意黑客有许多可为之图，但当奖励仅仅是一份用户的收藏链接列表时，他们没有动力去花费破解系统所需的精力。简单来说，不要认为仅仅将你的信息放置在 `PHP` 身份验证方案之后，你的信息就是安全的无的。

本章将深入探讨上述某些场景，以及一些额外的场景，例如将登录限制在一个域名内甚至一个 IP 地址范围内。

***

| ![](img/pixel.gif) |

| --- |

| ![](img/#index.htm)   ![Previous section](img/#ch07_split_000.htm)   ![Next section](img/#ch07lev1sec2.htm) |

| Top |

| --- |

| ![](img/#index.htm)   ![Previous section](img/#ch07lev1sec1.htm)   ![Next section](img/#ch07lev1sec3.htm) |

| --- |

***

### 生成密码

`md5()` 和 `crypt()` 函数对密码进行加密，但它们无法被解密。这些是单向算法。你可以通过比较用户进入网站时使用的密码的 `md5()` 或 `crypt()` 输出，来验证用户的密码是否与其最初提供的密码匹配。相同字符串的两个加密版本是匹配的（假设使用 `crypt()` 函数创建密码时使用了相同的“盐”（salt））。

这是好事，因为你永远不会存储用户的实际密码。如果你的密码文件落入别有用之手，他们对此也做不了什么。解密由 `md5()` 或 `crypt()` 加密的密码是非常困难的。由于你不存储用户的实际密码，即使获取你密码文件的恶意黑客也无法获取该密码并轻易用它尝试破解你的用户可能访问的其他网站，因为遗憾的是，大多数人不会为访问的每个网站使用不同的密码。

本章后面的脚本假设你已经创建了某种包含用户名和密码的文件。在文本文件中存储密码的通用惯例是每行放置一个用户名/密码组合，并用冒号分隔用户和密码。例如：

```
user1:sih2hDu1acVcA 
user2:aSP2C8UUWnxjA
```

本章的第一个脚本会针对你输入的任何字符串创建一个 `md5()` 加密密码和一个 `crypt()` 加密密码。如图 7-1 所示，你可以使用此脚本轻松地生成加密密码并显示它们。

#### 脚本 7-1 generate_passwords.php

```php
<<html>
<head>
<title>密码生成器</title>
</head>
<body>
<form action="generate_passwords.php" method="post">
<h3>输入密码以创建 MD5 和 Crypt 密码。</h3>
<input type="text" name="password">
<input type="submit" name="create" value="创建!">
</form>
<?
if(isset($_POST["password"])) {
?>
<h3>"<?=$password?>" 的密码为：</h3>
<ul>
<li>MD5: <?=md5($password)?></li>
<li>Crypt: <?=crypt($password)?></li>
</ul>
<?
}
?>
</body>
</html>
```

![图 7-1.密码]

#### 脚本 7-1 generate_passwords.php 逐行说明

| 行 | 说明 |
| --- | --- |
| 1–10 | 创建一个名为“password”的 HTML 输入字段和一个提交按钮。 |
| 11 | 开始 PHP。 |
| 12 | 检查变量 `$password` 是否已设置。如果是，跳转到第 13 行；否则跳转到第 20 行。 |
| 13–19 | 结束 PHP。输出经过 MD5 和 Crypt 函数加密后的密码。重新开始 PHP。 |
| 20 | 结束第 12 行的 if 语句。 |
| 21 | 结束 PHP。 |
| 23 | 输出页面的结束 HTML。 |

### 针对文本文件进行身份验证

并不是所有网站都包含存储数据的后端，某些网站可能永远不需要它们。尽管如此，你可能想限制对网站部分甚至整个网站的访问。一种方法是针对服务器某处的文本文件进行身份验证，最好放在 Web 服务器目录之外，这样别人无法访问它。

这种方法只需要标准文件函数以及 MD5 加密函数。

此脚本具有双重目的。它既允许你向密码文件添加用户，也可以测试身份验证。这样，你可以创建一个空白文本文件并填充一些用户名/密码组合，以便测试脚本的功能。

此脚本并不旨在完整地用于网站密码检查。在将脚本放置于自己的网站之前，你必须移除允许添加用户的功能。





```php
1.  <?
 2.  $password_file = "C:/apache/passwords/pass.txt";
 3.
4.  function check_pass($login, $password) {
 5.    global $password_file;
 6.    if(!$fh = fopen($password_file, "r")) {die("<P>Could Not Open Password File");}
 7.    $match = 0;
 8.    $password = md5($password);
 9.    while(!feof($fh)) {
10.      $line = fgets($fh, 4096);
11.      $user_pass = explode(":", $line);
12.      if($user_pass[0] == $login) {
13.        if(rtrim($user_pass[1]) == $password) {
14.          $match = 1;
15.          break;
16.        }
17.      }
18.    }
19.    if($match) {
20.      return 1;
21.    } else {
22.      return 0;
23.    }
24.    fclose($fh);
25.  }
26.
27.  function print_login_form($login) {
 28.    ?>
29.    <p>Please Log In:
30.    <form action=file_authentication.php method=post>
31.    <p>Login: <input type="text" name="login" value="<?=$login?>">
32.    <br>Password: <input type="password" name="password">
33.    <br><input type="submit" name="checkpass" value="Login!">
34.    </form>
35.    <?
36.  }
37.
38.  function print_add_form() {
39.    ?>
40.    <p>Add New User:
41.    <form action=file_authentication.php method=post>
42.    <p>Login: <input type="text" name="adduser">
43.    <br>Password: <input type="password" name="addpass">
44.    <br><input type="submit" name="add" value="Add User!">
45.    </form>
46.    <?
47.  }
48.
49.  function add_user($adduser, $addpass) {
50.    global $password_file;
51.    if(!$fh = fopen($password_file, "a+")) { die("<P>Could Not Open Password File"); }
52.    rewind($fh);
53.    while(!feof($fh)) {
54.      $line = fgets($fh, 4096);
55.      $user_pass = explode(":", $line);
56.      if($user_pass[0] == $adduser) {
57.        echo "<h2>Duplicate Login. Invalid!</h2>";
58.        return 0;
59.      }
60.    }
61.    $add = $adduser . ":" . md5($addpass) . "\n";
62.    if(!fwrite($fh, $add)) { die("<P>Could Not Write To Password File"); }
63.    fclose($fh);
64.    echo"<h2>User Added!</h2>";
65.  }
66.  /***** MAIN *****/
67.  if(isset($checkpass)) {
68.      if(check_pass($login, $password)) {
69.        echo "<h2>Login Success!</h2>";
70.      } else {
71.        echo "<h2>Login Failed</h2><p>Bad username or password. Login and Password are 
case-sensitive. Try again:";
72.      print_login_form($login);
73.      }
74.  } elseif(isset($add_form)) {
75.    print_add_form();
76.  } elseif(isset($add)) {
77.    add_user($adduser, $addpass);
78.  } else {
79.    print_login_form("");
80.  }
81.  ?>
82.  <p>You can <a href=file_authentication.php?add_form=1>Add Users</a> or <a 
href=file_authentication.php>login</a> an existing user.
```

### 脚本 7-2. file_authentication.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2 | 定义包含密码的文件。注意，你应该在你的机器上指定正确的路径指向密码文件。在*基于 ix 的系统*上，你显然会省略路径中的 `C:\` 这种无的内容。 |
| 4 | 创建一个函数，将用户输入的密码与密码文件中存储的用户名/密码组合进行比对。 |
| 5 | 允许此函数全局读取和修改密码文件。 |
| 6 | 尝试打开文件并将其分配给文件指针。如果无法打开文件，则打印错误并退出脚本。 |
| 7 | 初始化一个用于跟踪用户名/密码匹配的变量。将其初始化为假 (0)。 |
| 8 | 由于密码是加密的，使用 `md5()` 处理密码。 |
| 9 | 创建一个 `while` 循环，直到文件末尾 (EOF)。 |
| 10 | 在每次循环中，从文件中读取一行并将其放入 `$line`。 |
| 11 | 使用 `explode()` 对获取的行创建一个数组。 |
| 12 | 检查 `$user_pass[0]` 是否等于 `$login`。 |
| 13 | 检查 `rtrim($user_pass[1])` 是否匹配用户输入的密码。 |
| 14 | 如果密码匹配，将 `$match` 设置为真 (1)。 |
| 15 | 如果密码匹配，则 `break` 跳出循环。 |
| 16 | 关闭检查用户名的 `if` 语句。 |
| 17 | 关闭 `if` 语句。 |
| 18 | 关闭 `while` 循环。 |
| 19 | 如果 `$match` 为真，则返回 1。 |
| 20 | 将 1 返回给调用程序或函数。 |
| 21 | 否则，返回 0。 |
| 22 | 将 0 返回给调用程序或函数。 |
| 23 | 关闭 `else` 语句。 |
| 24 | 使用 `fclose()` 关闭文件。 |
| 25 | 函数结束。 |
| 27 | 创建一个打印登录表单的函数。该函数接受一个参数 `$login`，在没有匹配时用于自动填充用户名。 |
| 28 | 开始 PHP 解析页面。 |
| 29 | 开始显示登录表单。 |
| 30 | 打印标准表单。 |
| 31 | 打印用户名。如果是后续登录尝试，会自动输入用户名。 |
| 32 | 继续打印表单。 |
| 33 | 继续向页面打印表单。 |
| 34 | 关闭表单。 |
| 35 | 开始 PHP 解析页面。 |
| 36 | 函数结束。 |
| 38 | 创建一个打印表单的函数，允许向密码文件中添加用户名/密码组合。该函数不接受参数，因为它只是打印表单。 |
| 39 | 开始 PHP 解析页面。 |
| 40 | 打印“添加新用户”标题。 |
| 41 | 打印标准表单。 |
| 42 | 打印用户名字段。 |
| 43 | 继续打印表单。 |
| 44 | 继续打印表单。 |
| 45 | 关闭表单。 |
| 46 | 再次解析页面。 |
| 47 | 函数结束。 |
| 49 | 创建一个将用户名和密码组合添加到密码文件的函数。该函数接受两个参数：`$adduser` 和 `$addpass`。 |
| 50 | 允许此函数全局读取和修改密码文件。 |
| 51 | 尝试打开文件并将其分配给文件指针。如果无法打开文件，则打印错误并退出脚本。 |
| 52 | 由于使用追加模式 ("a+") 打开了文件，使用 `rewind($fh)` 使文件指针位于文件开头。追加模式默认将文件指针放在文件末尾。 |
| 53 | 创建一个 `while` 循环，直到文件末尾 (EOF)。 |
| 54 | 在每次循环中，从文件中读取一行并将其放入 `$line`。 |
| 55 | 使用 `explode()` 对获取的行创建一个数组。 |
| 56 | 检查 `$user_pass[0]` 是否与“添加用户”表单中输入的用户名相同。用户名应该是唯一的！此行确保不会向密码文件中输入重复用户名。 |
| 57 | 如果用户名匹配，则你正尝试输入重复用户名。向用户打印消息，告知他们输入的用户名无效。 |
| 58 | 返回假给调用程序或函数。 |
| 59 | 关闭 `if` 语句。 |
| 60 | 关闭 `while` 循环。 |
| 61 | 通过拼接 `$adduser`、 `:`、加密后的 `md5($addpass)` 和换行符创建一个字符串 `$add`。 |
| 62 | 如果 `fwrite($fh, $add)` 失败，则打印错误并退出脚本。 |
| 63 | 使用 `fclose()` 关闭文件。 |
| 64 | 打印“用户已添加！”标题。 |
| 65 | 函数结束。 |
| 66 | MAIN 部分开始。 |
| 67 | 如果 `isset($checkpass)` 为真： |
| 68 | 如果 `check_pass($login, $password)` 为真： |
| 69 | 打印“登录成功！”标题。 |
| 70 | 否则： |
| 71 | 打印“登录失败”标题和解释用户名或密码区分大小写的错误消息。 |
| 72 | 调用 `print_login_form($login)`。 |
| 73 | 关闭 `else` 语句。 |
| 74 | 关闭 `if` 语句。 |
| 75 | 如果 `isset($add_form)` 为真： |
| 76 | 调用 `print_add_form()`。 |
| 77 | 如果 `isset($add)` 为真： |
| 78 | 调用 `add_user($adduser, $addpass)`。 |
| 79 | 否则： |
| 80 | 调用 `print_login_form("")`。 |





| 61 || 既然执行到了这一行，说明输入的用户名是唯一的（如果不是唯一的，函数将在第 58 行通过 return 语句终止）。通过将用户名置于密码的 MD5 加密形式之前，创建一个用户名/密码组合。在两者之间放置一个冒号，以便脚本在检查用户名和密码时能够轻松解析。MD5 加密输出中不会出现冒号，因此使用冒号作为分隔这两个值的字符是安全的。（注意，脚本并没有禁止用户名中出现冒号，但如果用户在用户名中放置冒号，会导致用户身份验证始终失败。） |

| 62 || 尝试将新的用户名/密码组合写入文件末尾。你已经知道自己正处于文件末尾，因为 `while` 循环刚刚解析了整个文件。如果写入尝试失败，则显示错误并终止脚本。 |
| 63 || 关闭文件。 |
| 64 || 打印一条消息，让用户知道密码添加到密码文件中。 |
| 65 || 结束函数声明。 |
| 66 || 开始主文件执行。 |
| 67 || 检查 `$checkpass` 变量是否已设置。如果已设置，说明登录表单已提交给脚本。 |
| 68 || 如果 `$checkpass` 变量已设置，使用用户输入的用户名和密码运行 `check_pass()` 函数。 |
| 69 || 如果 `check_pass()` 函数返回 true (1)，则通知用户身份验证成功。在此时，你通常会显示你通过用户身份验证保护的内容。 |
| 70–73 || 如果 `check_pass()` 函数返回 false，则打印一条消息告知用户错误。 |
| 74–75 || 如果 `$checkpass` 变量未设置，但 `$add_form` 变量已设置，则打印表单以允许你向密码文件中添加新的用户名/密码组合。 |
| 76–77 || 如果 `$checkpass` 变量未设置且 `$add_form` 变量未设置，但 `$add` 变量已设置，则使用“添加用户”表单中输入的值运行 `add_user` 函数。 |
| 78–79 || 如果以上以上都不成立，则使用空值作为参数打印登录表单，这样 `login_form` 函数就不会生成关于使用未初始化变量的警告。 |
| 81 || 停止将页面解析为 PHP。 |
| 82 || 向浏览器打印一行包含两个链接的输出。第一个链接是设置 `add_form` 变量的链接，以便调用 `add_form` 函数并让你向密码文件中添加用户名/密码组合。第二个链接用于在你添加用户后显示登录表单。 |

*** *

### 通过 IP 地址进行用户身份验证

在某些少数情况下，你可能希望限制某些 IP 地址访问某个页面或多个页面。这可能是因为你拥有一个具有公开可见网站的内部网络。你可能希望某些页面仅供内部网络中的某些机器查看。

或者你可能拥有自己的远程网站，并希望限制对某个页面或多个页面的访问，使得只有你通过静态 IP 地址访问这些页面。

这些方法通过确定尝试查看页面的用户的 IP 地址并将其与一组值进行比对来工作。如果 IP 地址匹配，则可以查看页面。

注意，这种方法可能会被 IP 欺骗或其他攻击手段欺骗，不应将其用于保护敏感信息，例如信用卡号、专有信息等。这是一种简单的方法，可以保护页面免受大多数上网用户的访问。

在使用此脚本时，你应该意识到你的计算机可能有多个 IP 地址，并且你的浏览器向脚本报告的那个 IP 可能与你尝试进行验证的 IP 不相同。当浏览器和 Web 服务器位于同一台机器时，情况尤为如此，你在测试脚本时可能会遇到这种情况。

例如，计算机有一个默认的本地 IP 地址 `127.0.0.1`，也称为 "localhost"。当我启动 Web 服务器并输入 `http://localhost` 时，我的浏览器会告诉脚本我位于 IP 地址 `127.0.0.1`。然而，我电脑上的 Web 浏览器也运行在 IP 地址 `192.168.0.1`（一个用于内部网络的 IP 地址）。如果我输入 IP 地址 `192.168.0.1`，我的 Web 浏览器报告我位于 `192.168.0.1`，但脚本只接受 `127.0.0.1` 的 IP 地址。

#### 脚本 7-3 IP_authentication.php

```php
php
$accept = array("127", "0", "1");
$remote = explode(".", $_REMOTE_ADDR);
$match = 1;
for($i = 0; $i < sizeof($accept); $i++) {
  if($remote[$i] != $accept[$i]) {
    $match = 0;
  }
}
if($match) {
  echo "<h2>Access Granted</h2>";
} else {
  echo "<h2>Access Forbidden</h2>";
}
?>
```

##### 脚本 7-3 IP_authentication.php 逐行说明

| 行 | 描述 |
| --- | --- |
| 1 | 定义允许查看页面的 IP 地址数组。数组必须至少一项。 |
| 2 | 通过分解 `$_REMOTE_ADDR` 变量根据用户的 IP 地址创建一个数字数组。 |
| 3 | 定义变量 `$match` 并将其设置为 true (1)。 |
| 4–9 | 遍历接受 IP 地址数组。 |
| 5 | 比较接受的 IP 段与用户的 IP 段。 |
| 6 | 如果 IP 段不匹配，则将 `$match` 变量设置为 false (0)。 |
| 7 | 关闭 if 语句。 |
| 9 | 关闭 for 循环。 |
| 10–11 | 如果 `$match` 为 true，则允许访问并向用户打印消息。这就是你展示受保护内容的地方。 |
| 12–14 | 如果 `$match` 为 false (0)，则打印消息告诉用户他们无法访问该页面并退出脚本。 |
| 15 | 关闭第 10 行开始的 if 语句。 |

你可以通过向数组添加更多或更少的项目来限制子网。例如：`array("192","168","0","1")` 将访问页面的用户限制在 IP 地址 `192.168.0.1`。`array("192","168","0")` 将访问页面的用户限制在 IP 范围 `192.168.0.1` 到 `.255`。`array("192")` 允许任何以 `192` 开头的 IP 用户查看页面。这并不实用，但它是可以运行的！




PHP 对基本的“HTTP 身份验证”提供了一些内置支持。HTTP 身份验证是这类身份验证：浏览器会弹出一个小窗口提示你输入用户名和密码。图 7-2 和 图 7-3 分别显示了 Internet Explorer 和 Linux 版 Mozilla 中的 HTTP 身份验证窗口。HTTP 身份验证取决于服务器，最常见的例子是 Apache 的 HTTP 身份验证方法。这里描述的方法假设你使用的是 Apache 服务器。

### 图 7-2. Internet Explorer 中的 HTTP 身份验证登录窗口

![graphics/07fig02.jpg](img/07fig02.jpg)

### 图 7-3. Linux 上 Mozilla 中的 HTTP 身份验证窗口

![graphics/07fig03.jpg](img/07fig03.jpg)

通常，Apache 下的 HTTP 身份验证方法定义在 `.htaccess` 文件中`.htaccess` 文件通常限制整个目录。然而，PHP 提供了一种使用基于 Apache 的 HTTP 身份验证的方法，而无需为同类型的身份验证定义 `.htaccess` 文件。此外，你还可以轻松地按页面使用 PHP 的 HTTP 身份验证方法。

> ^(\[1\]) 详细信息请访问 [`httpd.apache.org/docs/howto/auth.html`](http://httpd.apache.org/docs/howto/auth.html)。

使用 PHP 方法，你还可以使用自己的密码方案。在 Apache 下，你通常将加密后的密码放在密码文件中（通常称为 `.htpasswd`）。使用 PHP 方法，你可以将密码放在文件、数据库或任何其他方法中。你还可以使用任何你想要的加密方案，而 Apache 仅限于 UNIX 加密密码、其自格式的 MD5 密码或明文。

然而，如果用户忘记了密码，你无法将密码发送给他们，因为你只知道加密后的版本。你必须重置密码，或者提供一个密码提示，帮助用户记住他们用的是什么密码。关于这一点，将在本章稍后部分进行详细介绍。

本章中的下一个脚本详细介绍了如何配合 Apache 服务器使用 PHP 的 HTTP 身份验证方法。该脚本还允许你使用通过 `crypt()` 函数加密的密码（这些密码是可的，可以与 Apache 默认的 HTTP 身份验证方法配合使用），或使用基础 PHP `md5()` 函数加密密码。如果你已经有多个使用 MD5 加密密码的应用程序，后者选项非常有用。

### 脚本 7-4 http_authentication.php

[[查看全屏]]&r=noccc&xmlid=0-13-008539-1/ch07lev1sec5#PLID0) 

```
1.  <?
 2.  function check_pass($login, $password, $mode) {
 3.    global $password_file;
 4.    if(!$fh = fopen($password_file, "r")) { die("<P>Could Not Open Password File"); }
 5.    $match = 0;
 6.    while(!feof($fh)) {
 7.      $line = fgets($fh, 4096);
 8.      $from_file = explode(":", $line);
 9.      if($from_file[0] == $login) {
10.        if($mode == "crypt"){
11.          $salt = substr($from_file[1],0,2);
12.          $user_pass = crypt($password,$salt);
13.        } elseif ($mode == "md5") {
14.          $user_pass = md5($password);
15.        }
 16.        if(rtrim($from_file[1]) == $user_pass) {
17.          $match = 1;
18.          break;
 19.       }
 20.     }
 21.   }
 22.   if($match) {
 23.     return 1;
 24.   } else {
 25.     return 0;
 26.   }
 27.   fclose($fh);
 28.  }
 29.  function authenticate() {
 30.    Header("WWW-Authenticate: Basic realm=\"RESTRICTED ACCESS\"");
 31.    Header("HTTP/1.0 401 Unauthorized");
 32.    echo ("<h1>INVALID USERNAME OR PASSWORD. ACCESS DENIED<h1>");
 33.    exit;
 34.  }
 35.  /*** MAIN ***/
 36.  //select md5 or crypt for $mode. md5 is for md5 encoded passwords, crypt is for 
passwords encoded using apache's httpasswd
 37.  $mode = "md5";
 38.  $password_file = "C:/apache/passwords/pass.txt";
 39.  if (!isset($PHP_AUTH_USER)) {
 40.    authenticate();
 41.  } else {
 42.    if(check_pass($PHP_AUTH_USER, $PHP_AUTH_PW, $mode)) {
 43.      ?>
 44.      <h1>ACCEPTED</h1>
 45.      <?
 46.    } else {
 47.    authenticate();
 48.    }
```




| 36 | 在脚本中添加一条注释，说明 `$mode` 变量的性质。 |
| 37 | 为 `$mode` 变量赋值 `"md5"`（如果你的密码使用 `crypt()` 函数进行加密，则赋值为 `"crypt"`）。 |
| 38 | 将密码文件的位置赋值给 `$password_file` 变量。 |
| 39 | 检查全局变量 `$PHP_AUTH_USER` 是否已设置。`$PHP_AUTH_USER` 是用于 HTTP 身份验证的特殊 PHP 变量。当用户使用 HTTP 身份验证窗口登录时，就会获取该变量。 |
| 40 | 如果 `$PHP_AUTH_USER` 变量未设置，则执行 `authenticate()` 函数。 |
| 41–42 | 如果设置了 `$PHP_AUTH_USER` ，则使用 `$PHP_AUTH_USER`、`$PHP_AUTH_PW` 和 `$mode` 变量作为参数执行 `check_pass()` 函数。`$PHP_AUTH_PW` 变量是从 HTTP 身份验证登录窗口获取的特殊 PHP 全局变量。 |
| 43–45 | 如果 `check_pass()` 函数返回真 (1)，则在屏幕上打印 `"ACCEPTED"`。你通常会在此处提供受保护的内容。 |
| 46–48 | 如果 `check_pass()` 函数返回假，则再次执行 `authenticate()` 函数。用户有三次机会正确输入用户名和密码。第三次失败后，脚本将返回第 31 和第 32 行。 |
| 49 | 关闭第 39 行开始的 if 语句。 |
| 50 | 结束脚本。 |

### 通过数据库查询验证用户

对于基于数据库的网站，最常用的身份验证方法是使用数据库。既然你可以随时利用 SQL 数据库的快速和方便，为什么还要费精力使用笨拙的文本文件呢？

基于数据库的身份验证可以使用与基于文件的验证相同的功能，例如 `md5()` 或 `crypt()` 加密。用户名和密码存储在数据库的表中。你还可以在此表中存储其他信息，例如电子邮件地址或姓名的，正如你在第 5 章的示例程序看到的那样。

接下来的脚本提供了一种使用数据库验证用户身份的基础方法。它使用明文密码，但你可以很容易利用本章之前脚本中的技术来包含加密密码。

#### 脚本 7-5 DB_authenticate.php

```
1.  <?
 2.
3.  /* SQL REQUIRED FOR THIS SCRIPT *****
 4.   create table users (
 5.    id INT NOT NULL,
 6.    username VARCHAR(16),
 7.    password VARCHAR(8),
 8.    primary key(id));
 9.  *****/
10.
11.  function connect() {
12.    if(!$db = @mssql_pconnect("localhost","mssqluser","password")){
13.      print("<h1>Cannot Connect to the DB!</h1>\n");
14.      return 0;
15.    } else {
16.      mssql_select_db("php", $db);
17.      return 1;
18.    }
19.  }
20.
21.  function check_user($user, $password) {
22.    if(connect()) {
23.      $password = substr($password, 0, 8);
24.      $sql = "select * from users where username = '$user' and password = '$password'";
25.      $result = mssql_query($sql);
26.      if (mssql_num_rows($result) == 1) {
27.        setcookie("user",$user);
28.        setcookie("password",$password);
29.        return 1;
30.      } else {
31.        ?>
32.        <h3>Sorry, you are not authorized!</h3>
33.        <?
34.        return 0;
35.      }
36.    }
37.  }
38.
39.  /***** MAIN *****/
40.  if(!isset($user) or !check_user($user, $password)) {
41.    ?>
42.    <h1>You must log in to view this page</h1>
43.    <form action = "DB_authenticate.php" method="post">
44.    <P>Username: <input type="text" name="user"><br>
45.    Password: <input type="password" name="password"><br>
46.    <input type="submit" name="submit">
47.    </form>
48.    ?>
49.  } else {
50.    ?>
51.    <h1>Authorized!</h1>
52.    <?
53.  }
```

#### 脚本 7-5 DB_authenticate.php 逐行解释

| 行号 | 说明 |
| :--- | :--- |
| 3–9 | 此脚本所需的 SQL ***** |
| 11–19 | 创建函数 `connect()`。该函数尝试连接到数据库。如果连接成功，则继续到第 22 行。否则，跳转到第 36 行（即函数的结束）。 |
| 21–37 | 创建函数 `check_user($user, $password)`，该函数根据数据库检查输入的用户名和密码。该函数接收参数 `$user` 和 `$password`，均由用户输入。 |
| 22 | 使用 `connect()` 函数尝试连接数据库。如果连接成功，则继续到第 23 行。 |
| 23 | 修改输入的密码以匹配数据库使用的格式。在此例中，脚本将密码截断为 8 位。如果你在数据库中存储了加密密码，此处可以使用 `md5()` 或 `crypt()` 函数之一。 |
| 24 | 生成一条 SQL 语句，从 "users" 表中与用户名和密码匹配的行。 |
| 25 | 执行 SQL 查询并将结果赋值给变量 `$result`。 |
| 26 | 检查查询结果是否恰好一行，因为用户名应该是唯一的（你没有在数据库中放入重复的用户名吧？） |
| 27–28 | 如果结果恰好有一行，意味着输入的用户名和密码与数据库中的匹配，则在用户的浏览器中设置会话 Cookie，以便他们在访问受保护页面期间保持“登录”状态。 |
| 29 | 返回 1，因为验证成功。 |
| 30–35 | 如果结果不是恰好一行，则输入的用户名和密码与数据库中的任何项都不匹配。打印错误信息并向调用程序返回假。 |
| 36 | 关闭第 22 行开始的 if 语句。 |
| 37 | 结束函数定义。 |
| 39 | 开始主程序。 |
| 40–48 | 检查 `$user` 变量是否设置，或者通过 `check_user()` 函数检查输入的用户名和密码是否与数据库中的项匹配。如果 `$user` 变量未设置，说明当前用户尚未尝试登录。如果 `$user` 变量已设置但 `check_user()` 函数返回假，则说明用户输入了错误的密码。在任何情况下，都打印登录表单以便用户输入正确的用户名和密码。 |





| 49–53 || 如果脚本执行到此处，说明 `$user` 变量已经设置，且 `check_user()` 返回了真值。这必须是一个有效用户！显示一条注释告诉用户他们已授权。在此处，你将显示你的受保护内容。 |

## 第 8 章 错误管理

### 本章内容

*   概述
*   错误报告

### 概述

Bug 是程序员日常生活中不可或缺的一部分。我们都会在某个时候漏掉一个分号或右括号。有时，我们会拼错变量名，并纳闷为什么本该显示在屏幕上的值值一直是空白的。其他时候，你可能会怀疑数据库服务器上潜伏着什么“小鬼”，因为数据没有按照你预期的方式存入（或取出）。你曾多少次反复查看某段代码，并纳闷你的程序到底为什么运行不通？

有些 Bug——那些好对付的、不介意被消灭的 Bug——会通过 PHP 解析器立即告诉你它们的存在。例如，诸如无处不在的“Parse error”（解析错误）或偶尔出现的“Warning: Division by zero”（警告：除以零）让你知道它们发生在哪一行。修复它们对你来说很容易：只需打开脚本，在这里添加一个分号，在那个处修改变量的拼写，就可以继续工作了。

遗憾的是，用户并没有这种待遇。你是否曾在某个在线购物网站上花费了一个小时左右，仔细为自己挑选了一些精美的装备，并经过漫长而艰巨的多页表单来提供地址和信用卡信息，最后点击了那个闪亮的提交按钮，结果页面只用普通字体显示了一句“Script Error—Database Connection Failed On Line 193”（脚本错误——第 193 行数据库连接失败），别无他物？你刚刚给这些人提供了信用卡号，而当他们的脚本崩溃时，你看到的只有“Script Error……”。

更好的网站、更智能的网站——也就是说，你的网站——不应该这样做。如果发生了错误，至少应该告知用户出现了一点问题并且已经通知了管理员。也许甚至可以有一条注释说明订单已处理（或未处理）。你想让你网站的用户遭受那些无法提供他们任何信息的丑陋错误信息吗？当然不想。

此外，错误可能会显示出对试图破解你网站的恶意用户有用的信息。错误通常会显示文件路径、数据库服务器信息以及可能危及你网站安全的信息。

本章解释了 PHP 的错误处理和日志函数。

### 错误报告

#### PHP 中的错误类型

在我们处理你网站上的丑陋错误信息之前，你需要了解不同类型的错误。PHP4 可以产生 11 种不同的错误，如下所示表 8-1 所示（注意致命错误会停止脚本执行）：

##### 表 8-1. PHP 错误类型

| 名称 (NAME) | 值 (VALUE) | 描述 (DESCRIPTION) |
| --- | --- | --- |
| `E_ERROR` | 1 | 运行时发生的致命错误。 |
| `E_WARNING` | 2 | 运行时发生的非致命错误（例如，脚本无法连接到 MySQL）。 |
| `E_PARSE` | 4 | 编译时因语法无效引起的错误。 |
| `E_NOTICE` | 8 | 非致命的“通知”。不完全是错误，但提示你可能正在做某些不想做的事，例如将数字除以零。 |
| `E_CORE_ERROR` | 16 | PHP 引擎启动时发生的致命错误。发生此错误时你无法运行任何 PHP 脚本。 |
| `E_CORE_WARNING` | 32 | PHP 引擎启动时发生的非致命错误。 |
| `E_COMPILE_ERROR` | 64 | 脚本编译时发生的致命错误。 |
| `E_COMPILE_WARNING` | 128 | 脚本编译时发生的非致命错误。 |
| `E_USER_ERROR` | 256 | 用户生成的致命错误。与 `E_ERROR` 相同，但由 PHP 抛出。 |
| `E_USER_WARNING` | 512 | 用户生成的非致命错误。与 `E_WARNING` 相同，但由 PHP 抛出。 |
| `E_USER_NOTICE` | 1024 | 用户生成的通知。与 `E_NOTICE` 相同，但由 PHP 抛出。 |
| `E_ALL` | 2047 | 所有错误的汇总。 |

在所有这些错误中，涉及到报告和日志时，你应该主要关注的是这些：

*   `E_WARNING`
*   `E_NOTICE`
*   `E_USER_ERROR`
*   `E_USER_WARNING`
*   `E_USER_NOTICE`

其他发生的错误通常会导致脚本停止执行。

#### php.ini 中的错误报告设置

| 旁注 |
| --- |
| 此信息适用于 PHP 4 及更高版本。这些设置对 PHP 3 版本不起作用。 |

你在编写代码时看到那些“丑陋”错误的原因是 PHP 默认设置为显示所有错误（E\_ALL），但除了 PHP 生成的通知（E\_NOTICE）。打开你的 php.ini 文件并滚动到“Error handling and logging”（错误处理和日志）部分。在所有注释的末尾，你应该看到类似下面的一行：

```
error_reporting = E_ALL & ~E_NOTICE
```

这是默认的错误报告设置。它使用位运算符编写，简单翻译为“错误报告使用所有且非 E\_NOTICE”。你也可以写成如下形式（注意我们去掉了 E\_NOTICE）：

```
error_reporting = E_ERROR | E_WARNING | E_PARSE | E_CORE_ERROR | E_CORE_WARNING | 
E_COMPILE_ERROR | E_COMPILE_WARNING | E_USER_ERROR | E_USER_WARNING | E_USER_NOTICE 
```

然而，由于你是一个 PHP 开发者，在开发应用程序时你真的应该将此行设置为如下：

```
error_reporting = E_ALL 
```

你想看到脚本产生的所有错误。你会惊讶于自己可能使用了多少未初始化的变量。

#### error\_reporting()

`error_reporting()` 函数允许你覆盖 php.ini 中使用的默认错误报告设置：

```
error_reporting(settings); 
```





`error_reporting` 函数接收一个参数，该参数可以是一个列出你想要使用的错误报告设置名称的字符串（通过位运算符分隔），也可以是一个你想要使用的值之和的整数。例如：

```php
error_reporting(10); 
```

它等同于：

```php
error_reporting("E_WARNING | E_NOTICE"); 
```

第一种版本更容易输入，但第二种版本更详尽。此外，你可以从 `E_ALL` 值（2047）中减去某些值来使用“除……之外的所有项”报告。下面的示例允许你显示除 `E_NOTICE` (2047 - 8) 之外的所有错误 (`E_ALL`)：

```php
error_reporting(2039); 
```

如果你不想报告任何错误，可以简单地使用：

```php
error_reporting(0); 
```

这会停止 PHP 在屏幕上显示由 `E_WARNING`、`E_NOTICE` 或任何用户抛出的警告引起的错误消息。请记住，任何其他警告都是由 PHP 自动抛出的，因为这意味着脚本本身真的出了问题（解析错误），或者服务器本身真的出了问题。

如果错误导致脚本无法编译（例如解析错误），你仍然可能会遇到问题。在这种情况下，你的脚本没有任何部分会被执行，且 `error_reporting()` 变量也不会运行。当发生这种情况时，PHP 将使用其 `php.ini` 中的错误报告设置。

### php.ini 设置：display_errors

此外，还有另一个设置可以防止错误消息显示在用户的浏览器上。此设置——`display_errors` 可以在 `php.ini` 中找到。如果你想确保错误绝不会显示在屏幕上，可以在你的 `php.ini` 文件中将此设置改为 "0"。在开发应用程序时，你应该将此设置保留为 "1" 或 "On"。你也可以使用 `ini_set()` 函数按文件更改 `display_errors` 设置。`ini_set()` 函数允许你更改当前脚本的 `php.ini` 文件设置。例如，如果你已经在 `php.ini` 文件中关闭了 `display_errors`，你可以使用以下代码开启它来调试你的脚本，这等同于 `php.ini` 中的 `display_errors = On`：

```php
ini_set("display_errors",1); 
```

记住，如果你的脚本遇到导致无法执行的错误，那么 PHP 将使用它在 `php.ini` 中找到的设置，无论你在脚本中指定了什么。

### 开发和测试的 php.ini 设置

在开发和测试脚本时，你应该在 `php.ini` 文件中使用以下设置：

```ini
error_reporting = E_ALL 
display_errors = 1
```

这允许你显示所有错误并获取 PHP 关于你脚本的所有信息。对于生产环境网站，你可能希望将 `php.ini` 文件设置为完全关闭任何错误显示：

```ini
display_errors = 0 
```

接下来的脚本演示了如何使用不同的错误报告设置报告警告和通知。

#### 脚本 8-1 error_reporting.php

```
1.  <?
 2.  define("EVERYTHING",E_ALL);
 3.  define("NO_NOTICE",(E_ALL &~E_NOTICE));
 4.  define("NO_NOTICE_OR_WARN",(E_ALL &~(E_NOTICE | E_WARNING)));
 5.  $error_level = array(EVERYTHING,NO_NOTICE,NO_NOTICE_OR_WARN);
 6.  for($i = 0; $i < sizeof($error_level); $i++) {
 7.    error_reporting($error_level[$i]);
 8.    echo "<h3>Error Reporting Set To " . $error_level[$i] . "</h3>";
 9.    echo $uninitialized;
10.    $connect = mysql_connect();
 11.    echo "<hr>";
12.  }
13.  ?>
14.  <?
15.  define("EVERYTHING",E_ALL);
```

#### 脚本 8-1 error_reporting.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2–4 | 在脚本中定义一些命名常量。我们定义这些常量是因为我们想使用一些自定义的错误报告选项，如第 3 和第 4 行所示。 |
| 5 | 创建之前几行定义的错误报告值的数组。 |
| 6–12 | 创建一个 for 循环来遍历数组中的值。 |
| 7 | 将错误报告值更改为数组中的当前值。`error_reporting` 函数不能接受位运算语句作为参数，因此我们使用在第 3 和第 4 行创建的值。 |
| 8 | 显示一个简短通知，说明正在使用哪个错误报告值。我们在第 2–4 行中定义的常量实际上是现有常量的重新定义，这些常量随后由 PHP 定义为错误报告级别的相应值。因此，屏幕上显示的值是数值。 |
| 9 | 打印未初始化变量的值。如果错误报告设置为显示 `E_USER_NOTICE`，则此处应该显示一个警告 (`E_USER_NOTICE`)。 |
| 10 | 尝试连接 MySQL 数据库。如果错误报告设置为显示 `E_USER_NOTICE`，这将产生一个警告消息。 |
| 12 | 关闭 for 循环。 |

*(注：原文中第 9-12 行的描述存在碎片化，已根据脚本上下文进行了整理。）*

### PHP 中的日志类型

`error_reporting` 函数接收一个参数，该参数可以是一个列出你想要使用的错误报告设置名称的字符串（通过位运算符分隔），也可以是一个你想要使用的值之和。

| 类型 | 描述 |
| --- | --- |
| 0 | 根据 `php.ini` 中的 `error_log` 设置，消息将发送到系统特定的文件。如果没有设置，它将出现在错误日志。 |
| 1 | 消息发送到 `php.ini` 中指定的电子邮件地址。这是唯一使用 `headers` 参数的类型。 |
| 2 | 消息发送到调试服务器。必须使用 `destination` 参数来指定调试服务器的主名或 IP 地址。 |
| 3 | 消息写入 `destination` 指定的文件末尾。如果 `destination` 文件不存在，PHP 会尝试创建它。你必须正确设置权限，以便 PHP 可以写入指定的目录。 |

#### 脚本 8-2 error_logging.php

```php
1.  <?
2.  echo "<p>Sending Error To Apache Error Log.";
3.  error_log("Test Error Message!",0);
4.  echo "<p>Sending Error To Email.";
5.  error_log("Test Error Message!",1,"admin@example.com","FROM: WEB ERROR LOG 
<error@example.com>");
6.  echo "<p>Sending Error to File.";
7.  error_log("Test Error Message!\r\n",3,"errors.txt");
8.  ?>
```





| 2 || 在屏幕上显示消息，说明错误正在发送到 Apache 错误日志。 |

| 3 || 将错误发送到 Apache 错误日志。 |

| 4 || 在屏幕上显示消息，说明错误正在发送到一个电子邮件地址。 |

| 5 || 将错误发送到电子邮件地址。将 `admin@example.com` 替换为您的电子邮件地址。 |

| 6 || 在屏幕上显示消息，说明错误正在发送到文件。 |

| 7 || 将错误发送到该文件。如果文件不存在，PHP 将尝试在当前目录中创建它。 |

## 自定义错误处理器

PHP 的默认错误处理器很有用，但它们的作用仅仅是通知你发生了错误。幸运的是，PHP 允许你使用自己自定义的错误处理器，这样你就可以根据发生的错误类型来采取特定操作。允许你使用自定义错误处理器的函数是 `set_error_handler()`：

```
set_error_handler($error_handler); 
```

`set_error_handler()` 接受一个参数 `$error_handler`，它是你创建的错误处理函数的名称。

如果你调用 `set_error_handler(0)`，则错误处理器将恢复为 PHP 的默认错误处理器。

```
set_error_handler(0); 
//错误处理器现为 PHP 的默认错误处理器
```

`set_error_handler()` 在调用时会返回旧的错误处理器的值。这允许你轻松恢复到旧的错误处理器。例如：

```
set_error_handler("foo"); 
$old_error_handler = set_error_handler("bar");
//$old_error_handler = "foo";
set_error_handler($old_error_handler);
//错误处理器现在是 "foo"
```

你也可以通过调用不接受参数的 `restore_error_handler()` 函数来轻松恢复到之前的错误处理器：

```
set_error_handler("foo"); 
set_error_handler("bar");
restor_error_handler();
//error_handler = "foo"
```

当触发错误时，PHP 会调用 `set_error_handler()` 中指定的函数，并向其传递以下参数（按以下顺序）：

*   错误编号——这是来自 表 8-1 的错误值。
*   错误文本。
*   发生错误的文件名和路径。
*   发生错误的代码行号。
*   错误发生时的上下文——基本上是一个大型数组，包含了错误发生时脚本可用的所有变量的状态。

你可以根据需要使用这些参数中的任意一个、多个或全部，但参数必须按照上述顺序出现。

|| 

## 旁注

如果 PHP 在你的 `error_handling` 函数中遇到错误，它将使用默认或之前的错误处理方法来处理该错误。 |

| --- |

下一个脚本提供了自定义错误处理器的示例。

### 脚本 8-3 error\_handler.php

[\[全屏查看\]](&r=noccc&xmlid=0-13-008539-1/ch08lev1sec2#PLID22) 

```
1.  <?
2.  error_reporting(E_ALL);
3.  function error_handler($number, $string, $file, $line) {
4.    error_log("Error ($number) on line $line in file $file. The error was \"$string\"\n", 
3, "errors.txt");
5.  }
6.  ini_set('display_errors',0);
7.  set_error_handler("error_handler");
8.  $row = mysql_fetch_array($result);
9.  ?>
```

### 脚本 8-3 error\_handler.php 逐行解释

| 行 | 描述 |

| --- | --- |

| 2 | 设置错误报告报告所有错误。 |
| 3–5 | 定义一个处理错误的函数。接受错误编号、错误字符串、发生错误的文件和错误行号作为参数。 |
| 4 | 将错误记录到文本文件。 |
| 5 | 关闭 `error_handler()` 函数。 |
| 6 | 使用 `ini_set()` 函数禁用屏幕上的错误显示。 |
| 7 | 将错误处理器设置为第 3 行定义的自定义处理器。 |
| 8 | 通过调用一个知道不会运行的函数来产生错误。 |

### 脚本 8-4 error\_handler.php 输出

[\[全屏查看\]](&r=noccc&xmlid=0-13-008539-1/ch08lev1sec2#PLID23)

```
1.  Error (8) on line 8 in file c:\apache\htdocs\chapter08\error_handler.php. The error was
"Undefined variable:  result"
2.  Error (2) on line 8 in file c:\apache\htdocs\chapter08\error_handler.php. The error was
"Supplied argument is not a valid result resource"
```

### 脚本 8-4 error\_handler.php 输出的逐行解释

| 行 | 描述 |

| --- | --- |

| 2 | 设置错误报告报告所有错误。 |
| 3–5 | 定义一个处理错误的函数。接受错误编号、错误字符串、发生错误的文件和错误行号作为参数。 |
| 4 | 将错误记录到文本文件。 |
| 5 | 关闭 `error_handler()` 函数。 |
| 6 | 使用 `ini_set()` 函数禁用屏幕上的错误显示。 |
| 7 | 将错误处理器设置为第 3 行定义的自定义处理器。 |
| 8 | 通过调用一个知道不会运行的函数来产生错误。 |

| 2 | 在屏幕上显示消息，说明错误正在发送到 Apache 错误日志。 |
| 3 | 将错误发送到 Apache 错误日志。 |
| 4 | 在屏幕上显示消息，说明错误正在发送到一个电子邮件地址。 |
| 5 | 将错误发送到电子邮件地址。将 `admin@example.com` 替换为您的电子邮件地址。 |
| 6 | 在屏幕上显示消息，说明错误正在发送到文件。 |
| 7 | 将错误发送到该文件。如果文件不存在，PHP 将尝试在当前目录中创建它。 |

## 旁注

如果 PHP 在你的 `error_handling` 函数中遇到错误，它将使用默认或之前的错误处理方法来处理该错误。 |

| --- |

下一个脚本提供了自定义错误处理器的示例。

### 脚本 8-3 error\_handler.php

[\[全屏查看\]](...) 

```
1.  <?
2.  error_reporting(E_ALL);
3.  function error_handler($number, $string, $file, $line) {
4.    error_log("Error ($number) on line $line in file $file. The error was \"$string\"\n", 
3, "errors.txt");
5.  }
6.  ini_set('display_errors',0);
7.  set_error_handler("error_handler");
8.  $row = mysql_fetch_array($result);
9.  ?>
```

### 脚本 8-3 error\_handler.php 逐行解释

| 行 | 描述 |

| --- | --- |

| 2 | 设置错误报告报告所有错误。 |
| 3–5 | 定义一个处理错误的函数。接受错误编号、错误字符串、发生错误的文件和错误行号作为参数。 |
| 4 | 将错误记录到文本文件。 |
| 5 | 关闭 `error_handler()` 函数。 |
| 6 | 使用 `ini_set()` 函数禁用屏幕上的错误显示。 |
| 7 | 将错误处理器设置为第 3 行定义的自定义处理器。 |
| 8 | 通过调用一个知道不会运行的函数来产生错误。 |

### 脚本 8-4 error\_handler.php 输出

```
1.  Error (8) on line 8 in file c:\apache\htdocs\chapter08\error_handler.php. The error was
"Undefined variable:  result"
2.  Error (2) on line 8 in file c:\apache\htdocs\chapter08\error_handler.php. The error was
"Supplied argument is not a valid MySQL result resource"
```

### 触发错误

有时，根据发生的情况触发自己的错误是非常用的。`trigger_error()` 函数的调用方式如下：

```
trigger_error(message, type);
```

`trigger_error()` 接受两个参数：

*   $message— 描述错误的字符串。
*   $type— 错误类型，可以是以下之一：
    *   E_USER
    *   E_WARNING
    *   E_NOTICE

### 脚本 8-5 error\_handler.php

```
1.  <?
2.  error_reporting(E_ALL);
3.  function error_handler($number, $string, $file, $line) {
4.    error_log("Error ($number) on line $line in file $file. The error was \"$string\"\n", 
3, "errors.txt");
5.  }
6.  ini_set('display_errors',0);
7.  set_error_handler("error_handler");
8.  $row = mysql_fetch_array($result);
9.  ?>
```

### 脚本 8-5 error\_handler.php 逐行解释

| 行 | 描述 |

| --- | --- |

| 2 | 设置错误报告报告所有错误。 |
| 3–5 | 定义一个处理错误的函数。接受错误编号、错误字符串、发生错误的文件和错误行号作为参数。 |
| 4 | 将错误记录到文本文件。 |
| 5 | 关闭 `error_handler()` 函数。 |
| 6 | 使用 `ini_set()` 函数禁用屏幕上的错误显示。 |
| 7 | 将错误处理器设置为第 3 行定义的自定义处理器。 |
| 8 | 通过调用一个知道不会运行的函数来产生错误。 |





* `$file`— 发生错误的文件路径和名称。
* `$line`— 发生错误的行数。

| 3 | 创建 `$timestamp` 变量并赋值为当前日期和时间。 |
| 4–25 | 创建一个 `switch` 语句来检查 PHP 在遇到错误时发送的 `$string` 变量。 |
| 5–8 | 如果 `$switch` 等于 "INVALID LOGIN"，则将错误记录到文件中并跳出 `switch` 语句。你必须在第 6 行将 `$username` 设为全局变量，以便在该函数中使用它。 |
| 9–19 | 如果 `$switch = "DATABASE CONNECT ERROR"`，则执行第 10–19 行。 |
| 10 | 将 `$mysqlerr` 设置为全局变量，以便其值可以在此函数中使用。 |
| 11–16 | 创建邮件消息文本并将其存储在 `$message` 变量中。该文本包含与此错误相关的信息。 |
| 17 | 使用 `error_log()` 函数将 `$message` 发送到指定的邮箱地址。 |
| 18 | 执行 `failure()` 函数。 |
| 19 | 跳出 `switch` 语句。 |
| 20–24 | 如果没有上述任何情况，则执行第 21–24 行。 |
| 21–23 | 如果错误值不等于 "8"（一个 E_NOTICE 错误），则将错误记录到文本文件中。 |
| 24 | 跳出 `switch` 语句。 |
| 25 | 关闭 `switch` 语句。 |
| 26 | 结束函数声明。 |
| 27–33 | 定义函数 `failure()`，用于发生会导致脚本无法按预期运行的错误时。 |
| 28–32 | 向用户显示消息，说明网站目前处于故障状态。 |
| 33 | 结束函数声明。 |
| 34 | 执行 `set_error_handler()` 函数，并将自定义错误处理器 "error_handler" 作为参数。这将禁用 PHP 内置的错误处理机制，并代之使用 `error_handler()`。 |
| 35 | 尝试连接 MySQL 数据库。我们假设这会失败，因为我们没有提供任何连接信息（主机、用户名、密码）。如果连接尝试导致错误（将会如此），则执行第 36–38 行。 |
| 36 | 将 MySQL 错误消息赋值给 `$mysqlerr` 变量。该变量将在 `error_handler()` 函数中使用。 |
| 37 | 使用自定义错误字符串 "DATABASE CONNECT ERROR" 触发错误。此字符串告诉自定义的 `error_handler()` 函数向管理员发送邮件，报告数据库连接无法工作。 |
| 39 | 创建变量 `$username` 来存储字符串 "bob"。这将用作测试用例，检查 `error_handler()` 函数是否正确记录了用户登录错误。 |
| 40 | 使用字符串 "INVALID LOGIN" 触发另一个错误。此错误会导致自定义错误处理器将无效登录记录到文件中。日志文件将存储登录失败时尝试登录的人的用户名。 |
| 41 | 创建一个变量来存储任意消息，发送到下一行的 `trigger_error()` 消息中。 |
| 42 | 使用 `$msg` 变量作为字符串触发另一个错误。此错误将被记录在 `error_log.txt` 文件中，因为错误字符串 (`$msg`) 不匹配 `error_handler()` 函数中的任何 `switch` 分支。 |

## 跟踪用户登录

接下来的脚本基于之前的示例，创建一个跟踪以下内容的小型应用程序：

* 有效登录— 脚本记录每次成功登录的日期、时间、用户名、IP 地址和浏览器。
*   无效登录— 脚本记录用户名以及用户尝试（未成功）访问网站的日期和时间。
*   数据库连接失败— 当数据库连接失败时，脚本向网站管理员的邮箱地址发送电子邮件。

## 备注

如果将此代码放在繁忙的网站上，可能会产生大量的垃圾邮件。每当数据库连接尝试失败时，都会向脚本指定的邮箱地址发送封邮件。如果你每天有 1000 次访问且数据库连接中断，请预计收件箱里至少会有 1000 封邮件（取决于每个页面发生多少连接尝试）。

### 脚本 8-6 login_track.php

查看全屏





```php
<?
  /* 此脚本所需的 SQL *****
  create table users (
    id INT NOT NULL,
    username VARCHAR(16),
    password VARCHAR(8),
    primary key(id));
  *****

function connect() {
  global $dbuser, $dbpw, $dbhost;
  if(!$db = @mysql_pconnect($dbhost,$dbuser,$dbpw)) {
    global $mysqlerr;
    $mysqlerr = mysql_error();
    trigger_error("DATABASE CONNECT ERROR",E_USER_NOTICE);
    failure();
  } else {
    mysql_select_db("php", $db);
    return 1;
  }
} //end connect()

function check_user($user, $password) {
  if(connect()) {
    $password = substr($password, 0, 8);
    $sql = "select * from users where username = '$user' and password = '$password'";
    if(!$result = mysql_query($sql)) {
      failure();
    }
    if (mysql_num_rows($result) == 1) {
      setcookie("user",$user);
      setcookie("password",$password);
      trigger_error("VALID LOGIN",E_USER_NOTICE);
      return 1;
    } else {
      trigger_error("INVALID LOGIN",E_USER_NOTICE);
      return 0;
    }
  }
} //end check_user

function error_handler($number, $string, $file, $line) {
  global $admin_email;
  $timestamp = date("m-d-Y H:i:s (T)");
  switch($string) {
    case("INVALID LOGIN"):
      global $user;
      error_log("Failed login attempt by $user on $timestamp\n",3,"failed_logins.txt");
      echo "<<h3>>Login Failed. Try Again!</</h3>>";
      break;
    case("VALID LOGIN");
      global $user, $REMOTE_ADDR, $HTTP_USER_AGENT;
      error_log("LOGIN: $user on $timestamp from $REMOTE_ADDR using $HTTP_USER_AGENT\n",
3,"valid_logins.txt");
      break;
    case("DATABASE CONNECT ERROR"):
      global $mysqlerr;
      $message = "Database Error!\n";
      $message .= "Unable to connect to database at $timestamp\n\n";
      $message .= "ERROR INFORMATION:\n";
      $message .= "FILE:\t$file\n";
      $message .= "LINE:\t$line\n";
      $message .="MYSQL:\t$mysqlerr\n";
      error_log($message,1,$admin_email, "FROM: PHP MONITOR <noreply@example.com>");
      failure();
      break;
    default:
      if($number != 0) {
        error_log("Error ($number) on line $line in file $file. The error was \"" . trim(
$string) . "\"\n", 3, "error_log.txt");
      }
      break;
  }
} //end error_handler

function failure() {
  ?>
  <h3>Sorry,</h3>
  <p>A problem has occured. The site administators have been notified and the problem 
  should be resolved shortly.
  <p>Please try again later.
  <?
  die();
} // end failure

function head() {
  ?>
  <html>
  <head>
  <title>Login Tracker</title>
  </head>
  <body bgcolor="#FFFFFF">
  <h1>Login Tracker</h1>
  <?
} //end head

/***** 主程序部分 *****/
$admin_email = "email@example.com";
$dbuser = "mysqluser";
$dbpw = "password";
$dbhost = "192.168.0.5";
$page = "login_track.php";
error_reporting(0);
set_error_handler("error_handler");
if(!isset($user) or !check_user($user, $password)) {
  head();
  ?>
  <h1>You must log in to view this page</h1>
  <form action="<?page?>" method="post">
  <p>Username: <input type="text" name="user"><br>
  Password: <input type="password" name="password" maxlength="8" size="8"><br>
  <input type="submit" name="submit" value="Submit">
  </form>
  <?
} else {
  head();
  ?>
  <h1>Authorized!</h1>
  <p>Your content here...
  <?
}
</body>
</html>

### 脚本 login_track.php 逐行解释

| 行号 | 描述 |
| :--- | :--- |
| 2–8 | 此脚本所需的 SQL。 |
| 10–21 | 定义函数 `connect()`，用于连接数据库。 |
| 11 | 允许在函数这些变量。 |
| 12 | 尝试连接数据库。如果发生错误，执行 13–16 行。如果没有发生错误，执行 17–20 行。 |
| 13 | 将变量 `$mysqlerr` 赋值给全局作用域。 |
| 14 | 将 `mysql_error()` 提供的错误信息赋值给变量 `$mysqlerr`。 |
| 15 | 触发自定义错误并发送到 `error_handler()` 函数。 |
| 16 | 执行 `failure()` 函数。 |
| 17–20 | 因为没有发生错误，在 MySQL 服务器上选择正确的数据库并返回 `1`。 |
| 21 | 函数定义结束。 |
| 23–40 | 定义函数 `check_user()`，用于将输入的用户名/密码与数据库中存储的值进行对比。 |
| 24 | 尝试连接数据库。如果连接失败，`connect` 函数会自动记录错误并终止脚本。 |
| 25 | 截断输入的密码，使其仅为 8 个字符。 |
| 26 | 定义 SQL 语句，从 `users'` 表中选择用户名和密码与输入值匹配的所有信息。 |
| 27–29 | 将查询发送到服务器并确保查询实际通过。如果没有通过，调用 `failure()` 函数向用户显示失败通知。 |
| 30 | 如果结果集中有一行，我们知道用户输入的值正确的。如果数据库没有返回任何行，我们知道用户的值与数据库中的值不匹配。（不应该有很多，因为你向数据库输入信息应该使用唯一的电子邮件地址。） |
| 31–32 | 在用户浏览器中设置 cookie，这样他们就不需要再次输入用户名和密码了，因为我们知道值是正确的。 |
| 33 | 触发错误以便将登录尝试存储在日志文件中。 |
| 34 | 向调用函数返回 `1`，使其知道尝试是成功的。 |
| 35–38 | 如果输入的值与数据库中的值不匹配，则记录该尝试并向调用函数返回 `0`。 |
| 39 | 关闭第 24 行开始的 `if` 语句。 |
| 40 | 函数定义结束。 |
| 42 | 定义错误处理函数，将错误代码 `$number`、错误字符串 `$string`、发生错误的文件（`file`）以及发生错误的行号（`line`）作为参数。 |
| 43 | 将 `$admin_email` 赋值为全局，以便此函数可以使用。 |
| 44 | 创建一个变量存储当前的日期时间。 |
| 45–71 | 创建一个 `switch` 语句遍历可能的错误字符串。 |
| 46–50 | 如果错误字符串为 "INVALID LOGIN"，从全局变量空间获取 `$user` 的值，将错误记录到 `"failed_logins.txt"` 文件，并向用户打印错误消息，然后跳出 switch 语句。 |
| 51–54 | 如果错误字符串为 "VALID LOGIN"，从全局变量空间获取 `$user`、`$REMOTE_ADDR`（用户 IP 地址）和 `$HTTP_USER_AGENT`（用户 浏览器）的值，并将信息记录到 `"valid_logins.txt"` 文件中，然后跳出 switch 语句。 |
| 55–65 | 如果错误字符串为 "DATABASE CONNECT ERROR"，则执行 56–65 行。 |
| 56 | 从全局变量空间获取 `$mysqlerr` 的值。该变量在错误首次发生时被赋值了一个值。 |
| 57–62 | 创建包含所有可用错误信息的长消息。 |
| 63 | 将消息发送给 `$admin_email` 变量的值。 |
| 64 | 执行 `failure()` 函数，它会在屏幕上打印错误消息并终止脚本。 |





- **66–70**: 如果错误字符串不是上述任何内容（且错误代码不是"0"，这仅仅是一个警告），则使用可用信息将错误记录到 `error_log.txt` 文件中。最后，跳出 switch 语句。
- **71**: 结束 switch 语句。
- **72**: 结束函数声明。
- **74–81**: 定义函数 `failure()`，该函数在调用时会向用户打印错误消息并终止脚本。
- **75–79**: 向用户打印错误消息。
- **80**: 使用 `die()` 函数终止脚本。
- **81**: 结束函数声明。
- **84–93**: 定义函数 `head()`，该函数会打印页面的起始部分 HTML 代码以及一个标题。
- **95**: 开始脚本的主执行阶段。
- **96–100**: 定义一些供脚本使用的变量。
- **102**: 使用 `error_reporting()` 函数关闭错误报告。
- **103**: 将错误处理程序设置为上面定义的自定义错误处理函数。
- **105**: 如果未设置 `$user` 变量或 `check_user()` 函数失败，则执行行 106–115。
- **106**: 打印页面的起始 HTML 代码。
- **107–114**: 打印表单，使用户可以输入用户名和密码查看页面内容。
- **115–121**: 如果设置了 `$user` 变量且 `check_user()` 函数返回 true，则用户有效并可以查看受保护的内容。
- **122–124**: 打印页面的结束 HTML 代码。

# 第 9 章 运用所学知识——会议跟踪应用程序

- 引言
- 设置
- 代码

## 引言
此会议管理器应用程序旨在作为一种协调会议的简单方法。您可以指定实际的会议地点，也可以使用内置的虚拟房间通过电话会议或 Web 服务进行会议。您可以直接在会议中指定电话号码和 Web 地址。

管理员通过管理界面设置用户和房间。完成设置后，用户就可以登录并开始安排会议。会议通过分步向导创建。向导会检查房间的可用性，仅允许使用当前会议时间未被安排的房间。已经安排了会议的用户被列为“忙碌”，但仍可以邀请参加会议。

一旦选定了会议时间、房间和用户，您就可以提供议程、会议电话和 Web 地址。会议确定后，将向所有参与者发送电子邮件通知。

当用户登录时，可以安排新会议或查看他们当前的会议。点击列表中的会议名称将显示该会议的完整详情。如果用户安排了会议，可以取消该会议。一旦会议取消，指定的房间将释放，所有用户都会收到取消通知。此外，会议将从日程中移除。

### 简单界面
会议管理器提供了一个简单的管理界面（如图 9-1 所示），允许管理员添加新用户或房间。一旦添加了用户或房间，即可用于安排会议。

##### 图 9-1 管理界面
![graphics/09fig01.jpg]

## 设置
设置会议管理器应用程序非常简单。只需安装下表指定的文件并使用提供的 SQL 设置您的数据库。记得更改代码中任何数据库和路径的参数以匹配您的系统。安装的总体布局如表 9-1 所示：

### 9-1 购物车的目录结构
| 文件夹 | 包含 |
| --- | --- |
| 顶层 | `meeting.php`, `meeting_inc.php` |
| admin 目录 | `admin.php` |

> a) 该目录必须经过保护！

## 代码
本节详细介绍了脚本涉及的代码。大部分主题已经涵盖，在介绍新主题时将提供额外的说明。

### meeting.sql
`meeting.sql` 是用于创建应用程序数据库的 SQL 代码。

####  9-1 meeting.sql
```sql
1.  CREATE TABLE users (
2.    id INT NOT NULL,
3.    first VARCHAR(32),
4.    last VARCHAR(32),
5.    phone VARCHAR(16),
6.    email VARCHAR(64),
7.    pass VARCHAR(8),
8.    PRIMARY KEY(id));
9.
10.  CREATE TABLE rooms (
11.    id INT NOT NULL,
12.    name VARCHAR(32),
13.    location VARCHAR(128),
14.    PRIMARY KEY(id));
15.
16.  INSERT INTO rooms VALUES(0,'Virtual Room','Virtual Location');
17.
18.  CREATE TABLE meetings (
19.    id INT NOT NULL,
20.    name VARCHAR(64),
21.    startdate DATETIME,
22.    enddate DATETIME,
23.    room INT,
24.    agenda TEXT,
25.    phone VARCHAR(16),
26.    web VARCHAR(128),
27.    originator INT,
28.    PRIMARY KEY(id));
29.
30.  CREATE TABLE meetingusers (
31.    meeting INT,
32.    userid INT);
```

##### 9-1 meeting.sql 逐行解释
| 行号 | 说明 |
| --- | --- |
| 1–8 | 创建存储用户信息的表。 |
| 10–14 | 创建存储房间信息的表。 |
| 16 | 创建用于电话或 Web 进行的“虚拟”会议的默认房间。 |
| 18–28 | 创建存储会议数据的表。“room”和“originator”是连接回用户和房间表的伪外键。 |
| 30–32 | 创建存储每个会议用户的表。表中的每行都对应一个用户和一个会议的键。一个会议可以在此表中有多条记录。 |

#### meeting.php
`meeting.php` 是应用程序的主脚本。它包含了所有常用的函数。




```php
<?php
  function addmeetingwizard($step) {
  session_start();
  head();
  global $fields, $page, $HTTP_POST_VARS, $user;
  switch($step) {
    case("1"):
      if(isset($fields)) { session_unregister("fields"); }
      ?>
      <form action="<?=$page?>" method="post">
      <table border=0>
      <tr><td colspan=2><h3>Add New Meeting - Step 1</h3></td></tr>
      <tr><<td>>Name: </td><<td><input type="text" name="name"></td></tr>
      <tr><<td>>Start Date & Time:</td>
        <td>
        <?createdate("start");?>
        </td></tr>
      <tr><<td>>End Date & Time: </td>
        <td>
        <?createdate("end");?>
        <br><i>(YYYY-MM-DD HH:MM)</i></td></tr>
      <tr><td colspan=2><input type="submit" name="addmeeting" value="Next"></td><tr>
      </table>
      <input type="hidden" name="step" value="2">
      </form>
      <?
      break;
    case("2"):
      ?><h2>Step 2 - Select Room</h2><?
      session_register("fields");
      if($HTTP_POST_VARS['name'] == "") {
        ?>
        <h2>You must select a name!</h2>
        <form action=<?=$page?> method="post">
        <input type="hidden" name="step" value="1">
        <input type="submit" name="addmeeting" value="Back">
        </form>
        <?
      } else {
        $dbconn = connect();
        $sql = "select id from users where email = '$user'";
        $result = $dbconn->query($sql);
        errortrap($result);
        $result->fetchInto($r);
        $fields['originator'] = $r['id'];
        $fields['name'] = $HTTP_POST_VARS['name'];
        $fields['startdate'] = $HTTP_POST_VARS['startyears'] . "-" . 
$HTTP_POST_VARS['startmonths'] . "-" . $HTTP_POST_VARS['startdays'] . " " . 
$HTTP_POST_VARS['starthours'] . $HTTP_POST_VARS['startminutes'];
        $fields['enddate'] = $HTTP_POST_VARS['endyears'] . "-" . 
$HTTP_POST_VARS['endmonths'] . "-" . $HTTP_POST_VARS['enddays'] . " " . 
$HTTP_POST_VARS['endhours'] . $HTTP_POST_VARS['endminutes'];
        $sql = "select room from meetings where startdate <= '" . $fields['enddate'] . 
"' AND enddate >= '" . $fields['startdate'] . "' AND room != '0'";
        $result = $dbconn->query($sql);
        errortrap($result);
        meetingdisplay($fields);
        ?>
        <p>
        <h3>The following rooms are available for your meeting time:</h3>
        <form action=<?=$page?> method=post>
        <input type="hidden" name="step" value="3">
        <p>Select One:
        <?
        $sql = "select * from rooms where id != '";
        while($result->fetchInto($row)) {
          $sql .= $row['room'] . "' AND id != '";
        }
        $sql .= "-1'";
        $result = $dbconn->query($sql);
        errortrap($result);
        while($result->fetchInto($row)) {
          $sql = "select * from rooms where id = '" . $row['id'] . "'";
          $resultroom = $dbconn->query($sql);
          errortrap($resultroom);
          $resultroom->fetchInto($roomrow);
          if($roomrow['id'] == '0') {
            ?>
            <br><input type="radio" name="roomchoice" value="<?roomrow['id']?>" checked> <?=$roomrow['name']?> $roomrow['location']?>
          } else {
            ?>
            <br><input type="radio" name="roomchoice" value="<?roomrow['id']?> <?=$roomrow['name']?> $roomrow['location']?>
          }
        }
        ?>
        <p><input type="submit" name="addmeeting" value="Next">
        </form>
        <?
      }
      break;
    case("3"):
      ?><h2>Step 3 - Select Attendees</h2><?
      $fields['roomchoice'] = $HTTP_POST_VARS['roomchoice'];
      $busyuser = array();
      $openuser = array();
      meetingdisplay($fields);
      ?>
      <p>Select People to Invite (CTRL-Click to choose multiple. Be sure to invite yourself!):
      <?
      $dbconn = connect();
      $sql = "select id from meetings where startdate <= '" . $fields['enddate'] .

AND enddate >= '" . $fields['startdate'] . "'";
      $result = $dbconn->query($sql);
      errortrap($result);
      while($result->fetchInto($row)) {
        $sql = "select userid from meetingusers where meeting = '" . $row['id'] . "'
order by userid";
        $userresult = $dbconn->query($sql);
        errortrap($userresult);
        while($userresult->fetchInto($row2)) {
          $busyuser[$row2['userid']] = $row2['userid'];
        }
      }
      $sql = "select id from users";
      $result = $dbconn->query($sql);
      errortrap($result);
      while($result->fetchInto($row)) {
        $count = 0;
        if(sizeof($busyuser) > 0) {
          foreach($busyuser as $buser) {
            if($row['id'] == $buser) {
              $count++;
            }
          }
        }
        if($count == 0) {
          $openuser[] = $row['id'];
        }
      }
      ?>
      <form action="<?page?>" method="post">
      <select name="attendees[]" size="8" multiple>
      <?
      foreach($openuser as $ouser) {
        $row = datafromid($dbconn, "users", $ouser);
        printf("<option value=%s>%s, %s</option>", $row['id'], $row['last'], $row['first']);
      }
      foreach($busyuser as $buser) {
        $row = datafromid($dbconn, "users", $buser);
        printf("<option value=%s>%s, %s (busy)</option)", $row['id'], $row['last'], $row['first']);
      }
      ?>
      </select>
      <input type="hidden" name="step" value="4">
      <p><input type="submit" name="addmeeting" value="Next">
      </form>
      <?
      break;
    case("4"):
      ?><h2>Step 4 - Define Agenda and Phone/Web Options</h2><?
      if(sizeof($fields['attendees']) == 0) {
        if($HTTP_POST_VARS['attendees'] != "") {
          $fields['attendees'] = $HTTP_POST_VARS['attendees'];
        }
      }
      if(sizeof($fields['attendees']) == 0) {
        ?>
        <h2>You must select at least one attendee!</h2>
        <form action=<?=$page?> method="post">
        <input type="hidden" name="step" value="3">
        <input type="submit" name="addmeeting" value="Back">
        </form>
        <?
      } else {
        meetingdisplay($fields);
        ?>
        <p>Define Phone, Web, and Agenda:
        <form action="<?=$page?>" method="post">
        Agenda:<textarea cols="20" rows="5" name="agenda"></textarea>
        <br>Web Address: <input type="text" name="web">
        <br>Phone Number: <input type="text" name="phone">
        <input type="hidden" name="step" value="5">
        <p><input type="submit" name="addmeeting" value="Next">
        </form>
        <?
      }
      break;
    case("5"):
      ?><h2>Step 5 - Confirmation</h2><?
      if($HTTP_POST_VARS['agenda'] == "") {
        ?>
        <h2>You must enter an agenda!</h2>
        <form action=<?=$page?> method="post">
        <input type="hidden" name="step" value="4">
        <input type="submit" name="addmeeting" value="Back">
        </form>
        <?
      } else {
        $fields['agenda'] = $HTTP_POST_VARS['agenda'];
        $fields['web'] = $HTTP_POST_VARS['web'];
        $fields['phone'] = $HTTP_POST_VARS['phone'];
        meetingdisplay($fields);
        ?>
        <h2>Click the button below to schedule your met!</h2>
        <form action=<?=$page?> method="post">
        <input type="hidden" name="step" value="6">
        <input type="submit" name="addmeeting" value="Finish!">
        </form>
        <?
      }
      break;
    case("6"):
      ?><h2>Finished!</h2><?
      $dbconn = connect();
      $id = $dbconn->nextID('meeting_id',true);
      errortrap($id);
      $sql = "insert into meetings values('$id', '" . $fields['name'] . "','" . $fields['startdate'] . "','" . $fields['enddate'] . "','" . $fields['roomchoice'] . "','" . $fields['agenda'] . "','" . $fields['phone'] . "','" . $fields['web'] . "','" . $fields['originator'] . "")')";
      $result = $dbconn->query($sql);
      errortrap($result);
      foreach($fields['attendees'] as $attendee) {
        $sql = "insert into meetingusers values('$id', '$attendee')";
        $result = $dbconn->query($sql);
        errortrap($result);
      }
      session_unset();
      session_destroy();
      notifyusers($id);
      choices();
      break;
    default:
      head();
      ?>
      <h3>There was an error. Please restart from the beginning.</h3>
      <?
      session_unset();
      session_destroy();
      ?>
      <form action=<?=$page?> method="post">
      <input type="hidden" name="step" value="1">
      <input type="submit" name="addmeeting" value="Restart">
      </form>
      <?
      break;
  } //end switch
} //end addmeetingwizard

  function meetingdisplay($fields) {
  ?>
  <h3>Meeting: <?=$fields['name']</h3>
  <h4>Start: <?=$fields['startdate']</h4>
  <h4>End: <?=$fields['enddate']</h4>
  <?
  if(sizeof($fields) > 4) {
  ?>
  <h4>Room:
    <?
    $dbconn = connect();
    $row = datafromid($dbconn, "rooms", $fields['roomchoice']);
    printf("%s - %s", $row['name'], $row['location']);
    ?>
    </h4>
  <?
  }
  if(sizeof($fields) > 5) {
    ?>
    <h4>Attendees:</h4>
    <?
    foreach($fields['attendees'] as $attendee) {
      $row = datafromid($dbconn, "users", $attendee);
      printf("<li>%s, %s - <a href=mailto:%s>%s</a>", $row['last'], $row['first'], $row['email'], $row['email']);
    }
    ?>
  }
  if(sizeof($fields) > 6) {
    ?>
    <h4>Agenda: <?=$fields['agenda']</h4>
    <h4>Web: <?=$fields['web']</h4>
    <h4>Phone: <?=$fields['phone']</h4>
    <?
  }
} //end meetingdisplay

  function viewschedule($email) {
  $dbconn = connect();
  $sql1 = "select id from users where email = '$email'";
  $result1 = $dbconn->query($sql1);
  errortrap($result1);
  $result1->fetchInto($row1);
  $userid = $row1['id'];
  $sql2 = "select meeting from meetingusers where userid = '$userid'";
  $result2 = $dbconn->query($sql2);
  errortrap($result2);
  $bgcolor = "#FFFF99";
  ?>
  <p>You have the following meetings on your schedule:</p>
  <table border=1 cellspacing=0 cellpadding=4>
  <tr bgcolor=$bgcolor?><td colspan=3><b>Meeting Name</b></td></tr>
  <tr bgcolor=$bgcolor?><<td><b>Start</b></td><td><b>End</b></td><td><b>Location</b></td></tr>
  <?
  $bgcolor ="FFFFFF";
  while($result2->fetchInto($row2)) {
    $row3 = datafromid($dbconn, "meetings", $row2['meeting']);
    $room = datafromid($dbconn, "rooms", $row3['room']);
    ?>
    <tr bgcolor=$bgcolor?>><td colspan=2><a href=<?=$page?>?action=viewmeetingdetails&id=$row2['meeting']><?=$row3['name']?></a></td><td>
    <?
    $sql = "select originator from meetings where id = '" . $row2['meeting'] . "'";
    $result = $dbconn->query($sql);
    errortrap($result);
    $result->fetchInto($r);
    if($r['originator'] == $userid) {
      ?>><a href=$page?>?action=viewmeetingdetails&id=$row2['meeting']>Cancel</a>
    } else {
      ?>&nbsp;
    }
    ?>
    </td>
    <tr bgcolor=$bgcolor?>><td><?=$row3['startdate']?></td><td><?=$row3['enddate']?></td><td><?=$row3['location']?></td></tr>
    <?
    if($bgcolor == "FFFFFF") {
      $bgcolor = "#FFFF99";
    }
  }
  ?>
  </table>
  <?
} //end viewschedule

  function deletemeeting($id) {
  $dbconn = connect();
  $sql = "select originator from meetings where id = '$id'";
  $result = $dbconn->query($sql);
  errortrap($result);
  $result->fetchInto($row);
  if($row['originator'] == $user) {
    $sql = "delete from meetings where id = '$id'";
    $result = $dbconn->query($sql);
    errortrap($result);
  }
  session_unset();
  session_destroy();
  notifyusers($id);
  choices();
  }
?>
</body>
</html>
```




图 9-2 显示了日程视图（Schedule View）的一个示例。

#### 图 9-2. meeting.pgp—查看日程

![graphics/09fig02.jpg](img/09fig02.jpg)

#### 脚本 9-2. meeting.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2–231 | 定义函数 `addmeetingwizard()`，引导用户完成会议创建。该函数接受一个参数，即向导的当前步骤。 |
| 3 | 启动会话以存储向导所需的变量。 |
| 4 | 打印页面 HTML 的起始部分。我们需要在 `session_start()` 函数之后执行此操作，因为已经向页面输出了文本，会话将无法工作。 |
| 5 | 定义脚本中使用的某些全局变量。 |
| 6 | 创建一个 switch 语句。switch 语句中的每个 `case` 对应于向导中的一个步骤。 |
| 7–27 | 开始向导的第一步。在这里我们询问用户会议名称以及会议持续时间。使用隐藏表单字段，以便在用户提交表单时将他们引导到下一步。 |
| 28–87 | 开始向导的第二步。此步首先检查用户是否输入了会议名称。如果没有输入名称，则将用户送回第一步。如果用户输入了名称，脚本将创建一个名为 `$fields` 的数组，用于存储会议的值。脚本还会获取用户 ID 并将其作为会议发起者存入 `$fields` 数组中。然后，它将会议名称和时间添加到 `$fields` 数组中。使用 `meetingdisplay()` 函数在屏幕上显示已输入的信息。脚本接着确定哪些房间可用，并列出空闲房间以及“虚拟”房间。一旦用户选择了房间，脚本将进入第三步。 |
| 88–144 | 开始向导的第三步。确定哪些用户已经安排了会议，并将他们列入列表中，并在名字旁边标注“(忙碌)”。一旦用户选择了参与者，继续继续到第四步。 |
| 145–173 | 开始向导的第四步。验证是否至少选择了一个用户作为参与者。如果没有选择参与者，则将用户送回第三步。如果至少选择了一个参与者，则提供一个表单，让用户输入会议议程、电话号码和网站。 |
| 174–197 | 开始向导的第五步。验证议程是否已填写。如果没有填写，则将用户送回第四步。如果议程已填写，则提供一个按钮让用户可以完成会议。 |
| 198–215 | 将会话 `$fields` 数组中的值输入数据库，并调用 `notifyuser()` 函数向所有受邀参与者发送电子邮件。 |
| 216–229 | 为 switch 提供一个默认 `default` 情况，以防发生任何情况导致函数跳过其他 `case`。向用户打印错误信息。 |
| 230 | 关闭在第 6 行开始的 switch 语句！ |
| 231 | 结束 `addmeetingwizard()` 的函数声明。 |
| 233–266 | 定义函数 `meetingdisplay()`，在用户通过会议创建向导时显示会议详情。由于 `$fields` 数组在每一步中都会添加项，因此我们只显示用户输入的信息。 |
| 268–315 | 定义函数 `viewschedule()`，允许用户在表格中一次查看他们所有的会议。该函数还提供了一个链接，使用户可以查看会议的完整详情，或者如果他们是发起者，提供取消会议的链接。 |
| 318–348 | 定义函数 `view_meeting_details()`，允许用户查看特定会议的完整详情。 |
| 350–379 | 定义函数 `deletemeeting()`，从数据库中删除会议，并通过电子邮件通知所有参与者会议已取消。 |
| 381–403 | 定义函数 `notifyusers()`，发送电子邮件通知用户他们被邀请参加新会议。 |
| 405–427 | 定义函数 `check_user()`，验证用户登录。这与第 7 章中使用的函数相似。 |
| 429–439 | 定义函数 `login()`，打印一个允许用户登录的表单。 |
| 441–447 | 定义函数 `choices()`，允许用户查看他们的日程或安排新会议。 |
| 449 | 开始主程序。 |
| 450 | 定义 `$page` 变量，用于那些带有表单的函数。 |
| 451 | 引入 `meeting_inc.php` 脚本，因为它包含了此脚本使用的函数。 |
| 452–453 | 检查用户是否已登录。如果没有，调用 `login()` 函数让用户登录。 |
| 454–456 | 如果用户已登录且 `$addmeeting` 变量已设置，则说明用户正在会议创建向导的中间。将用户送回向导。 |
| 457–479 | 如果用户已登录且 `$action` 变量已设置，则说明用户正在开始或完成特定任务。根据执行的操作将用户发送相应的函数。 |
| 480–483 | 如果用户已登录但没有创建会议或执行其他任务，则提供一些可以使用 `choices()` 函数的选项。 |
| 484 | 关闭在第 452 行开始的 if 语句。 |
| 486 | 结束页面的 PHP。 |
| 487–488 | 结束页面的 HTML。 |

#### meeting\_inc.php

meeting\_inc.php 包含了 meeting.php 和 admin.php 使用的代码。

##### 脚本 9-3 meeting\_inc.php





```php
1.  <?
 2.
3.  /***** FUNCTIONS *****/
 4.  function connect() {
 5.    ini_set("include_path", "G:\apache\Apache\php\pear");
 6.    require_once("DB.php");
 7.    $type = "mysql";
 8.    $username = "php";
 9.    $password = "password";
10.    $host = "localhost";
11.    $database = "meeting";
12.    $dsn = $type . "://" . $username . ":" . $password . "@" . $host . "/" . $database;
13.    $dbconn = DB::connect($dsn);
14.    errortrap($dbconn);
15.    $dbconn->setFetchMode(DB_FETCHMODE_ASSOC);
16.    return $dbconn;
17.  }//end connect
18.
19.  function errortrap($result) {
20.    if(DB::isError($result)) {
21.      ?><h3>There was an error!</h3><?
22.      die($result->getMessage());
23.    }
24.  } //end errortrap
25.
26.  function datafromid($dbconn, $table, $id) {
27.    $sql = "select * from $table where id = '$id'";
28.    $result = $dbconn->query($sql);
29.    errortrap($result);
30.    $result->fetchInto($row);
31.    return $row;
32.  } //end datafromid
33.
34.  function createdate($type) {
35.    $years = array("2002","2003","2004");
36.    $minutes = array(":00", ":15", ":30", ":45");
37.    $months = array();
38.    $days = array();
39.    $hours = array();
40.    for($i = 1; $i < 13; $i++) {
41.      if($i < 10) {
42.        $months[] = "0" . $i;
43.      } else {
44.        $months[] = $i;
45.      }
46.    }
47.    for($i = 1; $i < 32; $i++) {
48.      if($i < 10) {
49.        $days[] = "0" . $i;
50.      } else {
51.        $days[] = $i;
52.      }
53.    }
54.    for($i = 1; $i < 25; $i++) {
55.      $hours[] = $i;
56.    }
57.    $fields = array("years", "months", "days", "hours", "minutes");
58.    foreach($fields as $field) {
59.      ?>
60.      <select name="<? echo $type . $field ?>">
61.      <?
62.        foreach($$field as $item) {
63.          echo"<option value=$item>$item</option>\n";
64.        }
65.      ?>
66.      </select>
67.      <?
68.      if($field == "days") {
69.        echo " at ";
70.      }
71.    }
72.  } //end createdate
73.
74.  function head() {
75.    ?>
76.    <html
77.    <head>
78.    <style type=text/css>
79.    h1, h2, h3, p, td, li {font-family: verdana, sans-serif; }
80.    </style>
81.    </head>
82.    <body bgcolor="#FFFFFF">
83.    <div align=center>
84.    <table width="74%" border="0" cellspacing="0" cellpadding="0" height="128" 
85.bgcolor="#FFFFFF">
86.        <tr>
87.          <td height="134" align="center"><h1>A Meeting Manager</h1></td>
88.        </tr>
89.      </table
90.    </div
91.    <?
92.  }
93.  ?>
```

##### 脚本 9-3. meeting_inc.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 4–17 | 定义一个函数 `connect()`，用于建立与数据库的连接。请确保更改这些值以匹配你的特定设置。 |
| 19–24 | 定义一个函数 `errortrap()`，用于捕获可能任何 PEAR DB 错误。 |
| 26–32 | 定义一个函数 `datafromid()`，根据 `id` 从特定表中选择所有信息。该函数在整个脚本中使用，并减少了大量的输入工作。 |
| 34–72 | 定义一个函数 `createdate()`，为日期创建一个美观的下拉菜单。 |
| 74–91 | 定义一个函数 `head()`，用于打印任何页面的 HTML 头部。 |
| 92 | 结束脚本的 PHP。 |

图 9-4 显示了创建会议向导的示例。

##### 图 9-4. meeting.php—创建向导

`admin.php` 是该应用程序的管理界面。

##### 脚本 9-4 admin.php

```php
1.  <?
2.  function userform() {
3.    global $page;
4.    ?>
5.    <form action="<?page?>" method="post">
6.    <table border=0>
7.    <tr><td colspan=2><h3>Add User</h3></td></tr>
8.    <tr><td>First Name:</td><td><input type="text" name="first"></td></tr>
9.    <tr><td>Last Name:</td><td><input type="text" name="last"></td></tr>
10.    <tr><td>Phone:</td><td><input type="text" name="phone"></td></tr>
11.    <tr><td>Email:</td><td><input type="text" name="email"></td></tr>
12.    <tr><td>Password:</td><td><input type="text" name="password" size="8" maxlength="8"></td></tr>
13.    <tr><td colspan=2><input type="submit" name="adduser" value="Add User"></td></tr>
14.    </table>
15.    </form>
16.    <?
17.  } //end userform
18.
19.  function adduser($HTTP_POST_VARS) {
20.    if(($HTTP_POST_VARS['first'] or $HTTP_POST_VARS['last'] or $HTTP_POST_VARS['email']) == "") {
21.      return 0;
22.    } else {
23.      $dbconn = connect();
24.      $id = $dbconn->nextID('user_id',true);
25.      if(DB::isError($id)) {
26.        die($id->getMessage());
27.      }
28.      $sql = "INSERT INTO users VALUES('$id', '" . $HTTP_POST_VARS['first'] . "','" . $HTTP_POST_VARS['last'] . "','" . $HTTP_POST_VARS['phone'] . "', '" . $HTTP_POST_VARS['email'] . "', '$password')";
29.      $result = $dbconn->query($sql);
30.      errortrap($result);
31.      return 1;
32.    }
33.  } //end adduser
34.
35.  function addroomform() {
36.    global $page;
37.    ?>
38.    <form action="<?page?>" method="post">
39.    <table border=0>
40.    <tr><td colspan=2><h3>Add Room</h3></td></tr>
41.    <tr><td>Name:</td><td><input type="text" name="name"></td></tr>
42.    <tr><td>Location:</td><td><input type="text" name="location"></td></tr>
43.    <tr><td colspan=2><input type="submit" name="addroom" value="Add Room"></td></tr>
44.    </table>
45.    </form>
46.    <?
47.  } //end addroomform
48.
49.
50.  function addroom($HTTP_POST_VARS) {
51.    $dbconn = connect();
52.    $id = $dbconn->nextID('room_id',true);
53.    errortrap($id);
54.    $sql = "INSERT INTO rooms VALUES('$id', '" . $HTTP_POST_VARS['name'] . "','" . $HTTP_POST_VARS['location'] . "')";
55.    $result = $dbconn->query($sql);
56.    errortrap($result);
57.    return 1;
58.  } //end addroom
59.
60.
61.  function admin_choices() {
62.    ?>
63.    <li><a href="<?page?>?action=newuser">New User</a></li>
64.    <li><a href="<?page?>?action=newroom">New Room</a></li>
65.    <?
66.  }
67.
68.  /***** MAIN *****/
69.
70.  $page = "admin.php";
71.  require_once("../meeting_inc.php");
72.
73.  if(isset($addroom)) {
74.    if(addroom($HTTP_POST_VARS)) {
75.      echo "<h3>Room Added!</h3>";
76.    }
77.  }
78.  if(isset($adduser)) {
79.    if(adduser($HTTP_POST_VARS)) {
80.      echo "<h3>User Added!</h3>";
81.    } else {
82.      ?>
83.      <h2>You must enter First and Last Name, Email, and a Password!</h2>
84.      <h3>Please Try Again</h3>
85.      <?
86.      adduserform();
87.      ?>
88.    }
89.  }
90.
91.  if(isset($action)) {
92.    switch($action) {
93.      case("newuser"):
94.        adduserform();
95.        break;
96.      case("newroom"):
97.        addroomform();
98.        break;
99.      default:
100.       echo "Bad Action";
101.   }
102.  }
103.
104.  admin_choices();
105.  ?>
106. </body>
107. </html>
```





| 72 || 引入 `meeting_inc.php` 脚本以便此脚本可以使用其函数。 |
| 74–78 | 如果 `$addroom` 变量被设置，则说明管理员提交了添加房间的表单。调用 `addroom()` 函数来添加房间。 |
| 79–89 | 如果 `$adduser` 变量被设置，则说明管理员提交了添加用户的表单。验证名（First Name）、姓（Last Name）、邮箱和密码（Password）字段是否已填充，然后调用 `addroom()` 函数添加房间。 |
| 91–102 | 如果 `$action` 变量被设置，说明管理员点击了 `admin_choices()` 函数中的某个链接。根据点击的链接执行相应的操作。 |
| 104 | 执行 `admin_choices()` 函数，以便管理员可以添加房间或用户。 |
| 105 | 结束脚本的 PHP 代码。 |
| 106–107 | 结束页面的 HTML 代码。 |

## 第 10 章：PHP 与 XML

### 本章内容
* 概述
* 创建 XML 解析器
* 解析并转换 XML 文档
* 将数据库内容导出 XML 文件

### 概述
XML（可扩展标记语言）已正式进入主流，并展现了追随者自 XML 诞生以来一直推崇的优势。快速查看 Apache 和 Java 语言对 XML 的支持，就足以确认 XML 将长久存在。

PHP 以扩展的形式内置了对 XML 的支持。与其他扩展不同，XML 默认是编译在内部的，因此你不需要任何额外配置即可让 XML 正常工作。PHP XML 扩展使用了 James Clark 的 `expat` 库，其完整细节可以在 [www.jclark.com/xml/](http://www.jclark.com/xml/) 处找到。

快速查看 图 10-1 中包含 `phpinfo()` 函数的 PHP 页面，就可以确认你的 PHP 版本是否已启用 XML。

#### 图 10-1. 使用 phpinfo() 确认 XML 已启用
![graphics/10fig01.jpg](img/10fig01.jpg)

PHP 的 XML 扩展允许你解析 XML 文件。你可以遵循 XML 的节点和分支读取 XML 文件，并对其中包含的数据进行操作。

PHP 的 XML 扩展并不校验 XML 文件。也就是说，它无法将 XML 文件与 DTD（文档类型定义）对比，并根据 DTD 验证文件是否有效。尽管如此，你必须确保发送给 PHP 的 XML 或是有效的（valid）或格式良好的（well-formed）。

### 创建 XML 解析器
在用 PHP 的 XML 扩展读取 XML 文件之前，你必须创建一个解析器。由于 XML 文档是可扩展的，PHP 无法知道你正在 XML 中搜索哪些元素。因此，你必须告诉 PHP 如何解析文档。你通过定义一个新的 XML 解析器实例，然后定义元素数据处理器（element handlers）和字符处理器（character handlers）来告诉 PHP 如何解析文档。元素处理器简单来说就是在遇到一个元素时运行的函数。

#### 定义 XML 解析器
你通过 `xml_parser_create()` 函数来定义一个新的解析器：

```php
$parser = xml_parser_create($ENCODING);
```

你可以可选地指定解析器应使用的编码类型。你可以从三种编码中选择一种：
* ISO-8859-1（默认）
* US-ASCII
* UTF-8

一旦定义了解析器，你就可以创建处理器来执行读取 XML 的实际工作。

#### 定义元素处理器
使用 `xml_set_element_handler()` 函数定义元素处理器：

```php
xml_set_element_handler($parser, $START_FUNCTION, $END_FUNCTION);
```

`xml_set_element_handler()` 接受三个参数：
* `$parser`：你在调用 `xml_parser_create()` 时创建的变量。
* `$START_FUNCTION`:当解析器遇到起始元素时调用的函数名。
* `$END_FUNCTION`:当解析器遇到结束元素时调用的函数名。

#### 定义字符处理器
使用 `xml_set_character_handler()` 函数定义字符处理器：

```php
xml_set_character_handler($parser, $CHARACTER_FUNCTION);
```

`xml_set_character_handler()` 接受两个参数：
* `$parser`:你在调用 `xml_parser_create()` 时创建的变量。
* `$CHARACTER_FUNCTION`:当遇到字符数据时调用的函数名。

#### 启动解析器
拼图的最后一块是启动整个过程的函数 `xml_parse()`：

```php
xml_parse($parser, $XML);
```

`xml_parse()` 接受两个参数：
* `$parser`:你在调用 `xml_parser_create()` 时创建的变量。
* `$XML`:要解析的 XML。

#### 清理
在完成文档解析后，你应该调用 `xml_parser_free()` 函数来释放持有解析器的内存：

```php
xml_parser_free($parser);
```

`xml_parser_free()` 接受一个参数 `$parser`，即你在调用 `xml_parser_create()` 时创建的变量。

让我们通过一个示例来巩固刚刚讨论的原理。以下示例使用了刚刚讨论的所有函数。它打开一个命名为 `simple.xml` 的简单 XML 文件，并解析其中的 XML。图 10-2 显示了输出。这里是 `simple.xml`，你需要创建并将其与 `xml1.php` 示例放在同一目录下：

##### 脚本 10-1 simple.xml





```xml
<?xml version="1.0"?>
<document>
<title>XML 详解</title>
<body>揭秘 XML。在此处阅读相关内容。</body>
</document>
```

### 脚本 10-2 xml1.php

```php
<?
function startElement($xml_parser, $name, $attributes) {
  print("<p><i>遇到起始元素为:</i>$name\n");
}

function endElement($xml_parser, $name) {
  print("<p><i>遇到结束元素为:</i>$name\n");
}

function characterData($xml_parser, $data) {
  if($data != "\n") { 
    print("<p><i>遇到字符数据:</i>$data\n");
  }
}

function load_data($file) {
  $fh = fopen($file, "r") or die ("<P>无法打开文件!");
  $data = fread($fh, filesize($file));
  return $data;
}
/***** 主程序 *****/
$file = "simple.xml";
$xml_parser = xml_parser_create();
xml_set_element_handler($xml_parser, "startElement", "endElement");
xml_set_character_data_handler($xml_parser, "characterData");
xml_parse($xml_parser, load_data($file)) or die ("<P>XML 解析错误!");
xml_parser_free($xml_parser);
?>
```

### 图 10-2. xml1.php

![graphics/10fig02.jpg](img/10fig02.jpg)

### 脚本 10-2. xml1.php 逐行说明

| 行号 | 说明 |
| --- | --- |
| 2 | 创建一个名为 `startElement()` 的函数，用于处理脚本在解析 XML 时遇到的任何起始元素。该函数接受以下内容作为参数（PHP 的要求）：<br><ul><li`$xml_parser`</li><li`$name`</li><li`$attributes`</li></ul> |
| 3 | 当遇到起始元素时，向屏幕打印一条消息。 |
| 4 | 结束函数声明。 |
| 6 | 创建一个名为 `endElement()` 的函数，用于处理脚本在解析 XML 时遇到的任何结束元素。该函数接受以下内容作为参数（PHP 的要求）：<br><ul><li`$xml_parser`</li><li`$name`</li></ul> |
| 7 | 当遇到结束元素时，向屏幕打印一条消息。 |
| 8 | 结束函数声明。 |
| 10 | 创建一个名为 `characterData()` 的函数，用于处理脚本在解析 XML 时位于元素之间的数据。该函数接受以下内容作为参数（PHP 的要求）：<br><ul><li`$xml_parser`</li><li`$data`</li></ul> |
| 11–13 | 如果元素之间存在实际的字符数据（不仅仅是换行符），则在遇到字符数据时，向屏幕打印一条消息。 |
| 14 | 结束函数声明。 |
| 16 | 创建一个名为 `load_data()` 的函数，将数据从 XML 文件读取到脚本中以便解析。该函数接受一个参数 `$file`，它是你想要解析的 XML 文件的文件名（带有可选路径）。 |
| 17 | 尝试将文件句柄分配给文件。如果失败，则终止脚本并打印错误消息。 |
| 18 | 如果文件打开成功，将整个文件读取到 `$data` 变量中。注意，对于大文件，这种方法效率低下。 |
| 19 | 将 `$data` 变量返回给调用程序。 |
| 20 | 结束函数声明。 |
| 21 | 开始主程序。 |
| 22 | 将文件名赋值给 `$file` 变量。注意可以使用文件的完整路径，例如：<br><ul><liWindows: `$file = "C:\winnt\xml\myxmlfile.xml";`</li><liLinux: `$file = "/home/me/xml/myxmlfile.xml";`</li></ul> |
| 23 | 创建变量 `$xml_parser` 并使用 `xml_parser_create()` 函数将其赋值为 PHP XML 解析器。 |
| 24 | 使用 `xml_set_element_handler()` 函数定义上述自定义的起始结束元素处理函数。当 PHP 遇到起始或结束元素时，将使用相应的函数。 |
| 25 | 使用 `xml_set_character_data_handler()` 函数定义上述自定义的数据处理函数。当 PHP 遇到字符数据时，将使用 `characterData()` 函数。 |
| 26 | 使用 `xml_parse` 函数解析 XML。`xml_parse()` 函数需要 XML 解析器的名称（`xml_parser`）和要解析的 XML 数据。在这种情况下，我们通过使用自定义的 `load_data($file)` 函数提供 XML 数据。如果 `xml_parse()` 函数失败，则终止（`<P>XML 解析错误!`）。 |
| 27 | 使用 `xml_parser_free($xml_parser)` 释放与解析器相关的内存。 |




## XML 数据

以下是一个关于《星际牛仔》的 XML 结构示例，描述了 DVD 集和各个集的信息。

```xml
<?xml version="1.0"?>
<series title="Cowboy Bebop" genre="Anime" subgenre="Science Fiction">
  <dvd number="1">
    <episode number="1">
      <title>Asteroid Blues</title>
      <synopsis>Jet 和 Spike 追踪一名毒贩。</synopsis>
      <characters>
        <character>Jet</character>
        <character>Spike</character>
      </characters>
    </episode>
    <episode number="2">
      <title>Stray Dog Strut</title>
      <synopsis>Ein 加入了团队。</synopsis>
      <characters>
        <character>Jet</character>
        <character>Spike</character>
        <character>Ein</character>
      </characters>
    </episode>
    <episode number="3">
      <title>Honkey Tonk Woman</title>
      <synopsis>Faye Valentine 登场。</synopsis>
      <characters>
        <character>Jet</character>
        <character>Spike</character>
        <character>Ein</character>
        <character>Faye</character>
      </characters>
    </episode>
    <episode number="4">
      <title>Gateway Shuffle</title>
      <synopsis>在赌场玩乐。</synopsis>
    </episode>
    <episode number="5">
      <title>Ballad Of Fallen Angels</title>
      <synopsis>Spike 的过去再次回来纠缠着他。</synopsis>
    </episode>
  </dvd>
  <dvd number="2">
    <episode number="6">
      <title>Sympathy For The Devil</title>
      <synopsis>男孩 Wen 的谜团。</synopsis>
    </episode>
    <episode number="7">
      <title>Heavy Metal Queen</title>
      <synopsis>太空卡车司机。</synopsis>
    </episode>
    <episode number="8">
      <title>Waltz for Venus</title>
      <synopsis>欢迎来到金星。</synopsis>
    </episode>
    <episode number="9">
      <title>Jamming With Edward</title>
      <synopsis>Edward 加入了团队。</synopsis>
      <characters>
        <character>Jet</character>
        <character>Spike</character>
        <character>Ein</character>
        <character>Faye</character>
        <character>Edward</character>
      </characters>
    </episode>
    <episode number="10">
      <title>Ganymede Elegy</title>
      <synopsis>Jet 的回家之旅。</synopsis>
    </episode>
  </dvd>
</series>
```




- 31: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"EPISODE"`。
- 32: 将 `$TagsOpen["EPISODE"]` 标记设置为 true (1)，因为 `EPISODE` 标签是开启状态。
- 33–35: 在屏幕上打印关于 `EPISODE` 标签的信息，包括它的属性。
- 36: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 37: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"TITLE"`。
- 38: 将 `$TagsOpen["TITLE"]` 标记设置为 true (1)，因为 `TITLE` 标签是开启状态。我们不需要为 `TITLE` 打印任何内容，因为该标签没有关联属性。
- 39: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 40: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"SYNOPSIS"`。
- 41: 将 `$TagsOpen["SYNOPSIS"]` 标记设置为 true (1)，因为 `SYNOPSIS` 标签是开启状态。我们不需要为 `SYNOPSIS` 打印任何内容，因为该标签没有关联属性。
- 42: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 43: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"CHARACTERS"`。
- 44: 将 `$TagsOpen["CHARACTERS"]` 标记设置为 true (1)，因为 `CHARACTERS` 标签是开启状态。
- 45–47: 打印一些在打印单个角色名称时将使用的格式化。
- 48: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 49: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"CHARACTER"`。
- 50: 将 `$TagsOpen["CHARACTER"]` 标记设置为 true (1)，因为 `CHARACTER` 标签是开启状态。我们不需要为 `CHARACTER` 打印任何内容，因为该标签没有关联属性。
- 51: 递变量 `$counter`，因为它用于在显示单个角色名称时帮助格式化输出。
- 52: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 53: 关闭 switch 语句。
- 54: 结束函数声明。
- 56: 创建名为 `endElement()` 的函数，用于处理脚本在解析 XML 时遇到的任何结束元素。该函数接收以下参数（PHP 要求）：
  - `$xml_parser`
  - `$name`
- 57: 允许此函数访问并修改变量 `$TagsOpen` 和 `$counter`。`$TagsOpen` 是一个跟踪哪些标签已开启或关闭的数组。`$counter` 是一个整数，用于显示角色数据时的格式化。
- 58: 创建 switch 语句来评估起始元素名称的值。
- 59: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"SERIES"`。
- 60: 将 `$TagsOpen["SERIES"]` 标记设置为 false (0)，因为 `SERIES` 标签已关闭。
- 61: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 62: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"DVD"`。
- 63: 将 `$TagsOpen["DVD"]` 标记设置为 false (0)，因为 `DVD` 标签已关闭。
- 64: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 65: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"EPISODE"`。
- 66: 将 `$TagsOpen["EPISODE"]` 标记设置为 false (0)，因为 `EPISODE` 标签已关闭。
- 67: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 68: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"TITLE"`。
- 69: 将 `$TagsOpen["TITLE"]` 标记设置为 false (0)，因为 `TITLE` 标签已关闭。
- 70–72: 打印结束的 span 标签，该标签是在解析器发现开启的 `TITLE` 标签时开始的。
- 73: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 74: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"SYNOPSIS"`。
- 75: 将 `$TagsOpen["SYNOPSIS"]` 标记设置为 false (0)，因为 `SYNOPSIS` 标签已关闭。
- 76: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 77: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"CHARACTERS"`。
- 78: 将 `$TagsOpen["CHARACTERS"]` 标记设置为 false (0)，因为 `CHARACTERS` 标签已关闭。
- 79–81: 关闭 blockquote 和 span 标签，这些标签是在解析器遇到开启的 `CHARACTERS` 标签时开始的。
- 82: 将 `$counter` 变量设置为 0。`characterData()` 函数将使用此显示角色名称。
- 83: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 84: 在 switch 语句中添加一个 case，检查 `$name` 变量是否等于 `"CHARACTER"`。
- 85: 将 `$TagsOpen["CHARACTER"]` 标记设置为 false (0)，因为该标签已关闭。
- 86: 跳出 switch 语句，因为我们已经完成了对 `$name` 变量的评估。
- 87: 关闭 switch 语句。
- 88: 结束函数声明。
- 90: 创建名为 `characterData()` 的函数，用于处理脚本在解析 XML 时遇到的任何字符数据。该函数接收以下参数（PHP 要求）：
  - `$xml_parser`
  - `$data`
- 91: 允许此函数访问并修改变量 `$TagsOpen` 和 `$counter`。`$TagsOpen` 是一个跟踪哪些标签已开启或关闭的数组。`$counter` 是一个整数，用于显示角色数据时的格式化。
- 92: 创建 switch 语句来评估 `$TagsOpen` 数组的值。通过检查此数组，函数可以确定 PHP 处于 XML 的哪个位置并以正确的格式显示数据。
- 93: 在 switch 语句中添加一个 case，检查 `CHARACTER` 标签是否开启。在检查其他标签是否开启之前，先检查 `CHARACTER` 元素是否开启，因为 `CHARACTER` 元素是最内部的元素。
- 94–98: 检查 `$counter` 的值。如果计数器设置为 1，说明这是当前 XML 节点中的第一个角色。如果是第一个角色，直接打印角色名称。如果不是第一个角色，则打印逗号和角色名称。这允许你用逗号分隔条目。
- 99: 跳出 switch 语句，因为我们已经完成了对 `$TagsOpen` 变量的评估。
- 100: 在 switch 语句中添加一个 case，检查 `SYNOPSIS` 元素标签是否开启。我们接下来检查 `SYNOPSIS` 元素是否开启，因为它是最深层节点的上一层。
- 101: 如果 `SYNOPSIS` 标签已开启，则打印 `SYNOPSIS` 内部的数据。
- 102: 跳出 switch 语句，因为我们已经完成了对 `$TagsOpen` 变量的评估。
- 103: 在 switch 语句中添加一个 case，检查 `TITLE` 元素标签是否开启。我们接下来检查 `TITLE` 元素是否开启，因为它是 `SYNOPSIS` 的上一层。
- 104: 如果 `TITLE` 标签已开启，则打印 `TITLE` 内部的数据。
- 105: 跳出 switch 语句，因为我们已经完成了对 `$TagsOpen` 变量的评估。
- 106: 关闭 switch 语句。注意：我们不需要检查任何其他元素，因为这些元素在开启和关闭标签之间不包含任何实际的字符数据。它们只包含其他元素，因此不需要使用此函数来检查这些元素中的数据。
- 107: 结束函数声明。





| 108 | 创建一个名为 `load_data()` 的函数，将数据从 XML 文件读取到脚本中，以便对其进行解析。该函数接受一个参数 `$file`，它是你想要解析的 XML 文件的名称（带有可选路径）。 |
| 109 | 尝试将文件句柄分配给该文件。如果失败，则终止脚本并打印错误信息。 |
| 110 | 如果文件打开成功，则将整个文件读取到 `$data` 变量中。注意，对于大文件，这种方法极极低效。 |
| 111 | 将 `$data` 变量返回给调用程序。 |
| 112 | 结束函数声明。 |
| 114–122 | 定义并初始化 `$TagsOpen` 数组。你需要为每个需要跟踪的元素定义一个数组元素。数组项的键（key）是元素的名称，值是 1 或 0（真或假）。在开始时将所有值设置为假（0），因为在开始解析文件之前，本不应该有任何标签处于打开状态。 |
| 124 | 将变量 `$counter` 初始化为 "0"。 |
| 126 | 将文件名分配给 `$file` 变量。注意，你可以使用文件的完整路径，例如：\n* Windows: `$file = "C:\winnt\xml\myxmlfile.xml";`\n* Linux: `$file = "/home/me/xml/myxmlfile.xml";` |
| 127 | 使用 `xml_set_parser_option()` 函数定义解析选项。此函数更改解析器运行时的选项。它需要三个参数：\n* 使用 `xml_parser_create` 函数创建的 XML 解析器。\n* 你想要设置的选项。\n* 你正在设置的选项的值。\n 在此情况下，我们把选项 `XML_OPTION_CASE_FOLDING` 设置为 `true`，这会在解析器读取 XML 文件时将元素名称的大小转换为大写。通过这样，我们就不需要担心 XML 文件中的元素名称是否存在混合大小写了。在检查是否遇到特定元素时，你只需要检查该元素名称的大写版本即可。 |
| 128 | 创建一个名为 `$xml_parser` 的变量，并使用 `xml_parser_create()` 函数将其赋值为 PHP XML 解析器。 |
| 129 | 使用 `xml_set_element_handler()` 函数定义你上面创建自定义开始和结束元素处理函数。每当 PHP 遇到开始或结束元素时，它将使用相应的函数。 |
| 130 | 使用相应的函数定义你上面创建自定义数据处理函数。每当 PHP 遇到字符数据时，它将使用 `characterData()` 函数。 |
| 131 | 使用 `xml_parse` 函数开始解析 XML。`xml_parse()` 函数需要 XML 解析器的名称 `$xml_parser` 以及你想要解析的 XML 数据。在这种情况下，我们通过自定义的 `load_data($file)` 函数提供 XML 数据。如果 `xml_parse()` 函数失败，则终止脚本并显示错误信息。 |
| 132 | 在 `xml_parse()` 函数完成 XML 解析后，使用 `xml_parser_free()` 函数释放与解析器关联的内存。 |
| 133–135 | 停止作为 PHP 解析该页面，并关闭该页面的 HTML 标签。 |

### 将数据库内容导出到 XML 文件

虽然这不需要 PHP XML 函数，但使用 PHP 将数据从数据库导出到 XML 文件是获取结构化 XML 的极佳方法，你可以将其用于其他支持 XML 的应用程序。

数据库数据的性质非常适合在 XML 应用程序中使用。你已经创建了一个数据库结构。接下来的脚本提取地址录的内容，并将其存储在 XML 中。使用 PHP，你可以轻松地将这些数据导出到 XML 文件，或者在浏览器中显示。如果你在浏览器中检查是否遇到了某个特定元素，只需要检查该元素名称的大写版本即可。





| 33 | 生成一个 SQL 语句来选择表中的所有内容，并按姓氏、再名字对结果进行排序。 |
| 34 | 执行 SQL 查询并将结果存放在 `$result` 变量中。 |
| 35–52 | 使用 `while` 循环遍历结果集。 |
| 36–51 | 停止作为 PHP 继续页面的处理。由于我们正在输出大量数据，让服务器发送纯 XML 会比将每行都作为打印语句进行处理要简单。将当前行返回的每个结果作为 "contact" 元素的部分打印出来。在 "contact" 内部找到子元素包含了通讯录条目的详细信息。 |
| 52 | 关闭 `while` 循环。 |
| 53 | 通过打印根元素 `<addressbook>` 的闭合标签来结束 XML 的输出。 |
| 54 | 关闭在第 30 行开始的 `if` 语句。 |
| 55 | 结束脚本。 |

## 第 11 章：使用 PHP 生成动态图形

### 本章内容

* 概述
* GD 库
* 启用 GD 支持
* 使用 GD 生成图形

### 概述

PHP 能够动态生成和修改图像。若要在 PHP 中使用这些高级功能，你需要包含一些安装 PHP 时默认未包含的额外库。

### GD 库

PHP 提供了通过 GD 库来创建和操作图像的能力。GD 主页位于 [www.boutell.com/gd/](http://www.boutell.com/gd/)，其列出的 GD 定义为：

> “一个用于动态创建图像的 ANSI C 库。GD 可以创建 PNG 和 JPEG 图像等其他格式。GD 不创建 GIF 图像。”

此前，GD 被广泛用于创建 GIF 图像，但拥有 GIF 图像使用的 LZW 压缩算法专利的 Unisys 公司最近开始行使他们的专利权，GIF 创建功能随后从 GD 的功能列表中删除。

然而，GD 仍然可以用于创建 JPEG 和 PNG 图形，这两种格式都被大多数流行的 Web 浏览器支持。此外，GD 还支持创建 WBMP 图像，这种图像用于小型移动无线设备。

基本上，GD 可以很好地满足你脚本化图形创建的需求。请注意，GD 不是一个绘画程序。它可以通过向图像添加文本来操作现有图像，或者通过两个或多个现有图像创建新图像。

GD 在创建按钮图像以及在现有图像中嵌入说明时最为有用。

### 启用 GD 支持

GD 支持默认未启用。如果你使用的是 Windows，则必须启用扩展；如果你使用的是 Linux，则需要编译编译或链接该扩展。

#### 在 Windows 上启用 GD

在 Windows 上启用 GD 支持非常简单，因为 GD 的 DLL 文件已经过编译并包含在基础的 PHP Windows 安装包中。用文本编辑器打开你的 `php.ini` 文件，并搜索如下行：

```
extension_dir =  ./ 
```

此行应该指向 PHP 扩展文件所在的位置。如果你将扩展复制到了与 `php.ini` 文件相同的目录下，则不需要修改该行。如果你没有将 PHP 扩展移动到与 `php.ini` 相同的目录下，则需要编辑该行以指向正确的目录，例如：

```
extension_dir = C:\Apache\php\extensions 
```

接下来，在 `php.ini` 文件中找到如下部分：

```
;Windows Extensions 
```

该行后面会跟着几行。要启用 GD，取消包含 GD 的行开头的分号注释：

```
extension=gd.dll
```

取消该行的注释后，保存文件并重启 Apache 服务器。你可以使用图 11-1 所示的 `phpinfo()` 来验证 GD 是否正确安装。

##### 图 11-1 启用 GD 的 phpinfo() 结果

#### 在 Linux 上启用 GD

如果你使用 Apache 的 APXS 编译了 PHP，那么为 PHP 添加功能非常简单。在重新编译 PHP 之前，我建议你先删除 `config.cache` 并清理上次编译留下的文件。可以这样操作：

```
cd /path/to/php/source
rm config.cache
make clean
```

执行命令后，你会发现有很多文件被删除。不用担心，`make` 程序只是在清理重新编译时不需要的文件。如果不运行 `make clean` 命令，即使你没有更改任何内容，也可能会遇到一些问题，问题。

一旦你清理了上次编译的混乱，就可以开始新的编译。要编译带有 GD 支持的 PHP：

```
./configure --with-apxs=/usr/local/apache/apxs \
--with-gd \
--with-ttf
```

运行 `configure` 后，执行命令：

```
make
```

假设没有发生错误，你就可以执行命令：

```
make install
```

最后的命令将 `libphp4.so` 库复制到 `/path/to/apache/libexec/`。重启 Apache 以加载新库：

```
/path/to/apache/bin/apachectl restart
```

你可以通过 `phpinfo()` 函数验证 GD 是否正确安装。

### 使用 GD 生成图形

一旦你配置了 PHP 使用 GD 库，你就可以开始创建图形了。

#### 线和文本

使用 GD 库创建图像时使用的基础函数是 `ImageCreate()` 函数。

```
$length = 300; 
$width = 100;
$image = ImageCreate($length, $width);
```




```
$blue = ImageColorAllocate($image, 0, 0, 255); 
```

现在你已经创建了一个框并为它指定了颜色。现在剩下的工作是在浏览器中显示图像。要做到这一点，你还需要另外两行代码：

```
Header("Content-type: image/png"); 
ImagePNG($image);
```

第一行告诉浏览器期望一个 PNG 图像，第二行是将你创建的图像输出到浏览器的函数。不过，在你输入这些代码之前，让我们先添加一些文本。

既然你已经创建了基础图像，可以在其上添加一些形状。你可以为图像添加的最基础的“形状”是线。线段通过连接图像上的两个端点创建的。使用 `ImageLine()` 函数创建线条：

```
ImageLine($image, $x1, $y1, $x2, $y2, $color); 
```

你在 `ImageLine()` 函数中指定的点是 x,y 顶点，几乎就像数学中绘制点时使用的点，不同的是这里使用的网格略有不同。GD 中用于放置形状的网格从左上角的 x,y 点 0,0 开始。x 坐标向右移动，就像普通的数学图形一样。然而，y 坐标向下移动，而不是像数学图形那样向上移动，因此点 (10,20) 位于图像左上角右侧 10 像素、下方 20 像素处。

GD 还支持一些基本的字符串函数，允许你在图像上打印文本。你只能使用一种基本字体，并且只有五种大小，列在 表 11-1 中，但它对于不需要花哨字体的图形和图表效果良好。要向图像中添加文本：

```
IMageString($image, $fontSize, $x1, $y1, $string, 
$color);
```

##### 表 11-1. GD 字符串函数可字体大小

| 字体大小 || 字体 || 大小 |
| --- | --- | --- |
| 1 || gdFontTiny || 8 x 5 像素 |
| 2 || gdFontSmall || 13 x 6 像素 |
| 3 || gdFontMediumBold || 13 x 7 像素 |
| 4 || gdFontLarge || 15 x 8 像素 |
| 5 || gdFontGiant || 15 x 9 像素 |

下一个脚本创建了一个简单的图形，如图 11-2 所示，使用 `ImageLine()` 和 `ImageString()` 函数来说明图表的工作原理以及文本大小的外：

##### 脚本 11–1 gd\_grid.php

```
1.  <?
 2.  $height = 301;
 3.  $width = 301;
 4.  $image = ImageCreate($width, $height);
 5.  $white = ImageColorAllocate($image, 255, 255, 255);
 6.  $blue = ImageColorAllocate($image, 0, 0, 255);
 7.  $red = ImageColorAllocate($image, 255, 0, 0);
 8.  for($i = 0; $i < $height; $i = $i + 20) {
 9.    ImageLine($image, $i, 0, $i, $height, $blue);
 10.    ImageLine($image, 0, $i, $width, $blue);
 11.    ImageString ($image, 1, $i, 0, $i, $red);
 12.    ImageString ($image, 1, $2, $i, $red);
 13.  }
 14.  ImageString ($image, 1, 82, 22, "Size 1 Font", $red);
 15.  ImageString ($image, 2, 82, 62, "Size 2 Font", $red);
 16.  ImageString ($image, 3, 82, 102, "Size 3 Font", $red);
 17.  ImageString ($image, 4, 82, 142, "Size 4 Font", $red);
 18.  ImageString ($image, 5, 82, 182, "Size 5 Font", $red);
 19.  header ("Content-type: image/png");
 20.  ImagePng($image);
 21.  ImageDestroy($image);
 22.  ?>
```

##### 图 11-2. gd\_grid.php

![graphics/11fig02.jpg](img/11fig02.jpg)

##### 脚本 11-1. gd\_grid.php 逐行解释

| 行 || 说明 |
| --- | --- |
| 2 || 为图像定义 301 像素的高度（以便网格的最后线可见）。 |
| 3 || 为图像定义 301 像素的宽度。 |
| 4 || 使用 `ImageCreate()` 函数创建基础图像，指定之前定义的高宽。 |
| 5 || 使用 `ImageColorAllocate()` 定义变量 `$white`。参数允许白色（RGB 值 255,255,255）被 `$image` 使用。它也被用作 `$image` 的背景颜色，因为它是分配给 `$image` 的第一个颜色。 |
| 6 || 定义蓝色并允许被 `$image` 使用。 |
| 7 || 定义红色并允许被 `$image` 使用。 |
| 8–13 || 创建一个 `for` 循环，从坐标 0,0（图像左上角）开始每 20 像素绘制一条线。 |
| 9 || 在 `for` 循环中，在 `$image` 内部创建从点 `$i, 0` (0,0 20,40...) 到点 `$i, $height` (0,301 20,301...) 的线。循环的每次迭代从图像顶部到底部绘制一条垂直线，左右间距为 20 像素。 |
| 10 || 在 `for` 循环中，在 `$image` 内部创建从点 0, `$i` (0,0 20,40...) 到点 `$width, $i` (301,0 301,20 301,40...) 的线。循环的每次迭代从图像左侧到右侧绘制一条水平线，上下间距为 20 像素。 |
| 11 || 在 `for` 循环中，使用 `ImageString()` 函数创建一个小标签来显示当前垂直线的当前像素。记住 `ImageString($image, $fontsize, $x, $y, $text, $color);`。 |
| 12 || 在 `for` 循环中，创建一个小标签来显示当前水平线的当前像素 `ImageString()` 函数。 |
| 13 || 结束 `for` 循环。 |
| 14–18 || 在屏幕上不同位置创建文本以显示不同的字体。 |
| 19 || 将图像头发送到用户的浏览器。 |
| 20 || 显示你创建的图像 `$image`。 |
| 21 || 从服务器内存中销图像，因为它已经发送到了浏览器。 |

#### 为你的图像添加 TrueType 字体

你可以使用 TrueType 字体在图像上添加更好看的文本。实现此点的函数是 `ImageTTFText()`。

```
ImageTTFText($image, $size, $angle, $xcoord, $ycoord, $color, $font, $text);
```

`ImageTTFText()` 的参数为：

* `$image`— 你放置此字体的图像的句柄。
* `$size`— 文本的大小，以磅为单位。
* `$angle`— 文本倾斜的度数。注意这并不是字符本身的倾斜（例如使用斜体字体时），而是写入文本的“线”的倾斜。
* `$xcoord`— 图像中 `$text` 第一个字符左方的 x 坐标。
* `$ycoord`— 图像中 `$text` 第一个字符下方的 y 坐标。
* `$color`— 文本的颜色。
* `$font`— TrueType 字体文件的位置。
* `$text`— 你想要打印的文本。

下一个脚本创建了一个简单的图形，如图 11-2 所示，使用 `ImageLine()` 和 `ImageString()` 函数来说明图表的工作原理以及文本大小的外：

##### 脚本 11–1 gd\_grid.php

```
1.  <?
 2.  $height = 301;
 3.  $width = 301;
 4.  $image = ImageCreate($width, $height);
 5.  $white = ImageColorAllocate($image, 255, 255, 255);
 6.  $blue = ImageColorAllocate($image, 0, 0, 255);
 7.  $red = ImageColorAllocate($image, 255, 0, 0);
 8.  for($i = 0; $i < $height; $i = $i + 20) {
 9.    ImageLine($image, $i, 0, $i, $height, $blue);
 10.    ImageLine($image, 0, $i, $width, $blue);
 11.    ImageString ($image, 1, $i, 0, $i, $red);
 12.    ImageString ($image, 1, $2, $i, $red);
 13.  }
 14.  ImageString ($image, 1, 82, 22, "Size 1 Font", $red);
 15.  ImageString ($image, 2, 82, 62, "Size 2 Font", $red);
 16.  ImageString ($image, 3, 82, 102, "Size 3 Font", $red);
 17.  ImageString ($image, 4, 82, 142, "Size 4 Font", $red);
 18.  ImageString ($image, 5, 82, 182, "Size 5 Font", $red);
 19.  header ("Content-type: image/png");
 20.  ImagePng($image);
 21.  ImageDestroy($image);
 22.  ?>
```

##### 图 11-2. gd\_grid.php

![graphics/11fig02.jpg](img/11fig02.jpg)

##### 脚本 11-1. gd\_grid.php 逐行解释

| 行 || 说明 |
| --- | --- |
| 2 || 为图像定义 301 像素的高度（以便网格的最后线可见）。 |
| 3 || 为图像定义 301 像素的宽度。 |
| 4 || 使用 `ImageCreate()` 函数创建基础图像，指定之前定义的高宽。 |
| 5 || 使用 `ImageColorAllocate()` 定义变量 `$white`。参数允许白色（RGB 值 255,255,255）被 `$image` 使用。它也被用作 `$image` 的背景颜色，因为它是分配给 `$image` 的第一个颜色。 |
| 6 || 定义蓝色并允许被 `$image` 使用。 |
| 7 || 定义红色并允许被 `$image` 使用。 |
| 8–13 || 创建一个 `for` 循环，从坐标 0,0（图像左上角）开始每 20 像素绘制一条线。 |
| 9 || 在 `for` 循环中，在 `$image` 内部创建从点 `$i, 0` (0,0 20,40...) 到点 `$i, $height` (0,301 20,301...) 的线。循环的每次迭代从图像顶部到底部绘制一条垂直线，左右间距为 20 像素。 |
| 10 || 在 `for` 循环中，在 `$image` 内部创建从点 0, `$i` (0,0 20,40...) 到点 `$width, $i` (301,0 301,20 301,40...) 的线。循环的每次迭代从图像左侧到右侧绘制一条水平线，上下间距为 20 像素。 |
| 11 || 在 `for` 循环中，使用 `ImageString()` 函数创建一个小标签来显示当前垂直线的当前像素。记住 `ImageString($image, $fontsize, $x, $y, $text, $color);`。 |
| 12 || 在 `for` 循环中，创建一个小标签来显示当前水平线的当前像素 `ImageString()` 函数。 |
| 13 || 结束 `for` 循环。 |
| 14–18 || 在屏幕上不同位置创建文本以显示不同的字体。 |
| 19 || 将图像头发送到用户的浏览器。 |
| 20 || 显示你创建的图像 `$image`。 |
| 21 || 从服务器内存中销图像，因为它已经发送到了浏览器。 |





| 行号 | 描述 |
| :--- | :--- |
| 7 | 将字体文件赋值给变量 `$font`。你需要将此字体文件放置在执行此脚本的相同目录中。在 Windows 中，你通常可以在 `C:\Windows\Fonts` 或 `C:\WINNT\fonts` 中找到 TrueType 字体文件。你可以使用任何 TrueType 字体文件；只需确保复制到脚本相同目录下的 TrueType 字体文件名在此处定义即可。 |
| 8 | 将一个简单的文本字符串赋值给变量 `$text`。你可以使用 `\n\r` 语法进行换行和回车。某些 *nix* 系统不需要 `\r`。 |
| 9 | 使用 `ImageTTFText()` 函数向 `$image` 添加文本。 |
| 10 | 将图像头信息发送到用户的浏览器。 |
| 11 | 显示你创建的图像 `$image`。 |
| 12 | 从服务器内存中销毁图像，因为它已经发送到了浏览器。 |

#### 在基础图像上添加文本

GD 的另一个用处在于，你可以导入一张现有图像并作为新图像的基础进行处理。例如，你可以取一个空白的按钮图像，然后在其上叠加文本。通过这种方式，你只需要一个基础图像文件就可以创建出多个按钮。

要创建一个按钮，你需要使用两个新的 GD 函数。这些函数是 `ImageCreateFromPNG()` 和 `ImageTTFBbox()`。

`ImageCreateFromPNG()` 是一个非常简单的函数，它只需从现有的 PNG 文件创建一个新图像：

```php
$image = ImageCreateFromPNG("blank_blue_bttn.png"); 
```

然后，你可以像使用 `ImageCreate` 创建图像一样一样操作 `$image`。

你可以通过分别使用 `ImageSX($image)` 和 `ImageSY($image)` 函数，通过 `ImageCreateFromPNG()` 函数获取你创建的 `$image` 的长度和宽度；`SX` 和 `SY` 分别代表图像 X 轴的大小（宽度）和 Y 轴的大小（高度）。

`ImageTTFBbox()` 函数是一个相当复杂的函数，它返回文本周围边界框（bounding box）的角点坐标。你提供文本的大小、角度、字体和文本字符串，该函数以数组的形式返回角点坐标。该数组允许你计算文本占用了多少空间。脚本的用法如下：

```php
$textbox = ImageTTFBbox($size, $angle, $font, $text); 
```

[表 11-2] 列出了 `ImageTTFBbox()` 函数返回的数组中每个元素的坐标。此外，[图 11-4] 提供了边界框中数组元素的图形化表示。

##### 图 11-4. 边界框坐标的数组元素

![graphics/11fig04.gif](img/11fig04.gif)

##### 表 11-2. ImageTTFbox() 返回的坐标

| 数组位置 | 边界框坐标 |
| :--- | :--- |
| 0 | 左下角的 X 坐标 |
| 1 | 左下角的 Y 坐标 |
| 2 | 右下角的 X 坐标 |
| 3 | 右下角的 Y 坐标 |
| 4 | 右上角的 X 坐标 |
| 5 | 右上角的 Y 坐标 |
| 6 | 左上角的 X 坐标 |
| 7 | 左上角的 Y 坐标 |

接下来的脚本演示了如何获取空白按钮并在许多不同的按钮上添加文本。输出示例请参见 [图 11-5]。

##### 脚本 11-3 gd_button.php

```php
<?
$image = ImageCreateFromPNG("blank_blue_bttn.png"); 
$white = ImageColorallocate($image, 255, 255, 255);
$font = "arial.ttf";
$size = 20;
$angle = 0;
$text = "BUTTON";
$textbox = ImageTTFBbox($size, $angle, $font, $text);
$textbox_width = $textbox[2] - $textbox[0];
$textbox_height = $textbox[7] - $textbox[3];
$x = (imagesx($image) - $textbox_width) / 2;
$y = (imagesy($image) - $textbox_height) / 2 + $textbox_height;
header("Content-type: image/png");
imageTTFText($image, $size, $angle, $x, $y, $white, $font, $text);
imagepng($image);
imagedestroy($image);
?>
```





你也可以使用 HTML `<<img>>` 标签在页面上调用多个按钮，并通过对 "text" 使用不同的值来引用同一个脚本，如下面的短脚本所示。示例输出请参见图 11-7。

### 脚本 11–4 buttons.html

```
1.  <html>
 2.  <head>
 3.    <title>Buttons!</title>
 4.  </head>
 5.  <body><body>
 6.  <img src="gd_button.php?text=HOME"><br>
 7.  <img src="gd_button.php?text=GAMES"><br>
 8.  <img src="gd_button.php?text=NEWS"><br>
 9.  <img src="gd_button.php?text=LINKS">
10.  </body>
11.  </html>
```

### 图 11-7. buttons.html

![graphics/11fig07.jpg](img/11fig07.jpg)

### 使用 GD 创建矩形

除了文本和线条外，你还可以轻松使用 GD 创建矩形，可以是填充颜色的，也可以是不填充的（使用相同的参数调用 `ImageRectangle()` 来创建不填充矩形）：

```
ImageFilledRectangle($image, $x1coord, $y1coord, $x2coord, $y2coord, $color); 
```

`ImageRectangle()` 和 `ImageFilledRectangle()` 的参数如下：

* `$image`— 正在放置此矩形的图像的句柄。
* `$x1coord`— 矩形左上角的 x 坐标。
* `$y1coord`— 矩形左上角的 y 坐标。
* `$x2coord`— 矩形右下角的 x 坐标。
* `$y2coord`— 矩形右下角的 y 坐标。
* `$color`— 矩形的颜色。必须是之前分配给 `$image` 的颜色。

矩形从左上角到右下角绘制。请记住，坐标 `0,0` 起于图像的左上角，而不是像数学绘图中那样从右下角开始。

下一个脚本使用线条、文本和矩形来创建一个动态条形图。你可以将各种数值输入图表，并为图像指定尺寸和标签。图表会根据你输入的数值自动调整比例。图 11-8 展示了该图表输入界面。

### 脚本 11–5 gd_graph.php

[[查看全宽视图]](&r=noccc&xmlid=0-13-008539-1/ch11lev1sec4#PLID13) 

```
1.  <?
 2.  if(!isset($render)) {
 3.          ?>
 4.          <form action=gd_chart.php method=post>
 5.          <br>数值（用逗号分隔的数字）：
 6.          <br><textarea cols="40" rows="4" name="values_in">50,100,150,75,23,55,200,135,63,103</textarea>
 7.          <br>标签（用逗号分隔的标签）：
 8.          <br><textarea cols="40" rows="4" name="labels_in">Jan,Feb,Mar,Apr,May,Jun,Aug,Sep,Nov,Dec</textarea>
 9.         <br>图像高度：<input type="text" name="height" value="500">
 10.          <br>图像宽度：<input type="text" name="width" value="500">
 11.          <br>纵轴标签：<input type="text" name="vlabel" value="产量">
 12.          <br>横轴标签：<input type="text" name="hlabel" value="月份">
 13.          <br><input type="submit" name="render" value="渲染图表">
 14.          </form>
 15.          <?
 16.  else {
 17.  $values = explode(",", $values_in);
 18.  $labels = explode(",", $labels_in);
 19.  $xoffset = $width / 10;
 20.  $yoffset = $height / 10;
 21.  /* 确定字体大小 */
 22.  if (($width > 400) and ($height > 400)) {
 23.          $sm_font = 2;
 24.          $md_font = 3;
 25.          $lg_font = 4;
 26.  } else {
 27.          $sm_font = 1;
 28.          $md_font = 2;
 29.          $lg_font = 2;
 30.  }
 31.  /* 创建基础图像 */
 32.  $image = ImageCreate($width, $height);
 33.  /* 分配颜色 */
 34.  $white = ImageColorAllocate($image, 235, 235, 235);
 35.  $blue = ImageColorAllocate($image, 0, 0, 255);
 36.  $red = ImageColorAllocate($image, 255, 0, 0);
 37.  /* 查找数值中的最大值 */
 38.  $greatest = 0;
 39.  for($i = 0; $i < count($values); $i++) {
 40.          $values[$i] = trim($values[$i]);
 41.          if($values[$i] > $greatest)
 42.                  $greatest = $values[$i];
 43.  }
 44.  /* 确定比例和间距 */
 45.  $scale = ($height / $greatest) * .8;
 46.  $h_spacing = floor(($width - $xoffset) / count($values)) / 2;
 47.  $barwidth = $h_spacing;
 48.  /* 绘制条形、标签和数值 */
 49.  $x = $xoffset + 5;
 50.  for($i = 0; $i < count($values); $i++) {
 51.          $y = $height - ($values[$i] * $scale);
 52.          ImageFilledRectangle($image, $x, $y - $yoffset, $x + $barwidth, $height - $yoffset, $red);
 53.          ImageString ($image, $sm_font, $x, $y-$yoffset-12, $values[$i], $blue);
 54.          $labels[$i] = trim($labels[$i]);
 55.          ImageString ($image, $md_font, $x, $height - $yoffset + 2, $labels[$i], $blue);
 56.          $x+=($h_spacing * 2);
 57.  }
 58.  /* 确定刻度 */
 59.  $ticks_every = "1";
 60.  for($i = 1; $i < round(log10($greatest)); $i++) {
 61.          $ticks_every .= "0";
 62.  }
 63.  /* 绘制刻度和数字 */
 64.  for($i = 0; $i < $height - $yoffset; $i+= $ticks_every * $scale) {
 65.          $y = ($height - $yoffset) - $i;
 66.          ImageLine($image, $xoffset / 2, $y, $xoffset, $y, $blue);
 67.          ImageLine($image, $xoffset + 5, $y, $width + $xoffset, $y, $white);
 68.          ImageString ($image, $sm_font, $xoffset / 2, $y, $i / $scale , $blue);
 69.  }
 70.  /* 绘制图图的左侧和底部边缘 */
 71.  ImageLine($image, 0 + $xoffset, 0, $xoffset, $height - $yoffset, $blue);
 72.  ImageLine($image, 0 + $xoffset, $height - $yoffset, $width, $height - $yoffset, $blue);
 73.  }
 74.  header ("Content-type: image/png");
 75.  ImagePNG($image);
 76.  ImageDestroy($image);
 77.  ?>
```

### 图 11-8. graph.php 提交值之前

![graphics/11fig07.jpg](img/11fig07.jpg)

### 脚本 11-5 gd_graph.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2 | 检查 `$render` 变量是否设置。如果没有，执行 3–15 行，否则从 16 行到结束。 |
| 3–15 | 输出一个标准的 HTML 表单以请求某些值。你可以指定：br>* 条形图的数值，用逗号分隔。你应该为表单中的每个值准备一个标签。<br>* 图表的宽度和高度。<br>* 比例标签。<br>脚本输入了一些默认值进行测试。 |
| 17 | 将表单中输入的数值转换为数组，使用 `explode()` 函数并将数组赋值给 `$values` 变量。 |
| 18 | 将表单中输入的标签转换为数组，使用 `explode()` 函数并将数组赋值给 `$labels` 变量。 |
| 19 | 确定 x 轴偏移，它是图表总宽度的 1/10。该偏移为图表左侧留出了文本空间。1/10 是一个适用于宽度大于 300 像素图表的任意数字。 |
| 20 | 确定 y 轴偏移，它是图表总高度的 1/10。该偏移为图表底部留出了文本空间。 |
| 22–30 | 确定图表合适的字体大小。图表使用三种尺寸：小、中、大。如果图表小于 400x400，则使用较小的字体。否则使用较大的字体。 |
| 32 | 使用从表单获取的宽度和高度创建基础图像。 |
| 34–36 | 为图像分配三种颜色：白色、蓝色和红色。这里的白色（RGB: 235,235,235）实际上是浅灰色，以便图表从页面中脱颖而出。 |
| 38 | 将变量 `$greatest` 初始化为 0。 |





- **39–43**: 使用 `for` 循环遍历 `$values` 数组并找到最大值。一旦确定了需要绘制的最大数值，我们就可以确定图表的比例。请注意，在第 40 行，脚本会修剪数值值中的任何空格。这是为了避免用户在表单中输入数值时，除了逗号外还使用了空格分隔数值而导致错误。
- **45**: 通过将最大值除以高度并乘以 80% 来确定图表的比例。这创建了一个比例，使得图上最大的条形能够占据高度的 80%。
- **46**: 确定图表中每个条形的水平间距。计算方法是将宽度减去宽度偏移量（得到条形可用的总空间），四舍五入，然后除以需要绘制的数值个数，最后将该数字除以 2，因为我们想要创建一个等距的空间与条形比例。
- **47**: 确定条形的宽度。在这里将其设置为与间距相同，但你可能会发现需要根据特定的图表对其进行微调。如果你对其了修改，请考虑到上面的一行分配了一半的空间给间距。你可能也需要修改那一行。
- **49**: 初始化变量 `$x` 为偏移量加 5 像素。这允许第一个条形距离你分配给文本的边缘边缘 5 像素。
- **50–57**: 创建一个 `for` 循环遍历 `$values` 数组并在条形图上绘制条形。
- **51**: 确定条形的基 y 坐标。这有点复杂，因为脚本会根据最大值的大小自动调整条形的显示比例。要确定基础 y 坐标，你需要用数值乘以比例的结果减去高度。如果数值为 10，那么它会被缩缩小为 8。然后你减去 `y offset`（用于底部文本留出的额外空间）和图像的总高度（因为 `GD` 库使用图像的左上角作为 `0,0` 点，而不是左下角）。脚本计算的是条形应该从图像**顶部**多远开始，而不是条形实际有多长（当然，那样会更简单，但 `GD` 库似乎不让你那样做）。
- **52**: 使用 `ImageFilledRectangle()` 函数创建条形。前两个坐标参数（`$x` 和 `$y`）绘制矩形的左上角。后两个坐标参数（`$x + $barwidth` 和 `$height – $yoffset`）绘制矩形的右下角。
- **53**: 使用 `ImageString()` 函数在条形上方写入条形的数值。y 坐标列为 `$y – 12`，以便将数值写在条形本身上方 12 像素处。记住，脚本计算的是文本应该距离图像顶部多远，而不是距离条形顶部多远。
- **54**: 使用 `trim()` 函数修剪标签周围的任何空格。
- **55**: 在条形底部写入当前条形的标签。注意 y 坐标是 `$height – $yoffset + 2`。这会将标签放置在图像底部空白区域上方第 2 像素处。
- **56**: 增加下一个 x 坐标的值，以便为条形之间留足够的空间。如果你想调整间距，除了第 46 行和 47 行外，还需要修改此行。请注意，在大多数情况下，这里的编码方式应该正常工作。
- **57**: 关闭 `for` 循环。
- **59**: 初始化变量 `$ticks_every`。
- **60–62**: 创建一个 `for` 循环来确定条形上刻度线的比例。刻度线实际上是与图像背景颜色相同的线。它们绘制在条形上，使条形看起来像是等分的线段。由于你可能拥有几十或几千的数值，你可能不会自动希望每隔 10 个单位就有一个刻度线。此处的 `for` 循环是确定刻度线之间间隔多少个“刻度”的一种简单方法。它获取最大值并计算该值的 `log10`。每当执行且值小于 `$i` 时，就会向 `$ticks_every` 函数中添加一个“0”。基本上，如果最大值在 1 到 316 之间，则每 10 个刻度有一条线（不一定是像素，因为你需要考虑缩放）。从 316 到 3162，每 100 个刻度使用一个刻度线，以此此类推。这并不是精确的科学，但它能提供相当好的结果。
- **64–69**: 创建一个 `for` 循环在条形上绘制“刻度”标记，并在图表的 y 轴上根据 `$ticks_every` 定义的间隔间距绘制数字。
- **65**: 计算刻度线的 y 坐标。
- **66**: 在偏移量左侧绘制一条短线。这条蓝色短线用作图表 y 轴显示的数值比例之间的分隔符。
- **67**: 绘制一条横跨图像的长线，将条形分为等距易读的段。
- **68**: 在图表的 y 轴左侧显示“刻度”数字。
- **69**: 关闭 `for` 循环。
- **71**: 在图像底部绘制蓝色 x 轴线（条形与其标签之间）。
- **72**: 在图像右侧绘制蓝色 y 轴线（数字与条形之间）。
- **74**: 显示 x 轴标签。默认情况下，它是“月份”。
- **75**: 显示 y 轴标签。默认情况下，它是“产量（千件）”。
- **77**: 向用户的浏览器发送图像头信息。
- **78**: 显示你创建的图像 `$image`。
- **79**: 从服务器内存中销毁图像，因为它已经发送到了浏览器。
- **80**: 关闭在第 2 行开始的 `if` 语句。

图 11-9 显示了脚本的示例输出。





PHPGTK 使用 `GTK+` 来绘制任何 GUI 应用程序所需的“小部件”（widgets）。组件包括滚动条、文本输入框和按钮等。当你启动几乎任何 Windows 应用程序（如 Web 浏览器）时，你看到的就是一组组件。

组件需要被包含在某种框架中才能变得有用且符合逻辑。你不能简单地将许多按钮和文本框随机散布在屏幕上。为了解决这个问题，我们使用一种称为 `container`（容器）的特殊组件。容器是另一种结构，可以按照你认为最适合应用程序的方式来组织组件。例如，大多数应用程序顶部的菜单栏就是一个容器。

组件具有许多不同的属性，控制它们的外观和行为。每种类型的组件都有其独特的属性集，此外还包含与其他组件共有的属性。

当组件被激活时，它们会向你的程序发送信号。组件激活的一个示例是用户点击按钮。一旦组件发送了信号，你通常用回调（callback）来响应该信号。回调基本上只是一个函数。某些信号最终会被 GTK 自动处理的回调处理（默认处理程序）。其他信号则执行你的函数之一（用户定义处理程序）。用户定义的函数是用 PHP 编写的。

在编写本文文档时，PHPGTK 的当前版本是 `0.5.1`，于 2002 年 4 月 26 日发布。尽管处于早期阶段，但 PHPGTK `0.5.1` 比原始的 `0.1` 版本有了巨大的改进。

PHPGTK 非常复杂。它基本上是将两种完整的语言结合在一起。这一章无法希望详细解释可用的许多方法和类，但我希望在空间允许范围内提供 PHPGTK 的总体概览。请访问 PHPGTK 网站 [`gtk.php.net`](http://gtk.php.net) 获取丰富信息！

***

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm)   ![上一节](img/#ch12_split_000.htm)   ![下一节](img/#ch12lev1sec2.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm)   ![上一节](img/#ch12lev1sec1.htm)   ![下一节](img/#ch12lev1sec3_split_000.htm) |

***

### 安装 PHPGTK

在开始使用 PHPGTK 之前，你需要下载适当的文件。PHPGTK 团队在 [`gtk.php.net`](http://gtk.php.net) 建立了一个非常好的网站。PHPGTK 网站提供了 GTK 扩展的下载内容和文档。

#### 在安装之前

PHPGTK 尚未达到 `1.0` 版本，因此我不建议你在生产环境 Web 服务器上使用此版本的 PHP。事实上，你并没有理由想在生产环境 Web 服务器上安装 PHPGTK。它是一个客户端应用程序！

PHPGTK 目前只是是开发者的玩具，任何内容都可能发生变化，至少在 PHPGTK 达到 `1.0` 版本之前如此。尽情玩它，尝试一下，但不要将公司的下一个大产品建立在 PHPGTK `0.5.0` 上。

#### 在 Windows 上安装

在 Windows 机器上安装 PHPGTK 非常简单，类似于安装普通版本的 PHP。从 PHPGTK 网站 [`gtk.php.net`](http://gtk.php.net) 下载 Windows 二进制文件。

使用压缩工具解压文件。将文件解压到你的 `C:` 盘。

解压文件后会创建以下文件夹：
* `php4`——包含 PHP 可执行文件以及一些 GTK 库文件。
* `test`——包含一些使用组件的示例 *.php 文件。

如果你使用的是 Windows 98 或 Windows ME，你会发现了名为 `winnt` 和 `winnt/system32` 的文件夹。你应该将这些文件夹的内容拷贝到 `C:\windows` 目录。注意，你可能需要将系统文件设置为可见，以便将它们复制到 `C:\windows`。

此外，你应该看到一个新的 `php.ini` 文件。将其拷贝到 `C:\Windows` 或 `C:\WINNT` 目录。务必先备份现有的 `php.ini` 文件。

在命令提示符中输入以下内容来测试安装：

```
c:\php4\php.exe -q c:\test\gtk.php
```

查看图 12-1 中 `gtk.php` 运行的。

##### 图 12-1 Linux (Gnome) 和 Windows 2000 中的 gtk.php

![graphics/12fig01.jpg](img/12fig01.jpg)

#### 在 Linux 上安装

在 Linux 上安装 PHPGTK 比安装普通 PHP 更简单；你不需要担心 Apache。你可以将 GTK 功能编译到独立的 PHP 版本中，但为了我们，我们将从零开始创建一个内置 GTK 功能的新 PHP 可执行文件。在开始之前：
1. 从 [www.php.net](http://www.php.net) 下载 PHP 源码。
2. 从 [`gtk.php.net`](http://gtk.php.net) 下载 PHPGTK 源码。

一旦获得需要的文件，解压普通的 PHP 源码：

```bash
tar -zxvf php-4.x.tar.gz
```

这创建了一个名为 `php-4.x` 的新目录，“x”表示你下载的 PHP 具体版本号。

使用最小选项编译 PHP。我们只是想创建一个独立的可执行文件。如果你想添加额外功能，以后可以重新编译。进入新创建 PHP 源码目录。输入：

```bash
./configure
```

就这些。这会自动创建一个内置 MySQL 支持的可执行文件。

一旦你获得 `php` 二进制文件，必须将其拷贝到 `/usr/local/bin`。PHPGTK 安装将在该位置查找它。你需要 root 权限执行此操作。

```bash
cp php /usr/local/bin
```

现在该将 GTK 扩展构建到你的 PHP 了。回到下载 PHPGTK 源码的地方并提取它：

```bash
tar -zxvf php-gtk-0.5.0.tar.gz
```

这创建了一个名为 `php-gtk-0.5.0` 的目录。进入该目录。你需要 root 权限执行最后一步 `make install`。编译 PHPGTK 输入以下内容（输入每个命令后屏幕上将打印大量文本）：
1. `./configure`
2. `make`
3. `make install`

你可以通过进入 test 目录并运行几个脚本来测试安装。需要运行 X-Windows！

```bash
cd test
php -q gtk.php
```

应该弹出一个显示各种组件按钮的窗口。点击不同的组件来简单了解它们的功能。

图 12-1 显示了 gtk.php 文件在 Linux（使用 Gnome 桌面）和 Windows 2000 中的外观。

你也可以尝试运行 test 目录中的其他 *.php 文件。使用 `-q` 标志来抑制在屏幕上打印头部信息。

***

| ![](img/pixel.gif) |
| --- |
| ![](img/#index.htm)   ![上一节](img/#ch12lev1sec1.htm)   ![下一节](img/#ch12lev1sec3_split_000.htm) |
| 回到顶部 |
| --- |
| ![](img/#index.htm)   ![上一节](img/#ch12lev1sec2.htm)   ![下一节](img/#ch12lev1sec4.htm) |

***

### 创建基础 GTK 对象

GTK+ 扩展是 PHP 的面向对象编程 (OOP) 扩展。你需要使用 OOP 语法和结构来使用 GTK+ 库。如果你还没有这样做，你可能想回到第 1 章 复习关于 PHP 中 OOP 的材料。

#### 创建你的第一个 PHPGTK 窗口





在创建任何 PHPGTK 应用程序之前，你必须告诉 PHP 你想要使用哪种 GTK 库。由于 GTK 可以在 Windows 和多种版本的 UNIX 上运行，这留下了两种类型的库。Windows 使用动态链接库，也称为 DLLs。大多数基于 *nix 的操作系统使用 `.so` 库。由于你希望你的应用程序可以在不修改的情况下在两类操作系统上运行，你必须提供一种动态加载库的方法。这种方法的标准方法是：

```
if (!class_exists('gtk')) { 
if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
      dl('php_gtk.dll');
else
      dl('php_gtk.so');
}
```

## 注意
如果你打算让脚本运行在 Linux 或 Windows 以外的平台（如果 PHPGTK 的后续版本增加了对这些其他平台的支持），那么你必须确保以上述相同的方式加载正确的 PHPGTK 库。

## 主窗口
任何 PHPGTK 应用程序的核心部分都是主窗口。你创建的每个应用程序都应该有一个主窗口作为容器，你可以在其中放置其他组件（widgets）。

PHPGTK 中的基本窗口类是 `GtkWindow()`。你像这样创建一个新窗口对象：

```
$window = &new GtkWindow(); 
```

现在你有了一个窗口，你必须提供一种销毁该窗口的方法。在大多数操作系统中，用户可以通过点击窗口右上角的“X”来销毁窗口（某些 Linux 桌面提供了不同的控制控件）。

当你点击 PHPGTK 应用程序中的“X”时，会有两个信号被发送到应用程序。这些信号是 `delete_event` 和 `destroy`。现在我们只关注 `destroy` 信号。

信号通常是用户输入，而回调函数（callbacks）是你创建的用于响应用户输入并执行某些操作的函数。然而，你需要将信号连接到回调函数。要做到这一点，你使用 `connect()` 方法。为了将 destroy 信号连接到我们的 destroy 回调函数：

```
$window->connect('destroy','destroy'); 
```

第一个参数是 PHPGTK 发送的信号名称。第二个参数是你想要在响应信号时调用的函数（回调）名称。为了简单起见，我们将该函数（回调）命名为 'destroy'。

```
function destroy() { 
Gtk::main_quit();
}
```

`Gtk::main_quit()` 是杀死应用程序的 PHPGTK 函数。

现在我们创建了一个窗口，并为用户提供了移除窗口的方法。但我们仍然无法运行应用程序。PHPGTK 还需要完成另外两件事。首先，我们需要显示窗口。你通过调用 `show_all()` 方法来显示窗口：

```
$window->show_all(); 
```

最后，你需要通过调用特殊的 PHPGTK 函数 `main()` 来启动事件序列（轮询事件？）：

```
Gtk::main(); 
```

## 注意
使用 PHPGTK 时，必须使用完整的 `<?php` 标签开始你的脚本。使用简写形式 `<?` 可能会导致 PHPGTK 仅仅将整个脚本输出到屏幕上，而不是创建一个 GTK 窗口。

## 完整脚本示例
当我们将所有内容整合在一起时，你就会得到 `basic_window.php`。

### 脚本 12-1 basic_window.php
```
1.  <?php
 2.    if (!class_exists('gtk')) {
 3.    if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
 4.      dl('php_gtk.dll');
 5.    else
 6.      dl('php_gtk.so');
 7.  }
 8.  function destroy(){
 9.    Gtk::main_quit();
10. }
11.   $window = &new GtkWindow();
12.   $window->connect('destroy','destroy');
13.   $window->show_all();
14.  Gtk::main();
```

### 12-1. basic_window.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 1 | 如果 'gtk' 类尚未定义， |
| 2 | 如果。 |
| 3 | 检查 PHP_OS 的前三个字符。 |
| 4 | 如果是 WIN，则加载 php_gtk.dll。 |
| 5 | 否则， |
| 6 | 加载 php_gtk.so。 |
| 7 | 结束 if。 |
| 8 | 定义 destroy() 函数： |
| 9 | 调用 Gtk::main_quit()。 |
| 10 | 结束函数。 |
| 11 | 创建一个新的 GtkWindow 对象。 |
| 12 | 将 destroy 信号连接到 destroy 回调。 |
| 13 | 显示所有窗口。 |
| 14 | 启动 Gtk 主循环。 |

## 添加 GTK 按钮
为了增强我们的 Hello World 程序，让我们添加一个按钮。

### 脚本 12-2 hello.php
```
1.  <?php
 2.    if (!class_exists('gtk')) {
 3.    if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
 4.      dl('php_gtk.dll');
 5.    else
 6.      dl('php_gtk.so');
 7.  }
 8.  function destroy(){
 9.    Gtk::main_quit();
10. }
11.  function hello(){
12.    global $window;
13.    print "Hello World!\n";
14.    $destroy();
15.  }
16.  $window = &new GtkWindow();
17.  $window->connect('destroy','destroy');
18.  $button = &new GtkButton('Hello World!');
19.  $button->connect('clicked', 'hello');
20.  $window->add($button);
21.  $window->show_all();
22.  Gtk::main();
23.  ?>
```

### 图 12-3. hello.php 在 Linux (Gnome)
![graphics/12fig03.jpg](img/12fig03.jpg)

### 脚本 12-2. hello.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2–7 | 与 basic_window.php 相同。 |
| 8–10 | 与 basic_window.php 相同。 |
| 11–15 | 定义 hello()，它打印 "Hello World!" 并调用 destroy()。 |
| 16–17 | 与 basic_window.php 相同。 |
| 18 | 创建一个带有 "Hello World!" 标签的新 GtkButton。 |
| 19 | 将按钮的 clicked 信号连接到 hello 函数。 |
| 20 | 将按钮添加到窗口。 |
| 21 | 显示所有窗口。 |
| 22 | 启动 Gtk 主循环。 |





| 19 | 将按钮的 'clicked' 方法连接到 `hello()` 函数。 |
| 20 | 使用 `add()` 方法将按钮添加到窗口中。 |
| 21 | 对 `$window` 对象调用 `show_all()` 函数，以便显示对象内的所有内容。 |
| 22 | 调用 `Gtk::main()` 方法运行脚本。 |

#### 修改基础小部件的外观

创建按钮和窗口的语法看起来非常相似。这是因为它们都是 GTK 小部件（widget）类。每个对象（按钮、窗口等）都有某些可用的方法——例如，`connect()` 方法。

如果你运行 `hello.php` 脚本，你会发现窗口尺寸非常小——事实上，它的 own 只和内部的按钮一样大。这是因为 PHP 在创建窗口时将其缩小到最小尺寸。我们可以通过一些方法来修改 `GtkWindow` 小部件的默认外观。例如，如果你想为窗口设置默认大小，可以使用 `set_default_size($width, $height)` 方法：

```
$window->set_default_size(200,200); 
```

这将创建一个 200 像素乘 200 像素的窗口。你还可以设置窗口标题：

```
$window->set_title("My PHPGTK APP"); 
```

图 12-4 显示了通过 `set_default_size()` 和 `set_title()` 方法修改的窗口。

##### 图 12-4. 使用属性方法修改的窗口（Linux 和 Windows）

![graphics/12fig04.jpg](img/12fig04.jpg)

有很多可用方法可以影响 GTK 小部件的外观和行为。详情请参阅 [http://gtk.php.net] 上的这些方法的文档说明。

#### 文本输入

如果不能向桌面应用程序插入数据，它将非常不利。GTK 提供了一个文本输入小部件，允许你向应用程序输入一行文本。创建一个文本输入字段：

```
$text1 = &new GtkEntry(); 
```

如果没有某种方法为其标记，否则文本输入字段并没有真正的用处。这时 `GtkLabel` 就派上用场了：

```
$label1 = &new GtkLabel("A Text Entry Field:"); 
```

现在我们已经有了新的文本输入字段和标签，我们需要将其放入窗口中。但这里有一个小问题。你不能直接向顶层窗口 `add()` 多个小部件。相反，你需要在窗口中放置一个框（box），然后将你的子对象添加到该框中。

#### hbox 和 vbox

有两种类型的框可以用于将你的小部件固定在主窗口的相应位置。它们是 `hbox`（水平）和 `vbox`（垂直）。正如名称所示，`hbox` 允许你将对象放入其中并使其对象水平对齐，而 `vbox` 允许你将对象放入其中并使其对象垂直对齐。由于我们想让文本输入字段和标签水平对齐（像普通应用程序那样），我们将创建一个 `hbox` 并将其添加到窗口中：

```
$box = &new GtkHBox();
$window->add($box);
```

`hbox` 和 `vbox` 小部件是特殊的容器，可以向其中添加多个小部件。要添加它们，你需要将小部件“打包”（pack）到框中：

```
$box->pack_start($label1, false, 0);
$box->pack_start($text1, false, 0);
```

#### pack_start

`pack_start` 方法允许你将小部件添加到框中。如果你将小部件打包到 `vbox`，`pack_start` 会从框的顶部添加小部件。每当你向框中打包另一个小部件时，前一个部件向下移动，新添加的小部件位于 `vbox` 的顶部。如果你将小部件打包到 `hbox`，`pack_start` 会从左侧添加小部件。每当你向框中打包一个新的小部件时，它会被放置在上一个对象的右侧。

`pack_start()` 方法接受四个参数：

- 你正在打包的对象。
- 如果调整框 尺寸，是否扩展该对象（true 或 false）。
- 对象是否应该填充其可用空间（true 或 false）。
- 对象周围使用的内边距（padding）量（整数）。

如果没有指定，使用的默认参数为 `true`、`true`, `0`。这意味着扩展、填充且不使用内边距。让我们来看使用标签和文本输入的脚本。参见下方的 脚本 12-3，`text_entry.php`。示例请参见 图 12-5。

##### 脚本 12-3 text_entry.php

```
<?php
if (!class_exists('gtk')) {
  if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
    dl('php_gtk.dll');
  else
    dl('php_gtk.so');
}
function destroy(){
  Gtk::main_quit();
}
$window = &new GtkWindow();
$window->connect('destroy', 'destroy');
$text1 = &new GtkEntry();
$label1 = &new GtkLabel("A Text Entry Field:");
$box = &new GtkHBox();
$window->add($box);
$box->pack_start($label1, false, 0);
$box->pack_start($text1, false, 0);
$window->show_all();
Gtk::main();
?>
```





```php
1.  <?php
 2.    if (!class_exists('gtk')) {
 3.    if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
 4.      dl('php_gtk.dll');
 5.    else
 6.      dl('php_gtk.so');
 7.  }
 8.  function destroy(){
 9.    Gtk::main_quit();
10.  }
 11.  function submit(){
 12.    global $text1;
 13.    $input = $text1->get_text();
 14.    echo $input . "\n";
 15.    $text1->set_text('');
 16.  }
 17.  $window = &new GtkWindow();
 18.  $window->connect('destroy', 'destroy');
 19.  $window->set_border_width(5);
 20.  $text1 = &new GtkEntry();
 21.  $label1 = &new GtkLabel("A Text Entry Field");
 22.  $button1 = &new GtkButton('Submit Text!');
 23.  $button1->connect('clicked', 'submit');
 24.  $box = &new GtkHBox();
 25.  $window->add($box);
 26.  $box->pack_start($label1, false, false, 0);
 27.  $box->pack_start($text1, false, false, 0);
 28.  $box->pack_start($button1, false, false, 0);
 29.  $window->show_all();
 30.  Gtk::main();
 31.  ?>
```

### 图 12-6. text_submit.php

![graphics/12fig06.jpg](img/12fig06.jpg)

### 脚本 12-4. text_submit.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2 | 如果 GTK 类尚未定义，则执行第 3–7 行。如果 GTK 类已经定义，则脚本无需执行任何操作。 |
| 3 | 检查 `PHP_OS` 环境变量的前三个字符。 |
| 4 | 如果是 WIN，说明系统运行在 Windows 上。加载 Windows 版本的 PHPGTK 库。 |
| 5–7 | 如果 `PHP_OS` 环境变量不是 WIN，则假设 PHP 运行在 Linux 系统上并加载 Linux 版本的 PHPGTK 库。 |
| 8–10 | 定义一个函数 `destroy()`，在被调用时停止脚本。 |
| 9 | 执行 `Gtk::main_quit()` 方法以停止脚本并关闭 GTK 窗口。 |
| 10 | 结束函数声明。 |
| 11–16 | 定义一个函数 `submit()`，将用户输入的文本输出到标准输出（STDOUT）。 |
| 12 | 允许此函数访问变量 `$text1`。 |
| 13 | 通过调用 `$text1` 对象的 `get_text()` 方法，将用户输入的文本赋值给变量 `$input`。
| 14 | 带有换行符将用户输入的文本输出到标准输出。 |
| 15 | 通过调用 `$text1` 对象的 `set_text()` 方法并将新文本赋值为 `''`，清空输入中的用户文本。 |
| 16 | 结束函数声明。 |
| 17 | 创建名为 `$window` 的新窗口对象。 |
| 18 | 将 `'destroy'` 事件连接到 `destroy` 函数。 |
| 19 | 使用 `$window` 对象的 `set_border_width()` 方法设置 5 像素的边框。 |
| 20 | 创建名为 `$text1` 的文本输入对象。 |
| 21 | 创建名为 `$label1` 的标签对象，内容为“A Text Entry Field”。 |
| 22 | 创建名为 `$button1` 的按钮对象，内容为“Submit Text!”。 |
| 23 | 将 `'clicked'` 事件连接到 `submit` 函数。 |
| 24 | 创建名为 `$box` 的水平布局框（HBox）。 |
| 25 | 使用 `add()` 方法将 `$box` 添加到窗口。 |
| 26 | 将 `$label1` 对象打包到 `$box` 中。 |
| 27 | 将 `$text1` 对象打包到 `$box` 中。 |
| 28 | 将 `$button1` 对象打包到 `$box` 中。 |
| 29 | 对 `$window` 对象调用 `show_all()` 以显示所有内容。 |
| 30 | 调用 `Gtk::main()` 运行脚本。 |

### 对话框 (Dialog Boxes)

大多数 GUI 程序都能显示小窗口来通知用户错误或确认用户想要执行的操作。例如，当你尝试在不保存文档的情况下关闭应用程序时，大多数文字处理程序都会弹出“确定……”的对话框。PHPGTK 提供了 `GtkDialog` 类创建简单对话框的方法。

`GtkDialog` 类包含一个 `vbox`、一个分割和一个“操作区域”。你可以将文本放在 `vbox` 中，将按钮放在“操作区域”中。

下一个脚本演示了如何使用 `GtkDialog` 来确认用户是否想要退出应用程序。当用户点击“Quit”按钮或窗口右上角的“X”时，会显示一个对话框询问用户是否确定退出。如果用户点击对话框中的“OK”，应用程序将退出。如果用户点击“Cancel”或对话框右上角的“X”，对话框将关闭但应用程序仍保持打开。请参见图 12-7](#12fig07) 的示例输出。

### 脚本 12-5. dialog.php

```php
1.  <?php
2.  if (!class_exists('gtk')) {
3.    if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
4.      dl('php_gtk.dll');
5.    else
6.      dl('php_gtk.so');
7.  }
8.  function destroy() {
9.    Gtk::main_quit();
10.  }
11.  function close_dialog($button, $dialog){
12.    $dialog->destroy();
13.  }
14.  function delete_event(){
15.    confirm();
16.    return true;
17.  }
18.  function confirm(){
19.    global $window;
20.    $dialog = &new GtkDialog;
21.    $dialog->set_title("Are You Sure?");
22.    $dialog->set_default_size('100','100');
23.    $dialog->set_modal(TRUE);
24.    $dialog->set_transient_for($window);
25.    $dialog->set_policy(0,0,0);
26.    $label = &new GtkLabel("Are You Sure You To Quit?");
27.    $button_yes = &new GtkButton('OK');
28.    $button_yes->connect('clicked', 'destroy');
29.    $button_no = &new GtkButton('Cancel');
30.    $button_no->connect('clicked', 'close_dialog', $dialog);
31.    $vbox1 = $dialog->vbox;
32.    $vbox2 = $dialog->action_area;
33.    $vbox1->pack_start($label);
34.    $vbox2->pack_start($button_yes);
35.    $vbox2->pack_start($button_no);
36.    $dialog->show_all();
37.  }
38.  $window = &new GtkWindow();
39.  $window->connect('delete_event', 'delete_event');
40.  $button = &new GtkButton('Quit');
41.  $button->connect('clicked', 'confirm');
42.  $window->add($button);
43.  $window->show_all();
44.  Gtk::main();
45.  ?>
```

### 图 12-7. dialog.php—初始窗口和确认对话框

![graphics/12fig07.jpg](img/12fig07.jpg)

### 脚本 12-5. dialog.php 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2 | 如果 GTK 类尚未定义，则执行第 3–7 行。如果 GTK 类已经定义，则脚本无需执行任何操作。 |
| 3 | 检查 `PHP_OS` 环境变量的前三个字符。 |
| 4 | 如果是 WIN，说明系统运行在 Windows 上。加载 Windows 版本的 PHPGTK 库。 |
| 5–7 | 如果 `PHP_OS` 环境变量不是 WIN，则假设 PHP 运行在 Linux 系统上并加载 Linux 版本的 PHPGTK 库。 |
| 8–10 | 定义一个函数 `destroy()`，在被调用时停止脚本。 |
| 9 | 执行 `Gtk::main_quit()` 方法以停止脚本并关闭 GTK 窗口。 |
| 10 | 结束函数声明。 |
| 11–13 | 定义一个函数 `close_dialog()` 用于关闭对话框。该函数接收两个参数：`$button` 和 `$dialog`。参数的描述请参见第 30 行。 |
| 12 | 调用 `$dialog` 对象的 `destroy()` 方法以关闭对话框。 |
| 13 | 结束函数声明。 |
| 14–17 | 定义一个函数 `delete_event()`，捕获用户点击主应用程序窗口右上角“X”的操作并运行 `confirm()` 函数。`delete_event()` 是一个特殊方法，每当用户点击窗口右上角的“X”时都会运行。如果不使用 `delete_event` 连接点，则窗口将自动销毁。 |
| 15 | 执行 `confirm()` 函数以确保用户确实想要退出应用程序。 |





| 16 | 返回 true。如果你返回 false（当你没有为 `delete_event` 分配连接时，这是该事件的默认行为），则窗口将执行销毁。 |
| 17 | 结束函数声明。 |
| 18–37 | 定义一个函数 `confirm()`，用于确认用户想要退出应用程序。 |
| 19 | 允许此函数使用 `$window` 对象。 |
| 20 | 创建名为 `$dialog` 的新对话框对象。 |
| 21 | 设置对话框对象的标题。 |
| 22 | 将对话窗口的默认大小设置为 100 x 100 像素。 |
| 23 | 将对话窗口设置为模态。这意味着当此窗口存在时，无法访问主应用程序窗口。 |
| 24 | 将对话窗口设置为主窗口的瞬态（transient）。瞬态窗口不会在操作系统中为窗口创建额外的任务栏项。这在 Windows 上目前是的，但在 Linux 下工作正常。 |
| 25 | 设置窗口的缩放策略。`resize()` 方法接受三个布尔（true 或 false/0 或 1）参数：
    - `allow_shrink`—允许窗口比其子元素小（这应该始终设置为 false）。
    - `allow_grow`—允许窗口大于其原始大小。
    - `auto_shrink`—允许窗口覆盖其默认大小设置，收缩到任何子窗口的大小。 |
| 26 | 创建名为 `$label` 的新标签对象。 |
| 27 | 创建名为 `$button_yes` 的新按钮对象。它作为对话框中的“确定”按钮。 |
| 28 | 使用 `connect()` 方法，在点击此按钮时调用 `destroy()` 函数。 |
| 29 | 创建名为 `$button_no` 的新按钮。它作为对话框中的“取消”按钮。 |
| 30 | 使用 `connect()` 方法调用 `close_dialog()` 函数。注意，`connect` 方法在末尾带有一个额外的参数。通常，`connect()` 方法有两个参数：动作（例如 `clicked`）和被调用的函数（例如 `close_dialog`）。你可以添加第三个参数，即发送到函数的额外变量。在这种情况下，我们发送了对话框窗口对象 `$dialog`。由于我们发送了两个参数，而连接的函数默认通常只接收一个（即创建连接的对象），你必须在你创建连接的函数（在本例中 `close_dialog()`）中定义默认对象（`$button`）和额外对象（`$dialog`）。 |
| 31 | 由于 `GtkDialog` 对象内置了用于内容的“框”（boxes），你需要为该对象分配一个变量名。在这里，为 `GtkDialog` 的 `vbox` 分配一个变量名。 |
| 32 | 为 `GtkDialog` 的 `action_area` 分配一个变量名。 |
| 33 | 将标签对象打包到 `vbox` 中。 |
| 34–35 | 在 `GtkDialog` 的 `action_area` 中打包“确定和取消取消按钮。 |
| 36 | 显示对话框的内容。 |
| 37 | 结束函数声明。 |
| 38 | 创建名为 `$window` 的新窗口对象。 |
| 39 | 将窗口的 `delete_event` 方法连接到你之前定义的 `delete_event()` 函数。当用户点击应用程序右上角的“X”按钮时，会调用 `delete_event` 方法。在之前的示例中，我们省略了此方法，因为我们想直接销毁窗口。 |
| 40 | 创建名为 `$button` 的新按钮。 |
| 41 | 将按钮的 `clicked` 方法连接到 `confirm` 函数。 |
| 42 | 使用 `add()` 方法将按钮添加到窗口。 |
| 43 | 对 `$window` 对象调用 `show_all()` 函数，以显示所有内容。 |
| 44 | 调用 `Gtk::main()` 方法运行脚本。 |

### PHP GTK Application

此应用程序使用 GTK 控件创建一个加密密码的小程序。您在相应的字段中输入用户名和密码，然后点击“生成”按钮创建一个加密的用户名和密码组合。用户名和密码显示在应用程序中间的文本框中。当你创建了所需的密码，可以点击“写入文件”将数据写入文件。见图 12-8 的输出。

##### 脚本 12-6 password_gen.php

```php
<?php
if (!class_exists('gtk')) {
    if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
      dl('php_gtk.dll');
    else
      dl('php_gtk.so');
}
function destroy(){
    Gtk::main_quit();
}
function generate(){
    global $user_in, $pass_in, $output;
    $text = $user_in->get_text() . ":" . $pass_in->get_text() . "\n";
    $output->insert(null, null, $text);
    $user_in->set_text('');
    $pass_in->set_text('');
}
function encoded($text) {
    return md5($text);
}
function write(){
    global $output;
    $text = $output->get_chars(-1);
    $file = fopen("pass.txt", "w") or die("CANNOT OPEN FILE");
    fwrite($file, $text);
    fclose($file);
    $output->delete_text(-1);
    $complete = "Passwords written to file!\n";
    $output->insert(null, null, $complete);
}
$window = new GtkWindow();
$window->set_default_size(300, 300);
$window->connect('destroy', 'destroy');
$user_label = new GtkLabel("Username: ");
$user_in = new GtkEntry();
$user_box = new GtkHBox();
$user_box->pack_start($user_label, false, false, 0);
$user_box->pack_start($user_in, false, false, 0);
$pass_label = new GtkLabel("Password: ");
$pass_in = new GtkEntry();
$pass_box = new GtkHBox();
$pass_box->pack_start($pass_label, false, false, 0);
$pass_box->pack_start($pass_in, false, false, 0);
$button1 = new GtkButton('Generate Username:Password!');
$button1->connect('clicked', 'generate');
$output = new GtkText();
$button2 = new GtkButton('Write To File');
$button2->connect('clicked', 'write');
$vbox = new GtkVBox();
$vbox->pack_start($user_box, false, false, 0);
$vbox->pack_start($pass_box, false, false, 0);
$vbox->pack_start($button1, false, false, 0);
$vbox->pack_start($output, false, false, 0);
$vbox->pack_start($button2, false, false, 0);
$window->add($vbox);
$window->show_all();
Gtk::main();
?>
```

##### 图 12-8. 输出

![graphics/12fig08.jpg](img/12fig08.jpg)

##### 脚本 12-6 password_gen.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2 | 如果没有定义 `gtk` 类，则执行 3–7 行。如果 `gtk` 类已定义，则脚本不需要执行操作。 |
| 3 | 检查 `PHP_OS` 环境变量的前三个字符。 |
| 4 | 如果是 `WIN`，则系统正在运行 Windows。加载 Windows 的 PHPGTK 库。 |
| 5–7 | 如果 `PHP_OS` 环境变量不是 `WIN`，则假设 PHP 运行在 Linux 系统上并加载 Linux PHPGTK 库。 |
| 8–10 | 定义函数 `destroy()`，在调用时停止脚本。 |
| 9 | 执行 `Gtk::main_quit()` 方法以停止脚本并关闭 GTK 窗口。 |
| 11–17 | 定义函数 `generate()`，加密用户输入的用户名/密码组合并将其打印到应用程序内部的文本框中。 |
| 12 | 将 `$user_in`、`pass_in` 和 `$output` 变量设为全局变量，以便在该函数内部使用。 |
| 13 | 将用户输入的用户名和密码赋值给 `$text` 变量。 |
| 14 | 将 `$text` 插入 `$output` 对象中。 |
| 15 | 清空 `$user_in`。 |
| 16 | 清空 `$pass_in`。 |
| 18–20 | 定义函数 `encoded($text)`，返回文本的 MD5 哈希。 |
| 21–30 | 定义函数 `write()`，从 `$output` 获取字符并将其写入文件。 |
| 22 | 将 `$output` 设置为全局变量。 |
| 23 | 获取 `$output` 的所有字符。 |
| 24 | 以写入模式打开 `pass.txt`，如果无法打开则退出。 |
| 25 | 将 `$text` 写入文件。 |
| 26 | 关闭文件句柄。 |
| 27 | 删除 `$output` 中的所有文本。 |
| 28 | 定义完成消息 `$complete`。 |
| 29 | 将 `$complete` 插入 `$output` 中。 |
| 31 | 创建 `GtkWindow` 实例。 |
| 32 | 设置默认大小为 300x300。 |
| 33 | 连接 `destroy` 信号到 `destroy` 函数。 |
| 34–38 | 创建用户名的标签、输入框和水平布局框。 |
| 39–43 | 创建密码的标签、输入框和水平布局框。 |
| 44–45 | 创建“生成”按钮并将其 `clicked` 事件连接到 `generate` 函数。 |
| 46 | 创建 `GtkText` 对象用于输出。 |
| 47–48 | 创建“写入文件”按钮并将其 `clicked` 事件连接到 `write` 函数。 |
| 49–54 | 创建垂直布局框 `$vbox` 并所有框、按钮和文本区域打包其中。 |
| 55 | 将 `$vbox` 添加到窗口。 |
| 56 | 显示窗口的所有控件。 |
| 57 | 启动 GTK 主循环。 |





### 14
使用文本对象的 `insert()` 方法将用户名和编码后的密码插入文本框中。`insert()` 接受四个参数：
* `Font`— 一个 GDK 字体对象。
* `Color`— 一个 GDK 颜色对象。
* `Size`— 想要插入的字符数。
* `String`— 要插入的文本。
为了简单起见，我将前三个参数设置为 `null`，以便使用默认值。

### 15
通过向输入框插入空字符串，清除 `Username` 字段中用户输入的文本。

### 16
通过向输入框插入空字符串，清除 `Password` 字段中用户输入的文本。

### 17
结束函数声明。

### 18–20
定义一个函数 `$encode`，对输入的密码进行编码。

### 19
使用 `md5()` 函数对密码进行编码，并将其返回给调用函数。你可以根据需要更改加密方法（例如使用 `crypt()` 函数）。

### 20
结束函数声明。

### 21–30
定义一个函数 `write()`，将编码后的用户名/密码写入文件。

### 22
将 `$output` 变量赋值为全局变量，以便在该函数内部使用。

### 23
使用 `get_chars()` 方法从文本对象获取整个文本，并放入 `$text` 变量中。`get_chars()` 方法接受两个参数：
* 文本的起始位置（0 是第一个位置）。
* 文本的结束位置。
使用 `0` 和 `-1` 作为参数可以收集文本对象中的整个文本。

### 24
打开一个文件进行写入。注意，如果你已经有一个同名的文件，它将会被新的用户名/密码组合覆盖。你还必须设置文件权限以便进行写入。

### 25
将文本写入文件。

### 26
关闭文件。

### 27
删除文本区域中的文本。

### 28
创建一个字符串，通知用户文本已写入。

### 29
将该字符串写入文本区域。注意，如果你想再次创建密码，需要关闭并重启应用程序。

### 30
结束函数声明。

### 31
创建一个名为 `$window` 的窗口对象。

### 32
将窗口大小设置为 300x300 像素。

### 33
将窗口的 `destroy` 方法连接到你之前定义的 `destroy()` 函数。当用户点击窗口右上角的“X”时，会调用 `destroy` 方法。

### 34
为 `username` 创建一个新的标签对象。

### 35
为 `username` 创建一个新的文本输入对象。

### 36
创建一个新的 `hbox`，用于放置 `username` 标签和文本输入对象。

### 37
将标签对象打包到 `hbox` 中。

### 38
将文本输入对象打包到 `hbox` 中。

### 39
为 `password` 创建一个新的标签对象。

### 40
为 `password` 创建一个新的文本输入对象。

### 41
创建一个新的 `hbox`，用于放置 `password` 标签和文本输入对象。

### 42
将标签对象打包到 `hbox` 中。

### 43
将文本输入对象打包到 `hbox` 中。

### 44
为“Generate…”按钮创建一个新的按钮对象。

### 45
将“Generate…”按钮连接到 `generate()` 函数。

### 46
创建一个新的文本对象以显示输出结果。

### 47
为“Write To File”按钮创建一个新的按钮对象。

### 48
将“Write To File”按钮连接到 `write()` 函数。

### 49
创建一个新的 `vbox`，用于容其他的框和按钮。

### 50
将包含 `username` 标签和输入的 hbox 打包到 `vbox` 中。

### 51
将包含 `password` 标签和输入的 hbox 打包到 `vbox` 中。

### 52
将“Generate…”按钮打包到 `vbox` 中。

### 53
将文本对象打包到 `vbox` 中。

### 54
将“Write To File”按钮打包到 `vbox` 中。

### 55
将 `vbox` 添加到 `window` 中。

### 56
显示窗口的所有内容。

### 57
执行脚本。

