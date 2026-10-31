
# 按引用传递

如果你希望函数修改在函数调用中指定的变量所存储的数据，你必须按“引用”传递它。这允许函数直接操作原始数据。当按引用传递时，修改参数会影响变量中的原始数据。为了确保参数始终按引用传递给函数，只需在函数定义中参数名前加上 `&` 与号前缀即可。

![image](images/1o.jpg)
开始一个 PHP 脚本，使用一条语句初始化两个具有相同整数值的变量

```php
<?php
$a = $b = 5 ;
```

![image](images/commono.jpg)

`arguments.php`

![image](images/2o.jpg)
接下来，定义一个函数，接受两个整数参数——一个按值传递，另一个按引用传递

```php
function modify( int $val , int &$ref )
{
 // Statements to be inserted here.
}
```

![image](images/3o.jpg)
现在，插入语句输出传递的值，然后递增这些值并显示修改后的值

```php
echo "Passed values : $val , $ref<br>" ;
$val++ ;
$ref++ ;
echo "Incremented values : $val , $ref<hr>" ;
```

![image](images/4o.jpg)
在函数块之后，添加一条语句调用函数，将变量值作为参数传递

```php
modify( $a , $b ) ;
```

![image](images/5o.jpg)
最后，添加一条语句显示现在存储在每个变量中的值

```php
echo "Stored values : $a , $b" ;
?>
```

![image](images/6o.jpg)
将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `arguments.php`，然后通过 HTTP 打开页面以查看参数和变量值

![image](images/pg77_1.jpg)

![image](images/forget.jpg)

本示例中的 `int` 类型说明指定只有整数数据值可以作为参数传递给函数。

## 可变参数

![image](images/pg78_1.jpg)

函数定义中可以通过为参数名赋值的方式可选地指定默认参数值，如下所示：

```php
function function_name ( $arg_1 , $arg_2 = "Default String" )
{
 statement-to-be-executed ;
 statement-to-be-executed ;
 statement-to-be-executed ;
}
```

这允许进行函数调用，指定一个或两个参数值。如果只指定一个参数，它将被分配给第一个参数，第二参数使用默认值。当为参数指定默认值时，它们必须仅出现在参数列表中位于（右侧）没有指定默认值的参数之后。否则，缺少正确数量参数的调用将导致错误。

![image](images/snake.jpg)

如果指定了多个默认值，目前没有办法在函数调用中跳过某个参数以将参数值分配给特定参数。

如果你需要创建一个函数来接受未知数量的参数，PHP 为此目的提供了一个特殊的 `…` “splat” 运算符。可以在函数定义中使用，如下所示：

```php
function function_name ( ...$args )
{
 statement-to-be-executed ;
 statement-to-be-executed ;
 statement-to-be-executed ;
}
```

当在函数定义中使用 `…` splat 运算符作为参数名前缀时，可以向该参数传递多个参数以创建数组。该数组可以像其他任何数组一样遍历以操作传入的参数值。

![image](images/hot.jpg)

`…` splat 运算符有时也被称为“scatter”运算符。

此外，`…` splat 运算符还可用于“解包”函数调用中指定的数组，将其元素值作为单独的参数传递，如下所示：

```php
function function_name ( $arg_1 , $arg_2 , $arg_3 )
{
 echo $arg_1 + $arg_2 + $arg_3 ;
}
$arr = [ 1 , 2 , 3 ] ;
function_name( ...$arr ) ; # Outputs 6
```

![image](images/1o.jpg)
开始一个 PHP 脚本，通过定义一个为其两个参数提供默认字符串值的函数

```php
<?php
function drink( string $tmp = 'hot' , string $flavor = 'tea' )
{
 // Statement to be inserted here.
}
```

![image](images/commono.jpg)

`parameters.php`

![image](images/2o.jpg)
接下来，插入一条语句以显示其默认值或传入的参数值

```php
echo "Drinking $tmp $flavor.<br>" ;
```

![image](images/3o.jpg)
在函数块之后，添加可选地传递字符串参数的函数调用

```php
drink() ; drink( 'iced' ) ; drink( 'cold' , 'lemonade' ) ;
```

![image](images/4o.jpg)
现在，定义一个函数，可以接受多个整数参数并显示其总值

```php
function add( int ...$numbers )
{
 $total = 0 ;
 foreach( $numbers as $num ) { $total += $num ; }
 echo "<hr>Total : $total" ;
}
```

![image](images/5o.jpg)
最后，在函数块之后添加一条语句以调用上一步中的函数并传递三个值

```php
add( 1 , 2 , 3 ) ;
?>
```

![image](images/6o.jpg)
将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `parameters.php`，然后通过 HTTP 打开页面以查看参数和默认值

![image](images/pg79_1.jpg)

![image](images/hot.jpg)

你可以在使用 `…` splat 运算符接受多个参数的参数之前指定常规位置参数。只有超出位置元素数量的参数才会被添加到最终参数的数组中。

## 命名参数

![image](images/pg78_1.jpg)

函数定义通常包含参数，要求调用者在调用函数时按函数定义中列出的参数顺序传递参数值。因此，这些被称为“位置参数”。

PHP 还支持“命名参数”，允许调用者按任意顺序向函数传递参数值。在这种情况下，调用必须指定每个参数名和参数值，中间用冒号分隔。调用中的参数名是函数定义中指定的参数名——但不带 `$` 前缀。

```php
function function_name ( $arg_1 , $arg_2 )
{
 echo $arg_1 + $arg_2 ;
}
function_name( arg_1 : 'Hot' , arg_2 : 'Tea' ) ; # Outputs Hot Tea
function_name( arg_2 : 'Tea' , arg_1 : 'Hot' ) ; # Outputs Hot Tea
```

当函数定义为参数指定默认值，且调用者未为该参数传递参数值时，将使用默认值，就像调用位置参数时一样。

![image](images/hot.jpg)

命名参数是 PHP 8 中引入的一个很棒的新功能。

使用命名参数可以提高代码可读性，还允许调用者为特定参数传递参数值，同时为其他参数假设默认值。例如，给定一个有两个参数的函数定义，每个参数都有指定的默认值，位置参数调用无法单独为第二个参数指定参数值。它不能跳过第一个参数。另一方面，命名参数调用可以为第二个参数指定参数值，并假设第一个参数的默认值。

```php
function_name( arg_2 : arg_value ) ;
```

你可以在函数调用中使用命名参数和位置参数，但所有位置参数必须出现在命名参数之前。使用命名参数后使用位置参数将导致错误，因为 PHP 解析器无法正确分配参数值。

此外，`…` splat 运算符可用于函数定义中，以收集来自命名参数调用的参数名和值，并且其名称将被保留。

![image](images/1o.jpg)
开始一个 PHP 脚本，通过定义一个为其两个参数提供默认字符串值的函数

```php
<?php
function cook( string $prep = 'fried' , string $food = 'rice' )
{
```
