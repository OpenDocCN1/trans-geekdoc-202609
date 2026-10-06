

# 练习

- 1. 编写一个错误处理函数 `myErrorHandler()`，将任何 `E_WARNING` 或 `E_USER_WARNING` 消息发送到你的电子邮件地址，并将其他错误记录在 `non_serious_errors.log` 文件中。使用同时生成 `E_USER_WARNING` 和 `E_USER_NOTICE` 错误的代码来测试你的处理函数。
- 2. 创建一个 PHPUnit 测试用例，测试第 8 章中 `inheritance.php` 中定义的 `Circle` 类的所有方面。

# 练习答案

## 第2 章
### 练习解答

这里的技巧是再次调用 `date()`，并传入相应的字符来显示当前日期。以下是你可能编写脚本的方式（包括适当的注释）：

```php
<!DOCTYPE html> PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <title>Hello</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>
<?php

// 获取可读格式的当前时间
$currentTime = date("g:i:s a");

// 获取可读格式的当前日期
$currentDate = date("*M, j, Y*");

// 向访问者显示问候、时间和日期
echo "Hello, world! The current time is $currentTime on $currentDate";
?>
</h1>
</body>
</html>
```

# 附录 A：练习答案

## 第3 章

### 练习 1 PHP 解答

编写一个如下的 PHP 脚本：

```php
<?php
$x = 5;
$x = $x + 1;
$x += 1;
$x++;
echo $x;
?>
```

### 练习 2 解答

编写一个如下的 PHP 脚本：

```php
<?php
$x = 3;
$y = 4;
echo "Test 1 result: " . ($x == $y) . "<br />";
echo "Test 2 result: " . ($x > $y) . "<br />";
echo "Test 3 result: " . ($x <= $y) . "<br />";
echo "Test 4 result: " . ($x != $y) . "<br />";
?>
```

## 第4 章

### 练习 1 解答

你可以用多种方式编写此脚本。以下解决方案创建了一个 `for` 循环来计数，然后使用（三元）运算符判断一个数字是奇数、偶数还是质数。

```php
<!DOCTYPE html> PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <title>Testing the Numbers 1-10</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Testing the Numbers 1-10</h1>

<table border="1">
<tr>
<th>Number</th>
<th>Odd or Even?</th>
<th>Prime?</th>
</tr>
<?php
for ($i = 1; $i <= 10; $i++) {
  $oddEven = ($i % 2 == 0) ? "Even" : "Odd";
  switch ($i) {
    case 2:
    case 3:
    case 5:
    case 7:
      $prime = "Yes";
      break;
    default:
      $prime = "No";
  }
  echo "<tr>
    <td>$i</td>
    <td>$oddEven</td>
    <td>$prime</td>
  </tr>";
}
?>
</table>
</body>
</html>
```

