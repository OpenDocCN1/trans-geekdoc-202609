

如果不指定索引值，该值将被添加到数组末尾。下面的行会将“retriever”赋值给 $dogs[2]。

```
$dogs[] = "retriever";
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_142_0.png)

与许多编程语言一样，PHP 使用关联数组。如果你对这个概念比较陌生，关联数组中的元素拥有用于引用单个元素的键。（事实上，所有数组值都有键。关联数组的不同之处在于，其键是有意义的，可以是字符串也可以是整数，而在简单列表数组中，它们仅表示值在数组中的位置。）在处理数据库时，键尤其重要。当你从数据库查询中提取行时，通常会通过键来引用元素。

你可以使用键来赋值关联数组。这里，first_name、last_name 和 email 是键：

```
$person = array (
  "first_name" => "Jay",
  "last_name" => "Greenspan",
  "email" => "jgreen_1@yahoo.com"
);
```

如果想向该数组添加内容，可以赋予另一个值。请注意，下一行会向数组添加一个整数，因此该数组将包含四个值——三个字符串和一个整数：

```
$person['age'] = 32;
```

通常，如果想访问关联数组中的键和值，会使用 list()=each() 结构或 foreach() 循环。以下是一些示例：

```
while (list($key, $value) = each($person))
{
  echo "<b>key:</b> $key, <b>value:</b> = $value <br>\n";
}
```

第 5 章将更详细地介绍 list()=each() 结构。基本上，each() 获取单个数组元素的键和值；list() 获取这些值，并分别将其赋给 $key 和 $value。此过程会持续进行，直到数组中的每个元素都被访问。如果你想第二次遍历数组，需要使用 reset($person) 重置数组指针。

如果你只想获取值而不想获取键，或者正在使用非关联数组且想使用 list()=each() 结构，则必须这样做：

```
while (list( , $value) = each($person))
{
    echo "value = $value<br>\n";
}
```

或者，如果你只想获取键，可以这样做：

```
while (list($key) = each($person))
{
    echo "key = $key<br>\n";
}
```

你也可以使用 foreach() 循环遍历数组。以下将打印 $person 数组中每个元素的键和值：

```
foreach($person as $key=>$value)
{
    echo "key = $key; value = $value<br>\n";
}
```

以下将只打印数组元素的值：

```
foreach($person as $value)
{
    echo "value = $value<br>\n";
}
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_143_0.png)

考虑 PHP 数组时可以这样想：所有数组都是关联数组。几页前你已经看到，可以不指定关联键来赋值基本数组。例如，$myarray= array ("pug", "poodle")。完成此操作后，PHP 会从 0 开始为 $myarray 分配连续的数字键。它们的行为就像关联键一样。你可以使用 list()=each() 或 foreach() 遍历它们。它们使用相同的数组函数，其中许多在第 6 章中有所解释。

## 在脚本中赋值二维数组

PHP 还支持多维数组。最常用的多维数组是二维数组。二维数组很像表格。它们存储基于两个键的信息。例如，如果你想存储多个人的信息，二维数组非常合适。你会赋值一个名为 $people 的数组，它包含针对每个人的单独数组：

```
$people = array(
    "jay" => array (
        "last_name" => "greenspan",
        "age" => 32
    ),
    "john" => array (
        "last_name" => "doe",
        "age" => 52
    )
);
```

这里，$people 数组包含两个人（Jay 和 John）的信息。要访问任何单个值，需要同时使用两个键。要打印 John 的年龄，以下两条命令都有效：

```
echo $people['john']['age']; //prints 52
```

你可以通过遍历数组的两个维度来访问二维数组中的所有元素：

```
foreach ($people as $person => $person_array)
{
    echo "<b>What I know about $person</b><br>\n";
    foreach ($person_array as $person_attribute => $value)
    {
        echo "$person_attribute = $value<br>\n";
    }
}
```

## 访问从浏览器传递的变量

使用 PHP（或任何其他中间件包）的全部目的，就是根据用户偏好和需求提供定制化信息。通常，信息会通过 HTML 表单传递。但信息也可以来自其他地方，包括 HTML 锚点、Cookie 和会话。

### HTML 表单变量

传递变量信息最常见的方式之一是通过 HTML 表单。

附录 B 介绍了创建 HTML 表单的详细信息。如果你对这个主题不熟悉，在阅读本节之前请参阅该附录。

对于每个表单元素，都必须分配 `name` 和 `value` 属性（`name` 和 `value` 是在 HTML 代码中定义的设置）。当表单提交时，name/value 键值对会传递给 PHP。它们可以通过 GET 或 POST 方法传递给 PHP，具体取决于你在 `<FORM>` 标签的 METHOD 属性中选择的内容（默认值为 GET）。

在旧版 PHP（PHP 4.2 之前）中，表单提交后，表单元素会自动成为 PHP 中的全局变量。（全局变量和变量作用域在第 7 章中讨论。）请考虑以下简单的 HTML 表单：

```
<form action="mypage.php" method="POST">
    <input type=text name=email>
    <input type=text name=first_name>
    <input type=submit name=submit value=add>
</form>
```

用户单击提交按钮后，名为 $email、$first_name 和 $submit 的变量将在被调用的 PHP 页面中可用。清单 4-1 是 PHP 4.1 及更低版本脚本通常编写方式的简要示例。（假设页面名为 mypage.php。）

### 清单 4-1：旧版 PHP 中的常见变量用法

```
<?php
if (isset($submit) && $submit=="yes")
{
    echo "thank you for submitting your form.";
}
else
{

?>
<form action="mypage.php" method="POST">
<input type="text" name="email">
<input type="text" name="first_name">
<input type="submit" name="submit" value="yes">
</form>
<?php
}
?>
```

用户第一次访问此页面时，会看到一个表单。表单提交且页面使用新变量信息重新加载后，只会出现“thank you”消息。但是，来自表单的全局变量存在一个重大问题。即使是像清单 4-1 中这样简单得不能再简单的代码，也演示了这一问题。

用户输入的变量应通过 POST 方法——而非 GET 方法——传递到 PHP 脚本。但是，如果用户想在不向表单元素输入任何内容的情况下查看“thank you”消息，他或她只需在浏览器中输入的 URL 上附加一些信息即可。例如：

```
http://localhost/mypage.php?submit=yes
```

在旧版 PHP 中，当 PHP 引擎在查询字符串中遇到 submit 变量时，会自动将其注册为全局变量，因此脚本开头的测试—if (isset($submit) && $submit=="yes")—将为真。

许多程序员编写了利用全局变量的应用程序，无意中使其脚本易受攻击。我们不会在此深入探讨漏洞细节；只需指出，即使你有机会，也不应使用来自表单元素的全局变量。相反，你应该使用一组包含通过 HTTP 发送的变量的数组。

在 PHP 4.2 及更高版本中，你可以通过修改 php.ini 文件中的 register_globals 项，选择让 GET、POST、会话和 Cookie 变量作为全局变量可用。当前版本的 PHP 默认该设置为 off，这意味着 HTTP 变量不会作为全局变量可用。在大多数情况下，你应该保持此设置不变。但是，如果你正在运行没有时间修改的旧脚本，可能需要更改此设置。

