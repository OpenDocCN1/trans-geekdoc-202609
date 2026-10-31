
![image](images/pg33_1.jpg)

![image](images/pg33_2.jpg)

![image](images/hot.jpg)

你可以用 `count()` 函数来发现数组中的元素数量 – 例如，`$num = count( $array ) ;`

![image](images/forget.jpg)

不要在键很重要时使用 `sort()` 或 `rsort()` 函数。

## 描述维度

![image](images/pg34_1.jpg)

数组元素的编号更准确地称为“数组索引”，并且由于元素编号从零开始，有时也称为“零基索引”。使用单个索引创建的数组是一维数组，其中元素出现在单行中：

| 元素内容 || A || B || C || D || E |

| --- | --- | --- | --- | --- | --- |

| 索引编号 || \[0\] || \[1\] || \[2\] || \[3\] || \[4\] |

数组也可以具有多个索引 – 用于表示多个维度。使用两个索引创建的数组是二维数组，其中元素出现在多行中：

| 第一索引 || \[0\] || A || B || C || D || E |

| --- | --- | --- | --- | --- | --- | --- |

|  || \[1\] || F || G || H || I || J |

| 第二索引 ||  || \[0\] || \[1\] || \[2\] || \[3\] || \[4\] |

对于多维数组，每个元素包含的值是通过说明每个索引的编号来引用的。例如，上面二维数组中，位于 \[1\]\[2\] 的元素包含字母 H。

二维数组对于存储基于网格的信息很有用，例如 XY 坐标。创建具有三个索引的三维数组将允许存储 XYZ 坐标。

在 PHP 中创建多维数组只是在创建外部数组，其元素本身就是数组。如往常一样，您可以为每个元素可选地指定一个键名 – 在本例中表示每个内部数组。然后可以使用键名和内部索引号引用单个值：

`$matrix\[‘Letter’\]\[0\]`

然而，将使用带引号键的数组变量包含在字符串中时，始终必须用大括号括起来：

`echo “Element value is {$matrix\[‘Letter’\]\[0\]} ” ;`

可以使用 `foreach` 循环遍历数组来访问多维数组中的所有内部数组。然后嵌套的 `foreach` 循环可以依次引用每个元素。

![image](images/snake.jpg)

具有超过两个索引的多维数组会产生难以阅读的源代码并可能导致错误。

![image](images/1r.jpg)
创建一个有效的 HTML 文档，如 [此处第16页](#chapter01.xhtml#sec5) 所列，然后在 body 部分插入 PHP 标签

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commonr.jpg)

matrix.php

![image](images/2r.jpg)
现在，在 PHP 标签之间插入一条语句来创建并初始化两个常规变量数组以及一个带键名的二维数组

```
$letters \= array( ‘A’ , ‘B’ , ‘C’ ) ;
$numbers \= array( 1 , 2 , 3 ) ;
$matrix \=
array( ‘Letter’ \=> $letters , ‘Number’ \=> $numbers ) ;
```

![image](images/3r.jpg)
接下来，插入一条语句来显示单个存储的值

`echo “<p>Start : {$matrix\[‘Letter’\]\[0\]} </p>” ;`

![image](images/4r.jpg)
最后，插入语句以将所有元素中的键和值作为两个无序列表显示

```
foreach( $matrix as $array \=> $list )
{
echo ‘<ul>’ ;
foreach( $list as $key \=> $value )
{ echo “<li>$array \[ $key \] = $value ” ; }
echo ‘</ul>’ ;
}
```

![image](images/5r.jpg)
将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `matrix.php`，然后通过 HTTP 打开页面以查看变量数组值是否显示

![image](images/pg35_1.jpg)

![image](images/hot.jpg)

多维数组比你想象的更常见。例如，HTML 表单允许对具有相同名称的输入进行多次选择，并作为多维数组提交。

![image](images/forget.jpg)

使用带引号键的数组变量在包含在字符串中时必须用大括号括起来。

## 检查类型

![image](images/pg36_1.jpg)

PHP 变量可以存储各种类型的数据，因此清楚地了解每种数据类型非常重要：

• string – 一系列字符，每个字符大小为一个字节，最大长度为 2GB。用单引号括起来的字符串被视为文字，而双引号中的字符串会解释特殊字符。

• int – 一个介于 2,147,483,648 和 -2,147,483,647 之间的非小数，以十进制（10 进制）、十六进制（16 进制 – 前缀为 0x）或八进制（8 进制 – 前缀为 0）指定。

• float – 一个浮点小数或指数格式的数字。float 也称为“double”。

• bool – 布尔真值的表达式，只能为 true 或 false。

• array – 一个有序映射，关联多个数据值的键和值。键默认按索引编号，也可显式指定标签。

• object – 一个包含存储的数据属性的类，并提供处理数据的方法。

• resource – 对由特殊函数创建和使用的外部资源的引用。

• NULL – 一个没有任何值的变量。它可能未初始化，已被赋值为 NULL 常量，或已被 PHP `unset()` 函数清空。

任何项目的数据类型都可以通过将其指定为 `gettype()` 函数的参数来检查。例如，如果变量 `$num` 包含整数值，`gettype($num)` 将返回“integer”，如果变量 `$str` 包含字符串值，`gettype($str)` 将返回“string”，依此类推。如果无法识别数据类型，`gettype()` 函数将返回“unknown type”。

也许更有用的是，`var_dump()` 函数可以检查项目的数据类型，并转储显示其类型和值的结构化信息。

![image](images/hot.jpg)

PHP 类对象的创建和使用在 [第7章。](#chapter07.xhtml) 中得到充分演示

![image](images/1r.jpg)
创建一个有效的 HTML 文档，如 [此处第16页](#chapter01.xhtml#sec5) 所列，然后在 body 部分插入 PHP 标签

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commonr.jpg)

types.php

![image](images/2r.jpg)
接下来，在 PHP 标签之间插入一条语句来创建一个文件流资源和一个数组

```
$filestream \= fopen( ‘index.html’ , ‘r’ ) ;
$data \= array( ‘PHP’ , 1 , 2.3 , TRUE , NULL , array() ,
new Directory , $filestream ) ;
```

![image](images/3r.jpg)
现在，插入一条语句来显示每个数组元素中存储的数据类型

```
foreach( $data as $type )
{
var\_dump( $type ) ;
echo ‘<br> ‘ ;
}
```

![image](images/4r.jpg)
最后，插入语句来销毁文件流资源，然后再次尝试获取其数据类型

```
fclose( $filestream ) ;
echo gettype( $filestream ) ;
```

![image](images/5r.jpg)
将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `types.php`，然后通过 HTTP 打开页面以查看数据类型和值是否显示

![image](images/pg37_1.jpg)

![image](images/hot.jpg)

PHP 文件流资源的创建和使用在 [第8章。](#chapter08.xhtml) 中得到充分演示

![image](images/hot.jpg)

布尔常量 `TRUE` 和 `FALSE` 不区分大小写，因此可以写成 `true` 和 `false`。

## 定义常量

脚本中永远不会改变的固定数据值应存储在 PHP“常量”中，而不是变量中。常量是一个命名容器，其中可以存储数字或字符串值，并可以使用常量的名称引用。

![image](images/pg38_1.jpg)
