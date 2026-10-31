
你可以嵌套条件 `if` 测试（一个在另一个内部），这样内部块中的语句只有在两个测试都被判定为 `TRUE` 时才会被执行。

## 分支切换

![image](images/pg62_1.jpg)

由多个 if-elseif-else 语句执行的条件分支，在测试表达式仅评估一个条件时，通常可以用 `switch` 语句更高效地实现。

`switch` 语句的工作方式比较特殊。它以给定值作为参数参数，然后从多个 `case` 语句中寻找匹配该值的语句。每个 `case` 语句中都包含在找到匹配时要执行的代码。

重要的是，每个 `case` 语句都要以 `break` 关键字语句结束，这样 `switch` 语句在找到匹配后就会退出，而不会继续寻找进一步的匹配——除非这是有意为之的要求。

可选地，`case` 语句列表后可以跟一个单一的最终 `default` 语句，以指定在任何 `case` 语句中均未找到匹配时要执行的代码。因此，`switch` 语句的语法通常如下所示：

```
switch ( test-value )
{
case match-value : statements-to-execute-when-matched ; break ;
case match-value : statements-to-execute-when-matched ; break ;
case match-value : statements-to-execute-when-matched ; break ;
default : statements-to-execute-when-no-match-found ;
}
```

`switch` 语句可以有多个 `case` 语句，但其任意两个 `case` 语句都不能尝试匹配相同的值。

![image](images/hot.jpg)

总是建议包含一个 `default` 语句——即使只是为了在 `switch` 语句失败时输出错误消息。

当多个匹配值需要各自执行相同的语句时，只有最后一个 `case` 语句需要包含要执行的语句以及退出 `switch` 语句块的 `break` 语句。例如，要为匹配值 0、1 和 2 输出相同的消息：

```
switch ( $number )
{
case 0 :
case 1 :
case 2 : echo ‘Less than 3’ ; break ;
case 3 : echo ‘Exactly 3’ ; break ;
default : echo ‘Greater than 3 or less than zero’ ;
}
```

![image](images/forget.jpg)

`default` 语句不必出现在 `switch` 块的末尾，但在不需要 `break` 语句的情况下，将其放在那里是合乎逻辑的。

![image](images/1p.jpg) 在 PHP 标签之间，使用语句开始脚本以初始化两个变量，一个为整数值，一个为字符值

```
<?php
$number \= 2 ; $letter \= ‘B’ ;
```

![image](images/commonp.jpg)

switch.php

![image](images/2p.jpg) 接下来，添加一个 `switch` 语句来匹配整数值

```
switch ( $number )
{
case 1 : echo ‘Number is One<br>’ ; break ;
case 2 : echo ‘Number is Two<br>’ ; break ;
case 3 : echo ‘Number is Three<br>’ ; break ;
default : echo ‘Number is Unrecognized<br>’ ;
}
```

![image](images/3p.jpg) 现在，添加一个 `switch` 语句来匹配字符值

```
switch ( $letter )
{
case ‘A’ : echo ‘Letter is A<br>’ ; break ;
case ‘B’ : echo ‘Letter is B<br>’ ; break ;
case ‘C’ : echo ‘Letter is C<br>’ ; break ;
default : echo ‘Letter is Unrecognized<br>’ ;
}
```

![image](images/4p.jpg) 最后，添加一个 `switch` 语句来匹配多个整数值

```
switch ( $number )
{
case 0 : case 1 : case 2 : echo ‘Less than 3<br>’ ; break ;
default : echo ‘3 or more, or less than zero’ ;
}
?>
```

![image](images/5p.jpg) 将文档保存在你的 Web 服务器的 `/htdocs` 目录中，命名为 `switch.php`，然后通过 HTTP 打开页面以查看条件分支的结果

![image](images/pg63_1.jpg)

![image](images/hot.jpg)

在 `switch` 语句中，`case` 关键字、匹配值和冒号字符被视为一个唯一的“标签”。

## 匹配表达式

![image](images/pg64_1.jpg)

条件分支也可以通过 `match` 语句实现。这些是 `switch` 语句的替代方案，[此处第62-63页](#chapter04.xhtml#sec29)有描述，并且通常是更好的选择。

与 `switch` 语句块不同，`match` 语句是一个返回值的单一表达式。它以给定值作为参数参数，然后从用大括号括起来的以逗号分隔的备选列表中寻找匹配该值的项。找到匹配时要返回的值随后在 `=>` 粗箭头运算符之后指定。

重要的是，每个 `match` 语句在闭合大括号后都要以 `;` 分号结束，以终止该语句。

`match` 表达式不需要任何 `break` 语句，因此其代码比等效的 `switch` 块显著更短。`match` 语句的语法通常如下所示：

```
$result = match ( test-value )
{
match-value => return-value ,
match-value => return-value ,
match-value => return-value ,
default => return-value ,
} ;
```

![image](images/hot.jpg)

`match` 语句是 PHP 8 中引入的一个很棒的新特性。

当多个匹配值需要各自返回相同的值时，它们可以合并为一个以逗号分隔的单一列表。例如，要为匹配值 0、1 和 2 输出相同的消息：

```
echo match ( $number )
{
0 , 1 , 2 => ‘Less than 3’ ,
3 => ‘Exactly 3’ ,
default => ‘Greater than 3 or less than zero’ ,
} ;
```

有用的是认识到，`match` 语句比较值是否恒等，如使用 `===` 运算符，而 `switch` 语句比较值是否相等，如使用 `==` 运算符。

相反示例中的步骤使用 `match` 语句来复制之前 `switch` 语句示例的输出。

![image](images/1p.jpg) 在 PHP 标签之间，使用语句开始脚本以初始化两个变量，一个为整数值，一个为字符值

```
<?php
$number \= 2 ; $letter \= ‘B’ ;
```

![image](images/commonp.jpg)

match.php

![image](images/2p.jpg) 接下来，添加一个 `match` 语句来匹配整数值

```
echo match ( $number )
{
1 \=> ‘Number is One<br>’ ,
2 \=> ‘Number is Two<br>’ ,
3 \=> ‘Number is Three<br>’ ,
default => ‘Number is Unrecognized<br>’ ,
} ;
```

![image](images/3p.jpg) 现在，添加一个 `match` 语句来匹配字符值

```
echo match ( $letter )
{
‘A’ \=> ‘Letter is A<br>’ ,
‘B’ \=> ‘Letter is B<br>’ ,
‘C’ \=> ‘Letter is C<br>’ ,
default => ‘Letter is Unrecognized<br>’ ,
} ;
```

![image](images/4p.jpg) 最后，添加一个 `match` 语句来匹配多个整数值

```
echo match ( $number )
{
0 , 1 , 2\=> ‘Less than 3<br>’ ,
default => ‘3 or more, or less than zero’ ,
} ;
?>
```

![image](images/5p.jpg) 将文档保存在你的 Web 服务器的 `/htdocs` 目录中，命名为 `match.php`，然后通过 HTTP 打开页面以查看条件分支的结果

![image](images/pg65_1.jpg)

![image](images/hot.jpg)

将此示例中的代码与上一个示例中的 `switch` 语句进行比较，以了解 `match` 语句的简洁优势。

## 执行循环

![image](images/pg66_1.jpg)

循环是脚本中自动重复的一段代码。循环内所有语句的一次完整执行称为一次“迭代”或一次“遍历”。循环的长度由循环内进行的条件测试控制。只要测试的表达式被判定为 `TRUE`，循环就会继续——直到测试的表达式被判定为 `FALSE`，此时循环结束。

在 PHP 中有四种类型的循环结构：

• `for` 循环 – 执行指定次数的迭代。
• `while` 循环 – 仅在每次迭代开始时进行的测试评估为 `TRUE` 时执行迭代。
• `do while` 循环 – 仅在每次迭代结束时进行的测试评估为 `TRUE` 时执行迭代。
