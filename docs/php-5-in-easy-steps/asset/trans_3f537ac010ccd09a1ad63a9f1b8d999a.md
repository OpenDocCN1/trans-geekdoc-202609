

# 续

![](img/7faa63a7fa0add8f53300594ebae949f_72_0.png)

```html
<html><head><title>Calculation Result</title> </head>
<body
<?php
$val1 = $_POST['val1']; //assign value
$val2 = $_POST['val2']; //assign value
$calc = $_POST['calc']; //assign value
if( is_numeric($val1) && is_numeric($val2) )
    if ($calc != null) {
        switch ($calc) {
            case "add" :result = $val1 + $val2; break;
            case "sub" :result = $val1 - $val2; break;
            case "mul" :result = $val1 * $val2; break;
            case "div" :result = $val1 / $val2; break;
        }
        echo("Calculation result: $result");
    } else {
        echo("Invalid entry - please retry");
    }
}
?>
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_72_1.png)

switch 语句正在与 HTML 表单单按钮组的四种可能值进行匹配。

上面的表单处理脚本使用 PHP 的 is_numeric 函数来确保确实输入了两个数字。该函数接受一个值作为参数进行求值，并且仅当该值为数字时才返回 true。

如果选择了算术操作，switch 语句将确定操作类型并执行求和。（注意：文本说的是 "sum"，但代码执行了各种操作）。脚本将输出计算总和，或者在用户输入无效或不完整的内容时请求重试。

![](img/7faa63a7fa0add8f53300594ebae949f_72_2.png)

6. 生成动态内容 | 71

# 字符串处理

此示例演示了如何使用 PHP 的一些字符串函数对字符串进行处理。当表单提交时，函数名将作为键 "fcn" 关联的值发送到服务器。

![](img/7faa63a7fa0add8f53300594ebae949f_73_0.png)

```html
<html><head><title>String Manipulation</title> </head>
<body>
<form action="strings.php" method="post">
<b>在此处输入一些文本：</b> <br>
<textarea name="txt" rows="3" cols="45"></textarea>
<input type="radio" name="fcn" value="strlen">
查找文本长度
<input type="radio" name="fcn" value="strrev">
反转文本<br>
<input type="radio" name="fcn" value="str_toupper">
更改为全大写
<input type="radio" name="fcn" value="strtolower">
更改为全小写<br>
<input type="radio" name="fcn" value="ucwords">
将所有单词的首字母大写 <hr>
<input type="submit" value="Manipulate">
</form>
</body>
</html>
```

strings.html

在本示例中，要处理的字符串是 textarea 的文本输入内容，它通过 "txt" 键发送到服务器。

![](img/7faa63a7fa0add8f53300594ebae949f_73_1.png)

| 字符串处理 |
| :--- |
| 文件 编辑 视图 收藏 工具 帮助 |
| 地址 http://localhost/strings.html 转 |
| 在此处输入一些文本： |
| PHP 太棒了 - 很容易学！ |
| ○ 查找文本长度 反转文本 |
| ○ 更改为全大写 更改为全小写 |
| ○ 将所有单词的首字母大写 |
| 处理 |
| 完成 |

# 续

```html
<html><head><title>String Result</title></head><body>
<?php
$fcn = $_POST['fcn']; //assign value
$txt = $_POST['txt']; //assign value
echo ($fcn($txt)); 
?></body></html>
```

上面的表单处理脚本从变量 $fcn 获取函数名，并以 $txt 键的字符串作为参数调用它。以下是针对 textarea 中所示字符串的一些处理结果。（img/7faa63a7fa0add8f53300594ebae949f_74_0.png）

strlen() 函数返回给定字符串字符的整数总数。（img/7faa63a7fa0add8f53300594ebae949f_74_1.png）

strrev() 函数返回反序的给定字符串。（img/7faa63a7fa0add8f53300594ebae949f_74_2.png）

给定字符串可以通过 strtoupper() 完全转换为大写，或通过 strtolower() 转换为小写。（img/7faa63a7fa0add8f53300594ebae949f_74_3.png）

ucwords() 函数返回每个单词首字母大写的给定字符串。

| 字符串结果 |
| :--- |
| 文件 编辑 视图 收藏 帮助 |
| 地址 http://localhost/strings.php 转 |
| 40 |
| 字符串结果 |
| 文件 编辑 视图 收藏 帮助 |
| 地址 http://localhost/strings.php 转 |
| PHP 太棒了 - 很容易学！ |
| 字符串结果 |
| 文件 编辑 视图 收藏 帮助 |
| 地址 http://localhost/strings.php 转 |
| PHP 太棒了 - 很容易学！ |
| 完成  |

6. 生成动态内容 | 73

# 刷新页面

之前的示例使用了不同的文件作为表单处理器来处理数据，但通过将 PHP 环境变量 `$_SERVER['PHP_SELF']` 赋值给表单的 action 属性，可以使用页面自身的表单处理器。

下面的示例演示了一个数字游戏，它在首次加载时生成一个随机数并赋值给隐藏输入。页面包含一个调用 header() 的初始化块。指定的参数 "Cache-Control:no-cache" 表示浏览器应该刷新此页面而不是使用缓存。初始化块包含一个名为 setnum() 的函数，它生成一个 1 到 20 之间的随机数并赋值给变量 `$num`。随后页面刷新并保留 $num 变量的值。如果用户猜对了数字，脚本将调用 setnum() 函数为 $num 变量分配一个新的目标数字。

```php
<?php header("Cache-Control:no-cache");

function setnum() {
    global $num;
    $num = rand((double)microtime() * 1000000);
    $num = rand(1, 20);
}
```

```html
<html><head><title>Number guess</title></head><body>
<?php $num = $_POST['num']; $guess = $_POST['guess'];
$self = $_SERVER['PHP_SELF']; // assign values
?>
```

![](img/7faa63a7fa0add8f53300594ebae949f_75_0.png)

注意检查非数字输入的语法使用了 `is_numeric($guess)`。

```php
if ($num == null ) {
    $msg = "我想了一个 1 到 20 之间的数字";
    $msg = "<h3>猜猜是多少...</h3>";
}

# 无效输入的错误消息
if ($num == null && !is_numeric($guess )) {
    $msg = "你的猜测无效<h3>请重试！</h3>";
}
```

```php
else if ($guess == $num) {
    if ($num != null) {
        $msg = "正确！数字是 $num";
        $msg = "<h3><a href=$self\">";
        $msg .= "点击此处重试</a></h3>";
    }
    setnum(); // 设置一个要猜的数字
} else if ($guess > $num) {
    $msg="你猜了 $guess<h3>我的数字小了！</h3>";
} else if ($guess < $num) {
    $msg="你猜了 $guess<h3>我的数字大了！</h3>";
}
```

因为目标数字被写在 HTML 输入值中，可以通过查看浏览器中的源代码来发现。

![](img/7faa63a7fa0add8f53300594ebae949f_76_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_76_2.png)

6. 生成动态内容 | 75

