

## 第二章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_66_0.png)

图 2-4

## 工作原理

值 "5" 被赋值给变量 `movierate`，并且它被赋值为一个整数值而不是字符串。接的一行代码将导致 "5" 的值被视为字符串：

```php
$movierate="5";
```

通过将其保持为整数，你之后就可以对这个数字进行数学计算（例如给观众提供平均电影评分），如下例所示：

```php
<?php
$bsomsmovierate=5;
$joesmovierate=7;
$grahamsmovierate=2;
$zabbysmovierate=1;
$avgmovierate=($bsomsmovierate+$joesmovierate+$grahamsmovierate+$zabbysmovierate)/4;
echo "The average movie rating for this movie is: ";
echo $avgmovierate;
?>
```

## 创建 PHP 页面

PHP 还有许多内置数学函数，例如：

- rand(min, max): 生成一个随机整数。
- ceil(number): 将小数向上舍入到下一个最大的整数。
- floor(number): 将小数向下舍入到下一个最小的整数。
- number_format(number, [dec places], [dec point], [thousands]): 根据选择的小位数格式化数字，并使用指定的点和千分位分隔符。
- max(argument1, argument2, ...): 返回所提供参数的最大值。
- min(argument1, argument2, ...): 返回所提供参数的最小值。

要查看 PHP 数学函数的完整列表，请参阅附录 C。

## 在页面之间传递变量

我们讨论过如何在代码中使用变量，但如果能将变量值从一个页面移动到另一个页面不是很好棒吗？有三种方法可以完成此任务，你选择的方法取决于情况以及你当时的需求。

## 关于 register_globals 的说明

在决定三种解析页面的方法之前，理解像 `register_globals` 这样的层次概念是非常重要的。这是你的 `php.ini` 文件中的一个配置设置，当关闭时，它可以防止变量值被外部源错误地插入（从 PHP 4.2 版本开始，PHP 不再需要将其“开启”，默认已切换为“关闭”）。这是许多程序员彻夜工作的原因，因为如果 `register_globals` 关闭，你必须以不同的方式引用你的变量，否则会发现所有变量都是为空的。

虽然许多第三方 Web 主机开启了 `register_globals`，但出于安全考虑，并不是所有人都这样做；我们的决定是，在我们的教程中假设 `register_globals` 是关闭的。

