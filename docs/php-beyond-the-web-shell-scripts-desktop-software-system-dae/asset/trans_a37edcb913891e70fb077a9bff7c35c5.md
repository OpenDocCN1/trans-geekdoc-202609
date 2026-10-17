

### 3.4 为脚本传递命令行参数

如上所述，向 PHP 本身传递参数非常简单，按常规方式进行即可。但是，为 PHP 脚本传递参数则稍微复杂一些，因为 PHP 需要知道其自身参数在哪里结束，而你的脚本参数在哪里开始。研究 PHP 如何处理此问题的最佳方法是通过一些示例。请考虑以下 PHP 脚本：

```
1 <?
2 
3 echo "Number of arguments given :".$argc."\n";
4 
5 echo "List of arguments given :\n";
6 
7 print_r($argv);
```

上述脚本中有两个特殊变量：

*   `$argc`：记录传递给脚本的命令行参数数量

*   `$argv`：实际传递的参数数组。

让我们将脚本保存为 `arguments.php`。现在让我们按以下方式调用它：

```
1 ~$ php -e arguments.php -i -b=big -l red white "and blue"
```

你将得到以下输出：

```
 1 Number of arguments given :7
 2 List of arguments given :
 3 Array
 4 (
 5     [0] => arguments.php
 6     [1] => -i
 7     [2] => -b=big
 8     [3] => -l
 9     [4] => red
10     [5] => white
11     [6] => and blue
12 )
```

如你所见，命令中从文件名开始给出的所有参数都会传递给脚本。第一个参数 `-e` 是由 PHP 本身使用的，不会传递。因此，作为一般规则，文件名之后的所有内容都被视为脚本的参数，文件名之前的任何内容都被视为 PHP 本身的参数，而文件名则由两者共享。

当然，也有例外。如上所述，除了单独指定脚本的文件名外，我们还可以将其作为 `-f` 标志的一部分传递。因此，如果我们执行以下命令：

```
1 ~$ php -e -f arguments.php -i -b=big -l red white "and blue"
```

我们将得到以下意外输出：

```
 1 phpinfo()
 2 PHP Version => 5.4.6-1ubuntu1.3
 3 
 4 System => Linux dev-system 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:10:2\
 5 8 U
 6 TC 2013 i686
 7 Build Date => Jul 15 2013 18:23:34
 8 Server API => Command Line Interface
 9 Virtual Directory Support => disabled
10 Configuration File (php.ini) Path => /etc/php5/cli
11 <rest of output removed for brevity>
```

你可能会认出这是调用 `php -i` 的输出。PHP 没有将文件名之后的参数视为属于脚本，而是将 `-f` 参数视为其自身的参数之一，并继续“拥有”所有后续参数。由于 `-i` 是一个有效的 PHP 参数，它决定这就是你想要的，并调用其“信息”模式。如果你需要将文件名作为 `-f` 标志的一部分传递，而不是作为单独的参数，则需要使用 `--` 来分隔脚本的参数。因此，为了使上述命令按预期工作，我们需要将其更改为：

```
1 ~$ php -e -f arguments.php -- -i -b=big -l red white "and blue"
```

`--` 之后的所有内容，加上脚本文件名，都将作为参数传递给脚本，我们将得到预期的输出。

这可能会使你的脚本变得有点混乱，特别是如果你要传递大量参数，因此你可能希望查看下一节中关于自执行脚本的小节，它将向你展示如何将 PHP 的参数嵌入到脚本本身中，从而允许脚本声称所有传递给它的参数都是其自己的。

### 3.5 调用 PHP 脚本的多种方式

