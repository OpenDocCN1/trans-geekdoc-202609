
## 目录

- 标题页
- 版权页
- PHP 包精通：100 个必备工具一小时掌握 - 2024 版
- 索引
- 第 1 章 引言
- 第 2 章 标准库
- 第 3 章 外部库

## PHP 包最佳 100

### 一小时追看系列

一小时了解 100 个最重要的包的书籍

由 KANRO TOMOYA 撰写

畅销书

## 索引

### 第 1 章 引言

- 1. 目的

### 第 2 章 标准库

- 1. PDO (PHP 数据对象)
- 2. GD 库
- 3. BCMath
- 4. exif
- 5. Phar
- 6. DOMDocument
- 7. DateTime
- 8. hash
- 9. Reflection
- 10. stream_context_create
- 11. imagick
- 12. sockets
- 13. 文件系统函数
- 14. file_exists 和 is_writable
- 15. SPL (标准 PHP 库)
- 16. CURL
- 17. JSON
- 18. 多字节字符串 (mbstring)
- 19. XML 解析器
- 20. SimpleXML
- 21. ZipArchive
- 22. Filter
- 23. PCNTL
- 24. posix
- 25. Intl
- 26. GMP (GNU 多精度)
- 27. mysqli
- 28. ftp
- 29. array_diff
- 30. array_map

### 第 3 章 外部库

- 1. Guzzle
- 2. PHPMailer
- 3. Intervention Image
- 4. PHP dotenv
- 5. Slim Framework
- 6. Laminas
- 7. Twig
- 8. RedBeanPHP
- 9. Phinx
- 10. BulletPHP
- 11. Spatie Image Optimizer
- 12. Barryvdh Laravel Debugbar
- 13. ReactPHP
- 14. Ratchet
- 15. PHPUnit
- 16. Behat
- 17. Carbon
- 18. PHP-DI
- 19. PHP-Scoper
- 20. VichUploaderBundle
- 21. PHP League's Flysystem
- 22. Propel
- 23. Carbon
- 24. Monolog
- 25. Snappy
- 26. PHP League's Glide
- 27. VarDumper
- 28. PsySH
- 29. GuzzleHttp
- 30. PHPMailer
- 31. Aura.Sql
- 32. League\ColorExtractor
- 33. Swoole
- 34. ReactPHP Promise
- 35. Carbon Fields
- 36. Whoops
- 37. Faker
- 38. HTMLPurifier
- 39. PHP League's Plates
- 40. PhpSpreadsheet
- 41. ParagonIE Sodium Compat
- 42. PHPBench
- 43. Imagine
- 44. Faker
- 45. Symfony Security
- 46. Stomp PHP
- 47. Imagine
- 48. PHP League's CSV

## 第 1 章 引言

### 1. 目的

在快速发展的 Web 开发领域中，PHP 仍然是一种核心语言，驱动着互联网的很大一部分。其对初学者的简易性，结合其对高级用户强大的功能，使 PHP 成为各技能水平开发者的多功能选择。

本书旨在通过一种实用方法对 PHP 提供简洁而全面的概述：每个 PHP 开发者都应了解的 100 个必备包。无论你是刚刚起步还是希望扩展技能集，这些包都提供了一系列功能，可以增强你的项目并简化开发流程。

每一章都设计为可在一个小时内消化，确保你能够稳步进展而不感到不知所措。从处理数据库和用户认证到测试和部署，所选的包涵盖了 PHP 开发的各个方面，提供在真实场景中适用的见解和技术。

到本书结束时，你将对 PHP 生态系统及其可用于应对各种挑战的工具有一个扎实的理解。这段旅程不仅会为你提供增强项目的知识，还会激发你在 PHP 开发领域探索新可能性的灵感。

## 第 2 章 标准库

### 1. PDO (PHP 数据对象)

PDO 是一个数据库访问层，提供对多种数据库的统一访问方法。它不提供数据库抽象，但允许统一的接口。

Ex: PDO (PHP 数据对象)

```
// Example: Connecting to a MySQL database using PDO
$dsn = 'mysql:host=localhost;dbname=testdb;charset=utf8';
$user = 'username';
$password = 'password';
try {
$pdo = new PDO($dsn, $user, $password);
echo "Connected successfully";
} catch (PDOException $e) {
echo "Connection failed: " . $e->getMessage();
}
?>
```

连接成功

在此示例中，我们使用 PDO（PHP 数据对象）建立到 MySQL 数据库的连接。首先，我们定义 DSN（数据源名称），其中包括数据库类型（mysql）、主机（localhost）、数据库名称（testdb）和字符集（utf8）。然后，我们指定数据库的用户名和密码。try 块尝试使用提供的 DSN 和凭据创建一个新的 PDO 实例。如果成功，它会打印“Connected successfully”。catch 块捕获类型为 PDOException 的任何异常（如果连接失败则抛出），并打印包含失败原因的错误消息。这种方法对于在保持数据库凭据安全的同时进行调试至关重要。PDO 在不同类型的数据库之间提供一致的接口。这意味着你可以以最少的代码更改从一个数据库切换到另一个数据库，使你的应用程序更具适应性且更易于维护。

### 2. GD 库

GD 库用于动态图像创建。它允许创建、操作和渲染各种格式的图像（JPEG、PNG、GIF 等），使其成为图像处理任务的强大工具。

Ex: GD 库

```
// Creating a simple image with GD Library
header('Content-Type: image/png');
$im = imagecreatetruecolor(100, 100);
$white = imagecolorallocate($im, 255, 255, 255);
$black = imagecolorallocate($im, 0, 0, 0);
// Draw a black rectangle
imagefilledrectangle($im, 0, 0, 99, 99, $black);
// Draw a white ellipse
imageellipse($im, 50, 50, 80, 80, $white);
// Output the image
imagepng($im);
imagedestroy($im);
?>
```

一张 100x100 像素的图像，背景为黑色，中央有一个白色椭圆。

此 PHP 脚本演示了使用 GD 库创建简单图像。过程很简单：

- 设置 Content-Type 头：它告知浏览器服务器将返回图像。在此例中，我们指定 image/png，表示图像格式为 PNG。
- 创建空白图像：`imagecreatetruecolor(100, 100)` 创建一个 100x100 像素的真彩色图像。此函数返回一个图像资源标识符，表示该图像。
- 分配颜色：我们使用 `imagecolorallocate()` 创建可在图像中使用的颜色。在这里，我们通过指定 RGB 值定义白色和黑色。
- 绘制形状：使用图像资源和颜色，我们使用 `imagefilledrectangle()` 等函数在图像上绘制矩形，使用 `imageellipse()` 绘制椭圆。参数定义形状的位置和大小。
- 输出图像：`imagepng($im)` 以 PNG 格式将图像输出到浏览器。
- 清理：`imagedestroy($im)` 释放与图像关联的任何内存。

此示例突出了 GD 库动态创建和操作图像的能力，这对于即时生成图形（如图表、图形或验证码）尤其有用。

### 3. BCMath

BCMath（二进制计算器数学）是一个用于任意精度算术处理的库，特别适用于对大数或需要高精度的运算。

Ex: BCMath

```
// Adding two arbitrary precision numbers
$number1 = '123456789123456789123456789';
$number2 = '987654321987654321987654321';
$sum = bcadd($number1, $number2);
echo $sum;
?>
```

1111111111111111111111111110

在此示例中，我们使用 BCMath 的 bcadd 函数对两个非常大的数字进行加法运算，这些数字标准 PHP 整数类型无法准确表示。$number1 和 $number2 变量存储这些大数字的字符串表示形式，因为 PHP 的整数类型有最大值限制。bcadd 函数将这些字符串表示形式作为输入并返回它们的和作为字符串。这对于金融应用、科学计算或任何需要对非常大的数字保持精度的领域至关重要
