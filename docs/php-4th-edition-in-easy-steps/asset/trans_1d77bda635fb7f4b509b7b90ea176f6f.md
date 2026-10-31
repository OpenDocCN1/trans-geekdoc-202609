
- 多行块注释必须用 `/*` 和 `*/` 字符序列括起来。
- `OPcache` 将 OPcodes 存储在内存中以供 Zend 虚拟机执行。
- 即时编译生成低级指令，可直接由系统的 CPU 执行。

# 2 存储值

*本章演示了数据可以存储在其中的各种 PHP 容器。*

[创建变量](#chapter02.xhtml#sec10)
[引用字符串](#chapter02.xhtml#sec11)
[生成数组](#chapter02.xhtml#sec12)
[排序数组](#chapter02.xhtml#sec13)
[描述维度](#chapter02.xhtml#sec14)
[检查类型](#chapter02.xhtml#sec15)
[定义常量](#chapter02.xhtml#sec16)
[探索超全局变量](#chapter02.xhtml#sec17)
[摘要](#chapter02.xhtml#sec18)

## 创建变量

![image](images/pg26_1.jpg)

“变量”是在 PHP 脚本中用于存储数据值的命名容器。存储的值可以使用变量的名称引用，并在脚本执行过程中进行更改（变化）。脚本作者可以为变量选择任何名称，只要它遵循以下三个命名约定：

- 名称必须以 $ 美元符号开头 – 例如，`$name`。
- 名称可以包含字母、数字和下划线字符，但不能包含空格 – 例如，`$subtotal_1`。
- $ 美元符号后的第一个字符必须是字母或下划线字符 – 不能是数字。

请注意，PHP 中的变量名区分大小写，因此 `$name`、`$Name` 和 `$NAME` 是三个独立的变量。

![image](images/snake.jpg)

在 PHP 中 `$this` 是一个特殊变量，因此不能使用“this”作为变量名。

PHP 变量是“松散类型”的，这意味着它们可以包含任何类型的数据，这与某些语言中的“强类型”变量不同，在强类型变量中，创建变量时必须指定数据类型。因此，PHP 变量可以愉快地包含整数、浮点数、文本字符串、TRUE 或 FALSE 的布尔值、对象或 NULL 空值。

在 PHP 脚本中，变量只需声明其名称即可创建。然后可以使用 = 赋值运算符为其指定初始值（初始化）。此语句以及 PHP 中的所有其他语句都必须以分号结束，如下所示：

`$body_temp = 98.6 ;`

![image](images/forget.jpg)

脚本中可访问的变量必须具有唯一名称。有关“变量作用域”的更多信息，请参阅[第82页此处](#chapter05.xhtml#sec39)。

然后可以通过使用变量名引用它来显示变量中包含的值，如下所示：

`echo $body_temp ;`

有用的是，变量的值可以通过将字符串和变量名用双引号括起来作为混合字符串的一部分显示：

`echo "Body temperature is $body_temp degrees Fahrenheit" ;`

双引号可确保 PHP 评估整个字符串并用其存储的值替换命名变量。如果字符串用单引号括起来，此功能不起作用！

![image](images/snake.jpg)

不要混淆双引号和单引号的用途。请记住，PHP 仅对用双引号括起来的混合字符串进行变量替换。

![image](images/1r.jpg)创建有效的 HTML 文档，如[第16页此处](#chapter01.xhtml#sec5)所列，然后在 body 部分插入 PHP 标签

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commonr.jpg)

`variable.php`

![image](images/2r.jpg)现在，在 PHP 标签之间插入一条语句来创建并初始化变量

`$body_temp = 98.6 ;`

![image](images/3r.jpg)接下来，插入一条语句单独显示变量值

`echo $body_temp ;`

![image](images/4r.jpg)然后，插入一条语句以在混合字符串中显示变量值（用双引号赋值）

`echo "<p>Body temperature is $body_temp`
`degrees Fahrenheit " ;`

![image](images/5r.jpg)插入一条语句为变量分配新值

`$body_temp = 37.0 ;`

![image](images/6r.jpg)最后，插入一条语句以在混合字符串中显示新的变量值

`echo "( $body_temp degrees Celsius )</p>" ;`

![image](images/7r.jpg)将文档保存到 Web 服务器的 `/htdocs` 目录中，命名为 `variable.php`，然后通过 HTTP 打开页面以查看变量值是否显示

![image](images/pg27_1.jpg)

![image](images/hot.jpg)

请注意，像本示例中这样在脚本主体中创建的变量是“全局”可访问的 – 在整个 PHP 脚本中都可访问。

![image](images/forget.jpg)

PHP 语言中的每个语句都必须以分号结尾 – 就像英语中的每个语句都必须以句号结尾一样。

## 引用字符串

![image](images/pg28_1.jpg)

“字符串”文本可以像数值一样存储在变量中，但赋值必须用引号括起来以表示其开始和结束。单引号和双引号都可用于此目的，但必须使用相同类型的引号来表示文本字符串的开始和结束。例如，这两个语句都可进行有效的字符串赋值：

`$song_title = "Summertime Blues" ;`
`$song_title = 'Summertime Blues' ;`

如果要存储本身包含引号的文本字符串，可以通过在引号前加上 `\` 反斜杠字符来“转义”包含的引号，或在字符串中使用另一种类型的引号。例如，这两个语句都分配包含引号的字符串：

`$song_title = "the \"Summertime\" aria by George Gershwin" ;`
`$song_title = 'the "Summertime" aria by George Gershwin' ;`

第二种技术，即在字符串中使用双引号，更易于阅读，并在整本书中被优先采用。

![image](images/forget.jpg)

变量名不能包含空格 – 但下划线字符通常用于代替空格。

字符串值可以通过将混合字符串用双引号括起来作为混合字符串的一部分显示，如下所示：

`echo "Many regard $song_title as a popular classic" ;`

双引号可确保 PHP 评估混合字符串并用其存储的值替换命名变量。如果字符串用单引号括起来，此功能不起作用！

字符串值可以使用 . 串联运算符连接成一个字符串，如下所示：

`$hi = 'Hello' ;`
`$bye = 'Goodbye' ;`
`$song_title = $hi . $bye ;            # 'HelloGoodbye'`

此外，在连接字符串时可以有用地插入空格和标点符号，因此上面的标题赋值可以修改为包含逗号和空格：

`$song_title = $hi . ', ' . $bye ;      # 'Hello, Goodbye'`

![image](images/1r.jpg)创建有效的 HTML 文档，如[第16页此处](#chapter01.xhtml#sec5)所列，然后在 body 部分插入 PHP 标签

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commonr.jpg)

`string.php`

![image](images/2r.jpg)现在，在 PHP 标签之间插入一条语句来创建并初始化两个变量

`$phrase = 'The truth is rarely pure' ;`
`$author = 'Oscar Wilde' ;`

![image](images/3r.jpg)接下来，插入一条语句单独显示变量值

`echo $phrase ;`

![image](images/4r.jpg)然后，插入一条语句以在混合字符串中显示变量值（用双引号赋值）

`echo "<p>It is often said that <q>$phrase</q> </p>" ;`

![image](images/5r.jpg)插入一条语句将字符串连接到变量

`$phrase = $phrase . ' and never simple' ;`

![image](images/6r.jpg)最后，插入一条语句以在混合字符串中显示两个当前变量值

`echo "<p><q>$phrase</q><cite>$author</cite></p>" ;`

