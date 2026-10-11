# PHP 与 MySQL：从入门到精通的完整指南 —— 详解 PHP 编程掌握之道




## 第 88 章：`PSR`

#### 第 88.1 节：`PSR-4`：自动加载器

#### 第 88.2 节：`PSR-1`：基础编码标准

## 第 89 章：`PHPDoc`

#### 第 89.1 节：描述变量

#### 第 89.2 节：为函数添加元数据

#### 第 89.3 节：描述参数

#### 第 89.4 节：集合

#### 第 89.5 节：为文件添加元数据

#### 第 89.6 节：从父结构继承元数据

## 第 90 章：设计模式

#### 第 90.1 节：PHP 中的方法链

## 第 91 章：编译 `PHP` 扩展

#### 第 91.1 节：在 `Linux` 上编译

## 第 92 章：常见错误

#### 第 92.1 节：在布尔值上调用 `fetch_assoc`

#### 第 92.2 节：意外的 `$end`

## 第 93 章：错误和警告汇编

#### 第 93.1 节：解析错误：语法错误，意外的 `T_PAAMAYIM_NEKUDOTAYIM`

#### 第 93.2 节：通知：未定义索引

#### 第 93.3 节：警告：无法修改标头信息 - 标头已发送

## 第 94 章：异常处理和错误报告

#### 第 94.1 节：设置错误报告及显示位置

#### 第 94.2 节：记录致命错误

## 第 95 章：调试

#### 第 95.1 节：转储变量

#### 第 95.2 节：显示错误

#### 第 95.3 节：`phpinfo()`

#### 第 95.4 节：`Xdebug`

#### 第 95.5 节：错误报告（两者皆用）

#### 第 95.6 节：`phpversion()`

## 第 96 章：单元测试

#### 第 96.1 节：测试类规则

#### 第 96.2 节：`PHPUnit` 数据提供者

#### 第 96.3 节：测试异常

## 第 97 章：性能

#### 第 97.1 节：使用 `Xdebug` 进行性能分析

#### 第 97.2 节：内存使用

#### 第 97.3 节：使用 `XHProf` 进行性能分析

## 第 98 章：多进程

#### 第 98.1 节：使用内置 fork 函数进行多进程处理

#### 第 98.2 节：使用 `fork` 创建子进程

#### 第 98.3 节：进程间通信

## 第 99 章：多线程扩展

#### 第 99.1 节：入门

#### 第 99.2 节：使用池和工作进程

## 第 100 章：安全的记住我功能

#### 第 100.1 节：“保持登录状态” - 最佳实践

## 第 101 章：安全

#### 第 101.1 节：`PHP` 版本泄露

#### 第 101.2 节：跨站脚本攻击 (`XSS`)

#### 第 101.3 节：跨站请求伪造

#### 第 101.4 节：命令行注入

#### 第 101.5 节：剥离标签

#### 第 101.6 节：文件包含

#### 第 101.7 节：错误报告

#### 第 101.8 节：上传文件

## 第 102 章：密码学

#### 第 102.1 节：使用 `OpenSSL` 对大文件进行对称加密和解密

#### 第 102.2 节：对称密码

## 第 103 章：密码哈希函数

#### 第 103.1 节：创建密码哈希

#### 第 103.2 节：确定现有密码哈希是否可升级至更强算法

#### 第 103.3 节：验证密码是否匹配哈希值

## 第 104 章：为 `PHP` 手册做贡献

#### 第 104.1 节：改进官方文档

#### 第 104.2 节：为手册做贡献的技巧

## 第 105 章：为 `PHP` 核心做贡献

#### 第 105.1 节：搭建基础开发环境

## 附录 A：在 `Windows` 上安装 `PHP` 环境

#### 第 A.1 节：下载、安装和使用 `WAMP`

#### 第 A.2 节：安装 `PHP` 并配合 `IIS` 使用

#### 第 A.3 节：下载并安装 `XAMPP`

## 附录 B：在 `Linux/Unix` 环境上安装

#### 第 B.1 节：使用 `APT` 通过命令行安装 `PHP 7`

#### 第 B.2 节：在企业级 `Linux` 发行版中安装（`CentOS`、`Scientific Linux` 等）

## 致谢

## 您可能还喜欢

## 第 1 章：`PHP` 入门

#### 第 1.1 节：Web 服务器的 `HTML` 输出



# PHP 基础

PHP 可用于向 HTML 文件添加内容。HTML 由 Web 浏览器直接处理，而 PHP 脚本由 Web 服务器执行，生成的 HTML 发送给浏览器。

## Hello World

以下 HTML 标记包含一条将内容添加到输出的 PHP 语句：

```php
<?php echo "Hello World!"; ?>
```

将其保存为 PHP 脚本并由 Web 服务器执行时，将向用户浏览器发送以下 HTML：

```html
Hello World!
```

### PHP 5.4+ 版本

`echo` 还有一种快捷语法，可让你立即打印值。在 PHP 5.4.0 之前，此短语法仅在启用 `short_open_tag` 配置设置时有效。

例如，以下代码：

```php
<?= "Hello World!" ?>
```

其输出与以下代码相同：

```php
<?php echo "Hello World!"; ?>
```

在实际应用中，PHP 输出到 HTML 页面的所有数据都应正确转义，以防止 XSS（跨站脚本）攻击或文本损坏。

```php
<?= ... ?>
```

另请参阅：字符串和 [PSR-1](http://www.php-fig.org/psr/psr-1/)，其中描述了最佳实践，包括短标签的正确使用。

## Section 1.2: Hello, World!

PHP 中用于打印输出的最常用语言结构是 `echo`：

```php
echo "Hello World!";
```

或者，也可以使用 `print`：

```php
print "Hello World!";
```

两者功能相同，细微差别如下：

| 特性 | `echo` | `print` |
| :--- | :--- | :--- |
| 返回值 | 无返回值 | 返回值为 1 的 `int` |
| 参数 | 可接受多个参数（仅限无括号） | 仅接受单个参数 |
| 速度 | 略快 | 较慢 |

`echo` 和 `print` 都是语言结构，而非函数。因此，它们不需要在参数周围加括号。为与函数保持外观一致，可加上括号。关于 `echo` 和 `print` 的大量示例请参阅其他资料。

C 风格的 `printf` 及相关函数也可用，示例如下：

```php
printf("Hello %s!", "World");
```

请参阅“输出变量的值”，以全面了解 PHP 中输出变量的方法。

## Section 1.3: Web 服务器的非 HTML 输出

在某些情况下，使用 Web 服务器时，可能需要覆盖 Web 服务器的默认内容类型。

例如，你可能需要以纯文本、JSON 或 XML 形式发送数据。

`header()` 函数可发送原始 HTTP 头。你可以添加 `Content-Type` 头以通知浏览器发送的内容类型。

### 纯文本

```php
header("Content-Type: text/plain");
echo "Hello World";
```

这将生成包含以下内容的纯文本文档：

```text
Hello World
```

### JSON

要生成 JSON 内容，请改用 `application/json` 内容类型：

```php
header("Content-Type: application/json");
echo json_encode(["response" => "Hello World"]);
```

这将生成类型为 `application/json` 的文档，内容如下：

```json
{"response":"Hello World"}
```

> **注意**：`header()` 函数必须在 PHP 产生任何输出之前调用，否则 Web 服务器将已发送响应头。

例如以下代码：

```php
echo "Hello World";
header("Content-Type: text/plain");
```

将产生警告：

```text
Warning: Cannot modify header information - headers already sent by (output started at /dir/example.php:2) in /dir/example.php on line 3
```

使用 `header()` 时，其输出必须是服务器发送的第一个字节。因此，在 PHP 开启标签 `<?php` 之前，文件开头不得有空行或空格。出于同一原因，最佳实践（见 [PSR-2](http://www.php-fig.org/psr/psr-2/#2-2-files)）建议省略仅包含 PHP 的文件或文件末尾 PHP 代码块的关闭标签 `?>`。

请参阅输出缓冲部分，了解如何将内容“捕获”到变量中以便稍后输出（例如在输出头之后）。

## Section 1.4: PHP 内置服务器

PHP 5.4+ 自带内置开发服务器。无需安装 nginx 或 Apache 等生产级 HTTP 服务器即可运行应用程序。内置服务器仅用于开发和测试。

可使用 `-S` 标志启动：

```bash
php -S <host/ip>:<port>
```

### 示例用法

1. 创建 `index.php` 文件，内容如下：

```php
<?php echo "Hello World!"; ?>
```

2. 在命令行运行以下命令（勿包含 `http://`）：

```bash
php -S localhost:8080
```

这将启动一个 Web 服务器，在当前目录作为文档根目录的情况下监听 8080 端口。

3. 打开浏览器访问 `http://localhost:8080`。你应该能看到 "Hello World" 页面。

### 配置

要覆盖默认文档根目录（即当前目录），请使用 `-t` 标志：

```bash
php -S localhost:8080 -t public
```

例如，如果项目中有 `public/` 目录，可使用该命令从该目录提供服务。

### 日志

每次从开发服务器发出请求时，都会向命令行写入如下日志条目：

```text
[Mon Aug 15 18:20:19 2022] 127.0.0.1:54321 [200]: /index.php
```

## Section 1.5: PHP CLI

PHP 也可通过 CLI（命令行界面）直接从命令行运行。

CLI 基本与 Web 服务器上的 PHP 相同，除标准输入输出方面存在差异外。

### 触发方式

PHP CLI 提供四种运行 PHP 代码的方式：

1. **标准输入**。运行 `php` 命令且不带参数，但通过管道传入 PHP 代码：
   ```bash
   echo '<?php echo "Hello world!";' | php
   ```

2. **文件名作为参数**。运行 `php` 命令，首个参数为 PHP 源文件名：
   ```bash
   php hello_world.php
   ```

3. **代码作为参数**。在 `php` 命令中使用 `-r` 选项，后跟要运行的代码。不需要 `<?php` 开启标签，因为参数中的所有内容均视为 PHP 代码：
   ```bash
   php -r 'echo "Hello world!";'
   ```

4. **交互式 Shell**。在 `php` 命令中使用 `-a` 选项启动交互式 Shell。然后输入（或粘贴）PHP 代码并按回车：
   ```bash
   $ php -a
   Interactive mode enabled
   php > echo "Hello world!";
   Hello world!
   ```

##### 输出

Web 服务器 PHP 中产生 HTML 输出的所有函数或控制，在 CLI 中均可用于向 stdout 流（文件描述符 1）产生输出；Web 服务器 PHP 中产生错误日志输出的所有操作，在 CLI 中均会向 stderr 流（文件描述符 2）产生输出。

```php
fwrite(STDOUT, "Standard output\n");
fwrite(STDERR, "Error output\n");
```

### Shell 命令行

```bash
php script.php > output.log 2> error.log
```

### 输入

请参阅：命令行界面 (CLI)

## Section 1.6: 指令分隔

与大多数其他 C 风格语言一样，每条语句以分号终止。此外，关闭标签用于终止 PHP 代码块的最后一行代码。

```php
echo "No error";
```

如果 PHP 代码的最后一行以分号结尾，且该行后面没有其他代码，则关闭标签是可选的。例如，以下示例中 `;` 后可省略关闭标签：

```php
<?php echo "No error" ; // no closing tag is needed as long as there is no code below
```

但是，如果 PHP 代码块后面还有其他代码，则关闭标签不再是可选的：

```php
<?php echo "This will cause an error if closing tag is omitted" ?>
<html>
<body>
...
```



![](img/Image00023.jpg)

如果该 PHP 代码块有结束标签，我们也可以省略该代码块中最后一条语句的分号：

![](img/Image00024.jpg)

通常建议始终使用分号，并为每个 PHP 代码块使用结束标签，最后一个 PHP 代码块除外（如果该 PHP 代码块后面没有更多代码）。

因此，你的代码基本上应该如下所示：

![](img/Image00025.jpg)

#### 第 1.7 节：PHP 标签

文件中有三种标签用于标记 PHP 代码块。PHP 解析器会寻找开始标签和（如果存在）结束标签，以界定需要解析的代码。

### 标准标签

这些标签是在文件中嵌入 PHP 代码的标准方法。

![](img/Image00026.jpg)

**PHP 5.x 版本 ≥ 5.4**

### Echo 标签

这些标签在所有 PHP 版本中均可用，且自 PHP 5.4 起始终启用。在早期版本中，echo 标签只能结合短标签一起启用。

![](img/Image00027.jpg)

### 短标签

你可以使用选项 `short_open_tag` 来禁用或启用这些标签。

![](img/Image00028.jpg)

短标签：

![](img/Image00029.jpg)

- 在所有主要的 PHP [编码标准](http://www.php-fig.org/psr/psr-1/) 中均被禁止
- [官方文档](https://secure.php.net/manual/en/language.basic-syntax.phptags.php) 不建议使用
- 在大多数发行版中默认禁用
- 会干扰内联 XML 的处理指令
- 大多数开源项目的代码提交不接受短标签

### PHP 5.x 版本 ≤ 5.6 ASP 标签

通过启用 `asp_tags` 选项，可以使用 ASP 风格的标签。

![](img/Image00030.jpg)

这是一种历史遗留的怪癖，**永远不应该**使用。它们已在 PHP 7.0 中移除。

## 第 2 章：变量

#### 第 2.1 节：按名称动态访问变量（变量变量）

变量可以通过动态变量名来访问。变量的名称可以存储在另一个变量中，从而允许动态访问。这种变量被称为变量变量。

要将一个变量转变为变量变量，你需要在变量前加上一个额外的 `$`。

![](img/Image00031.jpg)

变量变量对于映射函数/方法调用很有用：

![](img/Image00032.jpg)

这在 PHP 类中变得特别有用：

![](img/Image00033.jpg)

将 `$variableName` 放在 `{}` 之间是可能的，但不是必须的：

![](img/Image00034.jpg)

以下两个示例是等效的，都输出 "baz"：

![](img/Image00035.jpg)

![](img/Image00036.jpg)

仅当变量名本身是一个表达式时，使用 `{}` 才是强制性的，如下所示：

![](img/Image00037.jpg)

不过，仍然建议始终使用 `{}`，因为它的可读性更好。

虽然不建议这样做，但可以链式调用此行为：

```
$$$$$$$$DoNotTryThisAtHomeKids = $value ;
```

![](img/Image00038.jpg)

重要的是要注意，许多开发人员认为过度使用变量变量是一种不良实践。因为它们不适合现代 IDE 进行静态分析，包含许多变量变量（或动态方法调用）的大型代码库会迅速变得难以维护。

##### PHP5 和 PHP7 之间的差异

始终使用 `{}` 或 `()` 的另一个原因是，PHP5 和 PHP7 处理动态变量的方式略有不同，这在某些情况下会导致不同的结果。

在 PHP7 中，动态变量、属性和方法现在将严格按从左到右的顺序求值，这与 PHP5 中的特殊情况混合处理形成对比。以下示例展示了求值顺序是如何改变的。

##### 情况 1：`$$foo['bar']['baz']`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$$foo['bar']['baz']` | `${$foo['bar']['baz']}` | `($$foo)['bar']['baz']` |
| `$foo['bar']['baz']` | `$foo['bar']['baz']` | `$foo['bar']['baz']` |
| `($$foo)['bar']['baz']` | `${$foo['bar']['baz']}` | `($$foo)['bar']['baz']` |

![](img/Image00039.jpg)

##### 情况 2：`$foo->$bar['baz']`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$foo->$bar['baz']` | `$foo->{$bar['baz']}` | `($foo->$bar)['baz']` |
| `$foo->{$bar['baz']}` | `$foo->{$bar['baz']}` | `$foo->{$bar['baz']}` |
| `($foo->$bar)['baz']` | `$foo->{$bar['baz']}` | `($foo->$bar)['baz']` |

![](img/Image00040.jpg)

##### 情况 3：`$foo->$bar['baz']()`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$foo->$bar['baz']()` | `$foo->{$bar['baz']}()` | `($foo->$bar)['baz']()` |
| `$foo->{$bar['baz']}()` | `$foo->{$bar['baz']}()` | `$foo->{$bar['baz']}()` |
| `($foo->$bar)['baz']()` | `$foo->{$bar['baz']}()` | `($foo->$bar)['baz']()` |

![](img/Image00041.jpg)

##### 情况 4：`Foo::$bar['baz']()`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `Foo::$bar['baz']()` | `Foo::{$bar['baz']}()` | `(Foo::$bar)['baz']()` |
| `Foo::{$bar['baz']}()` | `Foo::{$bar['baz']}()` | `Foo::{$bar['baz']}()` |
| `(Foo::$bar)['baz']()` | `Foo::{$bar['baz']}()` | `(Foo::$bar)['baz']()` |

![](img/Image00042.jpg)

#### 第 2.2 节：数据类型

针对不同目的有不同的数据类型。PHP 没有显式的类型定义，变量的类型由赋给它的值的类型决定，或者由它被转换成的类型决定。这是关于类型的简要概述，详细文档和示例请参阅 PHP 类型主题。

PHP 中有以下数据类型：`null`、`boolean`、`integer`、`float`、`string`、`object`、`resource` 和 `array`。

##### Null

`Null` 可以赋值给任何变量。它表示一个没有值的变量。

![](img/Image00043.jpg)

这会使变量失效，如果调用它，其值将是未定义或空的。变量将从内存中清除并由垃圾回收器删除。

##### Boolean

这是最简单的类型，只有两个可能的值。

![](img/Image00044.jpg)

布尔值可用于控制代码流程。

![](img/Image00045.jpg)

##### Integer

整数是正或负的整数。它可以用于任何数制。整数的大小取决于平台。PHP 不支持无符号整数。

![](img/Image00046.jpg)

##### Float

浮点数、"双精度数"或简称为"浮点数"是十进制数字。

![](img/Image00047.jpg)

##### Array

数组就像一个值列表。数组最简单的形式是由整数索引，并按索引排序，第一个元素位于索引 0 处。

```
$foo = array(1, 2, 3); // 一个整数数组
```

![](img/Image00048.jpg)

```
$bar = ["A", true, 123 => 5]; // 短数组语法，PHP 5.4+
```

![](img/Image00049.jpg)

数组也可以将非整数索引的键关联到一个值。在 PHP 中，所有数组在底层都是关联数组，但当我们专门提到“关联数组”时，通常指包含一个或多个非整数键的数组。

![](img/Image00050.jpg)

##### String

字符串就像一个字符数组。

![](img/Image00051.jpg)

像数组一样，字符串可以被索引以返回其单个字符：

![](img/Image00052.jpg)

##### Object

对象是类的实例。其变量和方法可以通过 `->` 运算符访问。

![](img/Image00053.jpg)

##### Resource

资源变量持有打开的文件、数据库连接、流、图像画布区域等的特殊句柄（正如[手册](https://secure.php.net/manual/en/language.types.resource.php#language.types.resource.casting)中所述）。

```
$fp = fopen('file.ext', 'r'); // fopen() 是在磁盘上将文件作为资源打开的函数。
var_dump($fp); // 输出：resource(2) of type (stream)
```

##### `gettype`

要以字符串形式获取变量的类型，请使用 `gettype()` 函数：

![](img/Image00055.jpg)

#### 第 2.3 节：全局变量最佳实践

我们可以用以下伪代码来说明这个问题：

![](img/Image00056.jpg)

你的第一个问题显而易见：

![](img/Image00057.jpg)

`$bob` 是从哪来的？

你困惑了吗？很好。你刚刚了解了为什么全局变量令人困惑，并被视为不良实践。

如果这是一个真实的程序，你接下来的“乐趣”就是去追踪所有 `$bob` 的实例，并希望你能找到正确的那个（如果 `$bob` 到处都在用，情况会更糟）。更糟的是，如果其他人定义了 `$bob`（或者你忘记了并重用了该变量），你的代码可能会崩溃（在上面的代码示例中，拥有错误的对象或根本没有对象会导致致命错误）。




# PHP 变量与作用域

##### 包含文件与全局变量的问题

```php
include 'file.php';
```

由于几乎所有 PHP 程序都使用类似 `);` 的代码，随着文件数量的增加，维护此类代码的难度将呈指数级上升。

此外，这使得应用程序测试变得非常困难。假设你使用全局变量来保存数据库连接：

![Image00058.jpg](img/Image00058.jpg)

为了单元测试此函数，你必须覆盖全局变量 `$dbConnector`，运行测试，然后将其重置为原始值，这非常容易出错：

![Image00059.jpg](img/Image00059.jpg)

##### 如何避免全局变量？

避免全局变量的最佳方式是一种称为 **依赖注入** 的理念。即将所需的工具（依赖）传递给函数或类。

![Image00060.jpg](img/Image00060.jpg)

这更易于理解和维护。无需猜测 `$bob` 在哪里被设置，因为调用者负责知道这一点（它将我们所需的内容传递给我们）。更棒的是，我们可以使用 [类型声明](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) 来限制传入的内容。

因此我们知道 `$bob` 要么是 `Bar` 类的实例，要么是 `Bar` 子类的实例，这意味着我们知道可以使用该类的方法。结合标准自动加载器（自 PHP 5.3 起可用），我们现在可以追踪 `Bar` 的定义位置。PHP 7.0 或更高版本包含扩展的类型声明，你也可以使用标量类型（如 `int` 或 `string`）。

> Version = 4.1

##### 超全局变量

PHP 中的超全局变量是预定义变量，始终可用，可在脚本的任何作用域中访问。

无需执行 `global $variable;` 即可在函数/方法、类或文件中访问它们。

以下是 PHP 超全局变量列表：

![Image00061.jpg](img/Image00061.jpg) [$GLOBALS](http://php.net/manual/en/reserved.variables.globals.php)

[$_SERVER](http://php.net/manual/en/reserved.variables.server.php)

[$_REQUEST](http://php.net/manual/en/reserved.variables.request.php)

[$_POST](http://php.net/manual/en/reserved.variables.post.php)

[$_GET](http://php.net/manual/en/reserved.variables.get.php)

[$_FILES](http://php.net/manual/en/reserved.variables.files.php)

[$_ENV](http://php.net/manual/en/reserved.variables.environment.php)

[$_COOKIE](http://php.net/manual/en/reserved.variables.cookies.php)

[$_SESSION](http://php.net/manual/en/reserved.variables.session.php)

## Section 2.4: 未初始化变量的默认值

虽然在 PHP 中并非强制要求，但初始化变量是一个非常好的实践。未初始化变量根据其使用上下文，具有其类型的默认值：

##### Unset AND unreferenced

![Image00062.jpg](img/Image00062.jpg)

##### Boolean

![Image00063.jpg](img/Image00063.jpg)

##### String

![Image00064.jpg](img/Image00064.jpg)

##### Integer

![Image00065.jpg](img/Image00065.jpg)

##### Float/double

![Image00066.jpg](img/Image00066.jpg)

##### Array

![Image00067.jpg](img/Image00067.jpg)

##### Object

```php
$unset_obj->foo = 'bar';
var_dump($unset_obj); // Outputs: object(stdClass)#1 (1) { ["foo"]=> string(3) "bar" }
```

![Image00068.jpg](img/Image00068.jpg)

依赖未初始化变量的默认值在将一个文件包含到另一个使用相同变量名的文件中时会有问题。

## Section 2.5: 变量值的真假性与全等运算符

在 PHP 中，变量值具有关联的“真假性”，因此即使是非布尔值也会等同于 `true` 或 `false`。这允许在条件块中使用任何变量，例如：

![Image00069.jpg](img/Image00069.jpg)

以下是不同类型变量值的一些基本规则：

![Image00070.jpg](img/Image00070.jpg)

![Image00071.jpg](img/Image00071.jpg)

```php
floatval('0') == floatval('-0')
```

在其双精度浮点数表示中，即 `)` 为 `true`。

![Image00072.jpg](img/Image00072.jpg)

##### 全等运算符

在 [PHP 文档比较运算符](http://php.net/manual/en/language.operators.comparison.php) 中，有一个全等运算符 `===`。该运算符可用于检查变量是否与参考值完全相同：

![Image00073.jpg](img/Image00073.jpg)

它有一个对应的不全等运算符 `!==`：

![Image00074.jpg](img/Image00074.jpg)

| is_null |
| --- |

全等运算符可作为语言函数（如 `()`）的替代方案。

| strpos |
| --- |

##### USE CASE WITH `strpos()`

```php
strpos($haystack, $needle)
```

| strpos |
| --- |

`strpos()` 语言函数用于定位 `$needle` 在 `$haystack` 中出现的索引位置，或判断其是否出现。`strpos()` 函数区分大小写；如果需要不区分大小写的查找，可以使用 `stripos()`。

```php
stripos($haystack, $needle)
```

`strpos` 和 `stripos` 函数还包含第三个参数 `offset` (int)，如果指定，搜索将从字符串开头开始计算的该字符数处开始。与 `strrpos` 和 `strripos` 不同，`offset` 不能为负数。

该函数可返回：

![Image00075.jpg](img/Image00075.jpg)
- 如果 `$needle` 在 `$haystack` 开头找到，返回 `0`；
- 如果在开头以外位置找到，返回非零整数索引；
- 如果未找到，返回 `false`。

| strpos |
| --- |

由于在 PHP 中 `0` 和 `false` 的真假性均为 `false`，但代表 `strpos()` 的不同情况，因此区分它们并使用全等运算符 `===` 精确查找 `false` 而非仅等同于 `false` 的值非常重要。

![Image00076.jpg](img/Image00076.jpg)

或者，使用不全等运算符：

![Image00077.jpg](img/Image00077.jpg)

# Chapter 3: 变量作用域

变量作用域指代码中可访问变量的区域，也称为可见性。在 PHP 中，作用域块由函数、类以及整个应用程序可用的全局作用域定义。

## Section 3.1: 超全局变量

超全局变量由 PHP 定义，无需 `global` 关键字即可从任何地方使用。

![Image00078.jpg](img/Image00078.jpg)

## Section 3.2: 静态属性与变量

定义为 `public` 可见性的静态类属性在功能上等同于全局变量。可从定义该类的任何位置访问。

![Image00079.jpg](img/Image00079.jpg)

函数也可在其自身作用域内定义静态变量。这些静态变量会在多次函数调用中持久化，这与函数作用域中定义的常规变量不同。这是实现单例设计模式的一种非常简单易用的方法：

```php
class Singleton {
    public static function getInstance() {
        // Static variable $instance is not deleted when the function ends
        static $instance;

        // Second call to this function will not get into the if-statement,
        // Because an instance of Singleton is now stored in the $instance
        // variable and is persisted through multiple calls
        if (!$instance) {
            // First call to this function will reach this line,
            // because the $instance has only been declared, not initialized
            $instance = new Singleton();
        }
    }
}
```

![Image00080.jpg](img/Image00080.jpg)
![Image00081.jpg](img/Image00081.jpg)

## Section 3.3: 用户定义的全局变量

任何函数或类之外的作用域均为全局作用域。当 PHP 脚本包含另一个脚本（使用 `include` 或 `require`）时，作用域保持不变。如果脚本在函数或类外部被包含，其全局变量将包含在同一全局作用域中；但如果脚本从函数内部被包含，则被包含脚本中的变量处于该函数的作用域内。

在函数或类方法的作用域内，可使用 `global` 关键字来访问用户定义的全局变量。

![Image00082.jpg](img/Image00082.jpg)

访问全局作用域变量的第二种方法是使用 PHP 预定义的特殊 `$GLOBALS` 数组。




`$GLOBALS` 数组是一个关联数组，全局变量的名称作为键，该变量的内容作为数组元素的值。请注意 `$GLOBALS` 存在于任何作用域中，这是因为 `$GLOBALS` 是一个超全局变量。

| log_message |
| --- |

这意味着 `log_message()` 函数可以重写为：

```
function log_message ( $message ) {
    // 通过 $GLOBALS 数组访问全局 $amount_of_log_calls 变量。无需 'global $GLOBALS;'，因为它
}
```

有人可能会问，既然 `global` 关键字也可以用来获取全局变量的值，为什么还要使用 `$GLOBALS` 数组？主要原因是使用 `global` 关键字会将变量引入当前作用域。这样你就无法在局部作用域中重复使用相同的变量名。

## 第 4 章：PHP 超全局变量

超全局变量是内置变量，它们在所有作用域中始终可用。

| global $variable |
| --- |

PHP 中的几个预定义变量是“超全局”的，这意味着它们在脚本的所有作用域中都可用。无需执行 `global $variable;` 即可在函数或方法中访问它们。

#### 第 4.1 节：超全局变量详解

##### 简介

简单来说，这些变量在你的脚本的所有作用域中都可用。

这意味着不需要将它们作为参数传递给函数，也不需要将它们存储在代码块外部以便在不同作用域中使用。

##### 什么是超全局变量？？

如果你认为它们像超级英雄——它们不是。

截至 PHP 7.1.3 版本，共有 9 个超全局变量。它们如下：

*   `$GLOBALS` \- 引用全局作用域中所有可用的变量
*   `$_SERVER` \- 服务器和执行环境信息
*   `$_GET` \- HTTP GET 变量
*   `$_POST` \- HTTP POST 变量
*   `$_FILES` \- HTTP 文件上传变量
*   `$_COOKIE` \- HTTP Cookies
*   `$_SESSION` \- Session 变量
*   `$_REQUEST` \- HTTP 请求变量
*   `$_ENV` \- 环境变量

请参阅 [文档](http://php.net/manual/en/language.variables.superglobals.php)。

Tell me more, tell me more

抱歉引用了《Grease》（注：音乐剧/电影《油脂》中的歌词）！[链接](https://www.youtube.com/watch?v=ZW0DfsCzfq4)

是时候对这些“超级英雄全局变量”进行一些解释了。

##### $GLOBALS

一个关联数组，包含对当前脚本全局作用域中定义的所有变量的引用。变量名是数组的键。

##### 代码

```
<?php
$myGlobal = "global";
function test() {
    $myLocal = "local";
    var_dump($GLOBALS);
}
test();
?>
```

##### 输出

```
array(2) {
  ["myGlobal"]=>
  string(6) "global"
  ["myLocal"]=>
  string(5) "local"
}
```

| test |
| --- |

在上面的示例中，`$myLocal` 第二次没有显示，因为它是在 `test()` 函数内部声明的，并在函数结束后被销毁。

##### 变为全局

为了解决这个问题，有两种选择。

```
global $myLocal;
$myLocal = "local";
```

`global` 关键字是变量的前缀，强制其成为全局作用域的一部分。

请注意，你不能在同一语句中使用 `global` 关键字的同时给变量赋值。因此，我不得不在下面单独赋值。（如果你去掉换行和空格也是可以的，但我不认为这很整洁。`global $myLocal; $myLocal = "local";`）。

```
$GLOBALS["myLocal"]
```

在这个例子中，我将 `$myLocal` 重新赋值为 `$GLOBALS["myLocal"]`，因为我发现写变量名比写关联数组更容易。

##### $_SERVER

`$_SERVER` 是一个包含诸如头信息、路径和脚本位置等信息的数组。该数组中的条目由 Web 服务器创建。无法保证每个 Web 服务器都会提供所有这些信息；服务器可能会省略某些条目，或提供此处未列出的其他条目。尽管如此，这些变量中的很大一部分在 [CGI/1.1 规范](http://www.faqs.org/rfcs/rfc3875) 中都有规定，所以你可以期望这些变量存在。

其输出示例可能如下所示（在我的 Windows PC 上使用 WAMP 运行）

```
C:\wamp64\www\test.php:2:
array (size=36)
  'HTTP_HOST' => string 'localhost' (length=9)
  'HTTP_CONNECTION' => string 'keep-alive' (length=10)
  'HTTP_CACHE_CONTROL' => string 'max-age=0' (length=9)
  'HTTP_UPGRADE_INSECURE_REQUESTS' => string '1' (length=1)
  'HTTP_USER_AGENT' => string 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Safari/537.36' (length=110)
  'HTTP_ACCEPT' => string 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' (length=74)
  'HTTP_ACCEPT_ENCODING' => string 'gzip, deflate, sdch, br' (length=23)
  'HTTP_ACCEPT_LANGUAGE' => string 'en-US,en;q=0.8,en-GB;q=0.6' (length=26)
  'HTTP_COOKIE' => string 'PHPSESSID=0gslnvgsci371ete9hg7k9ivc6' (length=36)
  'PATH' => string 'C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files (x86)\Intel\iCLS Client\;C:\Program Files\Intel\iCLS Client\;C:\ProgramData\Oracle\Java\javapath;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\;E:\Program Files\ATI Technologies\ATI.ACE\Core-Static;E:\Program Files\AMD\ATI.ACE\Core-Static;C:\Program Files (x86)\AMD\ATI.ACE\Core-Static;C:\Program Files (x86)\ATI Technologies\ATI.ACE\Core-Static;C:\Program Files\Intel\Intel(R) Managemen'... (length=1169)
  'SystemRoot' => string 'C:\WINDOWS' (length=10)
  'COMSPEC' => string 'C:\WINDOWS\system32\cmd.exe' (length=27)
  'PATHEXT' => string '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.PY' (length=57)
  'WINDIR' => string 'C:\WINDOWS' (length=10)
  'SERVER_SIGNATURE' => string '<address>Apache/2.4.23 (Win64) PHP/7.0.10 Server at localhost Port 80</address>' (length=80)
  'SERVER_SOFTWARE' => string 'Apache/2.4.23 (Win64) PHP/7.0.10' (length=32)
  'SERVER_NAME' => string 'localhost' (length=9)
  'SERVER_ADDR' => string '::1' (length=3)
  'SERVER_PORT' => string '80' (length=2)
  'REMOTE_ADDR' => string '::1' (length=3)
  'DOCUMENT_ROOT' => string 'C:/wamp64/www' (length=13)
  'REQUEST_SCHEME' => string 'http' (length=4)
  'CONTEXT_PREFIX' => string '' (length=0)
  'CONTEXT_DOCUMENT_ROOT' => string 'C:/wamp64/www' (length=13)
  'SERVER_ADMIN' => string 'wampserver@wampserver.invalid' (length=29)
  'SCRIPT_FILENAME' => string 'C:/wamp64/www/test.php' (length=26)
  'REMOTE_PORT' => string '5359' (length=4)
  'GATEWAY_INTERFACE' => string 'CGI/1.1' (length=7)
  'SERVER_PROTOCOL' => string 'HTTP/1.1' (length=8)
  'REQUEST_METHOD' => string 'GET' (length=3)
  'QUERY_STRING' => string '' (length=0)
  'REQUEST_URI' => string '/test.php' (length=13)
  'SCRIPT_NAME' => string '/test.php' (length=13)
  'PHP_SELF' => string '/test.php' (length=13)
  'REQUEST_TIME_FLOAT' => float 1491068771.413
  'REQUEST_TIME' => int 1491068771
```

这里有大量信息需要消化，所以我将在下面挑选一些重要的。如果你想了解所有变量，请查阅文档的 [索引部分](http://php.net/manual/en/reserved.variables.server.php#refsect1-reserved.variables.server-indices)。

也许有一天我会把它们都加上。或者有人可以编辑并在下面添加好的解释？暗示，暗示 ;) 对于下面所有的解释，假设 URL 为 [`www.example.com/index.php`](http://www.example.com/index.php)

##### HTTP_HOST \- 主机地址。

```
www.example.com
```

这将返回

```
93.184.216.34
```

##### SCRIPT_NAME \- 当前脚本的路径。

```
/index.php
```



# PHP 超全局变量

##### HTTP_USER_AGENT
用户代理的内容。这是一个字符串，包含关于客户端浏览器的所有信息，包括操作系统。

##### HTTP_COOKIE
所有 Cookie 连接成的一个字符串，以分号作为分隔符。

##### SERVER_ADDR
当前脚本运行所在服务器的 IP 地址。

##### PHP_SELF
当前执行脚本的文件名，相对于文档根目录。

这将返回 `/`

##### REQUEST_TIME_FLOAT
请求开始的时间戳，具有微秒精度。自 PHP 5.4.0 起可用。

##### REQUEST_TIME
请求开始的时间戳。自 PHP 5.1.0 起可用。

##### $_GET
![](img/Image00097.jpg)

一个关联数组，包含通过 URL 参数传递给当前脚本的变量。

`$_GET` 是一个包含所有 URL 参数的数组；这些就是 URL 中 `?` 后面的任何内容。

| `$_GET` | `[]` | `"myVar"` |
| --- | --- | --- |

以 [`www.example.com/index.php?myVar=myVal`](http://www.example.com/index.php?myVar=myVal) 为例。可以通过按此格式 `]` 访问来获取该 URL 中的信息，结果将是 `myVal`。

给不喜欢阅读文字的人看点代码。

```php
// URL = http://www.example.com/index.php?myVar=myVal
echo $_GET["myVar"] == "myVal" ? "true" : "false"; // 返回 "true"
```

上面的例子使用了三元运算符。

这展示了如何使用 `$_GET` 超全局变量访问 URL 中的值。

再来一个例子！

![](img/Image00099.jpg)

可以通过用 `&` 字符分隔，在 URL 中发送多个变量。

##### 安全风险
**非常重要**：不要通过 URL 发送任何敏感信息，因为它会保留在计算机的历史记录中，任何能访问该浏览器的人都能看到。

##### $_POST
![](img/Image00100.jpg)

一个关联数组，包含通过 HTTP POST 方法传递给当前脚本的变量，前提是请求中的 HTTP Content-Type 为 `application/x-www-form-urlencoded` 或 `multipart/form-data`。

与 `$_GET` 非常相似，都是将数据从一处发送到另一处。

我将直接从一个例子开始。（我省略了 `action` 属性，因为这会将信息发送到包含该表单的页面）。

![](img/Image00101.jpg)

以上是一个用于发送数据的基本表单。在真实环境中，`value` 属性不会被设置，这意味着表单将是空白的。然后它会发送用户输入的任何信息。

![](img/Image00102.jpg)

##### 安全风险
通过 POST 发送数据也不安全。使用 HTTPS 将确保数据更安全。

##### $_FILES
![](img/Image00103.jpg)

一个关联数组，包含通过 HTTP POST 方法上传到当前脚本的项目。该数组的结构在 [POST 方法上传](http://php.net/manual/en/features.file-upload.post-method.php) 章节中有概述。

让我们从一个基本表单开始。

![](img/Image00104.jpg)

| `enctype` | `=` | `"multipart/form-data"` |
| --- | --- | --- |

注意我省略了 `action` 属性（又是！）。另外，我添加了 `enctype`，这对任何处理文件上传的表单都很重要。

![](img/Image00105.jpg)

这用于上传单个文件。有时你可能想上传多个文件。为此有一个属性，叫做 `multiple`。

几乎任何东西都有属性。[抱歉了](https://www.youtube.com/watch?v=szrsfeyLzyg) 下面是一个提交多个文件的表单示例。

![](img/Image00106.jpg)

注意这里的更改；只有几处。

![](img/Image00107.jpg)

输入名称带有方括号。这是因为它现在是一个文件数组，所以我们告诉表单：

| `$_FILES` | `[]` | `"myVar"` |
| --- | --- | --- |

创建所选文件的数组。省略方括号将导致最后一个文件被设置为 `]`。

![](img/Image00108.jpg)

这是一个非常简单的例子，不处理诸如不允许的文件扩展名或以 PHP 代码命名的文件（如 SQL 注入的 PHP 等价物）等问题。请参阅文档。

第一步是检查是否有文件，如果有，将总数设置为 `$total`。

使用 `for` 循环可以遍历 `$_FILES` 数组并一次访问每一项。如果该文件没有遇到问题，则 `if` 语句为真，并运行单文件上传的代码。

如果遇到问题，则执行 `switch` 块，并根据该特定上传的错误显示错误信息。

##### $_COOKIE
![](img/Image00109.jpg)

一个关联数组，包含通过 HTTP Cookie 传递给当前脚本的变量。

Cookie 是包含数据并存储在客户端计算机上的变量。

与前述超全局变量不同，Cookie 必须通过函数创建（而不是通过赋值）。约定如下。

![](img/Image00110.jpg)

在本例中，为 Cookie 指定了一个名称（本例中为 `"myVar"`），一个值（本例中为 `"myVal"`，但也可以传递一个变量将其值赋给 Cookie），以及一个过期时间（本例中为一小时，因为 3600 秒是一分钟——*原文此处有误，3600 秒为一小时*）。

尽管创建 Cookie 的约定不同，但访问方式与其他超全局变量相同。

![](img/Image00111.jpg)

要销毁 Cookie，必须再次调用 `setcookie`，但将过期时间设为过去的任意时间。见下文。

![](img/Image00112.jpg)

这将取消设置 Cookie 并将其从客户端计算机上移除。

##### $_SESSION
![](img/Image00113.jpg)

一个包含当前脚本可用会话变量的关联数组。有关如何使用的更多信息，请参阅 [会话函数](http://php.net/manual/en/ref.session.php) 文档。

会话非常像 Cookie，只不过它们是服务端的。

| `session_start()` |
| --- |

要使用会话，必须在脚本顶部包含 `session_start()` 以启用会话功能。

设置会话变量与设置其他变量相同。见下例。

![](img/Image00114.jpg)

| `session_id()` |
| --- |

启动会话时，会设置一个随机 ID 作为 Cookie，名为 `"PHPSESSID"`，包含当前会话的会话 ID。可以通过调用 `session_id()` 函数访问它。

| `unset()` | `$_SESSION` | `[]` | `"myVar"` |
| --- | --- | --- | --- |

可以使用 `unset()` 函数销毁会话变量（例如 `unset($_SESSION["myVar"])` 将销毁该变量）。

| `session_destroy()` |
| --- |

另一种方法是调用 `session_destroy()`。这将销毁整个会话，意味着所有会话变量将不复存在。

##### $_REQUEST
![](img/Image00115.jpg)

一个关联数组，默认包含 [`$_GET`](http://php.net/manual/en/reserved.variables.get.php)、[`$_POST`](http://php.net/manual/en/reserved.variables.post.php) 和 [`$_COOKIE`](http://php.net/manual/en/reserved.variables.cookies.php) 的内容。

正如 PHP 文档所述，这只是将 `$_GET`、`$_POST` 和 `$_COOKIE` 汇总在一个变量中。

| `php.ini` |
| --- |

由于这三个数组都可能拥有相同名称的索引，`php.ini` 文件中有一个名为 `request_order` 的设置，可以指定三者中的优先顺序。

例如，如果设置为 `"GPC"`，则将使用 `$_COOKIE` 的值，因为它是从左到右读取的，意味着 `$_REQUEST` 会先将其值设为 `$_GET`，然后是 `$_POST`，最后是 `$_COOKIE`，既然 `$_COOKIE` 在最后，那么 `$_REQUEST` 中的值就是 `$_COOKIE` 的值。见 [此问题](http://stackoverflow.com/questions/43157933/what-is-the-request-precedence)。

##### $_ENV
![](img/Image00116.jpg)

一个关联数组，包含通过环境变量方法传递给当前脚本的变量。




这些变量是从运行 PHP 解析器的环境导入到 PHP 的全局命名空间中的。许多变量由运行 PHP 的 Shell 提供，不同的系统可能运行不同种类的 Shell，因此无法提供一份确定的列表。请参阅您的 Shell 文档以获取已定义环境变量的列表。

其他环境变量包括 CGI 变量，无论 PHP 是作为服务器模块还是 CGI 处理器运行，这些变量都会被放置在那里。

`$_ENV` 中存储的任何内容都来自 PHP 运行所在的环境。

| php | | . | ini |
| --- | --- | --- | --- |

只有当 `variables_order` 允许时，`$_ENV` 才会被填充。

请参阅 [此回答](http://stackoverflow.com/questions/3780866/why-is-my-env-empty/27077452#27077452) 以获取更多关于为什么 `$_ENV` 未被填充的信息。

#### 第 4.2 节：PHP5 超全局变量

以下是 PHP5 超全局变量

`$GLOBALS`

`$_REQUEST`

`$_GET`

`$_POST`

`$_FILES`

`$_SERVER`

`$_ENV`

`$_COOKIE`

`$_SESSION`

`$GLOBALS`：此超全局变量用于访问全局变量。

`$_REQUEST`：此超全局变量用于收集通过 HTML 表单提交的数据。

`$_GET`：此超全局变量用于收集通过带有 get 方法的 HTML 表单提交的数据。

`$_POST`：此超全局变量用于收集通过带有 post 方法的 HTML 表单提交的数据。

`$_FILES`：此超全局变量保存通过 HTTP Post 方法上传的文件信息。

`$_SERVER`：此超全局变量保存关于脚本、HTTP 头部和服务器路径的信息。

`$_ENV`：此超全局变量保存 PHP 运行所在的 Shell 环境变量详情。

`$_COOKIE`：此超全局变量用于通过给定的键检索 Cookie 值。

`$_SESSION`：此超全局变量用于设置和检索存储在服务器上的会话值。

## 第 5 章：输出变量的值

要构建动态且交互式的 PHP 程序，输出变量及其值非常有用。PHP 语言允许多种值输出方法。本主题涵盖在 PHP 中打印值的标准方法以及这些方法可以使用的场景。

#### 第 5.1 节：echo 和 print

| echo | | ( | "test" |
| --- | --- | --- | --- |

[echo](http://php.net/manual/en/function.echo.php) 和 [print](http://php.net/manual/en/function.print.php) 是语言结构，而非函数。这意味着它们不像函数那样要求参数周围必须有括号（尽管可以给几乎任何 PHP 表达式加上括号，因此 `echo("test")` 也不会造成任何伤害）。它们输出变量、常量或表达式的字符串表示形式。它们不能用于打印数组或对象。

##### echo 的简写语法

当在 [PHP 标签之外](http://php.net/manual/en/language.basic-syntax.phpmode.php) 时，默认可用 echo 的简写语法，使用 `<?=` 开始输出，`?>` 结束。例如：

```
<?= "Hello World" ?>
```

注意没有终止的 `;`。之所以有效，是因为结束 PHP 标签充当了单条语句的终止符。因此，按照惯例，在这种简写语法中省略分号。

##### print 的优先级

虽然 print 是语言结构，但它具有像运算符一样的优先级。它位于 `=`、`+=`、`-=`、`*=`、`**=`、`/=`、`.=`、`%=`、`&=` 和 `and` 运算符之间，并具有左结合性。示例：

```
print "hello " . print "world";
```

带括号的相同示例：
```
print "hello " . (print "world");
```
```
echo '1' . print ( '2' + 3); //输出 511
```

##### echo 和 print 的区别

简而言之，主要有两个区别：

*   `print` 只接受一个参数，而 `echo` 可以有多个参数。
*   `print` 返回一个值，因此可以作为表达式使用。

#### 第 5.2 节：输出数组和对象的结构化视图

| [print_r](http://php.net/manual/en/function.print-r.php) |
| --- |

`print_r()` - 为调试输出数组和对象

[print_r](http://php.net/manual/en/function.print-r.php) 将以人类可读的格式输出数组或对象。

您可能有一个是数组或对象的变量。尝试用 echo 输出它会抛出错误：

| Notice | | : | | Array to string conversion |
| --- | --- | --- | --- | --- |

。您可以改用 `print_r` 函数来转储该变量的人类可读格式。

```
$myarray = array('a', 'b', 'c');
print_r($myarray);
```

```
Array
(
    [0] => a
    [1] => b
    [2] => c
)
```

```
$myobj = new stdClass();
$myobj->foo = 'bar';
print_r($myobj);
```

```
stdClass Object
(
    [foo] => bar
)
```

此外，`print_r` 的输出可以作为字符串捕获，而不仅仅是直接输出。例如，以下代码会将 `$myarray` 的格式化版本转储到一个新变量中：

```
$output = print_r($myarray, true);
```

请注意，如果您在浏览器中查看 PHP 的输出，且其被解释为 HTML，则换行符将不会显示，输出将难以阅读，除非您执行类似以下的操作：

```
echo '<pre>' . print_r($myarray, true) . '</pre>';
```

或者，您可以告诉浏览器您输出的是纯文本，而非 HTML：

```
header('Content-Type: text/plain');
print_r($myarray);
```

| [var_dump](http://php.net/manual/en/function.var-dump.php) |
| --- |

`var_dump()` - 输出关于参数内容的可读调试信息，包括其类型和值

输出比 `print_r` 更详细，因为它还会输出变量的类型及其值，以及其他信息，如对象 ID、数组大小、字符串长度、引用标记等。

您可以使用 `var_dump` 为调试输出更详细的版本。

```
$myarray = array('a', 'b', 'c');
var_dump($myarray);
```

输出更详细：

```
array(3) {
  [0]=>
  string(1) "a"
  [1]=>
  string(1) "b"
  [2]=>
  string(1) "c"
}
```

注意：如果您在开发环境中使用 xDebug，`var_dump` 的输出默认会被限制/截断。请参阅 [官方文档](https://xdebug.org/docs/display) 了解更多关于更改此选项的信息。

| [var_export](http://php.net/manual/en/function.var-export.php) |
| --- |

`var_export()` - 输出有效的 PHP 代码

`var_export()` 转储项目的 PHP 可解析表示形式。

```
$myarray = array('a', 'b', 'c');
var_export($myarray);
```

```
array (
  0 => 'a',
  1 => 'b',
  2 => 'c',
)
```

要将内容放入变量，可以执行以下操作：

```
$array_export = var_export($myarray, true);
$string_export = var_export($mystring, true);
$int_export = var_export($myint, true);
```

之后，您可以这样输出：

```
printf('$myarray = %s; %s', $array_export, PHP_EOL);
printf('$mystring = %s; %s', $string_export, PHP_EOL);
printf('$myint = %s; %s', $int_export, PHP_EOL);
```

这将产生以下输出：

```
$myarray = array (
  0 => 'a',
  1 => 'b',
  2 => 'c',
);
$mystring = 'foo';
$myint = 123;
```

#### 第 5.3 节：使用 echo 进行字符串拼接

您可以在输出时使用 [拼接来连接字符串](https://secure.php.net/manual/en/language.operators.string.php) "首尾相连"（例如使用 `echo` 或 `print`）。

您可以使用 `.`（句点）拼接变量。

```
echo "Hello " . $name . "!";
```

与拼接类似，`echo`（不带括号时）可以使用逗号（`,`）将字符串和变量组合在一起（连同其他任意表达式）。

```
echo "Hello ", $name, "!";
```

```
echo "The sum is ", 1 + 2, ".";
```

### 字符串拼接 vs 向 echo 传递多个参数

向 `echo` 命令传递多个参数在某些情况下比字符串拼接更有优势。参数按传入的顺序写入输出。

```
echo "Hello ", $name, "!"; // 更快，无拼接开销
echo "Hello " . $name . "!"; // 先拼接，再输出
```




# 第 5 章：字符串输出与格式化

#### 第 5.4 节：printf 对比 sprintf

连接运算符的问题在于句点 `.` 在表达式中优先级较高。如果进行连接，上述表达式需要额外的括号才能表现出正确的行为。句点的优先级也会影响三元运算符。

![](img/Image00150.jpg)

[`printf`](http://php.net/manual/en/function.printf.php) 将使用占位符输出格式化字符串。

![](img/Image00151.jpg)

也可以使用这两个函数来格式化数字。这可用于格式化用于表示货币的十进制值，使其始终保留 2 位小数。

![](img/Image00152.jpg)

这两个函数 [`vprintf`](http://php.net/manual/en/function.vprintf.php) 和 [`vsprintf`](http://php.net/manual/en/function.vsprintf.php) 的操作方式与 [`printf`](http://php.net/manual/en/function.printf.php) 和 [`sprintf`](http://php.net/manual/en/function.sprintf.php) 相同，但它们接受一个格式字符串和一个值数组，而不是单独的变量。

#### 第 5.5 节：输出大整数

在 32 位系统上，大于 `PHP_INT_MAX` 的整数会自动转换为浮点数。要将这些值作为整数输出（即非科学计数法），可以使用 `printf` 并利用浮点数表示法，如下所示：

![](img/Image00153.jpg)

```
echo " " , $i , " \n " ;
}

// 输出：
```

![](img/Image00154.jpg)

```
pow (1024,  1)  integer                     1024                         1024   1024
pow (1024,  2)  integer              1048576                         1048576   1048576
pow (1024,  3)  integer           1073741824                         1073741824   1073741824
pow (1024,  4)   double          1099511627776                         1099511627776   1099511627776
pow (1024,  5)   double  1.1258999068426E+15                         1125899906842624 1.1258999068426E+15
pow (1024,  6)   double  1.1529215046068E+18                       1152921504606846976 1.1529215046068E+18
pow (1024,  9)   double  1.2379400392854E+27          1237940039285380274899124224 1.2379400392854E+27
pow (1024, 12)   double  1.3292279957849E+36  1329227995784915872903807060280344576 1.3292279957849E+36
```

注意：留意浮点数精度，它并非无限的！

虽然这看起来不错，但在这个人为构造的示例中，所有数字都可以表示为二进制数，因为它们都是 1024 的幂（因此也是 2 的幂）。例如见：

![](img/Image00155.jpg)

#### 第 5.6 节：输出多维数组及其索引和值并打印到表格中

![](img/Image00156.jpg)

![](img/Image00157.jpg)

在表格中输出带有索引和值的多维数组

![](img/Image00158.jpg)

## 第 6 章：常量

#### 第 6.1 节：定义常量

常量是使用 `const` 语句或 `define` 函数创建的。惯例是常量名使用大写字母。

![](img/Image00159.jpg)

```
define ( "BETTER_APP_LANGUAGES" , [ "lu" , "de" ]); // 数组
```

如果你已有一个常量，可以基于它定义另一个常量：

![](img/Image00160.jpg)

```
const TAU = PI * 2;
define ( "EARTH_IS_ROUND" , ! EARTH_IS_FLAT );
define ( "MORE_UNKNOWN" , UNKNOWN );
define ( "APP_ENV_UPPERCASE" , strtoupper ( APP_ENV )); // 字符串操作也可以
// 上面的例子（函数调用）不适用于 const：
// const TIME = time(); # 会报致命错误！非常量标量表达式
define ( "MAX_SESSION_TIME_IN_MINUTES" , MAX_SESSION_TIME / 60);
const APP_FUTURE_LANGUAGES = [-1 => "es"] + APP_LANGUAGES; // 数组操作
define ( "APP_BETTER_FUTURE_LANGUAGES" , array_merge (["fr"], APP_BETTER_LANGUAGES ));
```

##### 保留常量

某些常量名由 PHP 保留，无法重新定义。以下所有示例都会失败：

```
define ( "true" , false ); // 内部常量
define ( "false" , true ); // 内部常量
```

![](img/Image00161.jpg)

```
define ( "CURLOPT_AUTOREFERER" , "something" ); // 如果加载了 curl 扩展将会失败
```

并会发出一个 Notice（提示）：

![](img/Image00162.jpg)

##### 条件定义

如果你有多个文件可能定义同一个变量（例如，主配置文件然后是本地配置文件），以下语法可能有助于避免冲突：

![](img/Image00163.jpg)

```
defined ( "PI" ) || define ( "PI" , 3.1415 ); // "如果 PI 尚未定义则定义它"
```

##### const 对比 define

`define` 是运行时表达式，而 `const` 是编译时表达式。

因此 `define` 允许动态值（即函数调用、变量等），甚至动态名称和条件定义。但它始终相对于根命名空间进行定义。

`const` 是静态的（即仅允许与其他常量、标量或数组进行操作，且仅限于受限的操作集，即所谓的常量标量表达式，包括算术、逻辑和比较运算符以及数组解引用），但会自动加上当前活动命名空间作为前缀。

`const` 仅支持其他常量和标量作为值，不支持运算。

#### 第 6.2 节：类常量

常量可以使用 `const` 关键字在类内部定义。

![](img/Image00164.jpg)

这对于存储项目类型很有用。

![](img/Image00165.jpg)

#### 第 6.3 节：检查常量是否已定义

##### 简单检查

要检查常量是否已定义，请使用 `defined` 函数。注意，该函数不关心常量的值，只关心常量是否存在。即使常量的值是 `null` 或 `false`，该函数仍将返回 `true`。

![](img/Image00166.jpg)

![](img/Image00167.jpg)

请注意，常量只有在定义它的那一行之后，在你的代码中才会变得“可见”：

![](img/Image00168.jpg)

##### 获取所有已定义的常量

要获取所有已定义的常量（包括 PHP 创建的），请使用 `get_defined_constants` 函数：

![](img/Image00169.jpg)

要仅获取你的应用定义的常量，请在脚本开始时（通常在引导过程后）和结束时调用该函数：

![](img/Image00170.jpg)

这有时对调试很有用。

#### 第 6.4 节：使用常量

要使用常量，只需使用其名称：

![](img/Image00171.jpg)

或者如果你事先不知道常量的名称，请使用 `constant` 函数：

![](img/Image00172.jpg)

#### 第 6.5 节：常量数组

从 PHP 5.6 版本起，数组可用作普通常量和类常量：

![](img/Image00173.jpg)

![](img/Image00174.jpg)

```
const ANSWER = [2,4];
```

此外，从 PHP 7.0 版本起，此功能被移植到 [`define`](http://php.net/manual/en/function.define.php) 函数中，用于普通常量。

![](img/Image00175.jpg)

## 第 7 章：魔术常量

#### 第 7.1 节：`__FUNCTION__` 与 `__METHOD__` 的区别

`__FUNCTION__` 仅返回函数名称，而 `__METHOD__` 返回类名连同函数名称：

![](img/Image00176.jpg)

#### 第 7.2 节：`__CLASS__`、`get_class()` 与 `get_called_class()` 的区别

| `get_class()` |
| --- |

`__CLASS__` 魔术常量返回的结果与无参数调用的函数相同，它们都返回定义它的类的名称（即你编写函数调用/常量名的地方）。

| `get_class($this)` | | 和 | `get_called_class()` |
| --- | --- | --- | --- |

相比之下，函数调用将返回实际被实例化的类的名称：

![](img/Image00177.jpg)

![](img/Image00178.jpg)

#### 第 7.3 节：文件与目录常量

##### 当前文件

你可以使用 `__FILE__` 魔术常量获取当前 PHP 文件的名称（含绝对路径）。这最常用作记录/调试技术。

![](img/Image00179.jpg)

##### 当前目录

要获取当前文件所在目录的绝对路径，请使用 `__DIR__` 魔术常量。

![](img/Image00180.jpg)

| `dirname` | | ( | `__FILE__` |
| --- | --- | --- | --- |

要获取当前文件所在目录的绝对路径，请使用 `)` 。

![](img/Image00181.jpg)




##### 获取当前目录

获取当前目录常被 PHP 框架用于设置基础目录：

![](img/Image00182.jpg)

![](img/Image00183.jpg)

除了魔术常量，PHP 还提供了一些用于处理路径的固定常量：

![](img/Image00184.jpg)

`DIRECTORY_SEPARATOR` 常量用于分隔路径中的目录。在 *nix 系统上取值为 `/`，在 Windows 上取值为 `\`。带有视图的示例可以重写为：

```php
$view = 'page';
$viewFile = BASEDIR . DIRECTORY_SEPARATOR . 'views' . DIRECTORY_SEPARATOR . $view;
```

很少使用的 `PATH_SEPARATOR` 常量用于分隔 `$PATH` 环境变量中的路径。在 Windows 上为 `;`，其他系统上为 `:`。

## 第 8 章：注释

#### 第 8.1 节：单行注释

单行注释以 `//` 或 `#` 开头。遇到时，其右侧的所有文本将被 PHP 解释器忽略。

![](img/Image00185.jpg)

#### 第 8.2 节：多行注释

多行注释可用于注释掉大块代码。它以 `/*` 开始，以 `*/` 结束。

![](img/Image00186.jpg)

## 第 9 章：类型

#### 第 9.1 节：类型比较

有两种类型的[比较](http://php.net/manual/en/types.comparisons.php)：使用 `==` 的宽松比较和使用 `===` 的严格比较。严格比较确保运算符两边的类型和值都相同。

![](img/Image00187.jpg)

你也可以使用强比较（即严格比较）通过 `!==` 来检查类型和值是否不匹配。

一个 `==` 运算符不够用的典型例子，是那些可能返回不同类型的函数，比如 [strpos](http://php.net/manual/en/function.strpos.php)，如果未找到搜索词则返回 `false`，否则返回匹配位置（`int`）：

```php
if (strpos('text', 'searchword') == false)
    // strpos 返回 false，所以 == 比较在这里按预期工作，但是：
if (strpos('text bla', 'text') == false)
    // strpos 返回 0（在位置 0 找到匹配）且 0==false 为 true。
    // 这可能不是你期望的！
if (strpos('text', 'text') === false)
    // strpos 返回 0，且 0===false 为 false，所以这能按预期工作。
```

![](img/Image00188.jpg)

#### 第 9.2 节：布尔值

[布尔值](http://php.net/manual/en/language.types.boolean.php)是一种类型，有两个值，分别表示为 `true` 或 `false`。

这段代码将 `$foo` 的值设为 `true`，`$bar` 的值设为 `false`：

![](img/Image00189.jpg)

`true` 和 `false` 不区分大小写，所以 `TRUE` 和 `FALSE` 也可以使用，甚至 `FaLsE` 也是可能的。使用小写是最常见的，且在大多数代码风格指南中被推荐，例如 [PSR-2](http://www.php-fig.org/psr/psr-2/)。

布尔值可用于 `if` 语句，如下所示：

![](img/Image00190.jpg)

由于 PHP 是弱类型语言，如果上面的 `$foo` 不是 `true` 或 `false`，它会自动被强制转换为布尔值。

以下值结果为 `false`：

![](img/Image00191.jpg)

*   零值：`0`（整数）、`0.0`（浮点数）或 `'0'`（字符串）
*   空字符串 `''` 或空数组 `[]`
*   `null`（未设置变量的内容，或赋值给变量的 null）

任何其他值结果为 `true`。

为避免这种宽松比较，你可以使用 `===` 强制进行强比较，它同时比较值和类型。详见类型比较。

| bool | | ) or ( | boolean |
| --- | --- | --- | --- |

要将类型转换为布尔值，可以在类型前使用 `()` 强制转换。

![](img/Image00192.jpg)

或调用 `boolval()` 函数：

![](img/Image00193.jpg)

布尔值转字符串（注意 `false` 生成空字符串）：

![](img/Image00194.jpg)

布尔值转整数：

![](img/Image00195.jpg)

注意相反的转换也是可能的：

![](img/Image00196.jpg)

此外所有非零值都将返回 `true`：

![](img/Image00197.jpg)

#### 第 9.3 节：浮点数

![](img/Image00198.jpg)

浮点数是浮点型数字，其输出精度比普通整数更高。

由于 PHP 对变量类型的宽松转换，浮点数和整数可以一起使用：

![](img/Image00199.jpg)

PHP 不像其他语言那样将浮点数显示为浮点数格式，例如：

![](img/Image00200.jpg)

> **警告：浮点数精度**
>
> （来自 [PHP 手册页面](http://php.net/manual/en/language.types.float.php)）
>
> ![](img/Image00201.jpg)
>
> 浮点数精度有限。虽然取决于系统，PHP 通常因舍入而给出最大相对误差，数量级约为 1.11e-16。非基本算术运算可能给出更大的误差，当多个运算复合时必须考虑误差传播。
>
> 此外，在十进制中能精确表示为浮点数的有理数，如 `0.1` 或 `0.7`，在内部使用的二进制（基数 2）中没有精确的浮点数表示，无论尾数大小如何。因此，它们无法在不损失少量精度的情况下转换为内部二进制对应值。这可能导致令人困惑的结果：例如，`floor((0.1+0.7)*10)` 通常会返回 `7` 而不是预期的 `8`，因为内部表示可能类似 `7.9999999999999991118....`
>
> 所以永远不要信任浮点数结果的最后一位，也不要直接比较浮点数是否相等。如果需要更高精度，可使用任意精度数学函数和 gmp 函数。

#### 第 9.4 节：字符串

PHP 中的字符串是一系列单字节字符（即没有原生 Unicode 支持），可以通过四种方式指定：

##### 单引号

几乎完全“原样”显示内容。变量和大多数转义序列不会被解析。例外是要显示字面单引号，可以用反斜杠转义 `\'`，要显示反斜杠，可以用另一个反斜杠转义 `\\`。

![](img/Image00202.jpg)

##### 双引号

与单引号字符串不同，字符串中的简单变量名和[转义序列](http://php.net/manual/en/language.types.string.php#language.types.string.syntax.double)会被解析。花括号（如最后一个示例所示）可用于隔离复杂的变量名。

![](img/Image00203.jpg)

##### Heredoc

| <<< identifier |
| --- |

在 heredoc 字符串中，变量名和转义序列的解析方式类似于双引号字符串，但花括号不可用于复杂变量名。字符串的开始由 `<<< identifier` 界定，结束由 `identifier` 界定，其中 `identifier` 可以是任何合法的 PHP 名称。结束标识符必须单独占一行。标识符前后不允许有空白字符，尽管像 PHP 中的任何一行一样，它也必须以分号结尾。

![](img/Image00204.jpg)

##### Nowdoc

Nowdoc 字符串类似于 heredoc 的单引号版本，甚至最基本的转义序列也不被解析。字符串开头的标识符被单引号包裹。

**PHP 5.x 版本 ≥ 5.3**

```php
$my_string = <<< 'EOF'
```

![](img/Image00205.jpg)

语法类似于 heredoc，但类似于单引号字符串，没有任何内容被解析（甚至不包括转义的单引号 `\'` 和反斜杠 `\\`）。

![](img/Image00206.jpg)

#### 第 9.5 节：可调用类型

可调用类型是指任何可以作为回调被调用的东西。可称为“回调”的事物如下：

![](img/Image00207.jpg)

*   匿名函数
*   标准 PHP 函数（注意：不包括语言结构）
*   静态类
*   非静态类（使用替代语法）
*   特定的对象/类方法
*   对象本身，只要该对象位于数组的键 0 处

引用对象作为数组元素的示例：

![](img/Image00208.jpg)

自 PHP 5.4 起，回调可用 `callable` 类型提示标注。

![](img/Image00209.jpg)

#### 第 9.6 节：资源

[资源](https://secure.php.net/manual/en/language.types.resource.php)是一种特殊类型的变量，引用外部资源，如文件、套接字、流、文档或连接。

![](img/Image00210.jpg)

| `get_resource_type()` |
| --- |




# PHP 资源类型与类型系统

资源有不同的（子）类型。你可以使用 [`get_resource_type()`](https://secure.php.net/manual/en/function.get-resource-type.php) 来检查资源类型：

![Image00211.jpg](img/Image00211.jpg)

![Image00212.jpg](img/Image00212.jpg)

你可以在[这里](https://secure.php.net/manual/en/resource.php)找到内置资源类型的完整列表。

##### 类型转换

PHP 通常会根据变量使用的上下文正确推断你想要使用的数据类型；不过，有时手动强制转换类型很有用。这可以通过在声明前加上括号括起来的目标类型名称来实现：

![Image00213.jpg](img/Image00213.jpg)

但要小心：并非所有类型转换都如预期那样工作：

![Image00214.jpg](img/Image00214.jpg)

```php
// 以下 3 条语句适用于 32 位系统 (PHP_INT_MAX=2147483647)
// 大于 PHP_INT_MAX 的整数值会自动转换为浮点数：
var_dump(999888777666); // float(999888777666)
// 强制转为 (int) 会导致溢出：
var_dump((int) 999888777666); // int(-838602302)
// 但在字符串中它只返回 PHP_INT_MAX
var_dump((int) "999888777666"); // int(2147483647)

var_dump((bool) []);       // bool(false) (空数组)
var_dump((bool) [false]);  // bool(true)  (非空数组)
```

##### 类型演变

PHP 是一门弱类型语言。它不需要显式声明数据类型。变量使用的上下文决定了其数据类型；转换会自动进行：

![Image00215.jpg](img/Image00215.jpg)

![Image00216.jpg](img/Image00216.jpg)

##### Null

PHP 使用 [`null`](http://php.net/manual/en/language.types.null.php) 关键字表示“无值”。它有点类似于 C 语言中的空指针和 SQL 中的 `NULL` 值。

将变量设置为 null：

![Image00217.jpg](img/Image00217.jpg)

检查变量是否被设置为 null：

![Image00218.jpg](img/Image00218.jpg)

##### Null 与未定义变量

| 通知 | | 未定义变量 | | `nullvar` |
| :--- | :--- | :--- | :--- | :--- |

如果变量未定义或已被 unset，那么针对 `null` 的任何测试都会成功，但同时也会生成一个通知：

![Image00219.jpg](img/Image00219.jpg)

![Image00220.jpg](img/Image00220.jpg)

因此，必须使用 [`isset()`](http://php.net/manual/en/function.isset.php) 来检查未定义的值：

```php
if (!isset($nullvar)) {
    // 变量为 null 甚至未定义
}
```

##### 整数

PHP 中的整数可以原生地以二进制（基数 2）、八进制（基数 8）、十进制（基数 10）或十六进制（基数 16）指定。

![Image00221.jpg](img/Image00221.jpg)

整数长度为 32 位或 64 位，取决于平台。常量 `PHP_INT_SIZE` 以字节为单位保存整数大小。

`PHP_INT_MAX` 和（自 PHP 7.0 起）`PHP_INT_MIN` 也可用。

![Image00222.jpg](img/Image00222.jpg)

```php
printf("Integers are %d bits long" . PHP_EOL, PHP_INT_SIZE * 8);
printf("They go up to %d" . PHP_EOL, PHP_INT_MAX);
```

整数值会根据需要自动从浮点数、布尔值和字符串创建。如果需要显式类型转换：

![Image00223.jpg](img/Image00223.jpg)

整数溢出将通过转换为浮点数来处理：

![Image00224.jpg](img/Image00224.jpg)

PHP 中没有整数除法运算符，但可以通过隐式转换来模拟，它总是通过丢弃小数部分来“舍入”。自 PHP 7 版本起，新增了一个整数除法函数。

![Image00225.jpg](img/Image00225.jpg)

## 第 10 章：运算符

运算符是指接受一个或多个值（或用编程术语说是表达式）并产生另一个值的东西（以便该结构本身成为一个表达式）。

运算符可以根据它们接受的值的数量进行分组。

## Null 合并运算符 (??)

Null 合并是 PHP 7 中引入的新运算符。如果第一个操作数已设置且不为 `NULL`，则返回该操作数。否则，返回第二个操作数。

以下示例：

![Image00226.jpg](img/Image00226.jpg)

等同于以下两种写法：

![Image00227.jpg](img/Image00227.jpg)

和：

![Image00228.jpg](img/Image00228.jpg)

该运算符也可以链式使用（具有右结合语义）：

![Image00229.jpg](img/Image00229.jpg)

等同于：

![Image00230.jpg](img/Image00230.jpg)

**注意：**

在字符串连接上使用合并运算符时，别忘了使用括号 `()`。

![Image00231.jpg](img/Image00231.jpg)

这将只输出 `John`，如果 `$firstName` 为 `null` 而 `$lastName` 为 `Doe`，则会输出 `Unknown Doe`。为了输出 `John Doe`，我们必须像这样使用括号：

![Image00232.jpg](img/Image00232.jpg)

![Image00233.jpg](img/Image00233.jpg)

```php
echo ($firstName ?? "Unknown") . " " . ($lastName ?? "");
```

这将输出 `John Doe` 而不是仅输出 `John`。

## 太空船运算符 (<=>)

PHP 7 引入了一种新型运算符，可用于比较表达式。如果第一个表达式小于、等于或大于第二个表达式，该运算符将分别返回 `-1`、`0` 或 `1`。

![Image00234.jpg](img/Image00234.jpg)

对象不可比较，因此这样做会导致未定义行为。

| `<=>` |
| :--- |

![Image00235.jpg](img/Image00235.jpg)

该运算符在使用 `usort`、`uasort` 或 `uksort` 编写用户定义的比较函数时特别有用。例如，给定一个按其 `weight` 属性排序的对象数组，匿名函数可以使用 `<=>` 返回排序函数所期望的值。

```php
usort($list, function ($a, $b) {
    return $a->weight <=> $b->weight;
});
```

在 PHP 5 中，这需要一个相当复杂的表达式。

![Image00236.jpg](img/Image00236.jpg)

## 执行运算符 (``)

PHP 执行运算符由反引号 (``) 组成，用于运行 shell 命令。命令的输出将被返回，因此可以存储在变量中。

![Image00237.jpg](img/Image00237.jpg)

| [`shell_exec()`](http://php.net/manual/en/function.shell-exec.php) |
| :--- |

注意，执行运算符和 [`shell_exec()`](http://php.net/manual/en/function.shell-exec.php) 会给出相同的结果。

## 递增 (++) 和递减 (--) 运算符

变量可以分别使用 `++` 或 `--` 递增或递减 1。它们可以位于变量之前或之后，语义略有不同，如下所示。

![Image00238.jpg](img/Image00238.jpg)

关于递增和递减运算符的更多信息，请参阅[官方文档](http://php.net/manual/en/language.operators.increment.php)。

## 三元运算符 (?:)

三元运算符可以看作是一个内联的 `if` 语句。它由三部分组成：条件和两个结果。语法如下：

![Image00239.jpg](img/Image00239.jpg)

| `<true value>` |
| :--- |

| `<false value>` |
| :--- |

如果条件评估为 `true`，则返回第一块中的值 (`<true value>`)；否则返回第二块中的值 (`<false value>`)。因为我们将 `$value` 设置为三元运算符的结果，所以它将存储返回的值。

**示例：**

![Image00240.jpg](img/Image00240.jpg)

| `empty` | `(` | `$_POST` | `['action']` |
| :--- | :--- | :--- | :--- |

| `$_POST` | `['action']` |
| :--- | :--- |

如果 `empty($_POST['action'])` 评估为 `true`，`$action` 将包含字符串 `'default'`。否则，它将包含 `$_POST['action']` 的值。

| `expr3` |
| :--- |

| `expr1` | `)` | `?` | `(` | `expr2` |
| :--- | :--- | :--- | :--- | :--- |

![Image00241.jpg](img/Image00241.jpg)

表达式 `(expr1) ? (expr2) : (expr3)` 在 `expr1` 评估为 `true` 时求值为 `expr2`，在 `expr1` 评估为 `false` 时求值为 `expr3`。

| `expr1` | `?` | `:` | `expr3` |
| :--- | :--- | :--- | :--- |

可以省略三元运算符的中间部分。表达式 `expr1 ?: expr3` 在 `expr1` 评估为 `TRUE` 时返回 `expr1`，否则返回 `expr3`。`?:` 常被称为 Elvis 运算符。

这与 Null 合并运算符 `??` 行为类似，不同之处在于 `??` 要求左操作数严格为 `null`，而 `?:` 尝试将左操作数解析为布尔值并检查其是否为布尔 `false`。

**示例：**

![Image00242.jpg](img/Image00242.jpg)

在此示例中，`setWidth` 接受一个 `width` 参数，或默认值 `0`，以更改宽度的会话值。如果 `$width` 为 `0`：

| `getDefaultWidth()` |
| :--- |

| `getDefaultWidth()` |
| :--- |





#### 第 10.6 节：逻辑运算符（`&&`/`AND` 和 `||`/`OR`）

在 PHP 中，逻辑 AND 和 OR 运算符各有两个版本。

| 运算符 | 为真条件 |
| :--- | :--- |
| `$a and $b` | `$a` 和 `$b` 都为真 |
| `$a && $b` | `$a` 和 `$b` 都为真 |
| `$a or $b` | `$a` 或 `$b` 为真 |
| `$a || $b` | `$a` 或 `$b` 为真 |

请注意，`&&` 和 `||` 运算符的[优先级](http://php.net/manual/en/language.operators.precedence.php)高于 `and` 和 `or`。请见下表：

| 表达式 | `$e` 的结果 | 解析为 |
| :--- | :--- | :--- |
| `$e = ( false || true )` | True | `$e = false \|\| true` |
| `($e = false) or true` | False | `$e = false or true` |

因此，使用 `&&` 和 `||` 比使用 `and` 和 `or` 更安全。

#### 第 10.7 节：字符串运算符（`.` 和 `.=`）

![](img/Image00243.jpg)

#### 第 10.8 节：对象和类运算符

可以使用对象运算符（`->`）和类运算符（`::`）访问对象或类的成员。

![](img/Image00244.jpg)
![](img/Image00245.jpg)

| 正确 | 代替 | 错误 |
| :--- | :--- | :--- |
| `$object->a` | | `$object->$a` |

请注意，在对象运算符之后，不应写入 `$`。对于类运算符，情况并非如此，`$` 是必需的。对于类中定义的常量，永远不使用 `$`。

```
var_dump(MyClass::$d());
```

还请注意，只有当函数 `d()` 不引用对象时，才允许使用 `$d();`：

![](img/Image00246.jpg)

这会导致“PHP Fatal error: Uncaught Error: Using $this when not in object context”（PHP 致命错误：未捕获的错误：在非对象上下文中使用 $this）。这些运算符具有左结合性，可用于“链式调用”：

![](img/Image00247.jpg)

这些运算符具有最高优先级（甚至未在手册中提及），甚至高于 `clone`。因此：

![](img/Image00248.jpg)

在对象被克隆**之前**，`$o1` 的值就已增加！

请注意，在 PHP 5 及更早版本中，使用括号来影响优先级不起作用（在 PHP 7 中可行）：

![](img/Image00249.jpg)

#### 第 10.9 节：复合赋值（`+=` 等）

复合赋值运算符是对某个变量进行操作并随后将该新值赋值给该变量的快捷方式。

### 算术

![](img/Image00250.jpg)

### 同时处理多个数组

![](img/Image00251.jpg)

### 字符串的复合连接与赋值

![](img/Image00252.jpg)

### 复合二进制位运算赋值运算符

```
$a = 0b00101010;  // $a 现在是 42
$a &= 0b00001111; // $a 现在是 (00101010 & 00001111) => 00001010 (按位与)
$a |= 0b00100010; // $a 现在是 (00001010 | 00100010) => 00101010 (按位或)
$a ^= 0b10000010; // $a 现在是 (00101010 ^ 10000010) => 10101000 (按位异或)
$a >>= 3;         // $a 现在是 (10101000 >> 3) => 00010101 (右移 3 位)
$a <<= 1;         // $a 现在是 (00010101 << 1) => 00101010 (左移 1 位)
```

#### 第 10.10 节：改变运算符优先级（使用括号）

运算符的求值顺序由运算符优先级决定（另请参阅备注部分）。

![](img/Image00254.jpg)

可以使用括号来改变优先级：

![](img/Image00255.jpg)

#### 第 10.11 节：基本赋值（`=`）

![](img/Image00256.jpg)

结果是 `$a` 拥有值 `some string`。

赋值表达式的结果是被赋的值。请注意，单个等号 `=` **不是**用于比较的！

![](img/Image00257.jpg)

执行以下操作：

1.  第 1 行将 `3` 赋值给 `$a`。
2.  第 2 行将 `5` 赋值给 `$a`。该表达式也产生值 `5`。
3.  第 2 行接着将括号内表达式的结果（`5`）赋值给 `$b`。

因此：`$a` 和 `$b` 现在都拥有值 `5`。

#### 第 10.12 节：结合性

### 左结合

如果两个运算符的优先级相等，则结合性决定了分组（另请参阅备注部分）：

![](img/Image00258.jpg)

`*` 和 `%` 具有相同的优先级和左结合性。因为乘法首先发生（在左侧），所以它被分组。

![](img/Image00259.jpg)

现在，取模运算符首先发生（在左侧），因此被分组。

### 右结合

![](img/Image00260.jpg)

| 表达式 | 结果 |
| :--- | :--- |
| `$a = $b += 1` | `$a` 和 `$b` 现在都拥有值 2，因为 `1` 被分组，然后结果（`$b` 为 2）被赋值给 `$a`。 |

#### 第 10.13 节：比较运算符

### 相等性

对于基本的相等性测试，使用等于运算符 `==`。对于更全面的检查，请使用全等运算符 `===`。

全等运算符的工作方式与等于运算符相同，要求其操作数具有相同的值，但也要求它们具有相同的数据类型。

例如，下面的示例将显示“a and b are equal”（a 和 b 相等），但不会显示“a and b are identical”（a 和 b 全等）。

![](img/Image00261.jpg)

使用等于运算符时，数字字符串会被转换为整数。

### 对象比较

```
new stdClass() === new stdClass()
```

`===` 通过检查两个对象是否为完全相同的实例来进行比较。这意味着 `new stdClass() === new stdClass()` 解析为 false，即使它们是以相同方式创建的（并且具有完全相同的值）。

```
$a == $b
```

`==` 通过递归检查两个对象是否相等（深度相等）来进行比较。这意味着，对于 `$a == $b`，如果 `$a` 和 `$b`：

1.  属于同一个类
2.  设置了相同的属性，包括动态属性
3.  对于每个设置的属性 `$property`，`$a->property == $b->property` 为真（因此递归检查）。

### 其他常用运算符

它们包括：

1.  大于（`>`）
2.  小于（`<`）
3.  大于或等于（`>=`）
4.  小于或等于（`<=`）
5.  不等于（`!=`）
6.  不全等于（`!==`）

| 表达式 | 描述 |
| :--- | :--- |
| `$a > $b` | **大于**：如果 `$a` 的值大于 `$b`，则返回 true，否则返回 false。 |
| `$a < $b` | **小于**：如果 `$a` 的值小于 `$b`，则返回 true，否则返回 false。 |
| `$a >= $b` | **大于或等于**：如果 `$a` 的值大于 `$b` 或等于 `$b`，则返回 true，否则返回 false。 |
| `$a <= $b` | **小于或等于**：如果 `$a` 的值小于 `$b` 或等于 `$b`，则返回 true，否则返回 false。 |

**5/6. 不等于/不全等于**：重述一下前面关于相等性的示例，下面的示例将显示“a and b are not identical”（a 和 b 不全等），但不会显示“a and b are not equal”（a 和 b 不相等）。

![](img/Image00266.jpg)

#### 第 10.14 节：位运算符

### 前缀位运算符

位运算符类似于逻辑运算符，但按位执行，而不是按布尔值执行。

![](img/Image00267.jpg)

### 掩码-掩码运算符

**按位与 `&`**：仅当某位在两个操作数中都被设置时，该位才被设置

![](img/Image00268.jpg)

**按位或 `|`**：如果某位在任一或两个操作数中被设置，则该位被设置

![](img/Image00269.jpg)

**按位异或 `^`**：仅当某位在一个操作数中被设置而在另一个操作数中未被设置时，即该位在两个操作数中处于不同状态时，该位才被设置

![](img/Image00270.jpg)

### 位掩码的示例用法

这些运算符可用于操作位掩码。例如：

![](img/Image00271.jpg)

这里，`|` 运算符用于组合两个位掩码。虽然 `+` 具有相同的效果，但 `|` 强调你是在组合位掩码，而不是添加两个普通的标量整数。

![](img/Image00272.jpg)

这个示例（假设 `$option` 始终只包含一位）使用 `^` 运算符来方便地切换位掩码。




# 位运算符

## 按位或 (`|`)、非 (`~`)、与 (`&`)

- `|` 运算符会设置位，忽略其原始状态或其他位。
- `~` 运算符将仅设置了一个位的整数转换为仅未设置一个位的整数。
- `&` 运算符会清除位，利用了 `&` 的以下特性：
  - 与已设置的位进行 `&=` 操作不会做任何事 (`(1 & 1) === 1`, `(0 & 1) === 0`)。与仅有一个位未设置的整数进行 `&=` 操作将只清除该位，不影响其他位。
  - 与未设置的位进行 `&=` 操作将清除该位 (`(1 & 0) === 0`, `(0 & 0) === 0`)。
  - 将 `&` 运算符与另一个位掩码一起使用将过滤掉该位掩码中未设置的所有其他位。
  - 如果输出有任何位被设置，意味着位掩码中的任一选项已启用。
  - 如果输出有位掩码的所有位都被设置，意味着位掩码中的所有选项均已启用。

> **注意：** 请记住，这些比较运算符：(`<`, `>`, `<=`, `>=`, `==`, `===`, `!=`, `!==`, `<>`) 的优先级高于这些位掩码运算符：(`|`, `^`, `&`)。由于位运算结果经常使用这些比较运算符进行比较，这是一个需要注意的常见陷阱。

## 移位运算符

### 按位左移 (`<<`)
将所有位向左（更高位）移动给定的步数，并丢弃超过整数大小的位。

- `<< $x` 等同于清除最高的 `$x` 位并乘以 2 的 `$x` 次幂。

### 按位右移 (`>>`)
丢弃最低位，并将剩余位向右（更低位）移动。

- `>> $x` 等同于除以 2 的 `$x` 次幂并丢弃非整数部分。

### 移位运算的示例用法

**快速除以 16**（性能优于 `/= 16`）：
```
$x >> 4
```

**在不同架构上的行为：**
- 在 32 位系统上，`>> 32` 会丢弃整数中的所有位，将值设为 0。
- 在 64 位系统上，`>> 32` 会清除最高 32 位并保留最低 32 位，等同于：
  ```
  $x & 0xFFFFFFFF
  ```

> **注意：** 在示例 `printf("%'06b", $value)` 中，使用了格式说明符 `%\'06b`。它以 6 位二进制数字输出值。

#### 第 10.15 节：`instanceof`（类型运算符）

用于检查某个对象是否属于某个类，自 PHP 5 版本起可以使用（二元）`instanceof` 运算符。

- 第一个（左侧）参数是要测试的对象。如果该变量不是对象，`instanceof` 始终返回 `false`。如果使用常量表达式，将抛出错误。
- 第二个（右侧）参数是用于比较的类。类可以作为类名本身、包含类名的字符串变量（**不是字符串常量！**）或该类的对象来提供。

`instanceof` 也可用于检查对象是否属于继承自另一个类或实现了某个接口的类。

要检查对象是否**不**属于某个类，可以使用 `!` 运算符：
```
!$o instanceof MyClass
```
请注意，`$o instanceof MyClass` 周围不需要括号，因为 `instanceof` 的优先级高于 `!`，尽管加上括号可能会使代码更具可读性。

##### 注意事项

如果类不存在，会调用已注册的自动加载函数来尝试定义该类。在 PHP 5.1.0 之前的版本中，`instanceof` 运算符也会触发这些调用，从而实际定义该类（如果无法定义类，则会发生致命错误）。为避免这种情况，请使用字符串：
```
$o instanceof 'MyClass'
```
自 PHP 5.1.0 版本起，在这些情况下不再调用已注册的自动加载器。

##### PHP 旧版本（5.0 之前）

在 PHP 旧版本（5.0 之前）中，可以使用 `is_a()` 函数来确定对象是否属于某个类。该函数在 PHP 5 中被弃用，并在 PHP 5.3.0 中恢复使用。

## 第 11 章：引用

#### 第 11.1 节：按引用赋值

这是引用的第一阶段。本质上，当你[按引用赋值](http://php.net/manual/en/language.references.whatdo.php#language.references.whatdo.assign)时，你允许两个变量共享同一个值。

```
$foo = &$bar;
```
这里 `$foo` 和 `$bar` 相等。它们不互相指向。它们指向同一个位置（“值”）。

你也可以在 `array()` 语言结构中按引用赋值。虽然严格来说不是按引用赋值：
```
$arr = [&$value];
```

按引用赋值不仅限于变量和数组；函数和所有“按引用传递”关联也存在此情况。

```
function &myFunction() { ... }
```
如上所示，赋值在函数定义中至关重要。你不能按引用传递表达式，只能传递值/变量。因此示例中在 `myFunction()` 内实例化了 `$a`。

#### 第 11.2 节：按引用返回

有时你需要隐式地按引用返回。

```
function &myFunction() { ... }
```
当你想用函数来查找引用应绑定到哪个变量时，按引用返回很有用。**不要**为了提高性能而使用按引用返回。引擎会自动优化这一点。仅当你有正当的技术理由时才返回引用。

摘自 [PHP 文档：按引用返回](http://php.net/manual/en/language.references.return.php)。

按引用返回可以采取多种不同形式，包括以下示例：
```
function &myFunction() {
    $a = 5;
    return $a;
}
```

按引用返回不仅限于函数引用。你也可以隐式调用该函数：
```
echo &myFunction();
```

你不能直接引用函数调用；必须先将其赋值给变量才能利用它。要了解其工作原理，只需尝试 `myFunction();`。

##### 注意事项

你需要在打算使用引用的两个地方都指定引用（`&`）。这意味着在你的函数定义中（`function &myFunction() {`）和调用引用中（`callFunction(&$variable)` 或 `&myFunction()`）。

```
function &myFunction() { ... }
callFunction(&$variable);
```

> **提示：** 你只能按引用返回变量。因此示例中在函数内实例化了 `$a`。这意味着你不能返回表达式，否则将产生 `E_NOTICE` PHP 错误（“Only variable references should be returned by reference in ...”）。

按引用返回确实有合法的用例，但应谨慎使用，仅在探索了所有其他实现相同目标的潜在选项后才使用。

#### 第 11.3 节：按引用传递

这允许你将变量按引用传递给函数或允许修改原始变量的元素。

按引用传递不仅限于变量；以下内容也可以按引用传递：

- new 语句，例如 `foo(new SomeClass())`
- 从函数返回的引用
- 数组

```
$myElement = &$arr[0];
```
["按引用传递"](http://php.net/manual/en/language.references.pass.php) 的一个常见用例是在不创建新数组或不污染命名空间的情况下修改数组中的初始值。按引用传递很简单，只需在变量前加上 `&` => `&`。

下面是一个利用数组元素并将其初始值加 1 的示例。
```
foreach ($arr as &$value) {
    $value++;
}
```
现在当你访问 `$arr` 中的任何元素时，原始元素都会被更新，因为引用被增加了。你可以通过以下方式验证：
```
print_r($arr);
```

## 函数





## 第 12 章：数组

## 参数详解

键是数组的唯一标识符和索引。它可以是字符串或整数。因此，有效的键应该是：

`'foo'`、`'5'`、`10`、`'a2b`、...

对于每个键，都有一个对应的值（否则为 `null`，且访问时会发出通知）。值对输入类型没有限制。

数组是一种数据结构，它在单个值中存储任意数量的值。PHP 中的数组实际上是一个有序映射，其中映射是一种将值关联到键的类型。

#### 第 12.1 节：初始化数组

数组可以初始化为空：

```
$array = [];
```

数组可以初始化并预设值：

```
$array = [1, 2, 3];
```

数组也可以使用自定义索引进行初始化（也称为关联数组）：

```
$array = ['foo' => 'bar', 'baz' => 'qux'];
```

如果变量之前未被使用过，PHP 将自动创建它。虽然方便，但这可能会使代码更难阅读：

```
$array[] = 'value';
```

索引通常将从你停止的地方继续。PHP 会尝试将数字字符串作为整数使用：

```
$foo = [2 => 'apple', 'melon']; // Array([2] => apple, [3] => melon)
$foo = ['2' => 'apple', 'melon']; // 与上述相同
$foo = [2 => 'apple', 'this is index 3 temporarily', '3' => 'melon']; // 与上述相同！最后一项将覆盖第二项！
```

要使用固定大小初始化数组，可以使用 `SplFixedArray`：

```
$array = new SplFixedArray(5);
```

注意：使用 `SplFixedArray` 创建的数组对于大量数据集具有较小的内存占用，但键必须是整数。

要使用动态大小但具有 n 个非空元素（例如占位符）来初始化数组，可以使用如下循环：

```
$array = [];
for ($i = 0; $i < 10; $i++) {
    $array[] = null;
}
```

##### `array_fill`

```
array array_fill(int $start_index, int $num, mixed $value)
```

这将创建并返回一个包含 `num` 个 `value` 值的数组，键从 `start_index` 开始。

注意：如果 `start_index` 为负数，它将从负索引开始，后续元素从 0 继续。

```
$a = array_fill(5, 6, 'banana'); // Array([5] => banana, [6] => banana, ..., [10] => banana)
$b = array_fill(-2, 4, 'pear');  // Array([-2] => pear, [0] => pear, ..., [2] => pear)
```

##### `array_fill`

结论：使用 `array_fill()` 你能实际做的事情更受限。循环更灵活，并为你提供更广泛的机会。

##### `range`

每当你想要一个填充了数字范围的数组（例如 1-4）时，你可以向数组追加每个单独的元素，或者使用 `range()` 函数：

```
array range(mixed $start, mixed $end[, number $step = 1])
```

此函数创建一个包含一系列元素的数组。前两个参数是必需的，它们设置（包含的）范围的起点和终点。第三个参数是可选的，用于定义步长。创建一个从 0 到 4 步长为 1 的范围，生成的数组将包含以下元素：`0`、`1`、`2`、`3` 和 `4`。如果步长增加到 2（即 `(0, 4, 2)`），则生成的数组范围可以处理整数、浮点数、布尔值（将转换为整数）和字符串。然而，由于浮点数精度问题，使用浮点数作为参数时应谨慎。

#### 第 12.2 节：检查键是否存在

```
isset($map['foobar']);
```

`isset()` 将值为 null 的元素视为不存在。而 `!empty()` 对任何等于 false 的元素执行相同操作（使用弱比较；例如，`null`、`''` 和 `0` 都被 `empty()` 视为 false）。

```
isset($map['foobar']); // 为 true
!empty($map['foobar']); // 为 false
```

虽然如果 `$map` 根本未定义，`isset()` 和 `!empty()` 也能工作（并返回 false）。这使得它们在使用时容易出错：

```php
// 注意 "long" 与 "lang"，变量名中一个微小的拼写错误。
$my_array_with_a_long_name = ['foo' => true];
array_key_exists('foo', $my_array_with_a_lang_name); // 显示警告
isset($my_array_with_a_lang_name['foo']); // 返回 false
```

你也可以检查索引数组：

```
isset($array[0]);
```

注意 `isset()` 的性能优于 `array_key_exists()`，因为后者是函数而前者是语言结构。

##### `key_exists`

`key_exists()` 是 `array_key_exists()` 的别名。

你也可以使用 `array_key_exists()`。

#### 第 12.3 节：验证数组类型

##### `is_array`

如果变量是数组，函数 `is_array()` 返回 true。

```
is_array($variable);
```

你可以在函数中对数组类型进行类型提示以强制参数类型；传递其他任何内容将导致致命错误。

```
function foo(array $arr) {}
```

#### 第 12.4 节：创建变量数组

```
$vars = compact('var1', 'var2', 'var3');
```

此方法常用于框架中，在两个组件之间传递变量数组。

#### 第 12.5 节：检查值是否存在于数组中

##### `in_array`

如果项目存在于数组中，函数 `in_array()` 返回 true。

```
in_array('needle', $haystack);
in_array('needle', $haystack, true); // 严格模式
```

##### `array_search`

你也可以使用函数 `array_search()` 来获取数组中特定项目的键。

```
array_search('needle', $haystack);
```

PHP 5.x 版本 ≥ 5.5




# 第 12 章：ArrayAccess 和 Iterator 接口

#### 第 12.6 节：ArrayAccess 和 Iterator 接口

在 PHP 5.5 及更高版本中，你可以将 `array_column()` 与 `array_search` 结合使用。

这对于[检查值是否存在于关联数组中](http://stackoverflow.com/questions/6990855/php-check-if-value-and-key-exist-in-multidimensional-array/37935356#37935356)特别有用：

![Image00324.jpg](img/Image00324.jpg)

另一个有用的功能是在 PHP 中将自定义对象集合作为数组访问。PHP（>=5.0.0）核心中有两个可用的接口来支持此功能：`ArrayAccess` 和 `Iterator`。前者允许你将自定义对象作为数组访问。

##### ArrayAccess

假设我们有一个用户类和一个存储所有用户的数据库表。我们想要创建一个 `UserCollection` 类，该类将：

1. 允许我们通过用户名唯一标识符来定位特定用户
2. 对我们的用户集合执行基本操作（并非所有 CRUD，但至少包括创建、检索和删除）

考虑以下源代码（此后我们使用自版本 5.4 起可用的短数组创建语法 `[]`）：

![Image00325.jpg](img/Image00325.jpg)
![Image00326.jpg](img/Image00326.jpg)

然后我们可以：

```php
$users = new UserCollection();

var_dump(empty($users['testuser']), isset($users['testuser']));
$users['testuser'] = [
    'username' => 'testuser',
    'password' => 'testpassword',
    'email'    => 'test@test.com'
];
var_dump(empty($users['testuser']), isset($users['testuser']), $users['testuser']);
unset($users['testuser']);
var_dump(empty($users['testuser']), isset($users['testuser']));
```

假设在我们运行代码之前不存在 `testuser`，这将输出以下内容：

![Image00328.jpg](img/Image00328.jpg)

**重要：** 当你使用 `array_key_exists` 函数检查键是否存在时，`offsetExists` **不会**被调用。因此以下代码将输出两次 `false`：

```php
var_dump(array_key_exists('testuser', $users));
$users['testuser'] = [
    'username' => 'testuser',
    'password' => 'testpassword',
    'email'    => 'test@test.com'
];
var_dump(array_key_exists('testuser', $users));
```

![Image00329.jpg](img/Image00329.jpg)

##### Iterator

让我们通过添加来自 `Iterator` 接口的几个函数来扩展上面的类，以允许使用 `foreach` 和 `while` 对其进行迭代。

首先，我们需要添加一个保存我们当前迭代器索引的属性，将其作为 `$_position` 添加到类属性中：

![Image00330.jpg](img/Image00330.jpg)

其次，让我们将 `Iterator` 接口添加到我们的类所实现的接口列表中：

![Image00331.jpg](img/Image00331.jpg)

然后添加接口所需的函数本身：

![Image00332.jpg](img/Image00332.jpg)
![Image00333.jpg](img/Image00333.jpg)

所以总的来说，这里是同时实现两个接口的类的完整源代码。请注意，此示例并不完美，因为数据库中的 ID 可能不是连续的，但这只是为了给你一个主要思路：通过实现 `ArrayAccess` 和 `Iterator` 接口，你可以用任何可能的方式访问你的对象集合：

![Image00334.jpg](img/Image00334.jpg)

以及一个遍历所有用户对象的 `foreach` 循环：

![Image00335.jpg](img/Image00335.jpg)

这将输出类似以下的内容：

![Image00336.jpg](img/Image00336.jpg)

## 第 13 章：数组迭代

#### 第 13.1 节：同时迭代多个数组

有时需要同时迭代两个长度相同的数组，例如：

![Image00337.jpg](img/Image00337.jpg)

`array_map` 是实现此目的的最简单方法：

![Image00338.jpg](img/Image00338.jpg)

这将输出：

![Image00339.jpg](img/Image00339.jpg)

这可以通过公共索引来完成：

![Image00340.jpg](img/Image00340.jpg)

`array_values($array)[$i]` 可用于替换 `$array[$i]`。

如果两个数组没有递增的键，可以改用 `array_values` 或 `array_keys`。

如果两个数组具有相同顺序的键，你也可以在其中一个数组上使用带键的 `foreach` 循环：

![Image00341.jpg](img/Image00341.jpg)

只有当单独的数组长度相同且具有相同的键名时，才能循环遍历它们。这意味着如果你不提供键且它们是编号的，你将没问题；或者如果你命名了键并在每个数组中按相同顺序放置它们。

你也可以使用 `array_combine`。

```php
$combinedArray = array_combine($people, $foods);
// $combinedArray = ['Tim' => 'chicken', 'Tony' => 'beef', 'Turanga' => 'slurm'];
```

然后你可以通过执行与之前相同的操作来循环遍历它：

![Image00343.jpg](img/Image00343.jpg)

#### 第 13.2 节：使用递增索引

此方法通过将整数从 0 增加到数组中的最大索引来工作。

![Image00344.jpg](img/Image00344.jpg)

这也允许在不使用 `array_reverse` 的情况下按逆序迭代数组，如果数组很大，`array_reverse` 可能会导致开销。

![Image00345.jpg](img/Image00345.jpg)

使用此方法，你可以轻松跳过或倒回索引。

![Image00346.jpg](img/Image00346.jpg)

输出：

![Image00347.jpg](img/Image00347.jpg)

对于没有递增索引的数组（包括索引按逆序排列的数组，例如 `[1 => "bar"]`、`["foo" => "f", "bar" => "b"]`），无法直接执行此操作。可以改用 `array_values` 或 `array_keys`：

![Image00348.jpg](img/Image00348.jpg)

#### 第 13.3 节：使用内部数组指针

每个数组实例都包含一个内部指针。通过操作此指针，可以在不同时间从同一次调用中检索数组的不同元素。

##### 使用 `each`

每次调用 `each()` 都会返回当前数组元素的键和值，并将内部数组指针向前移动。

![Image00349.jpg](img/Image00349.jpg)

##### 使用 `next`

![Image00350.jpg](img/Image00350.jpg)

请注意，此示例假设数组中没有与布尔值 `false` 相同的元素。为防止此类假设，请使用 `key()` 检查内部指针是否已到达数组末尾：

![Image00351.jpg](img/Image00351.jpg)

这也便于在没有直接循环的情况下迭代数组：

![Image00352.jpg](img/Image00352.jpg)

#### 第 13.4 节：使用 foreach

##### 直接循环

![Image00353.jpg](img/Image00353.jpg)

##### 带键循环

![Image00354.jpg](img/Image00354.jpg)

##### 引用循环

在上面示例中的 `foreach` 循环中，直接修改值（`$color` 或 `$food`）不会改变其在数组中的值。需要 `&` 运算符，以便该值成为对数组中元素的引用指针。

![Image00355.jpg](img/Image00355.jpg)
![Image00356.jpg](img/Image00356.jpg)

这类似于：

![Image00357.jpg](img/Image00357.jpg)

##### 并发性

PHP 数组可以在迭代期间以任何方式修改，而不会出现并发问题（不像 Java `List` 等）。如果数组是按引用迭代的，后续迭代将受到数组更改的影响。否则，对数组的更改不会影响后续迭代（就好像你在迭代数组的副本一样）。比较按值循环：

![Image00358.jpg](img/Image00358.jpg)

输出：

![Image00359.jpg](img/Image00359.jpg)

但如果数组是按引用迭代的：

![Image00360.jpg](img/Image00360.jpg)

输出：

![Image00361.jpg](img/Image00361.jpg)

键值对 `4 => 5` 不再被迭代，且 `6 => 7` 被更改为 `6 => 17`。

#### 第 13.5 节：使用 ArrayObject 迭代器

PHP `ArrayIterator` 允许你在迭代数组和对象时修改和取消设置值。

示例：

![Image00362.jpg](img/Image00362.jpg)

输出：

![Image00363.jpg](img/Image00363.jpg)

## 第 14 章：对数组执行操作

#### 第 14.1 节：将函数应用于数组的每个元素

要将函数应用于数组中的每一项，请使用 `array_map()`。这将返回一个新数组。

![Image00364.jpg](img/Image00364.jpg)

你可以使用命名函数代替匿名函数。上面的代码可以写成：

![Image00365.jpg](img/Image00365.jpg)



如果命名函数是类方法，则该函数的调用必须包含对该方法所属类对象的引用：

![](img/Image00366.jpg)

| `array_walk()` | 和 | `array_walk_recursive()` |
| --- | --- | --- |

将函数应用到数组中每一项的另一种方式是 `array_walk()` 和 `array_walk_recursive()`。传入这些函数的回调函数接收每个数组项的键/索引和值。这些函数不会返回新数组，而是返回一个表示成功与否的布尔值。例如，打印简单数组中的每个元素：

![](img/Image00367.jpg)

回调函数的 `value` 参数可以按引用传递，允许你直接在原始数组中修改值：

![](img/Image00368.jpg)

| `array` |
| --- |

`$array` 现在是 `(2,3,4,5,6)`；

| `array_walk_recursive()` |
| --- |

对于嵌套数组，`array_walk_recursive()` 会深入到每个子数组中：

![](img/Image00369.jpg)

**注意**：`array_walk` 和 `array_walk_recursive` 允许你更改数组项的值，但不能更改键。将键按引用传递给回调函数在语法上有效，但没有任何效果。

#### 第 14.2 节：将数组分割成块

[`array_chunk()`](http://php.net/manual/en/function.array-chunk.php) 将数组分割成块。

假设我们有以下一维数组：

![](img/Image00370.jpg)

现在对上述 PHP 数组使用 `array_chunk()`：

![](img/Image00371.jpg)

上述代码将创建包含 2 个数组元素的块，并创建如下多维数组：

![](img/Image00372.jpg)

如果数组的所有元素不能被块大小整除，输出数组的最后一个元素将是剩余的元素。

如果我们将第二个参数传递为小于 1 的值，则会抛出 `E_WARNING`，输出数组将为 `NULL`。

| 参数 | 详情 |
| --- | --- |
| `$array` (array) | 输入数组，要操作的数组 |
| `$size` (int) | 每个块的大小（整数值） |
| `$preserve_keys` (boolean) (可选) | 如果你想让输出数组保留键，设为 `TRUE`，否则为 `FALSE`。 |

#### 第 14.3 节：将数组转换为字符串

| `implode()` |
| --- |

`implode()` 组合所有数组值，但会丢失所有键信息：

![](img/Image00373.jpg)

| `array_keys()` |
| --- |

可以使用 `array_keys()` 调用来组合键：

![](img/Image00374.jpg)

组合键和值更复杂，但可以使用函数式风格完成：

![](img/Image00375.jpg)

#### 第 14.4 节：使用 `list()` "解构" 数组

使用 [`list()`](http://php.net/manual/en/function.list.php) 快速将一组变量值赋值到数组中。另请参阅 `compact()`。

![](img/Image00376.jpg)

PHP 7.1（目前处于测试阶段）中，你将能够使用 [短列表语法](https://wiki.php.net/rfc/short_list_syntax)：

![](img/Image00377.jpg)

#### 第 14.5 节：`array_reduce`

`array_reduce` 将数组简化为单个值。基本上，`array_reduce` 会遍历每一项，带上上一次迭代的结果，并产生新值供下一次迭代使用。

| `array_reduce()` | | | `$array` | | `function` | | `$carry` | | `$item` | | `{` | `...` | `}` | `$defaul_value_of_first_carry` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

用法：`array_reduce($array, function($carry, $item) { ... }, $defaul_value_of_first_carry)`

`$carry` 是上一轮迭代的结果。`$item` 是数组中当前位置的值。

**数组求和**

![](img/Image00379.jpg)

![](img/Image00380.jpg)

结果：15

**数组中的最大数字**

![](img/Image00381.jpg)

结果：211

**所有项是否都大于 100**

![](img/Image00382.jpg)
```
$result = array_reduce([101, 230, 210, 341, 251], function ($carry, $item) {
    return $carry && $item > 100;
}, true); // 默认值必须设为 true
```
结果：true

**是否有任意项小于 100**

![](img/Image00383.jpg)
```
$result = array_reduce([101, 230, 21, 341, 251], function ($carry, $item) {
    return $carry || $item < 100;
}, false); // 默认值必须设为 false
```
结果：true

**类似 `implode($array, $piece)`**

![](img/Image00384.jpg)

结果："hello-world-PHP-language" 如果要实现一个 `implode` 方法，源代码将是：

![](img/Image00385.jpg)

#### 第 14.6 节：向数组推入值

| `$array` |
| --- |

![](img/Image00386.jpg) 向数组推入元素有两种方式：`array_push` 和 `[] =`。[`array_push`](http://php.net/manual/fr/function.array-push.php) 的用法如下：

`$array = [1,2,3];`

![](img/Image00387.jpg)
```
$newArraySize = array_push($array, 5, 6); // 该方法返回数组的新大小
print_r($array); // 数组按引用传递，因此原始数组被修改为
```

![](img/Image00388.jpg)

![](img/Image00389.jpg)

![](img/Image00390.jpg)

## 第 15 章：操作数组

#### 第 15.1 节：过滤数组

为了从数组中过滤出值并获得一个包含所有满足过滤条件的值的新数组，可以使用 `array_filter` 函数。

##### 过滤非空值

过滤最简单的情况是移除所有“空”值：

`$my_array = [1,0,2, null, 3, '', 4, [], 5,6,7,8];`

![](img/Image00391.jpg)
```
$non_empties = array_filter($my_array); // $non_empties 将包含 [1,2,3,4,5,6,7,8]
```

##### 按回调过滤

这次我们定义自己的过滤规则。假设我们只想获取偶数：

![](img/Image00392.jpg)

`array_filter` 函数接收要过滤的数组作为第一个参数，接收定义过滤谓词的回调函数作为第二个参数。

**版本 ≥ 5.6**

##### 按索引过滤

可以向 `array_filter` 函数提供第三个参数，用于调整传递给回调函数的值。该参数可以设置为 `ARRAY_FILTER_USE_KEY` 或 `ARRAY_FILTER_USE_BOTH`，这将导致回调函数接收数组中每个元素的键而不是值，或者同时接收值和键作为其参数。例如，如果你想处理索引而不是值：

![](img/Image00393.jpg)

注意 `array_filter` 保留原始数组键。一个常见的错误是尝试对过滤后的数组使用 `for` 循环：

![](img/Image00394.jpg)

![](img/Image00395.jpg)

之所以发生这种情况，是因为位于位置 1（值为 0）、3（值为 `null`）、5（空字符串 `''`）和 7（空数组 `[]`）的值连同其对应的索引键一起被移除了。

如果你需要遍历索引数组过滤后的结果，应该先在 `array_filter` 的结果上调用 `array_values`，以创建一个具有正确索引的新数组：

![](img/Image00396.jpg)

#### 第 15.2 节：从数组中移除元素

要移除数组内部的元素，例如索引为 1 的元素。

![](img/Image00397.jpg)

这将从列表中移除 apples，但请注意 `unset` 不会改变剩余元素的索引。所以 `$fruit` 现在包含索引 0 和 2。

对于关联数组，你可以这样移除：

![](img/Image00398.jpg)

现在 `$fruit` 是：

![](img/Image00399.jpg)

注意：

![](img/Image00400.jpg)

会取消设置变量，从而移除整个数组，意味着其元素都不再可访问。

##### 移除首尾元素

[`array_shift()`](http://php.net/manual/en/function.array-shift.php) - 将数组开头的元素移出。

示例：

![](img/Image00401.jpg)

输出：

![](img/Image00402.jpg)

[`array_pop()`](http://php.net/manual/en/function.array-pop.php) - 弹出数组末尾的元素。

示例：

![](img/Image00403.jpg)

输出：

![](img/Image00404.jpg)

#### 第 15.3 节：对数组排序

PHP 中有几个数组排序函数：

##### `sort()`

按值对数组进行升序排序。

![](img/Image00405.jpg)

结果为：

![](img/Image00406.jpg)

##### `rsort()`

按值对数组进行降序排序。

![](img/Image00407.jpg)

结果为：

![](img/Image00408.jpg)

##### `asort()`

按值对数组进行升序排序并保留索引。

![](img/Image00409.jpg)

结果为：

![](img/Image00410.jpg)

##### `arsort()`

按值对数组进行降序排序并保留索引。

![](img/Image00411.jpg)

结果为：

![](img/Image00412.jpg)

##### `ksort()`

按键对数组进行升序排序。

![](img/Image00413.jpg)

结果为：

![](img/Image00414.jpg)

##### `krsort()`

按键对数组进行降序排序。

![](img/Image00415.jpg)

结果为：

![](img/Image00416.jpg)




# 按键以降序对数组进行排序

![](img/Image00415.jpg)

结果为

![](img/Image00416.jpg)

##### `natsort()`

以人类的方式对数组进行排序（自然顺序）。

![](img/Image00417.jpg)

结果为

![](img/Image00418.jpg)

![](img/Image00419.jpg)

##### `natcasesort()`

以人类的方式对数组进行排序（自然顺序），但**区分大小写**

![](img/Image00420.jpg)

结果为

![](img/Image00421.jpg)

##### `shuffle()`

打乱数组（随机排序）。

![](img/Image00422.jpg)

正如描述中所写，这是随机的，所以这里只展示一种可能的结果示例

![](img/Image00423.jpg)

##### `usort()`

使用用户定义的比较函数对数组进行排序。

![](img/Image00424.jpg)

结果为

![](img/Image00425.jpg)

![](img/Image00426.jpg)

##### `uasort()`

使用用户定义的比较函数对数组进行排序，并**保留键名**。

![](img/Image00427.jpg)

结果为

![](img/Image00428.jpg)

##### `uksort()`

使用用户定义的比较函数，按键名对数组进行排序。

![](img/Image00429.jpg)

结果为

![](img/Image00430.jpg)

# 第 15 章：数组操作

#### 第 15.4 节：仅将某些数组键列入白名单

当你希望数组中仅允许特定的键，特别是当数组来自请求参数时，你可以将 `array_intersect_key` 与 `array_flip` 结合使用。

```
$parameters = ['foo' => 'bar', 'bar' => 'baz', 'boo' => 'bam'];
$allowedKeys = ['foo', 'bar'];
```

![](img/Image00431.jpg)
```
$filteredParameters = array_intersect_key($parameters, array_flip($allowedKeys));
// $filteredParameters 包含 ['foo' => 'bar', 'bar' => 'baz']
```

如果 parameters 变量不包含任何允许的键，则 filteredParameters 变量将由一个空数组组成。

自 PHP 5.6 起，你也可以为此任务使用 [`array_filter`](http://php.net/manual/en/function.array-filter.php#refsect1-function.array-filter-changelog)，将 [`ARRAY_FILTER_USE_KEY`](http://php.net/manual/en/array.constants.php#constant.array-filter-use-key) 标志作为第三个参数传递：

![](img/Image00432.jpg)

| `array_intersect_key` | | () 结合 | | `array_flip` |
| --- | --- | --- | --- | --- |

使用 `array_filter` 可以额外灵活地对键执行任意测试，例如 `$allowedKeys` 可以包含正则表达式模式，而不仅仅是纯字符串。与 `array_intersect_key` 结合 `array_flip` 相比，它也更明确地表达了代码的意图。

#### 第 15.5 节：向数组开头添加元素

| [`array_unshift`](http://php.net/array_unshift) |
| --- |

有时你想向数组开头添加一个元素，而不修改数组中当前元素的（顺序）。每当这种情况发生时，你可以使用 [`array_unshift`](http://php.net/array_unshift)。

`array_unshift` 将传入的元素**作为一个整体**预置到数组的前面。注意元素列表是

| `array_unshift` |
| --- |

![](img/Image00433.jpg) 作为一个整体被预置，因此预置的元素保持相同的顺序。所有数字键名将被修改为从零开始计数，而字面量键名不会被改动。

| `array_unshift` |
| --- |

摘自 [`array_unshift` 的 PHP 文档](http://php.net/array_unshift#refsect1-function.array-unshift-description)。

如果你想实现这一点，只需执行以下操作：

![](img/Image00434.jpg)

这将把 4 作为第一个元素添加到你的数组中。你可以通过以下方式验证：

![](img/Image00435.jpg)

| n + 1 |
| --- |

由于 `array_unshift` 强制数组重置键值对，因为新元素导致后续条目拥有这些键，因此创建一个新数组并将现有数组追加到新创建的数组中会更明智。

示例：

![](img/Image00436.jpg)

输出 ($joinedArray)：

![](img/Image00437.jpg)
```
Array
(
    [0] => oranges
    [1] => apples
    [2] => bananas
    [3] => pears
)
```

[示例/演示](http://www.tehplayground.com/#egwNCrZgr)

#### 第 15.6 节：交换键与值

`array_flip` 函数将交换所有键及其对应的元素。

![](img/Image00438.jpg)

#### 第 15.7 节：将两个数组合并为一个数组

![](img/Image00439.jpg)

关联数组：

![](img/Image00440.jpg)

1. 将一个或多个数组的元素合并在一起，以便一个数组的值被追加到前一个数组的末尾。它返回生成的数组。
2. 如果输入数组具有相同的字符串键名，则该键名稍后的值将覆盖前一个值。但是，如果数组包含数字键名，则稍后的值不会覆盖原始值，而是会被追加。
3. 输入数组中具有数字键名的值将在结果数组中重新编号，从零开始递增。

## 第 16 章：同时处理多个数组

#### 第 16.1 节：数组交集

`array_intersect` 函数将返回一个数组，包含所有传递给该函数的数组中都存在的值。

![](img/Image00441.jpg)

数组键名得以保留。原始数组的索引则不保留。

`array_intersect` 仅检查数组的值。`array_intersect_assoc` 函数将返回带有键名的数组交集。

```
$array_one = [1 => 'one', 2 => 'two', 3 => 'three'];
$array_two = [1 => 'one', 2 => 'two', 3 => 'two', 4 => 'three'];
$array_three = [1 => 'one', 2 => 'two'];
```

![](img/Image00442.jpg)
```
$intersect = array_intersect_assoc($array_one, $array_two, $array_three);
// $intersect 包含 [1 => 'one', 2 => 'two']
```

`array_intersect_key` 函数仅检查键名的交集。它将返回在所有数组中都存在的键名。

![](img/Image00443.jpg)

#### 第 16.2 节：合并或连接数组

![](img/Image00444.jpg)

注意 `array_merge` 会改变数字索引，但会覆盖字符串索引

![](img/Image00445.jpg)

如果无法重新编号索引，`array_merge` 会用第二个数组的值覆盖第一个数组的值。

你可以使用 `+` 运算符以一种永远不会覆盖第一个数组值的方式合并两个数组，但它不会重新编号数字索引，因此你会丢失第一个数组中也使用的索引的数组的值。

![](img/Image00446.jpg)

#### 第 16.3 节：将多维数组转换为关联数组

如果你有一个如下的多维数组：

![](img/Image00447.jpg)

并且你想将其更改为如下的关联数组：

![](img/Image00448.jpg)

你可以使用以下代码：

![](img/Image00449.jpg)

或者，你可以跳过设置 `$associativeArrayKeys` 和 `$associativeArrayValues`，使用这个简单的单行代码：

![](img/Image00450.jpg)
```
$associativeArray = array_combine(array_column($multidimensionalArray, 0), array_column($multidimensionalArray, 1));
```

#### 第 16.4 节：组合两个数组（键来自一个，值来自另一个）

以下示例展示了如何将两个数组合并为一个关联数组，其中键值将是第一个数组的项目，而值将来自第二个数组：

![](img/Image00451.jpg)

![](img/Image00452.jpg)

## 第 17 章：Datetime 类

#### 第 17.1 节：在 PHP 5.6 之前从可变 DateTime 创建不可变版本

要在 PHP 5.6+ 中创建 `\DateTimeImmutable`，请使用：

![](img/Image00453.jpg)

在 PHP 5.6 之前，你可以使用：

![](img/Image00454.jpg)
```
\DateTimeImmutable::createFromFormat(\DateTime::ISO8601, $mutable->format(\DateTime::ISO8601), $mutable->getTimezone());
```

#### 第 17.2 节：添加或减去日期间隔

我们可以使用类 [`DateInterval`](http://php.net/manual/pt_BR/class.dateinterval.php) 在 `DateTime` 对象中添加或减去某个间隔。

请看下面的例子，我们添加了一个 7 天的间隔并在屏幕上打印一条消息：

```
$now = new DateTime(); // 空参数返回当前日期
$interval = new DateInterval('P7D'); // 此对象代表 7 天的间隔
$lastDay = $now->add($interval); // 这将返回一个 DateTime 对象
```

![](img/Image00455.jpg)
```
$formatedLastDay = $lastDay->format('Y-m-d'); // 此方法格式化 DateTime 对象并返回一个字符串
echo "Samara says: Seven Days. You'll be happy on $formatedLastDay.";
```

这将输出（在 2016 年 8 月 1 日运行时）：



# 第 17 章：处理日期和时间

## 第 17.1 节：日期相减

我们可以用类似的方式使用 `sub` 方法来进行日期相减。

这将输出（在 2016 年 8 月 1 日运行时）：
Samara says: Seven Days. You were happy last on 2016-07-25.

## 第 17.2 节：getTimestamp

`getTimestamp` 是 datetime 对象的 Unix 表示形式。

这将输出一个整数，表示自 1970 年 1 月 1 日 星期四 00:00:00 UTC 以来经过的秒数。

## 第 17.3 节：setDate

`setDate` 在 `DateTime` 对象中设置日期。

此示例将日期设置为 2015 年 7 月 25 日，将产生以下结果：

## 第 17.4 节：从自定义格式创建 DateTime

PHP 能够解析[多种日期格式](https://secure.php.net/manual/en/datetime.formats.php)。如果你想解析非标准格式，或者希望代码明确指明所用的格式，则可以使用静态方法 `DateTime::createFromFormat()`：

**面向对象风格**

**过程化风格**

## 第 17.5 节：打印 DateTime

PHP 4+ 提供了一个 `format` 方法，可将 `DateTime` 对象按所需格式转换为字符串。根据 PHP 手册，这是面向对象的函数：

函数 `date()` 接受一个参数——格式，它是一个字符串。

### 格式

格式是一个字符串，使用单个字符来定义格式：

| 字符 | 说明 |
| :--- | :--- |
| `Y` | 年份的 4 位数字表示（例如：2016） |
| `y` | 年份的 2 位数字表示（例如：16） |
| `m` | 月份，数字表示（01 到 12） |
| `M` | 月份，三个字母表示（Jan, Feb, Mar 等） |
| `j` | 月份中的第几天，无前导零（1 到 31） |
| `D` | 星期中的第几天，三个字母表示（Mon, Tue, Wed 等） |
| `h` | 小时（12 小时制）（01 到 12） |
| `H` | 小时（24 小时制）（00 到 23） |
| `A` | AM 或 PM |
| `i` | 分钟，带前导零（00 到 59） |
| `s` | 秒，带前导零（00 到 59） |

完整列表可在[此处](http://php.net/manual/en/function.date.php)找到。

### 用法

这些字符可以各种组合使用，以几乎任何格式显示时间。以下是一些示例：

**过程化**

过程化格式类似：

## 第 18 章：处理日期和时间

#### 第 18.1 节：获取两个日期/时间之间的差值

最可行的方法是使用 `DateTime` 类。

示例：

此外，比较两个日期要容易得多，只需使用比较运算符，例如：

```php
<?php
// 创建一个日期时间对象，其值为约两年前
$twoYearsAgo = new DateTime("2014-01-18 20:05:56");

// 创建一个日期时间对象，其值为约现在
$now = new DateTime("2016-07-21 02:55:07");
var_dump($now > $twoYearsAgo); // 打印 bool(true)
var_dump($twoYearsAgo > $now); // 打印 bool(false)
var_dump($twoYearsAgo <= $twoYearsAgo); // 打印 bool(true)
var_dump($now == $now); // 打印 bool(true)
```

#### 第 18.2 节：将日期转换为另一种格式

### 基础知识

将一种日期格式转换为另一种格式的最简单方法是结合使用 `strtotime()` 和 `date()`。`strtotime()` 将日期转换为 [Unix 时间戳](http://en.wikipedia.org/wiki/Unix_time)。然后可以将该 Unix 时间戳传递给 `date()` 以将其转换为新格式。

或者写成单行代码：

```php
$new_date_format = date('Y-m-d H:i:s', strtotime('2008-07-01T22:35:17.02'));
```

请记住，`strtotime()` 要求日期采用[有效格式](https://php.net/manual/en/datetime.formats.php)。如果未提供有效格式，将导致 `strtotime()` 返回 false，进而导致你的日期变为 1969-12-31。

### 使用 `DateTime()`

自 PHP 5.2 起，PHP 提供了 `DateTime` 类，它为我们处理日期（和时间）提供了更强大的工具。我们可以使用 `DateTime` 重写上述代码，如下所示：

### 处理 Unix 时间戳

`date()` 接受 Unix 时间戳作为其第二个参数，并为你返回格式化的日期：

`DateTime()` 通过在时间戳前添加 `@` 来处理 Unix 时间戳：

如果你拥有的时间戳是以毫秒为单位的（可能以 000 结尾和/或时间戳长度为 13 位），则需要在转换为其他格式之前将其转换为秒。有两种方法可以做到这一点：

**使用 `substr()` 截取最后三位数字**

截取最后三位数字可以通过多种方式实现，但使用 `substr()` 是最简单的：

你也可以通过除以 1000 将时间戳转换为秒。由于时间戳太大，32 位系统无法对其进行数学运算，因此你需要使用 [BCMath](http://php.net/manual/en/book.bc.php) 库以字符串形式进行数学运算：

要获取 Unix 时间戳，可以使用 `strtotime()`，它返回一个 Unix 时间戳：

使用 `DateTime()` 时，可以使用 `DateTime::getTimestamp()`：

如果你运行的是 PHP 5.2，可以改用 `U` 格式化选项：

### 处理非标准和模棱两可的日期格式

不幸的是，开发人员必须处理的并非所有日期都采用标准格式。幸运的是，PHP 5.3 为我们提供了解决方案。`DateTime::createFromFormat()` 允许我们告诉 PHP 日期字符串采用的格式，以便它能成功解析为 `DateTime` 对象以供进一步操作。

```php
$date = DateTime::createFromFormat('F-d-Y h:i A', 'April-18-1973 9:48 AM');
$new_date_format = $date->format('Y-m-d H:i:s');
```

在 PHP 5.4 中，我们获得了在实例化时进行类成员访问的能力，这允许我们将 `DateTime` 代码变为单行：

```php
$new_date_format = (new DateTime('2008-07-01T22:35:17.02'))->format('Y-m-d H:i:s');
```

遗憾的是，这目前尚不适用于 `DateTime::createFromFormat`。

#### 第 18.3 节：将英语日期描述解析为日期格式



# 使用 `strtotime()` 和 `date()` 函数组合

使用 `date()` 函数可以解析不同的英文文本描述为日期：

```php
// Gets the current date
echo date("m/d/Y", strtotime("now")), "\n";
// prints the current date
echo date("m/d/Y", strtotime("10 September 2000")), "\n";
// prints September 10, 2000 in the m/d/Y format
echo date("m/d/Y", strtotime("-1 day")), "\n";
// prints yesterday's date
echo date("m/d/Y", strtotime("+1 week")), "\n";
// prints the result of the current date + a week
echo date("m/d/Y", strtotime("+1 week 2 days 4 hours 2 seconds")), "\n";
// same as the last example but with extra days, hours, and seconds added to it
echo date("m/d/Y", strtotime("next Thursday")), "\n";
// prints next Thursday's date
echo date("m/d/Y", strtotime("last Monday")), "\n";
// prints last Monday's date
echo date("m/d/Y", strtotime("First day of next month")), "\n";
// prints date of first day of next month
echo date("m/d/Y", strtotime("Last day of next month")), "\n";
// prints date of last day of next month
echo date("m/d/Y", strtotime("First day of last month")), "\n";
// prints date of first day of last month
echo date("m/d/Y", strtotime("Last day of last month")), "\n";
// prints date of last day of last month
```

# Section 18.4: 使用预定义常量进行日期格式化

我们可以在 `date()` 中使用预定义的日期格式常量，而不是传统的日期格式字符串（自 PHP 5.1.0 起可用）。

## 可用的预定义日期格式常量

| 常量 | 说明 | 示例 |
| :--- | :--- | :--- |
| `DATE_ATOM` | Atom | 2016-07-22T14:50:01+00:00 |
| `DATE_COOKIE` | HTTP Cookies | Friday, 22-Jul-16 14:50:01 UTC |
| `DATE_RSS` | RSS | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_W3C` | World Wide Web Consortium | 2016-07-22T14:50:01+00:00 |
| `DATE_ISO8601` | ISO-8601 | 2016-07-22T14:50:01+0000 |
| `DATE_RFC822` | RFC 822 | Fri, 22 Jul 16 14:50:01 +0000 |
| `DATE_RFC850` | RFC 850 | Friday, 22-Jul-16 14:50:01 UTC |
| `DATE_RFC1036` | RFC 1036 | Fri, 22 Jul 16 14:50:01 +0000 |
| `DATE_RFC1123` | RFC 1123 | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_RFC2822` | RFC 2822 | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_RFC3339` | Same as `DATE_ATOM` | 2016-07-22T14:50:01+00:00 |

## 使用示例

```php
// 示例代码图片占位符：Image00486.jpg
```

# Chapter 19: 控制结构

## Section 19.1: if else

示例中的 `if` 语句允许在条件满足时执行代码片段。当你想要在条件不满足时执行代码片段时，可以用 `else` 扩展 `if`。

```php
// 示例代码图片占位符：Image00487.jpg
```

参考：[PHP Manual - Control Structures - Else](http://php.net/manual/en/control-structures.else.php)

### 三元运算符作为 if-else 的简写语法

[三元运算符](http://php.net/manual/de/language.operators.comparison.php#language.operators.comparison.ternary) 根据条件是否为真来求值。它是一个比较运算符，常用于以更短的形式表达简单的 if-else 条件。它允许快速测试条件，并经常替换多行的 `if` 语句，使代码更紧凑。

```php
$a = 1;
$b = 2;
```

这是一个使用三元表达式和变量值的示例：

```php
echo ($a > $b) ? "a is greater than b" : "a is NOT greater than b";
```

输出：`a is NOT greater than b`。

## Section 19.2: 控制结构的替代语法

PHP 为某些控制结构提供了替代语法：`if`、`while`、`for`、`foreach` 和 `switch`。

| 结构 | 结束关键字 |
| :--- | :--- |
| `if` | `endif;` |
| `while` | `endwhile;` |
| `for` | `endfor;` |
| `foreach` | `endforeach;` |
| `switch` | `endswitch;` |

与普通语法相比，区别在于左大括号被冒号 (`:`) 替代，右大括号被对应的结束关键字（如 `endif;`）替代。有关单独示例，请参阅控制结构替代语法主题。

```php
// 示例代码图片占位符：Image00489.jpg
```

使用简写语法的多个 `elseif` 语句：

```php
// 示例代码图片占位符：Image00490.jpg
```

参考：[PHP Manual - Control Structures - Alternative Syntax](http://php.net/manual/en/control-structures.alternative-syntax.php)

## Section 19.3: while

`while` 循环会在指定条件为真时重复执行代码块。

```php
// 示例代码图片占位符：Image00491.jpg
```

输出：
```
123456789
```

详细信息请参阅 Loops 主题。

## Section 19.4: do-while

`do-while` 循环首先无条件执行一次代码块，然后在指定条件为真时重复执行该代码块。

```php
// 示例代码图片占位符：Image00492.jpg
```

详细信息请参阅 Loops 主题。

## Section 19.5: goto

`goto` 运算符允许跳转到程序的另一部分。自 PHP 5.3 起可用。

```php
goto MyLabel;
```

`goto` 指令后跟随目标标签。

```php
MyLabel:
```

跳转目标由标签加冒号 (`:`) 指定。

```php
// 示例代码图片占位符：Image00493.jpg
```

此例将输出 `Hello World!`。

## Section 19.6: declare

`declare` 用于为一段代码设置执行指令。

可识别的指令有：

*   [ticks](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.ticks)
*   [encoding](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.encoding)
*   [strict_types](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)

例如，设置 ticks 为 1：

```php
// 示例代码图片占位符：Image00494.jpg
```

要启用严格类型模式，请结合 `strict_types` 声明使用 `declare` 语句：

```php
// 示例代码图片占位符：Image00496.jpg
```

## Section 19.7: include & require

### require

`require` 类似于 `include`，不同之处在于失败时会产生致命的 `E_COMPILE_ERROR` 级别错误。`require` 失败会停止脚本执行；`include` 失败仅发出 `E_WARNING` 且不停止脚本。

```php
// 示例代码图片占位符：Image00497.jpg
```

参考：[PHP Manual - Control Structures - Require](http://php.net/manual/en/function.require.php)

### include

```php
// 示例代码图片占位符：Image00498.jpg
```

注意这种方法，因为它被认为是一种 [代码异味](https://en.wikipedia.org/wiki/Code_smell)，因为被包含的文件会改变给定作用域中已定义变量的数量和内容。

你也可以包含返回值的文件。这对于处理配置数组非常有用：

```php
// 示例代码图片占位符：Image00499.jpg
// 示例代码图片占位符：Image00500.jpg
```

这种方法可以防止被包含的文件用改变或新增的变量污染当前作用域。参考：[PHP Manual - Control Structures - Include](http://php.net/manual/en/function.include.php)

`include` 和 `require` 也可用于在文件返回值时将值赋给变量。

示例：`include1.php` 文件：

```php
// 示例代码图片占位符：Image00501.jpg
```

`index.php` 文件：

```php
// 示例代码图片占位符：Image00502.jpg
```

## Section 19.8: return

`return` 语句将程序控制权返回给调用函数。

当在函数内部调用 `return` 时，当前函数的执行将结束。

```php
// 示例代码图片占位符：Image00503.jpg
```

当你运行 `returnEndsFunctions();` 时，输出将为 `This is executed`。

当在函数内部带参数调用 `return` 时，当前函数的执行将结束，并将参数的值返回给调用函数。

## Section 19.9: for

`for` 循环通常用于你有一段想要重复指定次数的代码时。

```php
// 示例代码图片占位符：Image00504.jpg
```

输出：
```
123456789
```



有关详细信息，请参阅 Loops 主题。

## Section 19.10: foreach

`foreach` 是一种结构，可让您轻松遍历数组和对象。

![](img/Image00505.jpg)

输出：

123

.

要将 `foreach` 循环用于对象，该对象必须实现 `Iterator` 接口。

当您遍历关联数组时：

![](img/Image00506.jpg)

输出：color: red

有关详细信息，请参阅 Loops 主题。

## Section 19.11: if elseif else

`elseif` 结合了 `if` 和 `else`。`if` 语句得以扩展，以便在原始 `if` 表达式不满足时执行不同的语句。但是，只有当 `elseif` 条件表达式满足时，才会执行替代表达式。

以下代码显示 "a is bigger than b"、"a is equal to b" 或 "a is smaller than b"：

![](img/Image00507.jpg)

### Several elseif statements

您可以在同一个 `if` 语句中使用多个 `elseif` 语句：

![](img/Image00508.jpg)

![](img/Image00509.jpg)

## Section 19.12: if

`if` 结构允许有条件地执行代码片段。

![](img/Image00510.jpg)

[PHP Manual - Control Structures - If](http://php.net/manual/en/control-structures.if.php)

## Section 19.13: switch

`switch` 结构的功能与一系列 `if` 语句相同，但可以用更少的代码行完成工作。`switch` 语句中定义的待测试值将与每个 `case` 语句中的值进行相等比较，直到找到匹配项并执行该块中的代码。如果未找到匹配的 `case` 语句，则执行 `default` 块中的代码（如果存在）。

`case` 或 `default` 语句中的每个代码块都应以 `break` 语句结束。这将停止 `switch` 结构的执行，并继续执行其后的代码。如果省略 `break` 语句，则会执行下一个 `case` 语句的代码，即使没有匹配项。如果忘记 `break` 语句，这可能会导致意外的代码执行，但当多个 `case` 语句需要共享相同代码时，这也很有用。

![](img/Image00511.jpg)

除了测试固定值外，该结构还可以通过向 `switch` 语句提供布尔值并向 `case` 语句提供任意表达式，来强制测试动态语句。请记住，使用的是第一个匹配的值，因此以下代码将输出 "more than 100"：

![](img/Image00512.jpg)

![](img/Image00513.jpg)

关于使用 `switch` 结构时松散类型可能导致的问题，请参阅 Switch Surprises

# Chapter 20: Loops

循环是编程的一个基本方面。它们允许程序员创建重复执行指定次数（或迭代）的代码。迭代次数可以是显式的（例如 6 次迭代），也可以持续到满足某个条件为止（"until Hell freezes over"）。

本主题涵盖不同类型的循环、其相关的控制语句及其在 PHP 中的潜在应用。

## Section 20.1: continue

![](img/Image00514.jpg)

`continue` 关键字停止循环的当前迭代，但不会终止循环。

就像 `break` 语句一样，`continue` 语句位于循环体内。执行时，`continue` 语句会导致执行立即跳转到循环条件。

在以下示例中，循环根据数组中的值打印消息，但会跳过指定的值。

![](img/Image00515.jpg)

预期输出为：

![](img/Image00516.jpg)

`continue` 语句也可用于通过指定要跳过的循环层级数，立即继续执行外层循环。例如，考虑如下数据：

Fruit Color Cost

Apple Red 1

Banana Yellow 7

Cherry Red 2

Grape Green 4

为了仅使用成本低于 5 的水果制作派

![](img/Image00517.jpg)

![](img/Image00518.jpg)

| continue || 2 语句执行时，执行立即跳回到 || $data as $fruit |
| --- | --- | --- |

执行 `continue 2` 语句时，执行立即跳回到 `foreach ($data as $fruit)`，继续外层循环并跳过所有其他代码（包括内层循环中的条件判断。

## Section 20.2: break

![](img/Image00519.jpg)

`break` 关键字立即终止当前循环。

与 `continue` 语句类似，`break` 语句会停止循环的执行。然而，与 `continue` 语句不同的是，`break` 会导致循环立即终止，且不会再次执行条件语句。

![](img/Image00520.jpg)

此代码将产生

![](img/Image00521.jpg)

但不会执行 `$i` 为 0 的情况，否则会因除以 0 导致致命错误。

`break` 语句也可用于跳出多层循环。这种行为在执行嵌套循环时非常有用。例如，将字符串数组复制到输出字符串中，移除任何 `#` 符号，直到输出字符串恰好为 160 个字符

![](img/Image00522.jpg)

| break |
| --- |

`break 2` 命令立即终止内层和外层循环的执行。

## Section 20.3: foreach

![](img/Image00523.jpg)

`foreach` 语句用于遍历数组。

每次迭代时，当前数组元素的值被赋给 `$value` 变量，数组指针向后移动一位，下一次迭代将处理下一个元素。

以下示例显示赋值数组中的项目。

![](img/Image00524.jpg)

预期输出为：

![](img/Image00525.jpg)

您也可以使用 `foreach` 访问值的键/索引：

![](img/Image00526.jpg)

默认情况下，`$value` 是 `$list` 中值的副本，因此在循环内部所做的更改不会在之后反映在 `$list` 中。

![](img/Image00527.jpg)

要在 `foreach` 循环中修改数组，请使用 `&` 运算符按引用赋值 `$value`。重要的是之后要 `unset` 该变量，以便在其他地方重用 `$value` 时不会覆盖数组。

![](img/Image00528.jpg)

您也可以通过引用当前项目的数组键，在 `foreach` 循环中修改数组项。

![](img/Image00529.jpg)

## Section 20.4: do...while

![](img/Image00530.jpg)

| do ... while |
| --- |

![](img/Image00531.jpg)

`do ... while` 语句将至少执行一次代码块——然后只要条件为真，就会重复循环。

以下示例将 `$i` 的值至少增加一次，只要它的值小于 25，就会继续增加变量 `$i`；

![](img/Image00532.jpg)

预期输出为：

![](img/Image00533.jpg)

## Section 20.5: for

![](img/Image00534.jpg)

当您知道要执行语句或语句块的次数时，使用 `for` 语句。

初始化器用于设置循环迭代次数计数器的起始值。可以在此处为此目的声明一个变量，按照惯例通常将其命名为 `$i`。

以下示例迭代 10 次并显示 0 到 9 的数字。

![](img/Image00535.jpg)

预期输出为：

![](img/Image00536.jpg)

## Section 20.6: while

![](img/Image00537.jpg)

`while` 语句将在测试表达式为真时且只要为真时执行代码块。

如果测试表达式为真，则执行代码块。代码执行后，将再次对测试表达式求值，循环将继续，直到测试表达式被判定为假。

以下示例迭代直到总和达到 100 后终止。

![](img/Image00538.jpg)

预期输出为：

![](img/Image00539.jpg)

# Chapter 21: Functions

## Section 21.1: Variable-length argument lists

Version ≥ 5.6

PHP 5.6 引入了可变长度参数列表（又名 varargs、可变参数），在参数名称前使用 `...` 标记来指示该参数是可变的，即它是一个包含从该参数开始提供的所有参数的数组。

![](img/Image00540.jpg)

类型名称可以添加在 `...` 前面：

![](img/Image00541.jpg)

`&` 引用运算符可以添加在 `...` 之前，但在类型名称之后（如果有）。请考虑此示例：

![](img/Image00542.jpg)

输出：




# 第 21 章：函数参数与用法

## 第 21.1 节：可变参数函数与参数解包

另一方面，参数数组（或 `Traversable`）可以被解包，以参数列表的形式传递给函数：

```
Output:
```

对比这段不使用 `...` 的代码片段：

```
Output:
```

因此，现在可以轻松地为可变参数函数创建重定向函数，例如：

除了数组之外，`Traversable`（如 `Iterator`，特别是 SPL 中的许多子类）也可以被使用。例如：

```
$iterator = new LimitIterator(new ArrayIterator([0, 1, 2, 3, 4, 5, 6]), 2, 3);
echo bin2hex(pack("c*", ...$it));
// Output: 020304
```

如果迭代器无限迭代，例如：

不同版本的 PHP 表现不同：

##### 从 PHP 7.0.0 到 PHP 7.1.0 (beta 1)

将发生段错误

```
PHP 进程将以代码 139 退出
```

##### 在 PHP 5.6 中

将显示内存耗尽的致命错误 ("Allowed memory size of %d bytes exhausted")。PHP 进程将以代码 255 退出

```
注意：HHVM (v3.10 - v3.12) 不支持解包 Traversables。尝试时将显示警告消息 "Only containers may be unpacked"。
```

## 第 21.2 节：可选参数

函数可以拥有可选参数，例如：

## 第 21.3 节：按引用传递参数

函数参数可以“按引用传递”，允许函数修改函数外部使用的变量：

对象参数总是按引用传递：

为避免隐式按引用传递对象，你应该克隆该对象。

按引用传递也可用作返回参数的替代方式。例如 `socket_getpeername` 函数：

```
bool socket_getpeername(resource $socket, string &$address[, int &$port])
```

该方法实际上旨在返回对端的地址和端口，但由于有两个值需要返回，它选择使用引用参数。可以这样调用：

变量 `$address` 和 `$port` 不需要预先定义。它们将：

1.  首先被定义为 `null`，
2.  然后带着预定义的 `null` 值被传递给函数
3.  然后在函数内被修改
4.  最终在调用上下文中被定义为地址和端口。

## 第 21.4 节：基本函数用法

基本函数的定义和执行如下：

## 第 21.5 节：函数作用域

函数内部的变量处于局部作用域，如下所示

## 第 22 章：函数式编程

PHP 的函数式编程依赖于函数。PHP 中的函数提供了有组织的、可复用的代码来执行一组操作。函数简化了编码过程，防止了冗余逻辑，并使代码更易于理解。本主题描述了 PHP 中函数、参数、形参、返回语句和作用域的声明与使用。

#### 第 22.1 节：闭包

闭包是一个无法访问外部作用域的匿名函数。

当像这样定义一个匿名函数时，你正在为该函数创建一个“命名空间”。它目前只能访问该命名空间。

| use |
| --- |

它无法访问任何外部变量。要授予此命名空间访问外部变量的权限，你需要通过闭包 (`()`) 将其引入。

这主要归因于 PHP 严格的变量作用域——如果一个变量未在作用域内定义，或未通过 `global` 引入，则它不存在。

另请注意：

从父作用域继承变量与使用全局变量并不相同。全局变量存在于全局作用域中，无论执行哪个函数，该作用域都是相同的。

闭包的父作用域是声明该闭包的函数（不一定是调用它的函数）。

摘自 [PHP 文档：匿名函数](http://php.net/manual/en/functions.anonymous.php)

在 PHP 中，闭包使用早绑定方法。这意味着使用 `use` 关键字传递给闭包命名空间的变量，其值在闭包定义时就已确定。

要改变此行为，你应该按引用传递变量。

定义带有/不带有闭包的匿名函数时，默认参数不会被隐式要求。

#### 第 22.2 节：赋值给变量

[匿名函数](http://php.net/manual/en/functions.anonymous.php)可以赋值给变量，以便在需要回调的地方作为参数使用：

这些变量也可以作为独立的函数调用使用：

#### 第 22.3 节：对象作为函数

拥有 `__invoke` 方法的对象可以完全像其他函数一样使用。

`__invoke` 方法将有权访问对象的所有属性，并能够调用任何方法。

#### 第 22.4 节：使用外部变量

`use` 结构用于将变量导入匿名函数的作用域：

变量也可以按引用导入：

#### 第 22.5 节：匿名函数

匿名函数就是一个没有名称的函数。

在 PHP 中，匿名函数被视为一种表达式，因此，它应该以分号 `;` 结尾。

匿名函数应该赋值给一个变量。

或者它应该作为另一个函数的参数传递。

甚至可以从另一个函数返回。

### 自执行匿名函数：

### 向自执行匿名函数传递参数：

#### 第 22.6 节：纯函数

纯函数是指给定相同的输入，总是返回相同的输出，且没有副作用的函数。

一些副作用包括：更改文件系统、与数据库交互、打印到屏幕。

#### 第 22.7 节：PHP 中常见的函数式方法

### 映射

将函数应用于数组的所有元素：

请注意，这是列表中唯一一个回调函数位于第一个位置的方法。

### 归约（或折叠）

将数组归约为单个值：

### 过滤

仅返回回调函数返回 `true` 的数组项：

#### 第 22.8 节：使用内置函数作为回调

在接受 `callable` 作为参数的函数中，你也可以放入一个包含 PHP 内置函数名称的字符串。通常使用 `trim` 作为 `array_map` 的参数，以移除数组中所有字符串的首尾空白字符。

#### 第 22.9 节：作用域

在 PHP 中，匿名函数拥有自己的作用域，就像任何其他 PHP 函数一样。

在 JavaScript 中，匿名函数可以访问外部作用域的变量。但在 PHP 中，这是不允许的。

#### 第 22.10 节：将回调函数作为参数传递

有几个 PHP 函数接受用户定义的回调函数作为参数，例如：

| `call_user_func` | `usort` | `array_map` |
| --- | --- | --- |




[(](https://secure.php.net/manual/en/function.array-map.php) [)](https://secure.php.net/manual/en/function.array-map.php) .

根据用户定义的回调函数定义的位置，有不同的方式来传递它们：

过程式风格：

![](img/Image00585.jpg)

面向对象风格：

![](img/Image00586.jpg)

使用静态方法的面向对象风格：

![](img/Image00587.jpg)

## 第 23 章：控制结构的替代语法

#### 第 23.1 节：替代 if/else 语句

![](img/Image00588.jpg)

#### 第 23.2 节：替代 for 语句

![](img/Image00589.jpg)

#### 第 23.3 节：替代 while 语句

![](img/Image00590.jpg)

#### 第 23.4 节：替代 foreach 语句

![](img/Image00591.jpg)

![](img/Image00592.jpg)

#### 第 23.5 节：替代 switch 语句

![](img/Image00593.jpg)

## 第 24 章：字符串格式化

#### 第 24.1 节：字符串插值

你也可以使用插值将变量插入（插入）到字符串中。插值仅在双引号字符串和 heredoc 语法中有效。

![](img/Image00594.jpg)

[复杂（花括号）语法](http://php.net/manual/en/language.types.string.php#language.types.string.parsing.complex)格式提供了另一种选择，要求你将变量包裹在花括号 `{}` 中。当在文本内容中嵌入变量并有助于防止文本内容和变量之间可能出现的歧义时，这很有用。

![](img/Image00595.jpg)

`{}` 语法仅将以 `$` 开头的变量插值到字符串中。`{}` 语法不计算任意 PHP 表达式。

![](img/Image00596.jpg)

然而，`{}` 语法确实会计算变量、数组元素或属性上的任何数组访问、属性访问以及函数/方法调用：

```
$companions = [0 => [ 'name' => 'Amy Pond' ], 1 => [ 'name' => 'Dave Random' ]]; echo "The best companion is: {$companions[0]['name']} " ;
```

请注意，美元 `$` 符号可以像上面的例子一样出现在左花括号 `{` 之后，或者像在 Perl 或 Shell 脚本中一样，出现在它之前：

![](img/Image00599.jpg)

#### 第 24.2 节：提取/替换子字符串

单个字符可以使用数组（方括号）语法以及花括号语法来提取。这两种语法将仅从字符串返回单个字符。如果需要多个字符，则需要一个函数，即 [substr](http://php.net/manual/en/function.substr.php)

![](img/Image00600.jpg)

字符串也可以使用相同的方括号和花括号语法一次更改一个字符。替换多个字符需要一个函数，即 [substr_replace](http://php.net/manual/en/function.substr-replace.php)

![](img/Image00601.jpg)

```
substr_replace ( $foo , 'W' , 6, 1); // 也会导致 $foo = 'Hello World'
substr_replace ( $foo , 'Whi' , 6, 2); // 结果为 'Hello Whirled'

// 注意替换字符串不必与被替换的子字符串长度相同
```

## 第 25 章：字符串解析

#### 第 25.1 节：按分隔符分割字符串

[explode](http://php.net/explode) 和 [strstr](http://php.net/strstr) 是通过分隔符获取子字符串的更简单方法。

包含由公共字符分隔的多个文本部分的字符串可以使用 [explode](http://php.net/explode) 函数分割成多个部分。

```
$fruits = "apple,pear,grapefruit,cherry" ;
```

```
print_r ( explode ( "," , $fruits )); // ['apple', 'pear', 'grapefruit', 'cherry']
```

该方法还支持一个 limit 参数，可按如下方式使用：

![](img/Image00604.jpg)

```
如果 limit 参数为零，则将其视为 1。
print_r ( explode ( ',' , $fruits ,0)); // ['apple,pear,grapefruit,cherry']
```

```
如果设置了 limit 且为正数，返回的数组将包含最多 limit 个元素，最后一个元素包含字符串的其余部分。
print_r ( explode ( ',' , $fruits ,2)); // ['apple', 'pear,grapefruit,cherry']
```

如果 limit 参数为负数，则返回除最后 -limit 个组件外的所有组件。

```
print_r ( explode ( ',' , $fruits ,-1)); // ['apple', 'pear', 'grapefruit']
```

`explode` 可以与 [list](http://php.net/list) 结合使用，在一行中将字符串解析为变量：

![](img/Image00608.jpg)

但是，请确保 `explode` 的结果包含足够的元素，否则会触发未定义索引警告。`strstr` 会去除或仅返回给定 needle 第一次出现之前的子字符串。

![](img/Image00609.jpg)

#### 第 25.2 节：子字符串

Substring 返回由 start 和 length 参数指定的字符串部分。

![](img/Image00610.jpg)

如果有可能遇到多字节字符字符串，那么使用 `mb_substr` 会更安全。

![](img/Image00611.jpg)

另一个变体是 `substr_replace` 函数，它替换字符串一部分中的文本。

```
var_dump ( substr_replace ( "Boo" , "0" , 1, 1)); // string(3) "B0o"
var_dump ( substr_Replace ( "Boo" , "ts" , strlen ( "Boo" ))); // string(5) "Boots"
```

假设你想在字符串中查找特定单词 - 且不想使用正则表达式。

```
$hi = "Hello World!" ; $bye = "Goodbye cruel World!" ;

var_dump ( strpos ( $hi , " " )); // int(5)
var_dump ( strpos ( $bye , " " )); // int(7)

var_dump ( substr ( $hi , 0, strpos ( $hi , " " ))); // string(5) "Hello"
var_dump ( substr ( $bye , -1 * ( strlen ( $bye ) - strpos ( $bye , " " )))); // string(13) " cruel World!"
```

```
// 如果文本中的大小写不重要，则使用 strtolower 有助于比较字符串
var_dump ( substr ( $hi , 0, strpos ( $hi , " " )) == 'hello' ); // bool(false)
var_dump ( strtolower ( substr ( $hi , 0, strpos ( $hi , " " ))) == 'hello' ); // bool(true)
```

另一个选择是对电子邮件进行非常基本的解析。

![](img/Image00614.jpg)

```
if ( $wld == "co.uk" ) var_dump ( " $wrong is a UK address" );
if ( $nld == "co.uk" ) var_dump ( " $notld is a UK address" );
```

甚至在简介末尾加上“继续阅读”或“...”

![](img/Image00616.jpg)

#### 第 25.3 节：使用 strpos 搜索子字符串

`strpos` 可以理解为在 haystack 中第一次出现 needle 之前的字节数。

```
var_dump ( strpos ( "haystack" , "hay" )); // int(0)
var_dump ( strpos ( "haystack" , "stack" )); // int(3)
var_dump ( strpos ( "haystack" , "stackoverflow" ); // bool(false)
```

检查子字符串是否存在

当针对 TRUE 或 FALSE 进行检查时要小心，因为如果返回索引 0，if 语句会将其视为 FALSE。

![](img/Image00618.jpg)

整个示例的输出：

![](img/Image00619.jpg)

从偏移量开始搜索

![](img/Image00620.jpg)

![](img/Image00621.jpg)

![](img/Image00622.jpg)

#### 第 25.4 节：使用正则表达式解析字符串

`preg_match` 可用于使用正则表达式解析字符串。括在括号中的表达式部分称为子模式，通过它们你可以提取字符串的各个部分。

![](img/Image00623.jpg)

输出

![](img/Image00624.jpg)

## 第 26 章：类和对象

类和对象用于通过将相似任务分组，使你的代码更高效、重复性更低。

类用于定义用于构建对象的操作和数据结构。然后使用这个预定义的结构来构建对象。

#### 第 26.1 节：类常量

类常量提供了一种在程序中保存固定值的机制。也就是说，它们提供了一种为像 `3.14` 或 `"Apple"` 这样的值命名（并提供相关的编译时检查）的方法。类常量只能使用 `const` 关键字定义 - [define](http://php.net/define) 函数不能在此上下文中使用。



# 类常量

作为一个例子，在整个程序中拥有一个 π 值的简写表示可能会很方便。一个包含 `const` 值的类提供了一种简单的方式来保存此类值。

![](img/Image00625.jpg)

| MathValues :: PI |
| --- |

![](img/Image00626.jpg)

类常量可以通过在类上使用双冒号操作符（即所谓的作用域解析操作符）来访问，这很像静态变量。然而，与静态变量不同的是，类常量的值在编译时固定，不能重新赋值（例如 `= 7` 会产生致命错误）。

类常量对于定义类内部可能稍后需要更改的内容也很有用（但更改频率不足以值得存储在数据库中）。我们可以在内部使用 `self` 作用域解析器来引用它（它在实例化和静态实现中均有效）。

![](img/Image00627.jpg)

在版本 < 5.6 中，类常量只能包含标量值。

自 PHP 5.6 起，我们可以在常量中使用表达式，这意味着数学语句和带有连接的字符串都是可接受的常量。

![](img/Image00628.jpg)

自 PHP 7.0 起，用 `define` 声明的常量现在可以包含数组。

![](img/Image00629.jpg)

类常量不仅用于存储数学概念。例如，如果准备做派，拥有一个单一的 `Pie` 类来接收不同种类的水果可能会很方便。

![](img/Image00630.jpg)

然后我们可以这样使用 `Pie` 类：

![](img/Image00631.jpg)

这里出现的问题是，实例化 `Pie` 类时，没有提供关于可接受值的指导。例如，制作“boysenberry”派时，可能会拼写成 "boisenberry"。此外，我们可能不支持李子派。相反，如果在一个合理的地方预先定义好可接受的水果类型列表，那将很有用。比如一个名为 `Fruit` 的类：

![](img/Image00632.jpg)

| new Pie('aple') | Pie('apple') 均可通过编译器检查 | new Pie(Fruit::APLE) |
| --- | --- | --- |

将可接受的值列为类常量，为方法接受的可接受值提供了有价值的提示。它还能确保拼写错误无法通过编译器检查。虽然 `new Pie('aple')` 和 `new Pie(Fruit::APLE)` 会产生编译器错误。

最后，使用类常量意味着常量的实际值可以在单一位置修改，任何使用该常量的代码都会自动获得修改的效果。

| MyClass::CONSTANT_NAME |
| --- |

虽然访问类常量最常用的方法是 `MyClass::CONSTANT_NAME`，但也可以通过以下方式访问：

![](img/Image00633.jpg)

PHP 中的类常量按照惯例通常全部大写，单词之间以下划线分隔，尽管任何有效的标签名都可用作类常量名。

自 PHP 7.1 起，类常量现在可以定义为不同于默认 `public` 作用域的可见性。这意味着现在可以定义 `protected` 和 `private` 常量，以防止类常量不必要地泄露到公共作用域中（请参阅方法和属性可见性）。例如：

![](img/Image00634.jpg)

![](img/Image00635.jpg)

## `define` 对比 类常量

虽然这是一个有效的结构：

![](img/Image00636.jpg)

如果你尝试对类常量做同样的事情，会得到一个错误：

![](img/Image00637.jpg)

但你可以这样做：

![](img/Image00638.jpg)

更多信息，请参阅手册中的 [constants](http://php.net/manual/en/language.constants.php)。

## 使用 `::class` 获取类名

| ::class |
| --- |

PHP 5.5 引入了 `::class` 语法来获取完整的类名，会考虑命名空间作用域和 `use` 语句。

![](img/Image00639.jpg)

即使类未定义，上述代码也有效（即这段代码片段可以单独运行）。

当函数需要类名时，此语法很有用。例如，它可以与 `class_exists` 一起使用来检查类是否存在。无论返回值如何，此片段都不会生成错误：

![](img/Image00640.jpg)

#### 第 26.2 节：抽象类

抽象类是不能被实例化的类。抽象类可以定义抽象方法，这些方法没有任何主体，只有定义：

![](img/Image00641.jpg)

![](img/Image00642.jpg)

抽象类应由子类继承，子类随后可以提供这些抽象方法的实现。

此类类的主要目的是提供一种模板，允许子类继承，“强制”遵循一种结构。让我们通过一个例子详细说明：

在本例中，我们将实现一个 `Worker` 接口。首先定义接口：

![](img/Image00643.jpg)

| run() |
| --- |

为了简化后续 `Worker` 实现的开发，我们将创建一个抽象 Worker 类，它已经提供了来自接口的 `run()` 方法，但指定了一些需要由任何子类填充的抽象方法：

![](img/Image00644.jpg)

| getMemoryLimit() |
| --- |

首先，我们提供了一个抽象方法 `getMemoryLimit()`。任何继承自 `AbstractWorker` 的类都需要提供此方法并返回其内存限制。然后 `AbstractWorker` 设置内存限制并记录日志。

| prepareMain() 和 main() |
| --- |

其次，`AbstractWorker` 在记录日志后调用 `prepareMain()` 和 `main()` 方法。

最后，所有这些方法调用都被归组在一个 `try-catch` 块中。因此，如果子类定义的任何抽象方法抛出异常，我们将捕获该异常，记录日志并重新抛出。这防止了所有子类都必须自行实现此逻辑。

现在让我们定义一个继承自 `AbstractWorker` 的子类：

![](img/Image00645.jpg)

正如你所见，`TransactionProcessorWorker` 实现起来相当容易，因为我们只需指定内存限制并担心它需要执行的实际操作。`TransactionProcessorWorker` 中不需要错误处理，因为这在 `AbstractWorker` 中已处理。

##### 重要提示

![](img/Image00646.jpg)

继承自抽象类时，父类声明中标记为 `abstract` 的所有方法都必须由子类定义（或者子类本身也必须标记为 `abstract`）；此外，这些方法必须用相同（或限制更宽松）的可见性来定义。例如，如果抽象方法定义为 `protected`，函数实现必须定义为 `protected` 或 `public`，但不能是 `private`。

摘自 [PHP 文档 - 类的抽象](http://php.net/manual/en/language.oop5.abstract.php)。

如果你不在子类中定义父抽象类的方法，将会抛出如下致命 PHP 错误。

![](img/Image00647.jpg)

```
Fatal error: Class X contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (X::x) in
```

#### 第 26.3 节：静态后期绑定

| self:: |
| --- |

在 PHP 5.3+ 及以上版本中，你可以利用[静态后期绑定](http://php.net/manual/en/language.oop5.late-static-bindings.php)来控制从哪个类调用静态属性或方法。它的加入是为了克服 `self` 作用域解析器固有的问题。请看以下代码：

![](img/Image00648.jpg)

| whatToSay() |
| --- |

你可能期望 `MrEd` 类会覆盖父类的 `whatToSay()` 函数。但当我们运行它时，会得到意想不到的结果：

![](img/Image00649.jpg)

| self::whatToSay() |
| --- |

| static:: |
| --- |

问题在于 `self::whatToSay()` 只能指向 `Horse` 类，意味着它不服从 `MrEd`。如果我们改用 `static::` 作用域解析器，就没有这个问题。这个较新的方法告诉类服从调用它的实例。因此我们得到了预期的继承行为：

![](img/Image00650.jpg)

#### 第 26.4 节：命名空间和自动加载




# PHP 中的自动加载与面向对象概念

## 自动加载基础

从技术上讲，自动加载的工作原理是在需要某个 PHP 类但未找到时执行回调函数。此类回调通常尝试加载这些类。

通常，自动加载可以理解为：当需要某个类时，尝试根据该类的**完全限定名**（FQN）从适当的路径加载 PHP 文件（特别是 PHP 类文件，即一个 PHP 源文件专门用于定义一个特定的类）。

假设我们有以下类：

- `application\controllers\Base` 的类文件
- `application\controllers\Control` 的类文件
- `application\models\Page` 的类文件

在源文件夹下，这些类应根据其 FQN 分别放置在对应的路径中。

这种方法使得可以根据 FQN 以编程方式解析类文件路径，使用如下函数：

```php
function getClassPath(string $sourceFolder, string $className, string $extension = ".php") {
    return $sourceFolder . "/" . str_replace("\\", "/", $className) . $extension;
    // 注意 "/" 在 Windows 上也可作为目录分隔符
}
```

`spl_autoload_register()` 函数允许我们在需要时使用用户定义的函数来加载类。

该函数可以进一步扩展以使用备选加载方法。

请注意，PHP 并不会在加载使用该类的文件时立即尝试加载类。它可能在脚本执行的中间阶段加载，甚至在关闭函数中加载。这就是为什么开发者，尤其是使用自动加载的开发者，应避免在运行时替换正在执行的源文件，特别是在 phar 文件中。

#### 第 26.5 节：方法与属性可见性

您可以将三种可见性类型应用于类中的方法（类/对象函数）和属性（类/对象变量），它们为所应用的方法或属性提供访问控制。

您可以在 [PHP 文档：面向对象可见性](http://php.net/manual/en/language.oop5.visibility.php) 中详细阅读相关内容。

### Public（公有）

将方法或属性声明为 `public` 允许以下对象访问该方法或属性：

- 声明它的类。
- 继承自声明类的类。
- 类层级结构之外的任何外部对象、类或代码。

### Protected（受保护）

将方法或属性声明为 `protected` 允许以下对象访问该方法或属性：

- 声明它的类。
- 继承自声明类的类。

这**不**允许类层级结构之外的外部对象、类或代码访问这些方法或属性。如果使用该方法/属性的代码没有访问权限，则该方法/属性将不可用，并会抛出错误。只有声明类自身的实例（或其子类的实例）才能访问它。

上述示例指出，您只能在其自身的作用域内访问受保护的元素。本质上：“房子里的东西只能在房子里访问。”

### Private（私有）

将方法或属性声明为 `private` 允许以下对象访问该方法或属性：

- **仅**声明它的类（不包括子类）。

私有方法或属性仅在创建它的类内部可见且可访问。

请注意，即使对象不是同一个实例，同一类型的对象也将拥有对彼此私有和受保护成员的访问权。

如前所述，您只能从其定义的类内部访问私有方法/属性。

#### 第 26.6 节：接口

##### 简介

接口是类必须实现的公共 API 定义，以满足接口的要求。它们作为“契约”发挥作用，规定了一组子类**做什么**，但不规定**怎么做**。

接口的定义与类定义非常相似，只需将关键字 `class` 改为 `interface`。

接口可以包含方法和/或常量，但不能包含属性。接口常量具有与类常量相同的限制。接口方法隐式为抽象方法。

注意：接口不得声明构造函数或析构函数，因为这些是类层面的实现细节。

##### 实现

任何需要实现接口的类都必须使用 `implements` 关键字来实现。为此，该类需要为接口中声明的每个方法提供实现，并遵循相同的签名。

一个类可以同时实现多个接口。

当抽象类实现接口时，它们不需要实现所有方法。基类中未实现的任何方法必须由继承它的具体类来实现。

请注意，接口实现是一种继承特性。当扩展一个实现了接口的类时，您不需要在具体类中重新声明它，因为这是隐式的。

注意：在 PHP 5.3.9 之前，类不能实现两个指定了同名方法的接口，因为这会导致歧义。较新版本的 PHP 允许这样做，只要重复的方法具有相同的签名 [[1]](http://php.net/manual/en/language.oop5.interfaces.php)。

##### 继承

与类一样，可以使用相同的关键字 `extends` 在接口之间建立继承关系。主要区别在于接口允许多重继承。

##### 示例

在下面的示例中，我们有一个简单的车辆接口。车辆可以前进和后退。

然后我们创建两个实现该接口的类：`Bike` 和 `Car`。`Bike` 和 `Car` 在内部实现上截然不同，但两者都是车辆，必须实现 `VehicleInterface` 提供的相同公共方法。

类型提示允许方法和函数请求接口类型。假设我们有一个停车场类，它包含各种类型的车辆。

因为 `addVehicle()` 需要类型为 `VehicleInterface` 的 `$vehicle` —— 而不是具体的实现 —— 所以我们可以传入 `Bike` 和 `Car` 对象，`ParkingGarage` 可以对它们进行操作和使用。

#### 第 26.7 节：Final 关键字

**定义：** `final` 关键字通过在定义前加上 `final` 前缀，防止子类覆盖某个方法。如果类本身被定义为 `final`，则它不能被继承。

##### Final 方法

##### Final 类

##### Final 常量

与 Java 不同，`final` 关键字在 PHP 中**不**用于类常量。请改用关键字 `const`。

##### 为什么要使用 final？

1. 防止巨大的“厄运继承链”
2. 鼓励组合
3. 强迫开发者思考用户公共 API
4. 强迫开发者缩小对象的公共 API
5. Final 类始终可以变为可扩展的
6. `extends` 破坏封装
7. 你不需要那种灵活性
8. 你可以自由修改代码

##### 何时避免使用 final

Final 类仅在以下假设下有效工作：

1. 存在一个该 final 类实现的抽象（接口）
2. 该 final 类的所有公共 API 都是该接口的一部分

#### 第 26.8 节：自动加载

没有人想在每次使用类或继承时都去 `require` 或 `include`。因为这很痛苦且容易忘记，PHP 提供了所谓的自动加载。如果您已经在使用 Composer，请阅读关于使用 Composer 进行自动加载的内容。

##### 究竟什么是自动加载？




顾名思义。你不必获取存放所请求类的文件，而是由 PHP 自动加载。

如何在不使用第三方代码的基础 PHP 中实现这一点？

有一个 `__autoload` 函数，但被认为最佳实践是使用 `spl_autoload_register`。每当在给定空间内未定义类时，PHP 都会考虑这些函数。因此，向现有项目添加自动加载不是问题，因为已定义的类（例如通过 require）将像以前一样工作。为了严谨起见，以下示例将使用匿名函数；如果你使用 PHP < 5.3，可以定义函数并将其名称作为参数传递给 `spl_autoload_register`。

##### 示例

```
FooBar
```

上述代码只是尝试使用 `sprintf` 包含一个以类名加上扩展名 ".php" 命名的文件。如果需要加载 `FooBar`，它会检查 `FooBar.php` 是否存在，如果存在则包含它。

当然，这可以扩展以适应项目的个性化需求。如果类名中的 `_` 用于分组，例如 `User_Post` 和 `User_Image` 都指向 `User`，那么这两个类可以像这样保存在一个名为 "User" 的文件夹中：

```
User_Post
```

类 `User_Post` 现在将从 "User/Post.php" 加载，以此类推。

`spl_autoload_register` 可以定制以满足各种需求。所有包含类的文件都命名为 "class.CLASSNAME.php"？没问题。各种嵌套（`User_Post_Content` => "User/Post/Content.php"）？也没问题。

如果你想要一个更复杂的自动加载机制——但仍然不想引入 Composer——你可以在不添加第三方库的情况下工作。

```
spl_autoload_register(function ($class) {
    $prefix = 'MyApp\\';
    $base_dir = __DIR__ . '/src/';
    $len = strlen($prefix);
    if (strncmp($prefix, $class, $len) !== 0) {
        return;
    }
    $relative_class = substr($class, $len);
    $file = $base_dir . str_replace('\\', '/', $relative_class) . '.php';
    if (file_exists($file)) {
        require $file;
    }
});
```

使用这样的自动加载器，你可以愉快地编写如下代码：

```
use MyApp\Database;
use MyApp\User;
use MyApp\Post;
```

使用类：

```
foo/bar.php, foo.php, hello/world.php and demo/classes.php
```

这些示例将从 `MyApp` 包含类。

#### 第 26.9 节：实例化子类时调用父类构造函数

##### `__construct`

从其子类调用 `__construct()` 方法。如果你需要这样做，则需要使用 `parent::` 作用域解析操作符：

```
class ParentClass {
    function __construct() {
        echo "Parent constructor\n";
    }
}

class ChildClass extends ParentClass {
    function __construct() {
        parent::__construct();
        echo "Child constructor\n";
    }
}

$obj = new ChildClass();
```

现在在实际场景中利用这一点看起来会像这样：

```
class Database {
    protected $connection;
    public function __construct($host, $user, $pass) {
        $this->connection = new mysqli($host, $user, $pass);
    }
}

class User extends Database {
    public function __construct($host, $user, $pass) {
        parent::__construct($host, $user, $pass);
    }
}
```

##### `__construct`

以上将运行父类的 `__construct()`，从而导致 echo 被执行。

#### 第 26.10 节：动态绑定

动态绑定，也称为方法重写，是运行时多态的一个例子，当多个类包含同一方法的不同实现，但将调用该方法的对象直到运行时才知道时，就会发生这种情况。

如果某个条件决定使用哪个类来执行一个动作，而该动作在两个类中命名相同，这很有用。

```
interface Animal {
    public function makeNoise();
}

class Dog implements Animal {
    public function makeNoise() {
        echo "Bark";
    }
}

class Cat implements Animal {
    public function makeNoise() {
        echo "Meow";
    }
}
```

```
class User {
    public $petType = 'Dog';
    public function makePetNoise() {
        $pet = new $this->petType();
        $pet->makeNoise();
    }
}

$user = new User();
$user->makePetNoise(); // Outputs "Bark"
```

| Dog | | | Cat |
| --- | --- | --- | --- |

在上面的示例中，`Animal` 类的 `makeNoise()` 将调用哪个 `makeNoise` 直到运行时才知道，这取决于 `User` 类中的属性。

#### 第 26.11 节：$this、self 和 static 以及单例模式

| `$this->member` | 用于非静态成员，使用 | `self::$member` |
| --- | --- | --- |

```
class MyClass {
    public $prop = "I'm an instance property";
    public static $staticProp = "I'm a static property";
    
    public function showProps() {
        echo $this->prop;      // Correct: Accessing instance property
        echo self::$staticProp; // Correct: Accessing static property
    }
}
```
使用 `$this` 来引用当前对象。使用 `self` 来引用当前类。换句话说，对静态成员使用 `self::$member`。

| `sayHello()` | 和 | `sayGoodbye()` |
| --- | --- | --- |

在下面的示例中，`sayHello()` 和 `sayGoodbye()` 使用 `self` 和 `$this` 的区别可以在此观察到。

```
class Greeting {
    public static function sayHello() {
        echo "Hello ";
    }
    
    public function sayGoodbye() {
        self::sayHello();
        echo "Goodbye";
    }
}

$g = new Greeting();
$g->sayGoodbye(); // Outputs "Hello Goodbye"
```

```
class A {
    public static function who() {
        echo __CLASS__;
    }
    
    public static function test() {
        self::who();
    }
}

class B extends A {
    public static function who() {
        echo __CLASS__;
    }
}

B::test(); // Outputs "A" (because self refers to A)
```

`static` 指的是你在层次结构中调用该方法的任何类。它允许在类被继承时更好地复用静态类属性。

考虑以下代码：

```
class Car {
    public static $brand = 'unknown';
    
    public static function getBrand() {
        return self::$brand;
    }
}

class BMW extends Car {
    public static $brand = 'BMW';
}

class Mercedes extends Car {
    public static $brand = 'Mercedes';
}

echo Car::getBrand();    // unknown
echo BMW::getBrand();    // unknown (undesired)
echo Mercedes::getBrand(); // unknown (undesired)
```

这不会产生你想要的结果：

```
unknown unknown unknown
```

| brand |
| --- |

那是因为无论何时调用方法 `getBrand()`，`self` 都指向 `Car` 类。

要引用正确的类，你需要改用 `static`：

```
class Car {
    public static $brand = 'unknown';
    
    public static function getBrand() {
        return static::$brand; // Late Static Binding
    }
}

class BMW extends Car {
    public static $brand = 'BMW';
}

class Mercedes extends Car {
    public static $brand = 'Mercedes';
}
```

```
echo Car::getBrand();    // unknown
echo BMW::getBrand();    // BMW
echo Mercedes::getBrand(); // Mercedes
```

这确实产生了期望的输出：

```
unknown
BMW
Mercedes
```

另请参阅静态延迟绑定。

##### 单例模式

如果你有一个创建成本高昂或代表某个你想复用的外部资源连接的对象，即没有连接池的数据库连接或通往其他系统的套接字，你可以在类中使用 `static` 和 `self` 关键字使其成为单例。关于单例模式是否应该使用存在强烈的观点分歧，但它确实有其用途。

```
class Database {
    private static $instance = null;
    private $connection;
    
    private function __construct() {
        $this->connection = new PDO('mysql:host=localhost;dbname=test', 'user', 'pass');
    }
    
    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }
    
    public function getConnection() {
        return $this->connection;
    }
}
```

正如你在示例代码中所见，我们定义了一个私有静态属性 `$instance` 来保存对象引用。由于这是静态的，此引用在该类型的**所有**对象间共享。

##### `getInstance`

`getInstance()` 方法使用一种称为惰性实例化的方法，将创建对象延迟到最后可能的时刻，因为你不希望内存中躺着从未打算使用的未使用对象。它还节省了页面加载时不必加载不必要对象的时间和 CPU。该方法检查对象是否已设置，如果没有则创建它，并返回它。这确保了永远只创建一个此类对象。

我们还将构造函数设为私有，以确保没有人从外部使用 `new` 关键字创建它。如果你需要从此类继承，只需将 `private` 关键字改为 `protected`。

要使用此对象，只需编写以下内容：

```
$db = Database::getInstance();
$conn = $db->getConnection();
```

现在我**确实**恳请你在可能的地方使用依赖注入并以松耦合对象为目标，但有时这根本不合理，单例模式可能会有用。

#### 第 26.12 节：定义基本类

PHP 中的对象包含变量和函数。对象通常属于一个类，该类定义了该类所有对象将包含的变量和函数。

定义类的语法是：

```
class MyClass {
    public $property = 'value';
    
    public function myMethod() {
        return 'Hello World';
    }
}
```

一旦定义了类，你可以使用以下方式创建实例：

```
$obj = new MyClass();
```

对象上的变量和函数这样访问：

```
echo $obj->property; // Outputs 'value'
echo $obj->myMethod(); // Outputs 'Hello World'
```

##### 构造函数

##### `__construct`

类可以定义一个特殊的 `__construct()` 方法，它作为对象创建的一部分被执行。这通常用于指定对象的初始值：

```
class Person {
    public $name;
    
    public function __construct($name) {
        $this->name = $name;
    }
}

$person = new Person('John');
echo $person->name; // Outputs 'John'
```

##### 扩展另一个类

类定义可以扩展现有的类定义，添加新的变量和函数，以及修改父类中定义的那些。

这是一个扩展前面示例的类：

```
class Shape {
    public $color = 'red';
}

class Square extends Shape {
    public $sides = 4;
}
```

```
$square = new Square();
echo $square->color; // Outputs 'red' (inherited from Shape)
echo $square->sides; // Outputs '4' (defined in Square)
```

`Square` 类包含 `Shape` 类和 `Square` 类的变量和行为：

```
$square = new Square();
$square->color = 'blue';
echo $square->color; // Outputs 'blue'
```

#### 第 26.13 节：匿名类

匿名类在 PHP 7 中引入，以便轻松创建快速的一次性对象。它们可以接受构造函数参数、扩展其他类、实现接口并使用 trait，就像普通类一样。

在其最基本的形式中，匿名类如下所示：

```
$util = new class {
    public function sayHello() {
        echo "Hello";
    }
};

$util->sayHello(); // Outputs "Hello"
```




嵌套在另一个类内部的匿名类无法访问该外部类的 `private` 或 `protected` 方法或属性。可以通过让匿名类继承外部类来获得对外部类 `protected` 方法和属性的访问权限。可以通过构造函数将外部类的 `private` 属性传递给匿名类来获得访问权限。

例如：

![](img/Image00706.jpg)

![](img/Image00707.jpg)

## 第 27 章：命名空间

## 27.1 节：声明命名空间

命名空间声明如下所示：

| `namespace MyProject` |
| --- |

| `namespace MyProject\Security\Cryptography` |
| --- |

| `namespace MyProject` | `{` | `...` |
| --- | --- | --- |

![](img/Image00708.jpg)；`- 声明命名空间 MyProject`
`;` `- 声明嵌套命名空间`
`}` `- 使用大括号声明命名空间。`

建议每个文件只声明一个命名空间，尽管你可以在单个文件中声明任意数量：

![](img/Image00709.jpg)

每次声明命名空间后，随后定义的类都将属于该命名空间：

![](img/Image00710.jpg)

| `namespace MyProject\Shapes` |
| --- |

命名空间声明可以在不同文件中多次使用。上例在单个文件中于 `MyProject\Shapes` 命名空间下定义了三个类。最好将其拆分为三个文件，每个文件均以 `namespace MyProject\Shapes;` 开头。详见 PSR-4 标准示例。

## 27.2 节：引用命名空间中的类或函数

如“声明命名空间”所示，可按如下方式在命名空间中定义类：

![](img/Image00711.jpg)

引用该类需使用完整路径（含命名空间）：

![](img/Image00712.jpg)

可通过 `use` 语句导入类以简化引用：

![](img/Image00713.jpg)

PHP 7.0 起，可使用大括号在一条语句中分组多个 `use` 语句：

![](img/Image00714.jpg)

有时两个类同名。若处于不同命名空间则无问题，但若尝试用 `use` 语句导入则会冲突：

![](img/Image00715.jpg)

可用 `as` 关键字自定义别名解决：

![](img/Image00716.jpg)

引用当前命名空间外的类需用 `\` 转义，否则会假定为相对于当前命名空间的相对路径：

![](img/Image00717.jpg)

## 27.3 节：声明子命名空间

声明具有层级的单个命名空间示例：

![](img/Image00718.jpg)

![](img/Image00719.jpg)

上例创建了：

常量 `MyProject\Sub\Level\CONNECT_OK`、类 `MyProject\Sub\Level\Connection` 和函数 `MyProject\Sub\Level\connect`。

## 27.4 节：什么是命名空间？

PHP 社区开发者众多，代码量巨大。这意味着某库的 PHP 代码可能与另一库使用相同的类名。当两个库在同一命名空间下使用时，会发生冲突并导致问题。

命名空间解决了此问题。正如 PHP 参考手册所述，命名空间可类比为操作系统目录对文件的命名空间划分；同名文件可共存于不同目录。同理，同名 PHP 类可共存于不同 PHP 命名空间。

为代码添加命名空间至关重要，这样其他开发者使用时无需担心与其他库冲突。

## 第 28 章：会话

## 28.1 节：`session_start()` 选项

| [ph](http://php.net/manual/en/ini.list.php) [p](http://php.net/manual/en/ini.list.php) | [.](http://php.net/manual/en/ini.list.php) | [in](http://php.net/manual/en/ini.list.php) [i](http://php.net/manual/en/ini.list.php) |
| --- | --- | --- |

PHP 7 起，可向 `session_start` 函数传递包含[基于会话的](http://php.net/manual/en/ini.list.php)[选项](http://php.net/manual/en/ini.list.php)的数组。

示例

![](img/Image00720.jpg)

| `php` | `.` | `ini` | `setting named` | `session` | `.` | `lazy_write` |
| --- | --- | --- | --- | --- | --- | --- |

此特性还引入了 `session.lazy_write`，默认为 `true`，表示仅在会话数据变更时才重写。

参考：[`wiki.php.net/rfc/session-lock-ini`](https://wiki.php.net/rfc/session-lock-ini)

## 28.2 节：会话锁定

| `session_start` |
| --- |

| `session_start` |
| --- |

众所周知，PHP 将会话数据写入服务端文件。当请求调用 `session_start()` 的 PHP 脚本时，PHP 会锁定该会话文件，导致相同 `session_id` 的其他传入请求阻塞/等待，直到会话文件锁释放。

会话文件保持锁定直到脚本结束或手动关闭会话。为避免多请求阻塞，可启动会话后关闭会话，释放文件锁，允许后续请求继续。

![](img/Image00721.jpg)

即使会话关闭，仍可读取会话值，因会话数据仍可用。

![](img/Image00722.jpg)

PHP >= 7.0 支持 `read_only`、`read_write` 和 `lazy_write` 会话，可能无需使用 `session_write_close()`。

## 28.3 节：操作会话数据

`$_SESSION` 变量是数组，可像普通数组一样检索或操作。

![](img/Image00723.jpg)

更多数组操作参考“操作数组”。

注意：若在会话中存储对象，仅当有类自动加载器或类已加载时才能优雅恢复。否则对象会作为 `__PHP_Incomplete_Class` 类型返回，可能导致[崩溃](http://stackoverflow.com/q/1055728/3990767)。自动加载详见“命名空间与自动加载”。

警告：

会话数据可能被劫持。详见：《Pro PHP Security: From Application Security Principles to the Implementation of XSS Defense - Chapter 7: Preventing Session Hijacking》（https://books.google.com.au/books?id=EUc6NlZRDqcC&pg=PA97#v=onepage&q&f=false）

强烈建议切勿在 `$_SESSION` 中存储任何个人信息。最关键的是信用卡号、政府颁发的 ID、密码；也包括姓名、邮箱、电话等不太敏感但可让黑客冒充/攻破合法用户的数据。通用原则：会话数据仅使用无价值/非个人值，如数字标识符。

## 28.4 节：销毁整个会话

| [`session_destroy`](http://php.net/session_destroy) |
| --- |

若需销毁会话，可用 `session_destroy()`：

![](img/Image00724.jpg)

![](img/Image00725.jpg)

| `session_destroy()` | 与 `$_SESSION = array();` 不同 |
| --- | --- |

`session_destroy()` 会移除 SESSION 超全局变量中所有存储的值，但不会销毁实际存储的会话版本。

| `$_SESSION = array();` | 代替 `session_unset()` |
| --- | --- |

注意：用 `$_SESSION = array();` 是因[手册](http://php.net/session_destroy)规定：

![](img/Image00726.jpg) 仅在不使用 `$_SESSION` 的旧弃用代码中使用 `session_unset()`。

## 28.5 节：无错误的安全会话启动



许多开发者在处理大型项目时会遇到这个问题，特别是当他们在某些模块化 CMS 的插件、附加组件、组件等上工作时。这里提供了一种安全启动会话的解决方案：首先检查 PHP 版本以覆盖所有版本，然后检查会话是否已启动。如果会话不存在，则安全地启动会话。如果会话已存在，则不执行任何操作。

![](img/Image00727.jpg)

#### 第 28.6 节：会话名称

### 检查会话 Cookie 是否已创建

会话名称是用于存储会话的 Cookie 的名称。你可以用它来检测是否已为用户创建了会话的 Cookie：

![](img/Image00728.jpg)

请注意，除非你真的不想不必要地创建 Cookie，否则这种方法通常没有用处。

### 更改会话名称

| `session_name` |
| --- |

你可以通过调用 `session_name()` 来更新会话名称。

![](img/Image00729.jpg)

| `session_name` |
| --- |

如果 `session_name()` 未提供参数，则返回当前的会话名称。

![](img/Image00730.jpg)

它应仅包含字母数字字符；应简短且具有描述性（即针对启用了 Cookie 警告的用户）。会话名称不能仅由数字组成，至少必须包含一个字母。否则，每次都会生成一个新的会话 ID。

## 第 29 章：Cookies

##### 参数详情

Cookie 的名称。这也是你可以用来从 `$_COOKIE` 超全局变量中检索值的键。这是唯一的必需参数。

| name | value | expire | path | domain | secure | httponly |
| --- | --- | --- | --- | --- | --- | --- |
| Cookie 的名称。这也是你可以用来从 `$_COOKIE` 超全局变量中检索值的键。这是唯一的必需参数。 | 存储在 Cookie 中的值。此数据可被浏览器访问，因此请勿在此存储任何敏感信息。 | 一个 Unix 时间戳，表示 Cookie 何时过期。如果设置为零，Cookie 将在会话结束时过期。如果设置为小于当前 Unix 时间戳的数字，Cookie 将立即过期。 | Cookie 的作用域。如果设置为 `/`，Cookie 将在整个域名下可用。如果设置为 `/path/`，则 Cookie 仅在该路径及其子路径下可用。默认为设置 Cookie 的文件的当前路径。 | Cookie 可用的域名或子域名。如果设置为裸域名，则 Cookie 将在该域名及所有子域名下可用。如果设置为子域名，则 Cookie 仅在该子域名及其所有子子域名下可用。 | 当设置为 `TRUE` 时，仅当客户端和服务器之间存在安全的 HTTPS 连接时才会设置 Cookie。 | 指定 Cookie 仅应通过 HTTP/S 协议提供，不应提供给 JavaScript 等客户端脚本语言。仅在 PHP 5.2 或更高版本中可用。 |

HTTP Cookie 是网站发送的一小段数据，当用户浏览网页时，由用户的 Web 浏览器存储在用户的计算机上。

#### 第 29.1 节：修改 Cookie

可以通过重置 Cookie 来修改其值。

![](img/Image00731.jpg)

#### 第 29.2 节：设置 Cookie

| `setcookie` |
| --- |

使用 `setcookie()` 函数设置 Cookie。由于 Cookie 是 HTTP 头部的一部分，你必须在向浏览器发送任何输出之前设置 Cookie。

![](img/Image00732.jpg)

示例：`setcookie("user", "Tom", time() + 86400, "/");` // 检查函数参数的语法

说明：

![](img/Image00733.jpg)

创建一个名为 `user` 的 Cookie

（可选）Cookie 的值为 `Tom`

（可选）Cookie 将在 1 天后过期（86400 秒）

（可选）Cookie 在整个网站 `/` 可用

（可选）Cookie 仅通过 HTTPS 发送

（可选）Cookie 不可被 JavaScript 等脚本语言访问

创建或修改的 Cookie 只能在后续请求中访问（路径和域名匹配时），因为超全局变量 `$_COOKIE` 不会立即填充新数据。

#### 第 29.3 节：检查 Cookie 是否已设置

| `isset` |
| --- |

对超全局变量 `$_COOKIE` 使用 `isset()` 函数来检查 Cookie 是否已设置。

示例：

![](img/Image00734.jpg)

#### 第 29.4 节：删除 Cookie

要删除 Cookie，请将过期时间戳设置为过去的时间。这会触发浏览器的删除机制：

![](img/Image00735.jpg)

如果当前页面使用该 Cookie，取消设置 `$_COOKIE` 值也是个好主意：

![](img/Image00736.jpg)

#### 第 29.5 节：获取 Cookie

### 获取并输出名为 user 的 Cookie

可以使用全局变量 `$_COOKIE` 检索 Cookie 的值。示例：如果我们有一个名为 `user` 的 Cookie，可以这样检索它：

![](img/Image00737.jpg)

## 第 30 章：输出缓冲控制

### 函数详情

| `ob_start` | `ob_get_contents` | `ob_end_clean` |
| --- | --- | --- |
| `ob_start()` 启动输出缓冲区，在此之后的任何输出将被捕获而不显示 | `ob_get_contents()` 返回 `ob_start()` 捕获的所有内容 | `ob_end_clean()` 清空输出缓冲区并关闭当前嵌套级别的输出缓冲 |

| `ob_get_clean` | `ob_get_level` | `ob_flush` | `ob_implicit_flush` | `ob_end_flush` |
| --- | --- | --- | --- | --- |
| `ob_get_clean()` 同时触发 `ob_get_contents()` 和 `ob_end_clean()` | `ob_get_level()` 返回输出缓冲区的当前嵌套级别 | `ob_flush()` 刷新内容缓冲区并发送到浏览器，但不结束缓冲区 | `ob_implicit_flush()` 在每次输出调用后启用隐式刷新。 | `ob_end_flush()` 刷新内容缓冲区并发送到浏览器，同时结束缓冲区 |

#### 第 30.1 节：基本用法——获取缓冲区间的内容并清除

输出缓冲控制允许你将任何文本内容（文本、HTML）存储在变量中，并在脚本结束时作为一个整体发送给浏览器。默认情况下，PHP 在解析内容时就会发送内容。

![](img/Image00738.jpg)

| `ob_start` | `ob_get_clean` |
| --- | --- |

`ob_start()` 与 `ob_get_clean()` 之间输出的任何内容都将被捕获并放入变量 `$content` 中。

| `ob_get_clean` | `ob_get_contents` | `ob_end_clean` |
| --- | --- | --- |

调用 `ob_get_clean()` 会同时触发 `ob_get_contents()` 和 `ob_end_clean()`。

#### 第 30.2 节：通过回调处理缓冲区

| `ob_start` |
| --- |

你可以通过向 `ob_start()` 传递一个可调用对象，对输出应用任何类型的额外处理。

![](img/Image00739.jpg)

![](img/Image00740.jpg)

输出：

![](img/Image00741.jpg)

```
<h1> LoremIpsum </h1><p><strong> Pellentesquehabitantmorbitristique </strong> senectusetnetusetmalesuada famesacturpisegestas. < ahref = "#" > Donecnonenim </a> inturpispulvinarfacilisis. </p><h2> HeaderLevel2 </h2> <ol><li> Loremipsumdolorsitamet,consectetueradipiscingelit. </li><li> Aliquamtinciduntmauriseurisus. </ li></ol>
```

#### 第 30.3 节：嵌套输出缓冲区

| `ob_get_level()` |
| --- |

你可以嵌套输出缓冲区，并使用该函数获取级别以提供不同的内容。

![](img/Image00742.jpg)

![](img/Image00743.jpg)

输出：

![](img/Image00744.jpg)

#### 第 30.4 节：在任何内容之前运行输出缓冲区

![](img/Image00745.jpg)

在此示例中，我们假设 `$users` 是一个多维数组，并遍历它以查找所有访问级别为 7 的用户。

如果没有结果，我们将重定向到错误页面。

| `header` |
| --- |

我们在这里使用输出缓冲区，因为我们根据循环的结果触发 `header()` 重定向。

#### 第 30.5 节：向客户端流式传输输出

![](img/Image00746.jpg)

#### 第 30.6 节：使用输出缓冲区将内容存储到文件中，适用于报表、发票等

![](img/Image00747.jpg)

| `echo $html;` |
| --- |

此示例获取完整文档并将其写入文件，它不会将文档输出到浏览器，但可以通过使用 `echo $html;` 来输出。

#### 第 30.7 节：`ob_start` 的典型用法及使用原因

当页面上有重定向时，`ob_start` 尤其方便。例如，以下代码将无法工作：

![](img/Image00748.jpg)

| `headers already sent by < xxx > on line < xxx >` |
| --- |



将给出的错误类似于： 。

为了修复此问题，你需要在页面开头编写类似如下的代码：

![](img/Image00749.jpg)

并在页面末尾编写类似如下的代码：

![](img/Image00750.jpg)

这会将所有生成的内容存储到输出缓冲区中，并一次性显示。因此，如果你的页面上有任何重定向调用，它们将在发送任何数据之前触发，从而消除“headers already sent”（标头已发送）错误发生的可能性。

#### 第 30.8 节：捕获输出缓冲区以供后续重用

在此示例中，我们有一个包含部分数据的数组。

我们在 `$items_li_html` 中捕获输出缓冲区，并在页面中使用它两次。

![](img/Image00751.jpg)

| output_buffer | | . | php | and run it via | php output_buffer | . | php |
| --- | --- | --- | --- | --- | --- | --- | --- |

将上述代码保存到文件 中。

你应该能看到我们上面创建的 2 个列表项，以及我们使用输出缓冲区在 PHP 中生成的相同列表项：

![](img/Image00752.jpg)

![](img/Image00753.jpg)

## 第 31 章：JSON

##### 参数详情

##### `json_encode`

| 参数 | 说明 |
| --- | --- |
| `value` | 待编码的值。可以是除 resource 类型以外的任何类型。所有字符串数据必须采用 UTF-8 编码。 |
| `options` | 由 `JSON_HEX_QUOT`、`JSON_HEX_TAG`、`JSON_HEX_AMP`、`JSON_HEX_APOS`、`JSON_NUMERIC_CHECK`、`JSON_PRETTY_PRINT`、`JSON_UNESCAPED_SLASHES`、`JSON_FORCE_OBJECT`、`JSON_PRESERVE_ZERO_FRACTION`、`JSON_UNESCAPED_UNICODE`、`JSON_PARTIAL_OUTPUT_ON_ERROR` 组成的位掩码。这些常量的行为在 [JSON 常量](http://php.net/manual/en/json.constants.php) 页面中有描述。 |
| `depth` | 设置最大深度。必须大于零。 |

##### `json_decode`

| 参数 | 说明 |
| --- | --- |
| `json` | 待解码的 JSON 字符串。此函数仅适用于 UTF-8 编码的字符串。 |
| `assoc` | 函数是否应返回关联数组而非对象。 |
| `options` | JSON 解码选项的位掩码。目前仅支持 `JSON_BIGINT_AS_STRING`（默认行为是将大整数转换为浮点数）。 |

[JSON](http://www/json.org/) ([JavaScript Object Notation](https://en.wikipedia.org/wiki/JSON)) 是一种与平台和语言无关的方式，用于将对象序列化为纯文本。因为它常用于 Web，PHP 也是如此，所以 PHP 中有一个用于处理 JSON 的 [基础扩展](https://secure.php.net/manual/en/book.json.php)。

#### 第 31.1 节：解码 JSON 字符串

| `json_decode` |
| --- |

`json_decode()` 函数接受一个 JSON 编码的字符串作为其第一个参数，并将其解析为 PHP 变量。

| `json_decode` |
| --- |

通常，如果 JSON 对象中的顶层项是字典，`json_decode()` 将返回一个 [`\stdClass`](http://php.net/manual/en/reserved.classes.php) 对象；如果 JSON 对象是数组，则返回索引数组。对于某些标量值（如简单字符串、`"true"`、`"false"` 和 `"null"`），它也将返回标量值或 `NULL`。发生任何错误时也会返回 `NULL`。

```php
// 返回一个对象（JSON 字符串中的顶层项是 JSON 字典）
$json_string = '{"name": "Jeff", "age": 20, "active": true, "colors": ["red", "blue"]}';

$object = json_decode($json_string);
printf('Hello %s, You are %s years old.', $object->name, $object->age);
//> Hello Jeff, You are 20 years old.

// 返回一个数组（JSON 字符串中的顶层项是 JSON 数组）
$json_string = '["Jeff", 20, true, ["red", "blue"]]';

$array = json_decode($json_string);
printf('Hello %s, You are %s years old.', $array[0], $array[1]);
```

| `var_dump` |
| --- |

使用 `var_dump()` 查看我们上面解码的对象中每个属性的类型和值。

![](img/Image00755.jpg)

输出（注意变量类型）：

![](img/Image00756.jpg)

![](img/Image00757.jpg)

注意：JSON 中的变量类型已转换为其 PHP 对应类型。

| `json_decode` |
| --- |

要让 JSON 对象返回 [关联数组](http://php.net/manual/en/language.types.array.php) 而不是对象，请将 `true` 作为 [第二个参数](http://php.net/manual/en/function.json-decode.php#refsect1-function.json-decode-parameters) 传递给 `json_decode()`。

```php
$json_string = '{"name": "Jeff", "age": 20, "active": true, "colors": ["red", "blue"]}';

$array = json_decode($json_string, true); // 注意第二个参数
var_dump($array);
```

输出（注意关联数组结构）：

![](img/Image00759.jpg)

如果要返回的变量不是对象，则第二个参数 (`$assoc`) 无效。

| `json_encode` |
| --- |

注意：如果你使用 `$assoc` 参数，将会丢失空数组和空对象之间的区别。这意味着再次对解码后的输出运行 `json_encode()` 将导致不同的 JSON 结构。

| `json_decode` |
| --- |

如果 JSON 字符串的“深度”在递归中超过 512 个元素（5.2.3 版本之前为 20 个元素，5.2.3 版本为 128 个元素），`json_decode()` 函数将返回 `NULL`。在 5.3 或更高版本中，可以使用第三个参数 (`$depth`) 来控制此限制，如下所述。

根据手册：

![](img/Image00760.jpg)PHP 实现了原始 [»](http://www.faqs.org/rfcs/rfc4627) [RFC 4627](http://www.faqs.org/rfcs/rfc4627) 中指定的 JSON 超集——它还会编码和解码标量类型和 `NULL`。RFC 4627 仅支持这些值嵌套在数组或对象内部时的情况。尽管此超集与较新的 [»](http://www.faqs.org/rfcs/rfc7159) [RFC 7159](http://www.faqs.org/rfcs/rfc7159)（旨在取代 RFC 4627）和 [»](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) 中“JSON 文本”扩展定义一致，但当编码单个标量值时，可能会与严格遵循 RFC 4627 的旧版 JSON 解析器产生互操作性问题。

这意味着，例如，在 PHP 中简单字符串将被视为有效的 JSON 对象：

![](img/Image00761.jpg)

输出：

![](img/Image00762.jpg)

但不在数组或对象中的简单字符串不属于 [RFC 4627](http://www.faqs.org/rfcs/rfc4627) 标准。因此，诸如 [JSLint](http://www.jslint.com/)、[JSON Formatter & Validator](https://jsonformatter.curiousconcept.com/)（在 RFC 4627 模式下）等在线检查器会报错。

有一个第三个参数 `$depth` 用于设置递归深度（默认值为 512），即原始对象中待解码的嵌套对象数量。

有一个第四个参数 `$options`。目前它仅接受一个值：`JSON_BIGINT_AS_STRING`。默认行为（即省略此选项）是将大整数转换为浮点数而非字符串。

![](img/Image00763.jpg) 无效的非小写形式的 `true`、`false` 和 `null` 字面量不再被接受为有效输入。

因此此示例：

```php
var_dump(json_decode('tRue'), json_last_error_msg());
var_dump(json_decode('tRUe'), json_last_error_msg());
var_dump(json_decode('tRUE'), json_last_error_msg());
var_dump(json_decode('TRUe'), json_last_error_msg());
var_dump(json_decode('TRUE'), json_last_error_msg());
var_dump(json_decode('true'), json_last_error_msg());
```

PHP 5.6 之前：

![](img/Image00765.jpg)

PHP 5.6 及之后：

![](img/Image00766.jpg)

`false` 和 `null` 也会出现类似行为。

| `json_decode` |
| --- |

注意，如果字符串无法转换，`json_decode()` 将返回 `NULL`。

![](img/Image00767.jpg)

![](img/Image00768.jpg)

| `json_decode` |
| --- |



仅依赖返回值为 `NULL` 来检测错误是不安全的。例如，如果 JSON 字符串仅包含 `"null"`，即使没有发生错误，`json_decode()` 也会返回 `null`。

#### 第 31.2 节：编码 JSON 字符串

[`json_encode`](http://php.net/manual/en/function.json-encode.php) 函数将 PHP 数组（或自 PHP 5.4 起实现了 `JsonSerializable` 接口的对象）转换为 JSON 编码的字符串。成功时返回 JSON 编码的字符串，失败时返回 `FALSE`。

![](img/Image00769.jpg)

编码过程中，PHP 数据类型字符串、整数和布尔值将转换为其 JSON 对应类型。关联数组编码为 JSON 对象，而使用默认参数调用时，索引数组编码为 JSON 数组。（除非数组键不是从 0 开始的连续数字序列，在这种情况下数组将被编码为 JSON 对象。）

![](img/Image00770.jpg)

输出：

![](img/Image00771.jpg)

```
{ "name" : "Jeff" , "age" : 20 , "active" : true , "colors" :[ "red" , "blue" ], "values" :{ "0" : "foo" , "3" : "bar" }}
```

##### 参数

自 PHP 5.3 起，`json_encode` 的第二个参数是一个位掩码，可以是以下一个或多个常量。

与任何位掩码一样，它们可以通过二进制或运算符 `|` 组合。

##### PHP 5.x 版本 ≥ 5.3 [`JSON_FORCE_OBJECT`](http://php.net/manual/en/json.constants.php#constant.json-force-object)

强制创建对象而不是数组。

![](img/Image00772.jpg)

输出：

![](img/Image00773.jpg)

##### [`JSON_HEX_TAG`](http://php.net/manual/en/json.constants.php#constant.json-hex-tag)、[`JSON_HEX_AMP`](http://php.net/manual/en/json.constants.php#constant.json-hex-amp)、[`JSON_HEX_APOS`](http://php.net/manual/en/json.constants.php#constant.json-hex-apos)、[`JSON_HEX_QUOT`](http://php.net/manual/en/json.constants.php#constant.json-hex-quot)

确保编码期间进行以下转换：

| 常量 | 输入 | 输出 |
| --- | --- | --- |
| `JSON_HEX_TAG` | `<` | `\u003C` |
| `JSON_HEX_TAG` | `>` | `\u003E` |
| `JSON_HEX_AMP` | `&` | `\u0026` |
| `JSON_HEX_APOS` | `'` | `\u0027` |
| `JSON_HEX_QUOT` | `"` | `\u0022` |

![](img/Image00774.jpg)

```
$array = [ "tag" => "<>" , "amp" => "&" , "apos" => "'" , "quot" => "\"" ];
echo json_encode ( $array );
echo json_encode ( $array , JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT );
```

输出：

```
{ "tag" : "<>" , "amp" : "&" , "apos" : "'" , "quot" : "\"" }
```

![](img/Image00775.jpg)

```
{ "tag" : "\u003C\u003E" , "amp" : "\u0026" , "apos" : "\u0027" , "quot" : "\u0022" }
```

##### PHP 5.x 版本 ≥ 5.3 [`JSON_NUMERIC_CHECK`](http://php.net/manual/en/json.constants.php#constant.json-numeric-check)

确保数字字符串转换为整数。

![](img/Image00776.jpg)

输出：

![](img/Image00777.jpg)

```
[ "23452" ,23452]
[23452,23452]
```

##### PHP 5.x 版本 ≥ 5.4 [`JSON_PRETTY_PRINT`](http://php.net/manual/en/json.constants.php#constant.json-pretty-print)

使 JSON 易于阅读。

![](img/Image00778.jpg)

输出：

![](img/Image00779.jpg)

##### [`JSON_UNESCAPED_SLASHES`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-slashes)

输出中包含未转义的 `/` 正斜杠。

![](img/Image00780.jpg)

输出：

![](img/Image00781.jpg)

```
{ "filename" : "example.txt" , "path" : "\/full\/path\/to\/file" }
{ "filename" : "example.txt" , "path" : "/full/path/to/file" }
```

##### [`JSON_UNESCAPED_UNICODE`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-unicode)

输出中包含 UTF8 编码字符，而不是 `\u` 编码的字符串。

![](img/Image00782.jpg)

输出：

![](img/Image00783.jpg)

##### PHP 5.x 版本 ≥ 5.5 [`JSON_PARTIAL_OUTPUT_ON_ERROR`](http://php.net/manual/en/json.constants.php#constant.json-partial-output-on-error)

遇到无法编码的值时允许编码继续进行。

![](img/Image00784.jpg)

输出：

![](img/Image00785.jpg)

```
{ "file" : null , "name" : "foo.txt" }
```

##### PHP 5.x 版本 ≥ 5.6 [`JSON_PRESERVE_ZERO_FRACTION`](http://php.net/manual/en/json.constants.php#constant.json-preserve-zero-fraction)

确保浮点数始终作为浮点数编码。

![](img/Image00786.jpg)

输出：

![](img/Image00787.jpg)

##### PHP 7.x 版本 ≥ 7.1 [`JSON_UNESCAPED_LINE_TERMINATORS`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-line-terminators)

与 `JSON_UNESCAPED_UNICODE` 结合使用时，恢复旧版 PHP 的行为，不转义字符 U+2028 LINE SEPARATOR（行分隔符）和 U+2029 PARAGRAPH SEPARATOR（段分隔符）。尽管这些字符在 JSON 中有效，但它们在 JavaScript 中无效，因此 `JSON_UNESCAPED_UNICODE` 的默认行为在 7.1 版本中发生了变化。

![](img/Image00788.jpg)

```
$array = [ "line" => "\xe2\x80\xa8" , "paragraph" => "\xe2\x80\xa9" ];
echo json_encode ( $array , JSON_UNESCAPED_UNICODE );
echo json_encode ( $array , JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_LINE_TERMINATORS );
```

输出：

![](img/Image00789.jpg)

![](img/Image00790.jpg)

#### 第 31.3 节：调试 JSON 错误

当 `json_encode` 或 `json_decode` 无法解析提供的字符串时，将返回 `false`。PHP 本身不会引发任何错误或警告；责任在于用户使用 [`json_last_error()`](http://php.net/manual/en/function.json-last-error.php) 和 [`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 函数来检查是否发生错误，并在应用程序中做出相应处理（调试、显示错误消息等）。

以下示例展示了处理 JSON 时的常见错误，即由于传递了错误的 UTF-8 编码字符串等原因，导致 JSON 字符串解码/编码失败。

![](img/Image00791.jpg)

##### [`json_last_error_msg`](http://php.net/manual/en/function.json-last-error-msg.php)

[`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 返回尝试编码/解码字符串时发生的最后一个错误的人类可读消息。

![](img/Image00792.jpg)

即使未发生错误，此函数始终返回 `string`。

默认的非错误字符串为 `No Error`。

如果发生其他（未知）错误，将返回 `false`。

在循环中使用时要小心，因为 [`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 将在每次迭代中被覆盖。

你应该仅使用此函数获取用于显示的消息，而不应在控制语句中用它进行判断。

![](img/Image00793.jpg)

此函数在 PHP 5.5 之前不存在。以下是一个 polyfill 实现：

![](img/Image00794.jpg)

```
if (! function_exists ( 'json_last_error_msg' )) {
     function json_last_error_msg () {
         static $ERRORS = array (
             JSON_ERROR_NONE => 'No error' ,
             JSON_ERROR_DEPTH => 'Maximum stack depth exceeded' ,
             JSON_ERROR_STATE_MISMATCH => 'State mismatch (invalid or malformed JSON)' ,
             JSON_ERROR_CTRL_CHAR => 'Control character error, possibly incorrectly encoded' ,
             JSON_ERROR_SYNTAX => 'Syntax error' ,
             JSON_ERROR_UTF8 => 'Malformed UTF-8 characters, possibly incorrectly encoded'
         );
         $error = json_last_error ();
```

![](img/Image00795.jpg)

##### [`json_last_error`](http://php.net/manual/en/function.json-last-error.php)

[`json_last_error()`](http://php.net/manual/en/function.json-last-error.php) 返回一个整数，映射到 PHP 提供的预定义常量之一。

| 常量 | 含义 |
| --- | --- |
| `JSON_ERROR_NONE` | 未发生错误 |
| `JSON_ERROR_DEPTH` | 超过最大堆栈深度 |
| `JSON_ERROR_STATE_MISMATCH` | 无效或格式错误的 JSON |
| `JSON_ERROR_CTRL_CHAR` | 控制字符错误，可能编码不正确 |
| `JSON_ERROR_SYNTAX` | 语法错误（自 PHP 5.3.3 起） |




##### JSON 错误常量

| 常量 | 描述 |
| :--- | :--- |
| `JSON_ERROR_UTF8` | UTF-8 字符格式错误，可能编码不正确（自 PHP 5.5.0 起） |
| `JSON_ERROR_RECURSION` | 待编码的值中存在一个或多个递归引用 |
| `JSON_ERROR_INF_OR_NAN` | 待编码的值中存在一个或多个 NAN 或 INF 值 |
| `JSON_ERROR_UNSUPPORTED_TYPE` | 给定了一个无法编码的类型的值 |

# 第 31 章：JSON 处理（续）

#### 第 31.4 节：在对象中使用 `JsonSerializable`

**PHP 5.x 版本 ≥ 5.4**

当你构建 REST API 时，可能需要减少传递给客户端应用程序的对象信息量。为此，本例演示了如何使用 `JsonSerializable` 接口。

在本例中，类 `User` 实际上扩展了一个假设的 ORM 的数据库模型对象。

![Image00796.jpg](img/Image00796.jpg)

##### `jsonSerialize`

通过提供 `jsonSerialize()` 方法，向类添加 `JsonSerializable` 实现。

![Image00797.jpg](img/Image00797.jpg)

##### `json_encode`

现在在你的应用程序控制器或脚本中，当将对象 `User` 传递给 `json_encode()` 时，你将获得 `jsonSerialize()` 方法返回的 JSON 编码数组，而不是整个对象。

![Image00798.jpg](img/Image00798.jpg)

将返回：

![Image00799.jpg](img/Image00799.jpg)

*属性值示例。*

这既减少了从 RESTful 端点返回的数据量，又允许从 JSON 表示中排除对象属性。

##### 配合 `json_encode` 使用私有和受保护属性

为了避免使用 `JsonSerializable`，也可以使用私有或受保护属性来隐藏 `json_encode()` 输出中的类信息。该类随后无需实现 `\JsonSerializable`。

![Image00800.jpg](img/Image00800.jpg)
![Image00801.jpg](img/Image00801.jpg)

#### 第 31.5 节：JSON 头部与返回响应

通过添加内容类型为 JSON 的头部：

![Image00802.jpg](img/Image00802.jpg)
![Image00803.jpg](img/Image00803.jpg)

该头部的存在是为了让你的应用程序能够检测返回了什么数据以及应如何处理它。请注意：内容头部只是关于返回数据类型的信息。

如果你使用的是 UTF-8，可以使用：

![Image00804.jpg](img/Image00804.jpg)

##### jQuery 示例

![Image00805.jpg](img/Image00805.jpg)

## 第 32 章：SOAP 客户端

##### 参数详情

| 参数 | 描述 |
| :--- | :--- |
| `$wsdl` | WSDL 的 URI，若使用非 WSDL 模式则为 `NULL` |
| `$options` | `SoapClient` 的选项数组。非 WSDL 模式要求设置 `location` 和 `uri`，所有其他选项均为可选。可能的值见下表。 |

#### 第 32.1 节：WSDL 模式

首先，创建一个新的 `SoapClient` 对象，传入 WSDL 文件的 URL，并可选择性地传入一个选项数组。

![Image00806.jpg](img/Image00806.jpg)
![Image00807.jpg](img/Image00807.jpg)

#### 第 32.2 节：非 WSDL 模式

这与 WSDL 模式类似，不同之处在于我们将 `NULL` 作为 WSDL 文件传入，并确保设置了 `location` 和 `uri` 选项。

![Image00808.jpg](img/Image00808.jpg)

#### 第 32.3 节：类映射

在 PHP 中创建 SOAP 客户端时，你也可以在配置数组中设置 `classmap` 键。此 `classmap` 定义了 WSDL 中定义的哪些类型应映射到实际的类，而不是默认的 `StdClass`。这样做的原因是你可以获得这些类的字段和方法调用的自动补全功能，而不必猜测常规 `StdClass` 上设置了哪些字段。

![Image00809.jpg](img/Image00809.jpg)
![Image00810.jpg](img/Image00810.jpg)

配置 `classmap` 后，每当你执行返回类型为 `Address` 或 `Book` 的特定操作时，`SoapClient` 将实例化该类，用数据填充字段，并从操作调用中返回它。

![Image00811.jpg](img/Image00811.jpg)

#### 第 32.4 节：追踪 SOAP 请求与响应

有时我们想查看 SOAP 请求中发送和接收的内容。以下方法将返回请求和响应中的 XML：

![Image00812.jpg](img/Image00812.jpg)

例如，假设我们有一个 `ENVIRONMENT` 常量，当该常量的值设置为 `DEVELOPMENT` 时，我们希望在调用 `getAddress` 抛出错误时输出所有信息。一种解决方案可能是：

![Image00813.jpg](img/Image00813.jpg)
![Image00814.jpg](img/Image00814.jpg)

## 第 33 章：在 PHP 中使用 cURL

##### 参数详情

| 函数 | 描述 |
| :--- | :--- |
| `curl_init` | 初始化一个 cURL 会话 |
| `curl_setopt` | 为 cURL 传输设置一个选项 |
| `curl_exec` | 执行一个 cURL 会话 |
| `curl_close` | 关闭一个 cURL 会话 |

##### `curl_init` 参数

| 参数 | 描述 |
| :--- | :--- |
| `url` | cURL 请求中使用的 URL |

##### `curl_setopt` 参数

| 参数 | 描述 |
| :--- | :--- |
| `ch` | cURL 句柄（`curl_init()` 的返回值） |
| `option` | 要设置的 `CURLOPT_XXX` - 选项列表及可接受值见 [PHP 文档](http://php.net/manual/en/function.curl-setopt.php) |
| `value` | 为给定选项在 cURL 句柄上设置的值 |

##### `curl_exec` 参数

| 参数 | 描述 |
| :--- | :--- |
| `ch` | cURL 句柄（`curl_init()` 的返回值） |

##### `curl_close` 参数

| 参数 | 描述 |
| :--- | :--- |
| `ch` | cURL 句柄（`curl_init()` 的返回值） |

#### 第 33.1 节：基本用法（GET 请求）

cURL 是一个利用 URL 语法传输数据的工具。它支持 HTTP、FTP、SCP 等众多协议（cURL >= 7.19.4）。请记住，你需要[安装并启用 cURL 扩展](http://php.net/manual/en/curl.installation.php)才能使用它。

![Image00815.jpg](img/Image00815.jpg)

#### 第 33.2 节：POST 请求

如果你想模拟 HTML 表单的 POST 动作，可以使用 cURL。

![Image00816.jpg](img/Image00816.jpg)
![Image00817.jpg](img/Image00817.jpg)

#### 第 33.3 节：使用 Cookie

cURL 可以保留响应中接收到的 Cookie，以供后续请求使用。对于内存中的简单会话 Cookie 处理，只需一行代码即可实现：

![Image00818.jpg](img/Image00818.jpg)

如果你需要在 cURL 句柄销毁后保留 Cookie，可以指定存储它们的文件：

![Image00819.jpg](img/Image00819.jpg)

然后，当你想再次使用它们时，将它们作为 Cookie 文件传递：

![Image00820.jpg](img/Image00820.jpg)

但请记住，除非你需要在不同的 cURL 句柄之间传递 Cookie，否则这两个步骤并非必要。对于大多数用例，将 `CURLOPT_COOKIEFILE` 设置为空字符串就是你所需要的一切。

Cookie 处理可用于例如从需要登录的网站检索资源。这通常是一个两步过程。首先，向登录页面发送 POST 请求。

![Image00821.jpg](img/Image00821.jpg)

第二步（在完成标准错误检查后）通常是一个简单的 GET 请求。重要的是要为第二个请求重用现有的 cURL 句柄。这确保了来自第一个响应的 Cookie 将自动包含在第二个请求中。

![Image00822.jpg](img/Image00822.jpg)

这仅作为 Cookie 处理的一个示例。在现实生活中，情况通常更复杂。通常你必须先对登录页面执行初始 GET 以获取一个需要包含在 POST 中的登录令牌。其他网站可能会根据其 User-Agent 字符串阻止 cURL 客户端，这就要求你更改它。

#### 第 33.4 节：使用 `multi_curl` 发起多个 POST 请求

有时我们需要向一个或多个不同的端点发起大量 POST 请求。为了应对这种情况，我们可以使用 `multi_curl`。

首先，我们完全按照简单示例的方式创建所需数量的请求，并将它们放入一个数组中。

我们使用 `curl_multi_init` 并将每个句柄添加到其中。

在本例中，我们使用了 2 个不同的端点：

![Image00823.jpg](img/Image00823.jpg)
![Image00824.jpg](img/Image00824.jpg)

然后，我们使用 `curl_multi_exec` 发送请求：

![Image00825.jpg](img/Image00825.jpg)

该示例可能的返回如下：

![Image00826.jpg](img/Image00826.jpg)

> 请求 'http://www.example.com' 在 2 秒内返回了 'fruits'。
>
> 请求 'http://www.example2.com' 在 5 秒内返回了 'seafood'。

#### 第 33.5 节：在一个请求中使用 `CurlFile` 发送多维数据和多个文件

假设我们有一个如下所示的表单。我们想通过 AJAX 将数据发送到我们的 Web 服务器，然后再发送到运行在外部服务器上的脚本。

![Image00827.jpg](img/Image00827.jpg)

因此我们有普通输入框、一个多选字段和一个文件拖放区，我们可以在其中上传多个文件。

假设 AJAX POST 请求成功，我们在 PHP 端获得以下数据：

![Image00828.jpg](img/Image00828.jpg)

文件应该如下所示：

![Image00829.jpg](img/Image00829.jpg)
![Image00830.jpg](img/Image00830.jpg)



到目前为止一切顺利。现在我们想使用带有 `CurlFile` 类的 cURL 将这些数据和文件发送到外部服务器。

由于 cURL 只接受简单数组而不接受多维数组，我们必须先将 `$_POST` 数组扁平化。

为此，你可以使用[例如这个函数](http://codereview.stackexchange.com/a/14685)，它将给你以下结果：

![](img/Image00831.jpg)

下一步是为上传的文件创建 `CurlFile` 对象。这通过以下循环完成：

![](img/Image00832.jpg)

`curl_file_create` 是 `CurlFile` 类的一个辅助函数，用于创建 `CurlFile` 对象。我们将每个对象保存在 `$files` 数组中，键名为 `"upload[0]"` 和 `"upload[1]"`，对应我们的两个文件。

我们现在必须将扁平化的 post 数组和文件数组合并，并将其保存为 `$data`，如下所示：

![](img/Image00833.jpg)

最后一步是发送 cURL 请求：

![](img/Image00834.jpg)

由于 `$data` 现在是一个简单（扁平）数组，cURL 会自动以 Content Type: `multipart/form-data` 发送此 POST 请求。

在外部服务器的 `upload.php` 中，你现在可以像平常一样使用 `$_POST` 和 `$_FILES` 获取 post 数据和文件。

#### 第 33.6 节：使用自定义方法创建并发送请求

默认情况下，PHP Curl 支持 GET 和 POST 请求。也可以使用 `CURLOPT_CUSTOMREQUEST` 参数发送自定义请求，例如 `DELETE`、`PUT` 或 `PATCH`（甚至非标准方法）。

![](img/Image00835.jpg)

#### 第 33.7 节：在 PHP 中获取和设置自定义 HTTP 头

##### 发送请求头

![](img/Image00836.jpg)

##### 读取自定义头

![](img/Image00837.jpg)

##### 输出：

![](img/Image00838.jpg)

我们也可以使用下面的语法发送头：

![](img/Image00839.jpg)

## 第 34 章：反射

#### 第 34.1 节：类或对象的特性检测

类的特性检测可以部分通过 `property_exists` 和 `method_exists` 函数完成。

![](img/Image00840.jpg)

```
$r = new ReflectionClass('MyClass');

$check = $r->hasProperty('public_field');  // true
```

![](img/Image00841.jpg)
```
$check = $r->hasMethod('public_function'); // true
$check = $r->hasConstant('CONSTANT');      // true
```

// 对 protected、private 和/或 static 成员同样适用。

注意：对于 `property_exists` 和 `method_exists`，也可以提供感兴趣类的对象实例，而不必提供类名。使用反射时，应使用 `ReflectionObject` 类代替 `ReflectionClass`。

#### 第 34.2 节：测试私有/受保护方法

有时测试私有和受保护方法以及公共方法很有用。

![](img/Image00842.jpg)

![](img/Image00843.jpg)

测试驱动方法最简单的方式是使用反射

![](img/Image00844.jpg)

如果该方法是静态的，则在类实例的位置传入 `null`

![](img/Image00845.jpg)

![](img/Image00846.jpg)

#### 第 34.3 节：访问私有和受保护的成员变量

反射常被用作软件测试的一部分，例如用于模拟对象的运行时创建/实例化。它也非常适合在任意时间点检查对象的状态。下面是一个在单元测试中使用反射来验证受保护的类成员是否包含预期值的示例。

下面是一个非常基础的 Car 类。它有一个受保护的成员变量，将包含代表汽车颜色的值。因为该成员变量是受保护的，我们无法直接访问它，必须使用 getter 和 setter 方法分别来获取和设置其值。

![](img/Image00847.jpg)

| Car::setColor | |
| --- | --- |
| Car::getColor | |
| --- | --- |

为了测试这一点，许多开发人员会创建一个 Car 对象，使用 `setColor()` 设置汽车颜色，使用 `getColor()` 获取颜色，并将该值与他们设置的颜色进行比较：

![](img/Image00848.jpg)

| Car::getColor | |
| --- | --- |
| Car::$color | |
| --- | --- |

表面上这看起来没问题。毕竟，`getColor()` 所做的只是返回受保护成员变量 `$color` 的值。但这个测试有两个缺陷：

| Car::getColor | |
| --- | --- |
| 1. | 它执行了 `getColor()`，这超出了本次测试的范围 |
| --- | --- |
| 2. | 它依赖 `getColor()`，而 `getColor()` 本身可能有 bug，这会导致测试出现假阳性或假阴性 |
| --- | --- |

让我们看看为什么不应该在单元测试中使用 `getColor()` 而应该使用反射。假设一位开发人员被分配任务，要在每种汽车颜色前加上 "Metallic"。于是他们尝试修改 `getColor()` 以在汽车颜色前预置 "Metallic"：

![](img/Image00849.jpg)

| Car::getColor | |
| --- | --- |
| Car::setColor | |
| --- | --- |
| Car::setColor | |
| --- | --- |

你看出错误了吗？开发人员在尝试将 "Metallic" 预置到汽车颜色前时，使用了分号而不是连接运算符。结果，无论汽车的实际颜色是什么，每当调用 `getColor()` 时，都会返回 "Metallic "。结果，我们的 `getColor()` 单元测试将会失败，即使 `setColor()` 工作完美且未受此更改影响。

| Car::$color | 包含我们通过 | Car::setColor | 设置的值 |
| --- | --- | --- | --- |
| --- | --- | --- | --- |

那么我们如何验证 `setColor()`？我们可以使用反射直接检查受保护的成员变量。怎么做呢？我们可以使用反射使受保护的成员变量对我们的代码可访问，从而获取其值。

让我们先看代码，然后再分解它：

![](img/Image00850.jpg)

| Car::$color | |
| --- | --- |
| --- | --- |

以下是我们在上面的代码中使用反射获取 `$color` 值的方法：

1.  我们创建一个代表我们 Car 对象的新 [ReflectionObject](http://php.net/manual/en/class.reflectionobject.php)
2.  我们获取 `$color` 变量的 [ReflectionProperty](http://php.net/manual/en/class.reflectionproperty.php)
3.  我们使 `$color` 可访问
4.  我们获取 `$color` 的值，而无需调用 `getColor()` 或 `setColor()` 或任何其他可能导致测试结果无效的访问器函数。

正如你所见，通过使用反射，我们可以在不调用 `getColor()` 或 `setColor()` 或任何其他可能导致测试结果无效的访问器函数的情况下获取 `$color` 的值。现在我们针对 `setColor()` 的单元测试是安全且准确的。

## 第 35 章：依赖注入

依赖注入（DI）是“传递依赖”的花哨说法。它真正的含义是通过构造函数和/或 setter 方法将对象的依赖传递进去，而不是在对象内部创建时创建它们。依赖注入也可能指依赖注入容器，它们自动化构建和注入过程。

#### 第 35.1 节：构造函数注入

对象通常会依赖其他对象。不应在构造函数中创建依赖，而应将依赖作为参数传递给构造函数。这确保了对象之间没有紧耦合，并支持在类实例化时更改依赖。这有许多好处，包括通过使依赖显式化来使代码更易读，以及使测试更简单，因为依赖可以更容易地被替换和模拟。

在下面的示例中，`Component` 将依赖一个 `Logger` 实例，但它不创建一个。它要求在构造函数中将一个作为参数传入。

![](img/Image00851.jpg)

如果不使用依赖注入，代码可能看起来像这样：

![](img/Image00852.jpg)

在构造函数中使用 `new` 创建新对象表明未使用依赖注入（或未完全使用），并且代码存在紧耦合。这也是代码测试不完整或可能拥有脆弱测试的迹象，这些测试会对程序状态做出错误的假设。



在上述示例中，我们使用的是依赖注入，如果有必要，我们可以轻松更换为不同的 `Logger`。例如，我们可能会使用一个记录到不同位置的 `Logger` 实现，或者使用不同的日志格式，又或者是记录到数据库而不是文件。

#### 第 35.2 节：Setter 注入

依赖也可以通过 setter 方法注入。

![](img/Image00853.jpg)

![](img/Image00854.jpg)

当类的核心功能不依赖于该依赖项即可工作时，这种方式特别有用。

在这里，唯一需要的依赖是 `DatabaseConnection`，所以它放在构造函数中。`Logger` 依赖是可选的，因此不需要成为构造函数的一部分，这使得类更易于使用。

请注意，当使用 setter 注入时，最好是扩展功能而不是替换它。设置依赖时，无法确认该依赖不会在某个时刻发生变化，这可能导致意外结果。例如，最初设置了一个 `FileLogger`，随后又设置了一个 `MailLogger`。这破坏了封装性，并使日志难以查找，因为我们替换了依赖。

为了防止这种情况，我们应该使用 setter 注入来添加依赖，如下所示：

![](img/Image00855.jpg)

![](img/Image00856.jpg)

这样，每当我们使用核心功能时，即使没有添加 logger 依赖也不会出错，并且任何添加的 logger 都会被使用，即使之前已经添加过另一个 logger。我们是在扩展功能，而不是替换它。

#### 第 35.3 节：容器注入

在使用依赖注入容器（DIC）的语境下，依赖注入（DI）可以被视为构造函数注入的超集。DIC 通常会分析类构造函数的类型提示并解析其需求，从而有效地注入实例执行所需的依赖。

具体实现远超出了本文档的范围，但其核心在于，DIC 依赖于使用类的签名……

![](img/Image00857.jpg)

……来自动实例化它，大多数情况下依赖于自动加载系统。

![](img/Image00858.jpg)

如果你使用的 PHP 版本至少是 5.5，并想要以如上所示的方式获取类名，正确的方法是第二种方式。这样你可以利用现代 IDE 快速查找类的用法，这将极大地帮助你进行潜在的重构。你不应该依赖普通字符串。

在这种情况下，`Documentation\Example` 知道它需要一个 `Meaning`，DIC 反过来会实例化一个 `Meaning` 类型。具体实现无需依赖消费实例。

相反，我们在对象创建之前在容器中设置规则，指示如果需要，特定类型应如何实例化。

这有许多优势，因为 DIC 可以

![](img/Image00859.jpg)共享通用实例

提供工厂以解析类型签名

解析接口签名

如果我们定义关于如何管理特定类型的规则，就可以对共享、实例化或从工厂创建哪些类型进行精细控制。

## 第 36 章：XML

#### 第 36.1 节：使用 DomDocument 创建 XML

要使用 `DOMDocument` 创建 XML，基本上我们需要使用 `createElement()` 和 `createAttribute()` 方法创建所有标签和属性，然后使用 `appendChild()` 创建 XML 结构。

下面的示例包含标签、属性、一个 CDATA 部分以及第二个标签的不同命名空间：

![](img/Image00860.jpg)

这将输出以下 XML：

![](img/Image00861.jpg)

#### 第 36.2 节：使用 DOMDocument 读取 XML 文档

与 SimpleXML 类似，你可以使用 `DOMDocument` 从字符串或 XML 文件解析 XML。

1. 从字符串

![](img/Image00862.jpg)

2. 从文件

![](img/Image00863.jpg)

解析示例

考虑以下 XML：

![](img/Image00864.jpg)

这是解析它的示例代码：

```
$books = $doc->getElementsByTagName('book');
foreach ($books as $book) {
    $title = $book->getElementsByTagName('name')->item(0)->nodeValue;
    $price = $book->getElementsByTagName('price')->item(0)->nodeValue;
    $id = $book->getElementsByTagName('id')->item(0)->nodeValue;
    print_r("The title of the book $id is $title and it costs $price." . "\n");
}
```

这将输出：

![](img/Image00866.jpg)The title of the book 1 is PHP - An Introduction and it costs $5.95.

The title of the book 2 is PHP - Advanced and it costs $25.00.

#### 第 36.3 节：利用 PHP 的 SimpleXML 库处理 XML

SimpleXML 是一个强大的库，它将 XML 字符串转换为易于使用的 PHP 对象。

以下假设 XML 结构如下。

![](img/Image00867.jpg)

将数据读入 SimpleXML

首先，我们需要将数据读入 SimpleXML。我们可以通过 3 种不同的方式来实现。首先，我们可以[从 DOM 节点加载数据](http://php.net/manual/en/function.simplexml-import-dom.php)。

![](img/Image00868.jpg)

我们的下一个选项是[从 XML 文件加载数据](http://php.net/manual/en/function.simplexml-load-file.php)。

![](img/Image00869.jpg)

最后，我们可以[从变量加载数据](http://php.net/manual/en/function.simplexml-load-string.php)。

![](img/Image00870.jpg)

无论你选择从 [DOM 元素](http://php.net/manual/en/function.simplexml-import-dom.php)、[文件](http://php.net/manual/en/function.simplexml-load-file.php) 还是 [字符串](http://php.net/manual/en/function.simplexml-load-string.php) 加载，你现在都得到了一个名为 `$xmlElement` 的 `SimpleXMLElement` 变量。现在，我们可以开始在 PHP 中使用我们的 XML 了。

访问 SimpleXML 数据

访问 `SimpleXMLElement` 对象中数据的最简单方法是[直接调用属性](http://php.net/manual/en/simplexml.examples-basic.php#example-6325)。如果我们想访问第一个 `bookName`，即 StackOverflow SimpleXML Example，则可以按如下方式访问。

![](img/Image00871.jpg)

此时，SimpleXML 会假设因为我们没有明确告诉它想要哪本书，所以我们想要第一本。然而，如果我们决定不想要第一本，而是想要 Another SimpleXML Example，则可以按如下方式访问。

![](img/Image00872.jpg)

值得注意的是，使用 `[0]` 与不使用它的效果相同，所以

![](img/Image00873.jpg)

的效果与

![](img/Image00874.jpg)

相同。

遍历 XML

你可能希望[遍历 XML](http://php.net/manual/en/simplexml.examples-basic.php#example-6327) 有很多原因，例如你有许多项（在我们的例子中是书），想要在网页上显示。为此，我们可以使用 [foreach 循环](http://php.net/manual/en/control-structures.foreach.php) 或标准的 [for 循环](http://php.net/manual/en/control-structures.for.php)，利用 [SimpleXMLElement 的 count 函数](http://php.net/manual/en/simplexmlelement.count.php)。

![](img/Image00875.jpg)

或

![](img/Image00876.jpg)

错误处理

现在我们已经走到了这一步，重要的是要意识到我们只是凡人，最终很可能会遇到错误——尤其是如果我们一直在摆弄不同的 XML 文件的话。因此，我们需要处理这些错误。

假设我们创建了一个 XML 文件。你会注意到，虽然这个 XML 与我们之前的很相似，但这个 XML 文件的问题在于最后的结束标签是 `/doc` 而不是 `/document`。

![](img/Image00877.jpg)

![](img/Image00878.jpg)

现在，假设我们将其作为 `$file` 加载到 PHP 中。

![](img/Image00879.jpg)

我们将看到以下内容：

![](img/Image00880.jpg)

然而，一旦我们修复了这个问题，就会显示 "Happy Days"。

#### 第 36.4 节：使用 XMLWriter 创建 XML 文件

实例化一个 `XMLWriter` 对象：

![](img/Image00881.jpg)




| var | | / | | www | | example | . | com | | xml | | output | . | xml |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

接下来打开您要写入的文件。例如，要写入 `/`，请使用：

![](img/Image00882.jpg)

开始文档（创建 XML 开放标签）：

![](img/Image00883.jpg)

这将输出：

![](img/Image00884.jpg)

现在您可以开始编写元素：

![](img/Image00885.jpg)

这将生成 XML：

![](img/Image00886.jpg)

如果您需要比仅包含纯值的节点稍微复杂一点的内容，您也可以“开始”一个元素，并在关闭它之前向其添加属性：

![](img/Image00887.jpg)

这将输出：

![](img/Image00888.jpg)

#### 第 36.5 节：使用 SimpleXML 读取 XML 文档

您可以从字符串或 XML 文件解析 XML。

1. 从字符串

![](img/Image00889.jpg)

2. 从文件

![](img/Image00890.jpg)

解析示例

考虑以下 XML：

![](img/Image00891.jpg)

这是解析它的示例代码：

![](img/Image00892.jpg)

这将输出：

![](img/Image00893.jpg)书籍 1 的标题是 PHP - An Introduction，价格为 $5.95。书籍 2 的标题是 PHP - Advanced，价格为 $25.00。

## 第 37 章：SimpleXML

#### 第 37.1 节：将 XML 数据加载到 simplexml 中

从字符串加载

使用 `simplexml_load_string` 从字符串创建 `SimpleXMLElement`：

```
$xmlString = "<?xml version='1.0' encoding='UTF-8'?>";
$xml = simplexml_load_string($xmlString) or die("Error: Cannot create object");
```

请注意，此处必须使用 `or` 而不是 `||`，因为 `or` 的优先级高于 `=`。`or` 后面的代码仅在 `$xml` 最终解析为 `false` 时才会执行。

从文件加载

使用 `simplexml_load_file` 从文件或 URL 加载 XML 数据：

![](img/Image00895.jpg)

URL 可以是 PHP 支持的任何[方案](http://php.net/wrappers)，或自定义流包装器。

## 第 38 章：解析 HTML

#### 第 38.1 节：从字符串解析 HTML

PHP 实现了一个符合 [DOM Level 2](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/) 的解析器，允许您使用熟悉的方法（如 `getElementById()` 或 `appendChild()`）来处理 HTML。

![](img/Image00896.jpg)

输出：

![](img/Image00897.jpg)

| `libxml_use_internal_errors()` | 在导入 HTML 之前。然后您可以使用 | `libxml_get_errors()` |
| --- | --- | --- |

请注意，PHP 会针对 HTML 的任何问题发出警告，特别是当您导入文档片段时。为了避免这些警告，请通过调用 `libxml_use_internal_errors()` 告诉 DOM 库（libxml）自行处理错误，以便在需要时处理错误。

#### 第 38.2 节：使用 XPath

![](img/Image00898.jpg)

输出：

![](img/Image00899.jpg)

#### 第 38.3 节：SimpleXML

简介

![](img/Image00900.jpg)SimpleXML 是一个 PHP 库，它提供了一种处理 XML 文档的简便方法（特别是读取和遍历 XML 数据）。

![](img/Image00901.jpg)唯一的限制是 XML 文档必须是格式良好的。

![](img/Image00902.jpg)

![](img/Image00903.jpg)

使用面向对象方法解析 XML

![](img/Image00904.jpg)

访问子元素和属性

![](img/Image00905.jpg)当 SimpleXML 解析 XML 文档时，它会将所有 XML 元素或节点转换为生成的 `SimpleXMLElement` 对象的属性。

此外，它将 XML 属性转换为关联数组，可从其所属的属性访问。

![](img/Image00906.jpg)

XML 文档中的属性。

当您不知道它们的名称时（或者您不想知道它们）：

![](img/Image00907.jpg)

## 第 39 章：正则表达式 (regexp/PCRE)

参数详情

`$pattern` 包含正则表达式（PCRE 模式）的字符串

#### 第 39.1 节：全局正则表达式匹配

可以使用 `preg_match_all` 执行全局正则表达式匹配。`preg_match_all` 返回目标字符串中所有匹配的结果（与 `preg_match` 相反，后者仅返回第一个）。

`preg_match_all` 函数返回匹配的数量。第三个参数 `$matches` 将包含由第四个参数中给出的标志控制格式的匹配项。

如果给定一个数组，`$matches` 将包含一个格式类似于 `preg_match` 返回结果的数组，不同之处在于 `preg_match` 在第一个匹配处停止，而 `preg_match_all` 会遍历字符串直到字符串被完全消耗，并将每次迭代的结果以多维数组形式返回，其格式可由第四个参数中的标志控制。

第四个参数 `$flags` 控制 `$matches` 数组的结构。默认模式为 `PREG_PATTERN_ORDER`，可能的标志为 `PREG_SET_ORDER` 和 `PREG_PATTERN_ORDER`。

![](img/Image00908.jpg)

来自 `PREG_SET_ORDER` 的第一个 `var_dump` 给出以下输出：

![](img/Image00909.jpg)

![](img/Image00910.jpg)

`$matches` 有三个嵌套数组。每个数组代表一次匹配，其格式与 `preg_match` 的返回结果相同。

第二个 `var_dump`（`PREG_PATTERN_ORDER`）给出以下输出：

![](img/Image00911.jpg)

当相同的正则表达式通过 `preg_match` 运行时，返回以下数组：

![](img/Image00912.jpg)

#### 第 39.2 节：使用正则表达式进行字符串匹配

`preg_match` 检查字符串是否与正则表达式匹配。

![](img/Image00913.jpg)

如果您传入第三个参数，它将被填充为正则表达式的匹配数据：

```
preg_match('%^([a-zA-Z]+): ([0-9]+)$%', 'This is a string which contains numbers: 12345', $matches);
// $matches 现在包含正则表达式匹配结果的数组。
echo json_encode($matches); // ["numbers: 12345", "numbers", "12345"]
```

`$matches` 包含一个数组，第一个元素是完整匹配，随后是正则表达式中由括号括起来的子串，按左括号的偏移量顺序排列。这意味着，如果您有 `/z(a(b))/` 作为正则表达式，索引 0 包含整个子串 `zab`，索引 1 包含外层括号括起来的子串 `ab`，索引 2 包含内层括号括起来的 `b`。

#### 第 39.3 节：通过正则表达式将字符串分割为数组

![](img/Image00915.jpg)

输出：

![](img/Image00916.jpg)

| `preg_split` |
| --- |

要将字符串分割为数组，只需传递字符串和一个供 `preg_split()` 匹配和搜索的正则表达式，添加第三个参数（`limit`）允许您设置执行的“匹配”次数，剩余的字符串将被添加到数组末尾。

第四个参数是（`flags`），此处我们使用 `PREG_SPLIT_NO_EMPTY`，它防止我们的数组包含任何空键/值。

#### 第 39.4 节：使用正则表达式进行字符串替换

```
$string = "a;b;c\nd;e;f";
echo preg_replace("/(^([^;]+);([^;]+);([^;]+)$)/m", "$3;$2;$1", $string);
// $1、$2 和 $3 分别代表第一、第二和第三个捕获组
```

输出

![](img/Image00918.jpg)

搜索分号之间的所有内容并反转顺序。

#### 第 39.5 节：使用回调进行字符串替换

`preg_replace_callback` 通过将每个匹配的捕获组发送给定义的回调函数，并用回调函数的返回值替换它来工作。这允许我们基于任何类型的逻辑替换字符串。

![](img/Image00919.jpg)

![](img/Image00920.jpg)

## 第 40 章：Traits（特性）

#### 第 40.1 节：什么是 Trait？

PHP 只允许单继承。换句话说，一个类只能扩展另一个类。但如果您需要包含不属于父类的内容怎么办？在 PHP 5.4 之前，您必须想办法变通，但在 5.4 版本中引入了 Traits。Traits 允许您基本上将一部分类“复制并粘贴”到您的主类中。





# PHP Traits 和 Composer 依赖管理器

## 第 40.1 节：Traits 简介

这里我们有 `MrEd`，它已经继承自 `Horse`。但并非所有马都会 `Talk`，所以我们为此定义了一个 `Trait`。让我们看看这在做什么。

首先，我们定义 `Trait`。我们可以配合自动加载和命名空间使用它（另请参阅在命名空间中引用类或函数）。然后我们使用关键字 `use` 将其包含到 `MrEd` 类中。

你会注意到 `MrEd` 直接使用了 `Talk` 的函数和变量，而无需定义它们。还记得我们说的复制粘贴吗？这些函数和变量现在都在类中定义了，就好像这个类自己定义了它们一样。

##### Traits 对比 抽象类

Traits 与抽象类关系最为密切，因为你可以在其中定义变量和函数。你也无法直接实例化一个 `Trait`（即 `new Trait()`）。Traits 不能像抽象类或接口那样强制类隐式定义函数。Traits 仅用于显式定义（因为你可以实现任意数量的接口，请参阅接口）。

##### 何时应该使用 Trait？

当考虑使用 `Trait` 时，首先要问自己这个重要问题：

**我能否通过重构代码来避免使用 Trait？**

在大多数情况下，答案是 **Yes**。Traits 是单继承导致的边缘情况。滥用或过度使用 Traits 的诱惑可能很大。但请考虑，`Trait` 为你的代码引入了另一个来源，这意味着又增加了一层复杂性。在本例中，我们只处理 3 个类。但 Traits 意味着你现在可能要处理更多的类。每增加一个 `Trait`，你的类就变得更难处理，因为你现在必须去引用每个 `Trait` 以了解它定义了什么（以及可能发生冲突的位置，请参阅冲突解决）。理想情况下，你应该在代码中保持尽可能少的 Traits。

## 第 40.2 节：Traits 促进水平代码复用

假设我们有一个用于日志记录的接口：

```php
interface Logger {
    public function log(string $message);
}
```

现在假设我们有 `Logger` 接口的两个具体实现：`FileLogger` 和 `ConsoleLogger`。

```php
class FileLogger implements Logger {
    public function log(string $message) {
        // 写入文件
    }
}

class ConsoleLogger implements Logger {
    public function log(string $message) {
        echo $message;
    }
}
```

现在如果你定义了另一个类 `Foo`，也想让它能够执行日志记录任务，你可以这样做：

```php
class Foo {
    private $logger;

    public function setLogger(Logger $logger) {
        $this->logger = $logger;
    }

    public function doSomething() {
        if ($this->logger) {
            $this->logger->log("Doing something");
        }
    }
}
```

`Foo` 现在也是一个 `Logger`，但其功能依赖于通过 `setLogger()` 传递给它的 `Logger` 实现。如果我们现在想让类 `Bar` 也拥有这个日志记录机制，我们就必须在 `Bar` 类中复制这段逻辑。

我们可以定义一个 trait 来代替复制代码：

```php
trait Loggable {
    private $logger;

    public function setLogger(Logger $logger) {
        $this->logger = $logger;
    }

    public function log(string $message) {
        if ($this->logger) {
            $this->logger->log($message);
        }
    }
}
```

现在我们已在 trait 中定义了逻辑，可以使用该 trait 将逻辑添加到 `Foo` 和 `Bar` 类中：

```php
class Foo {
    use Loggable;
    // ...
}

class Bar {
    use Loggable;
    // ...
}
```

## 第 40.3 节：冲突解决

尝试在一个类中使用多个 trait 可能会导致涉及冲突方法的问题。你需要手动解决此类冲突。

例如，让我们创建这个层级结构：

```php
trait Cat {
    public function say() {
        echo "Meow";
    }
}

trait Dog {
    public function say() {
        echo "Woof";
    }
}
```

现在，尝试创建以下类：

```php
class TalkingParrot {
    use Cat, Dog;
}
```

PHP 解释器将返回致命错误：

```
Fatal error: Trait method say has not been applied, because there are collisions with other trait methods on TalkingParrot
```

解决冲突：

```php
class TalkingParrot {
    use Cat, Dog {
        Cat::say insteadof Dog;
        Dog::say as dogSay;
    }
}

$parrot = new TalkingParrot();
$parrot->say();    // 输出: Meow
$parrot->dogSay(); // 输出: Woof
```

## 第 40.4 节：使用 Traits 实现单例模式

**免责声明**：此例绝不提倡使用单例模式。单例模式必须谨慎使用。

在 PHP 中实现单例有一种相当标准的方式：

```php
class Singleton {
    private static $instance = null;

    private function __construct() {}

    private function __clone() {}

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }
}
```

为了防止代码重复，将此行为提取到 trait 中是个好主意。

```php
trait SingletonTrait {
    private static $instance = null;

    private function __construct() {}

    private function __clone() {}

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    public function __wakeup() {
        throw new \Exception("Cannot unserialize a singleton.");
    }
}
```

现在任何想作为单例运行的类只需使用该 trait：

```php
class MyService {
    use SingletonTrait;
    // ...
}

$service = MyService::getInstance();
```

即使现在无法序列化单例，禁用反序列化方法仍然很有用。

## 第 40.5 节：Traits 保持类整洁

随着时间的推移，我们的类可能会实现越来越多的接口。当这些接口拥有许多方法时，我们类中的方法总数将变得非常庞大。

例如，假设我们有两个接口和一个实现它们的类：

```php
interface Printable {
    public function print();
    public function printPreview();
}

interface Savable {
    public function save();
    public function saveAs();
}

class Article implements Printable, Savable {
    // ... 此处有许多方法
}
```

我们可以使用单独的 Traits 来实现这些接口，而不是在 `Article` 类中实现所有接口方法，从而保持类的精简，并将接口实现的代码与类分离。

例如，要实现 `Printable` 接口，我们可以创建这个 trait：

```php
trait PrintableTrait {
    public function print() {
        // 实现
    }

    public function printPreview() {
        // 实现
    }
}
```

并让类使用该 trait：

```php
class Article implements Printable, Savable {
    use PrintableTrait;
    use SavableTrait; // 假设 SavableTrait 存在
    // ...
}
```

主要好处是我们的接口实现方法将与类的其余部分分离，并存储在一个 trait 中，该 trait 承担为该特定类型对象实现接口的唯一责任。

## 第 40.6 节：多 Traits 使用

```php
trait Hello {
    public function sayHello() {
        echo "Hello ";
    }
}

trait World {
    public function sayWorld() {
        echo "World";
    }
}

class MyClass {
    use Hello, World;
}

$obj = new MyClass();
$obj->sayHello();
$obj->sayWorld();
```

上例将输出：

```
Hello World
```

## 第 40.7 节：修改方法可见性

```php
trait HelloWorld {
    public function sayHello() {
        echo "Hello World";
    }
}

class MyClass1 {
    use HelloWorld;
}

class MyClass2 {
    use HelloWorld { sayHello as protected; }
}

class MyClass3 {
    use HelloWorld { sayHello as private myPrivateHello; }
}
```

运行此例：

```php
$obj1 = new MyClass1();
$obj1->sayHello(); // 正常: public

$obj2 = new MyClass2();
// $obj2->sayHello(); // 致命错误: 调用受保护方法

$obj3 = new MyClass3();
// $obj3->sayHello(); // 致命错误: 调用私有方法
// $obj3->myPrivateHello(); // 致命错误: 调用私有方法
```

**注意**：因此请注意，在 `MyClass2` 的最后一个例子中，来自 `HelloWorld` 的原始未别名方法仍按原样可访问。

## 第 41 章：Composer 依赖管理器

##### 参数详情

| 参数 | 描述 |
| :--- | :--- |
| `license` | 定义项目中要使用的许可证类型。 |
| `authors` | 定义项目的作者及作者详细信息。 |
| `support` | 定义支持邮箱、IRC 频道和各种链接。 |
| `require` | 定义实际依赖及包版本。 |
| `require-dev` | 定义开发项目所需的包。 |
| `suggest` | 定义包建议，即安装后可能有帮助的包。 |
| `autoload` | 定义项目的自动加载策略。 |
| `autoload-dev` | 定义开发项目的自动加载策略。 |

[Composer](https://getcomposer.org/) 是 PHP 最常用的依赖管理器。它类似于 Node 中的 `npm`、Python 的 `pip` 或 .NET 的 `NuGet`。

#### 第 41.1 节：什么是 Composer？

[Composer](https://getcomposer.org/) 是 PHP 的依赖/包管理器。它可用于安装、跟踪和更新项目依赖。Composer 还负责自动加载应用程序所依赖的依赖项，让你轻松在项目中使用依赖，而无需担心在任何给定文件顶部包含它们。

##### `composer.json`

项目的依赖列在 `composer.json` 文件中，该文件通常位于项目根目录。此文件保存关于生产环境和开发环境所需包版本的信息。

`composer.json` 模式的完整大纲可在 [Composer 官网](https://getcomposer.org/doc/04-schema.md) 找到。

##### 安装包

```bash
composer require <package>
##### 或用于开发依赖
composer require --dev <package>
```

此文件可使用任何文本编辑器手动编辑，或通过命令行自动编辑，命令如上所示。

##### 初始化项目

要在项目中开始使用 composer，你需要创建 `composer.json` 文件。你可以手动创建，或直接运行 `composer init`。在终端运行 `composer init` 后，它会询问你关于项目的一些基本信息：

*   **包名** (vendor/package - 例如 `laravel/laravel`)
*   **描述** - 可选
*   **作者**
*   以及其他一些信息，如最低稳定性、许可证和所需包。




`composer.json` 文件中的 `require` 键指定了项目依赖哪些包。`require` 接受一个对象，该对象将包名（例如 `monolog/monolog`）映射到版本约束（例如 `1.0.*`）。

![](img/Image00946.jpg)

要安装已定义的依赖项，你需要运行 `composer install` 命令，它将查找符合所提供版本约束的已定义包，并将其下载到 `vendor` 目录中。将第三方代码放入名为 `vendor` 的目录中是一种惯例。

##### `composer.lock`

你会注意到 install 命令还创建了一个 `composer.lock` 文件。

##### `composer.lock`

`composer.lock` 文件由 Composer 自动生成。此文件用于跟踪当前安装的依赖项的版本和状态。运行 `composer install` 将把包安装到锁文件中存储的确切状态。

#### 第 41.2 节：使用 Composer 进行自动加载

虽然 Composer 为 PHP 项目提供了一个管理依赖的系统（例如来自 [Packagist](https://packagist.org/)），但它也可以充当自动加载器，指定在哪里查找特定的命名空间或包含通用函数文件。

##### `composer.json`

从 `composer.json` 文件开始：

![](img/Image00947.jpg)

##### `functions.php`

此配置代码确保命名空间 `MyVendorName\MyProject` 中的所有类都映射到 `src` 目录，而 `MyVendorName\MyProject\Tests` 中的所有类映射到 `tests` 目录（相对于你的根目录）。它还将自动包含 `functions.php` 文件。

##### `composer.json`

##### `autoload.php`

##### `composer install --no-dev`。`autoload.php`

##### `composer.json`

将此内容放入 `composer.json` 文件后，在终端运行 `composer update`，让 Composer 更新依赖项、锁文件并生成 `autoload.php` 文件。部署到生产环境时，你应该使用 `composer install --no-dev`。`autoload.php` 文件位于 `vendor` 目录中，该目录应生成在 `composer.json` 所在的目录下。

你应该在应用程序生命周期的早期设置点通过类似下面的代码引入此文件。

![](img/Image00948.jpg)

##### `autoload.php`

一旦包含，`autoload.php` 文件将负责加载你在 `composer.json` 文件中提供的所有依赖项。

类路径到目录映射的一些示例：

##### `src/Shapes/Square.php`

##### `tests/Shapes/Square.php`

![](img/Image00949.jpg)
`MyVendorName\MyProject\Shapes\Square` ➔ `src/Shapes/Square.php`。
`MyVendorName\MyProject\Tests\Shapes\Square` ➔ `tests/Shapes/Square.php`。

#### 第 41.3 节：'composer install' 和 'composer update' 的区别

##### `composer.json`

`composer update` `composer update` 将按照 `composer.json` 中的指定更新我们的依赖项。

例如，如果我们的项目使用此配置：

![](img/Image00950.jpg)

假设我们实际安装了该包的 `2.0.1` 版本，运行 `composer update` 将导致该包升级（例如升级到 `2.0.2`，如果已发布）。

详细来说 `composer update` 将：

##### `composer.json`

##### `composer.json`

##### `composer.lock`

![](img/Image00951.jpg)
读取 `composer.json`
移除 `composer.json` 中不再需要的已安装包
检查所需包的最新版本的可用性
安装包的最新版本
更新 `composer.lock` 以存储已安装包的版本

##### `composer.lock`

`composer install`

##### `composer.lock`

`composer install` 将按照 `composer.lock` 文件中指定的版本（锁定版本）安装所有依赖项，而不更新任何内容。

详细来说：

##### `composer.lock`

##### `composer.lock`

![](img/Image00952.jpg)
读取 `composer.lock` 文件
安装 `composer.lock` 文件中指定的包

![](img/Image00953.jpg)

##### 何时安装以及何时更新

`composer update` 主要用于“开发阶段”，以升级项目包。

##### `composer.lock`

`composer install` 主要用于“部署阶段”，使用由 `composer update` 创建的 `composer.lock` 文件中存储的相同依赖项，在生产服务器或测试环境上安装应用程序。

#### 第 41.4 节：Composer 可用命令

| 命令 | 用法 |
| --- | --- |
| about | Composer 的简短信息 |
| archive | 创建此 Composer 包的归档文件 |
| browse | 在浏览器中打开包的仓库 URL 或主页。 |
| clear-cache | 清除 Composer 的内部包缓存。 |
| clearcache | 清除 Composer 的内部包缓存。 |
| config | 设置配置选项 |
| create-project | 从包在给定目录中创建新项目。 |
| depends | 显示哪些包导致给定包被安装 |
| diagnose | 诊断系统以识别常见错误。 |
| dump-autoload | 转储自动加载器 |
| dumpautoload | 转储自动加载器 |
| exec | 执行供应商提供的二进制文件/脚本 |
| global | 允许在全局 Composer 目录 ($COMPOSER_HOME) 中运行命令。 |
| help | 显示命令的帮助 |
| home | 在浏览器中打开包的仓库 URL 或主页。 |
| info | 显示包的信息 |
| init | 在当前目录创建一个基本的 `composer.json` 文件。 |
| install | 如果存在 `composer.lock` 文件，则从中安装项目依赖项，否则回退到 `composer.json`。 |
| licenses | 显示依赖项的许可证信息 |
| list | 列出命令 |
| outdated | 显示有更新可用的已安装包列表，包括其最新版本。 |
| prohibits | 显示哪些包阻止给定包被安装 |
| remove | 从 require 或 require-dev 中移除包 |
| require | 将所需包添加到 `composer.json` 并安装它们 |
| run-script | 运行 `composer.json` 中定义的脚本。 |
| search | 搜索包 |
| self-update | 将 `composer.phar` 更新到最新版本。 |
| selfupdate | 将 `composer.phar` 更新到最新版本。 |
| show | 显示包的信息 |
| status | 显示本地修改过的包列表 |
| suggests | 显示包建议 |
| update | 根据 `composer.json` 将依赖项更新到最新版本，并更新 `composer.lock` 文件。 |
| validate | 验证 `composer.json` 和 `composer.lock` |
| why | 显示哪些包导致给定包被安装 |
| why-not | 显示哪些包阻止给定包被安装 |

#### 第 41.5 节：使用 Composer 的好处

##### `composer.lock`

Composer 在一个名为 `composer.lock` 的文件中跟踪你安装的包版本，该文件旨在提交到版本控制系统，以便将来克隆项目时，只需运行 `composer install` 即可下载并安装项目的所有依赖项。

Composer 按项目处理 PHP 依赖项。这使得在一台机器上拥有多个依赖于同一 PHP 包的不同版本的项目变得容易。

Composer 跟踪哪些依赖项仅用于开发环境

![](img/Image00954.jpg)

Composer 提供了一个自动加载器，使得开始使用任何包变得极其简单。例如，在使用 `composer require` 安装 [Goutte](https://github.com/FriendsOfPHP/Goutte) 后：

`composer require fabpot/goutte`

你可以立即在新项目中开始使用 Goutte：

![](img/Image00955.jpg)



# Composer

Composer 允许您轻松将项目更新到 `composer.json` 允许的最新版本。例如：

| composer update fabpot | | goutte |
| --- | --- | --- |

，或者更新项目的每个依赖项：`composer update .`

#### 第 41.6 节：安装

您可以在本地安装 Composer，作为项目的一部分，或者全局安装为系统范围的可执行文件。

##### 本地安装

要安装，请在终端中运行以下命令。

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

![](img/Image00956.jpg) # 要检查下载的安装程序的有效性，请在此处对照 SHA-384 进行检查： # https://composer.github.io/pubkeys.html

```
php composer-setup.php
```

```
php -r "unlink('composer-setup.php');"
```

| composer | | phar |
| --- | --- | --- |

| composer | | phar |
| --- | --- | --- |

这将把 `composer.phar`（一个 PHP 归档文件）下载到当前目录。现在您可以运行 `php composer.phar` 来使用 Composer，例如：

![](img/Image00957.jpg)

##### 全局安装

要全局使用 Composer，请将 `composer.phar` 文件放置到 PATH 环境变量包含的目录中

![](img/Image00958.jpg)

| php composer.phar |
| --- |

现在您可以在任何地方使用 `composer` 代替 `php composer.phar`，例如：

![](img/Image00959.jpg)

## 第 42 章：魔术方法

#### 第 42.1 节：`__call()` 和 `__callStatic()`

| `__call()` | | `__callStatic()` |
| --- | --- | --- |

当在对象上下文或静态上下文中调用不存在的对象方法时，会被调用。

![](img/Image00960.jpg)

![](img/Image00961.jpg)

示例：

![](img/Image00962.jpg)

#### 第 42.2 节：`__get()`、`__set()`、`__isset()` 和 `__unset()`

每当您尝试从类中检索某个字段时，如下所示：

![](img/Image00963.jpg)

| `__get` | | `($name` |
| --- | --- | --- |

PHP 会调用魔术方法 `__get()`，在这种情况下 `$name` 等于 "height"。向类字段写入值，如下所示：

![](img/Image00964.jpg)

| `__set` | | `($name` | | `,` | ` $value` |
| --- | --- | --- | --- | --- | --- |

将调用魔术方法 `__set()`，其中 `$name` 等于 "height"，`$value` 等于 10。

| `isset` | `()` | `unset` |
| --- | --- | --- |

PHP 还有两个内置函数 `isset()`，用于检查变量是否存在，以及 `unset()`，用于销毁变量。

检查对象的字段是否已设置，如下所示：

![](img/Image00965.jpg)

| `__isset` | | `($name` |
| --- | --- | --- |

将在该对象上调用 `__isset()` 函数。销毁变量，如下所示：

![](img/Image00966.jpg)

| `__unset` | | `($name` |
| --- | --- | --- |

将在该对象上调用 `__unset()` 函数。

通常，当您未在类中定义这些方法时，PHP 只会按原样检索存储在类中的字段。但是，您可以重写这些方法来创建能够像数组一样保存数据，但像对象一样使用的类：

![](img/Image00967.jpg)

![](img/Image00968.jpg)

##### `empty()` 函数和魔术方法

| `empty` | `()` | `__isset` |
| --- | --- | --- |

请注意，在类属性上调用 `empty()` 将会调用 `__isset()`，因为正如 PHP 手册所述：

![](img/Image00969.jpg)

> `empty()` 本质上等同于 `!isset($var) || $var == false` 的简洁写法

#### 第 42.3 节：`__construct()` 和 `__destruct()`

| `__construct` |
| --- |

`()` 是 PHP 中最常见的魔术方法，因为它用于在类初始化时进行设置。

| `__construct()` | | `__destruct` |
| --- | --- | --- |

`__construct()` 方法的相反面。当您创建的对象不再有任何引用，或者您强制删除它时，将调用此方法。PHP 的垃圾回收机制将通过先调用其析构函数，然后将其从内存中移除来清理对象。

![](img/Image00970.jpg)

![](img/Image00971.jpg)

#### 第 42.4 节：`__toString()`

| `__toString` |
| --- |

每当对象被当作字符串处理时，就会调用 `__toString()` 方法。此方法应返回类的字符串表示形式。

![](img/Image00972.jpg)

#### 第 42.5 节：`__clone()`

`__clone` 通过使用 `clone` 关键字来调用。它用于在对象实际被克隆后，操作克隆时的对象状态。

![](img/Image00973.jpg)

示例：

![](img/Image00974.jpg)

#### 第 42.6 节：`__invoke()`

当用户尝试将对象作为函数调用时，将调用此魔术方法。可能的用例可能包括函数式编程或某些回调等方法。

![](img/Image00975.jpg)

![](img/Image00976.jpg)

#### 第 42.7 节：`__sleep()` 和 `__wakeup()`

`__sleep` 和 `__wakeup` 是与序列化过程相关的方法。`serialize` 函数会检查类是否有 `__sleep` 方法。如果有，它将在任何序列化之前执行。`__sleep` 应返回一个数组，包含对象中所有应被序列化的变量名。

如果类中存在 `__wakeup`，则会在 `unserialize` 时执行。其目的是重新建立资源以及反序列化时需要初始化的其他事项。

![](img/Image00977.jpg)

#### 第 42.8 节：`__debugInfo()`

![](img/Image00978.jpg)

##### 版本 ≤ 5.6

![](img/Image00979.jpg)

上面的示例将输出：

![](img/Image00980.jpg)

##### 版本 ≥ 5.6

![](img/Image00981.jpg)

上面的示例将输出：

![](img/Image00982.jpg)

## 第 43 章：文件处理

| 参数 | 说明 |
| --- | --- |
| filename | 要读取的文件名。 |
| use_include_path | 您可以使用可选的第二个参数并将其设置为 `TRUE`，如果您想在 `include_path` 中也搜索该文件。 |
| context | 一个上下文流资源。 |

#### 第 43.1 节：便捷函数

原始直接 IO `file_get_contents` 和 `file_put_contents` 提供了在单次调用中从文件读取/写入到 PHP 字符串或从 PHP 字符串写入到文件的能力。`file_put_contents` 也可以与 `FILE_APPEND` 位掩码标志一起使用，以追加内容到文件，而不是截断并覆盖文件。它可以与 `LOCK_EX` 位掩码一起使用，以在写入过程中获取文件的独占锁。位掩码标志可以通过 `|` 按位或运算符组合使用。

![](img/Image00983.jpg)

![](img/Image00984.jpg)

`FILE_APPEND` 便于向日志文件追加内容，而 `LOCK_EX` 有助于防止多进程写入文件时的竞争条件。例如，将当前会话信息写入日志文件：

```
file_put_contents("logins.log", "{$_SESSION["username"]} logged in", FILE_APPEND | LOCK_EX);
```

##### CSV IO

![](img/Image00985.jpg)

`fgetcsv` 从打开的文件中解析一行并检查 CSV 字段。成功时以数组形式返回 CSV 字段，失败时返回 `FALSE`。

默认情况下，它将只读取 CSV 文件的一行。

![](img/Image00986.jpg)

| contacts.csv |
| --- |

![](img/Image00987.jpg)

输出：

![](img/Image00988.jpg)

![](img/Image00989.jpg)

##### 直接将文件读取到标准输出

`readfile` 将文件复制到输出缓冲区。`readfile()` 本身不会出现任何内存问题，即使发送大文件也是如此。

![](img/Image00990.jpg)

##### 或者从文件指针

或者，要在文件中查找起始点以复制到标准输出，请改用 `fpassthru`。在下面的示例中，最后 1024 字节被复制到标准输出：

![](img/Image00991.jpg)

`file` 将传入文件中的行以数组形式返回。数组的每个元素对应文件中的一行，并保留换行符。

![](img/Image00992.jpg)

| test.txt |
| --- |

![](img/Image00993.jpg)

输出：

![](img/Image00994.jpg)

#### 第 43.2 节：删除文件和目录

##### 删除文件

`unlink` 函数删除单个文件，并返回操作是否成功。

![](img/Image00995.jpg)

##### 删除目录，支持递归删除




## 第 43.2 节：删除目录

另一方面，目录应使用 `rmdir` 删除。但是，此函数仅删除空目录。要删除包含文件的目录，请先删除目录中的文件。如果目录包含子目录，则可能需要递归。

以下示例扫描目录中的文件，递归删除成员文件/目录，并返回已删除的文件数（不包括目录）。

![](img/Image00996.jpg)

#### 第 43.3 节：获取文件信息

##### 检查路径是目录还是文件

`is_dir` 函数返回参数是否为目录，而 `is_file` 返回参数是否为文件。使用 `file_exists` 检查它是否为两者之一。

![](img/Image00997.jpg)

```
$file = "/this/is/a/file.txt";
```

![](img/Image00998.jpg)
```
echo is_dir($dir) ? "$dir is a directory" : "$dir is not a directory", PHP_EOL,
     is_file($dir) ? "$dir is a file" : "$dir is not a file", PHP_EOL,
     file_exists($dir) ? "$dir exists" : "$dir doesn't exist", PHP_EOL,
     is_dir($file) ? "$file is a directory" : "$file is not a directory", PHP_EOL,
     is_file($file) ? "$file is a file" : "$file is not a file", PHP_EOL,
     file_exists($file) ? "$file exists" : "$file doesn't exist", PHP_EOL;
```

这将输出：

![](img/Image00999.jpg)

##### 检查文件类型

使用 `filetype` 检查文件类型，可能的值为：

![](img/Image01000.jpg)
`fifo` `char` `dir` `block` `link` `file` `socket` `unknown`

将文件名直接传递给 `filetype`：

![](img/Image01001.jpg)

请注意，如果文件不存在，`filetype` 将返回 `false` 并触发 `E_WARNING`。

##### 检查可读性和可写性

将文件名传递给 `is_writable` 和 `is_readable` 函数，分别检查文件是否可写或可读。

如果文件不存在，这些函数会优雅地返回 `false`。

##### 检查文件访问/修改时间

使用 `filemtime` 和 `fileatime` 返回文件上次修改或访问的时间戳。返回值为 Unix 时间戳 —— 详情请参阅“处理日期和时间”。

![](img/Image01002.jpg)
```
echo "File was last modified on " . date("Y-m-d", filemtime("file.txt"));
echo "File was last accessed on " . date("Y-m-d", fileatime("file.txt"));
```

![](img/Image01003.jpg)

![](img/Image01004.jpg)

此示例将输出：

![](img/Image01005.jpg)

![](img/Image01006.jpg)

##### 解析文件路径信息

`$path` 要解析的文件的完整路径

四个可用选项 `$option` 之一：`PATHINFO_DIRNAME`、`PATHINFO_BASENAME`、`PATHINFO_EXTENSION` 或 `PATHINFO_FILENAME`

| image | | . | | jpg | | . | | png | | would be | | . | | png |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

![](img/Image01007.jpg)
如果未传递选项（第二个参数），则返回关联数组，否则返回字符串。

不验证文件是否存在。

仅将字符串解析为各部分。不对文件进行任何验证（无 MIME 类型检查等）。

| jpg |
| --- |

扩展名仅仅是 `$path` 的最后一个扩展名，即使它技术上是一个 `.` 文件，也会返回该文件的路径。没有扩展名的文件在数组中不会返回扩展名元素。

#### 第 43.4 节：基于流的文件 IO

##### 打开流

`fopen` 打开一个文件流句柄，可配合各种函数用于读取、写入、定位及其他操作。此值为资源类型，无法将其传递给其他线程并保持其功能。

![](img/Image01008.jpg)
```
$f = fopen("errors.log", "a"); // Will try to open errors.log for writing
```

第二个参数是文件流的模式：

| 模式 | 说明 |
| --- | --- |
| r | 以只读模式打开，文件指针指向文件开头 |
| r+ | 以读写模式打开，文件指针指向文件开头 |
| w | 以只写模式打开，文件指针指向文件开头。如果文件存在则将其清空。如果不存在则尝试创建。 |
| w+ | 以读写模式打开，文件指针指向文件开头。如果文件存在则将其清空。如果不存在则尝试创建。 |
| a | 以只写模式打开，文件指针指向文件末尾。如果文件不存在，则尝试创建。 |
| a+ | 以读写模式打开，文件指针指向文件末尾。如果文件不存在，则尝试创建。 |
| x | 创建并以只写模式打开。如果文件已存在，`fopen` 调用将失败。 |
| x+ | 创建并以读写模式打开。如果文件已存在，`fopen` 调用将失败。 |
| c | 以只写模式打开文件。如果文件不存在则尝试创建。文件指针指向文件开头，但不会在写入前清空文件。 |
| c+ | 以读写模式打开文件。如果文件不存在则尝试创建。文件指针指向文件开头，但不会在写入前清空文件。 |

| `\n` | | " 行尾转换为 " | | `\r\n` |
| --- | --- | --- | --- | --- |

在模式后添加 `t`（例如 `a+b`、`wt` 等）在 Windows 下处理文件时会将 `""` 进行转换。如果不希望这样（特别是二进制文件），请在模式后添加 `b`。

PHP 应用程序应在不再使用流时使用 `fclose` 关闭它们，以防止“Too many open files”错误。这在 CLI 程序中尤为重要，因为流仅在运行时关闭时才会关闭 —— 这意味着在 Web 服务器中，如果你不期望进程长时间运行且不会打开许多流，则可能不必关闭流（但作为防止资源泄漏的实践，仍然应该关闭）。

### 读取

使用 `fread` 将从文件指针读取给定字节数，或直到遇到 EOF。

##### 读取行

使用 `fgets` 将读取文件直到遇到 EOL，或读取给定长度。

`fread` 和 `fgets` 在读取时都会移动文件指针。

##### 读取剩余所有内容

使用 `stream_get_contents` 将流中所有剩余字节读取到字符串中并返回。

##### 调整文件指针位置

打开流后，文件指针最初位于文件开头（如果使用模式 `a` 则位于末尾）。使用 `fseek` 函数将文件指针移动到新位置，相对于以下三个值之一：

![](img/Image01009.jpg)
`SEEK_SET`：这是默认值；文件位置偏移量将相对于文件开头。

`SEEK_CUR`：文件位置偏移量将相对于当前位置。

`SEEK_END`：文件位置偏移量将相对于文件末尾。传递负偏移量是此值最常见的用法；它将文件位置移动到文件末尾前指定字节数处。

| SEEK_SET |
| --- |

| fseek | ( | $fh |
| --- | --- | --- |

![](img/Image01010.jpg)
`rewind` 是 `fseek($fh, 0, SEEK_SET)` 的便捷快捷方式。

使用 `ftell` 将显示文件指针的绝对位置。

例如，以下脚本读取 file.txt 时跳过前 10 字节，读取接下来的 10 字节，跳过 10 字节，读取接下来的 10 字节，然后读取最后 10 字节：

![](img/Image01011.jpg)

![](img/Image01012.jpg)

##### 写入

使用 `fwrite` 将提供的字符串从当前文件指针处开始写入文件。

![](img/Image01013.jpg)

#### 第 43.5 节：移动和复制文件及目录




##### 复制文件

[copy](http://php.net/copy) 将第一个参数中的源文件复制到第二个参数指定的目标位置。解析后的目标路径必须位于一个已存在的目录中。

![](img/Image01014.jpg)

##### 复制目录（递归方式）

复制目录与删除目录非常相似，区别在于：对于文件使用 [copy](http://php.net/copy) 而不是 [unlink](http://php.net/unlink)；对于目录，在函数开头使用 [mkdir](http://php.net/mkdir) 而不是在函数末尾使用 [rmdir](http://php.net/rmdir)。

![](img/Image01015.jpg)

##### 重命名/移动

重命名/移动文件和目录要简单得多。整个目录可以通过单次调用 [rename](http://php.net/rename) 函数来移动或重命名。

```
rename("~/file.txt", "~/file.html");
```

![](img/Image01016.jpg)

```
rename("~/dir", "~/old_dir");
```

```
rename("~/dir/file.txt", "~/dir2/file.txt");
```

![](img/Image01017.jpg)

# 第 43 章：处理大文件时最小化内存使用

#### 第 43.6 节：处理大文件时最小化内存使用

如果我们需要解析一个大文件，例如一个包含数百万行、超过 10 MB 的 CSV 文件，某些人会使用 `file` 或 `file_get_contents` 函数，结果导致触及 `memory_limit` 设置，报出

![](img/Image01018.jpg) Allowed memory size of XXXXX bytes exhausted

错误。请看下面的源代码（top-1m.csv 正好有 100 万行，大小约 22 MB）

![](img/Image01019.jpg)

输出结果为：

![](img/Image01020.jpg)

因为解释器需要将所有行保存在 `$arr` 数组中，所以消耗了约 200 MB 内存。注意我们甚至还没有对数组内容做任何处理。

现在看看下面的代码：

![](img/Image01021.jpg)

输出结果为

![](img/Image01022.jpg)

因此我们没有使用一丁点额外的内存，却解析了整个 CSV 并将其保存到另一个文件中，同时反转了第 2 列的值。这是因为 `fgetcsv` 每次只读取一行，而 `$row` 在每次循环中都会被覆盖。

## 第 44 章：流

##### 流语法

| 参数 | 名称 | 描述 |
| --- | --- | --- |
| `<scheme>://<target>` | 流资源 | 由该语法组成的数据提供者 |

#### 第 44.1 节：注册流包装器

流包装器为一个或多个特定的协议提供处理程序。

下面的示例展示了一个简单的流包装器，当流关闭时发送 PATCH HTTP 请求。

![](img/Image01023.jpg)

![](img/Image01024.jpg)

此示例仅展示了通用流包装器可能包含的一些方法示例。这并非所有可用方法。可实现的完整方法列表请见 [`php.net/streamWrapper`](http://php.net/streamWrapper)。

## 第 45 章：类型提示

#### 第 45.1 节：类和接口的类型提示

PHP 5 中新增了对类和接口的类型提示支持。

##### 类类型提示

![](img/Image01025.jpg)

上述脚本输出：

![](img/Image01026.jpg) Chris is being enrolled at University of Edinburgh

##### 接口类型提示

![](img/Image01027.jpg)

![](img/Image01028.jpg)

上例输出与之前相同：

![](img/Image01029.jpg) Chris is being enrolled at University of Edinburgh

##### Self 类型提示

`self` 关键字可用作类型提示，表明该值必须是声明该方法的类的实例。

#### 第 45.2 节：标量类型、数组和可调用类型的类型提示

PHP 5.1 中新增了对数组参数（PHP 7.1 后支持返回值）的类型提示支持，使用关键字 `array`。任何维度和类型的数组，以及空数组，均为有效值。

```
is_callable(array(class_name|object, method_name))
```

PHP 5.4 中新增了对可调用类型的类型提示支持。凡是 `is_callable()` 返回 true 的值，均可用于参数和返回值提示为 `callable` 的情况，即闭包对象、函数名字符串和数组。

如果函数名出现拼写错误导致其不再 `is_callable()`，将显示一个不太明显的错误消息：

![](img/Image01030.jpg)

非静态方法也可以以静态格式作为可调用类型传递，在 PHP 7 和 PHP 5 中分别会导致弃用警告和 `E_STRICT` 级别错误。

方法可见性会被考虑在内。如果带有可调用参数的方法的上下文无法访问提供的可调用对象，最终结果将如同该方法不存在一般。

![](img/Image01031.jpg)

![](img/Image01032.jpg)

输出：

![](img/Image01033.jpg) Fatal error: Uncaught TypeError: Argument 1 passed to r() must be callable, array given

PHP 7 中新增了对标量类型的类型提示支持。这意味着我们获得了对 `int`、`float`、`string` 和 `bool` 的类型提示支持。

默认情况下，PHP 会尝试将提供的任何参数转换为匹配其类型提示的类型。将调用改为 `add(1.5)` 会产生完全相同的输出，因为 PHP 将 float `1.5` 转换为了 `int`。

```
declare(strict_types=1);
```

要禁止此行为，必须在每个需要严格模式的 PHP 源文件顶部添加 `declare(strict_types=1);`。

![](img/Image01035.jpg)

上述脚本现在会产生致命错误：

![](img/Image01036.jpg) Fatal error: Uncaught TypeError: Argument 1 passed to add() must be of the type integer, float given

##### 例外：特殊类型

某些 PHP 函数可能会返回 `resource` 类型的值。由于这不是标量类型，而是特殊类型，因此无法对其进行类型提示。

`curl_init()` 会返回 `resource`，`fopen()` 也是。当然，这两种资源彼此不兼容。因此，当显式对 `resource` 进行类型提示时，PHP 7 将始终抛出以下 TypeError：

![](img/Image01037.jpg) TypeError: Argument 1 passed to sample() must be an instance of resource, resource given

#### 第 45.3 节：可空类型提示

##### 参数

PHP 7.1 中新增了可空类型提示，在类型提示前使用 `?` 运算符。

![](img/Image01038.jpg)

PHP 7.1 之前，如果参数有类型提示，必须声明默认值 `null` 才能接受 null 值。

![](img/Image01039.jpg)

##### 返回值

PHP 7.0 中，带有返回类型的函数不能返回 `null`。

PHP 7.1 中，函数可以声明可空返回类型提示。不过，函数仍必须返回 `null`，而不能是 void（无/空返回语句）。

![](img/Image01040.jpg)

#### 第 45.4 节：泛型对象的类型提示

由于 PHP 对象不继承自任何基类（包括 `stdClass`），因此不支持对泛型对象类型进行类型提示。

例如，下面的代码将无法工作。

![](img/Image01041.jpg)

并会抛出致命错误：

![](img/Image01042.jpg) Fatal error: Uncaught TypeError: Argument 1 passed to doSomething() must be an instance of object, instance of OperationOne given

一种变通方法是声明一个不定义任何方法的退化接口，并让所有对象实现该接口。

![](img/Image01043.jpg)

#### 第 45.5 节：无返回值类型提示

PHP 7.1 中新增了 `void` 返回类型。虽然 PHP 没有实际的 void 值，但在编程语言中普遍认为返回 nothing 的函数返回的是 `void`。这不应与返回 `null` 混淆，因为 `null` 是一个可以返回的值。

![](img/Image01044.jpg)

注意，如果你声明了 `void` 返回类型，就不能返回任何值，否则会报致命错误：

![](img/Image01045.jpg)

不过，使用 `return` 退出函数是有效的：

![](img/Image01046.jpg)

## 第 46 章：过滤器与过滤器函数

##### 参数详情

| 参数 | 详情 |
| --- | --- |
| `variable` | 要过滤的值。注意标量值在内部过滤前会被转换为字符串。 |




# PHP Filter 扩展

| 参数 | 说明 |
| :--- | :--- |
| `filter` | 要应用的过滤器 ID。过滤器类型手册页列出了可用的过滤器。如果省略，将使用 `FILTER_DEFAULT`，这等同于 `FILTER_UNSAFE_RAW`。这将导致默认情况下不进行任何过滤。 |
| `options` | 选项的关联数组或标志的按位析取。如果过滤器接受选项，标志可以在数组的 "flags" 字段中提供。对于 "callback" 过滤器，应传递 callable 类型。回调必须接受一个参数（要过滤的值），并返回过滤/净化后的值。 |

此扩展通过验证或净化来过滤数据。当数据源包含未知（或外部）数据（如用户提供的输入）时，这非常有用。例如，这些数据可能来自 HTML 表单。

#### 第 46.1 节：验证布尔值

```php
var_dump(filter_var(true, FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // true
var_dump(filter_var(false, FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var(1, FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // true
var_dump(filter_var(0, FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var('1', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // true
var_dump(filter_var('0', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var('', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var(' ', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var('true', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // true
var_dump(filter_var('false', FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
var_dump(filter_var([], FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // NULL
var_dump(filter_var(null, FILTER_VALIDATE_BOOLEAN, FILTER_NULL_ON_FAILURE)); // false
```

#### 第 46.2 节：验证数字是否为浮点数

验证值为浮点数，成功时转换为浮点数。

**不带 `FILTER_FLAG_ALLOW_THOUSAND`：**

```php
var_dump(filter_var(1, FILTER_VALIDATE_FLOAT));
var_dump(filter_var(1.0, FILTER_VALIDATE_FLOAT));
var_dump(filter_var(1.0000, FILTER_VALIDATE_FLOAT));
var_dump(filter_var(1.00001, FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1.0', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1.0000', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1.00001', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1,000', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1,000.0', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1,000.0000', FILTER_VALIDATE_FLOAT));
var_dump(filter_var('1,000.00001', FILTER_VALIDATE_FLOAT));
```

**带 `FILTER_FLAG_ALLOW_THOUSAND`：**

```php
var_dump(filter_var(1, FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var(1.0, FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var(1.0000, FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var(1.00001, FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1.0', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1.0000', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1.00001', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1,000', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1,000.0', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1,000.0000', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
var_dump(filter_var('1,000.00001', FILTER_VALIDATE_FLOAT, FILTER_FLAG_ALLOW_THOUSAND));
```

#### 第 46.3 节：验证 MAC 地址

验证值是否为有效的 MAC 地址。

```php
var_dump(filter_var('FA-F9-DD-B2-5E-0D', FILTER_VALIDATE_MAC));
var_dump(filter_var('DC-BB-17-9A-CE-81', FILTER_VALIDATE_MAC));
var_dump(filter_var('96-D5-9E-67-40-AB', FILTER_VALIDATE_MAC));
var_dump(filter_var('96-D5-9E-67-40', FILTER_VALIDATE_MAC));
var_dump(filter_var('', FILTER_VALIDATE_MAC));
```

#### 第 46.4 节：净化电子邮件地址

移除字母、数字和 `!#$%&'*+-=?^_\`{|}~@.[]` 以外的所有字符。

```php
var_dump(filter_var('john@example.com', FILTER_SANITIZE_EMAIL));
var_dump(filter_var("!#$%&'*+-=?^_\`{|}~.[]@example.com", FILTER_SANITIZE_EMAIL));
var_dump(filter_var('john/@example.com', FILTER_SANITIZE_EMAIL));
var_dump(filter_var('john\\@example.com', FILTER_SANITIZE_EMAIL));
var_dump(filter_var('joh n@example.com', FILTER_SANITIZE_EMAIL));
```

#### 第 46.5 节：净化整数

移除数字、加号和减号以外的所有字符。

```php
var_dump(filter_var(1, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var(-1, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var(+1, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var(1.00, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var(+1.00, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var(-1.00, FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('1', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('-1', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('+1', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('1.00', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('+1.00', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('-1.00', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('1 unicorn', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('-1 unicorn', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var('+1 unicorn', FILTER_SANITIZE_NUMBER_INT));
var_dump(filter_var("!#$%&'*+-=?^_\`{|}~@.[]0123456789abcdefghijklmnopqrstuvwxyz", FILTER_SANITIZE_NUMBER_INT));
```

#### 第 46.6 节：净化 URL

移除字母、数字和 `$-_.+!*'(),{}|\\^~[]\`<>#%";/?:@&=` 以外的所有字符。

```php
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_SANITIZE_URL));
var_dump(filter_var("http://www.example.com/path/to/dir/index.php?test=y!#$%&'*+-=?^_\`{|}~.[]", FILTER_SANITIZE_URL));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=a b c', FILTER_SANITIZE_URL));
```

**结果：**

```
string(51) "http://www.example.com/path/to/dir/index.php?test=y"
string(72) "http://www.example.com/path/to/dir/index.php?test=y!#$%&'*+-=?^_\`{|}~.[]"
string(53) "http://www.example.com/path/to/dir/index.php?test=abc"
```

#### 第 46.7 节：验证电子邮件地址

| 函数 | 说明 |
| :--- | :--- |
| `filter_var` | 当过滤电子邮件地址时，`filter_var()` 将返回过滤后的数据（电子邮件地址），如果找不到有效的电子邮件地址则返回 `false`。 |

```php
var_dump(filter_var('john@example.com', FILTER_VALIDATE_EMAIL));
var_dump(filter_var('notValidEmail', FILTER_VALIDATE_EMAIL));
```

> **注意：** 此函数不验证非拉丁字符。国际化域名可以以其 punycode 形式进行验证。




请注意，在发送邮件之前，你无法知道邮箱地址是否正确。你可能想做一些额外的检查，例如检查 MX 记录，但这并非必要。如果你发送确认邮件，别忘了在短时间内删除未使用的账户。

#### 第 46.8 节：验证值是否为整数

### `filter_var`

当过滤一个应为整数的值时，`filter_var()` 将返回过滤后的数据（在此例中为整数），如果该值不是整数则返回 `false`。浮点数不属于整数：

```
var_dump(filter_var('10', FILTER_VALIDATE_INT));
var_dump(filter_var('a10', FILTER_VALIDATE_INT));
var_dump(filter_var('10a', FILTER_VALIDATE_INT));
var_dump(filter_var('', FILTER_VALIDATE_INT));
var_dump(filter_var('10.00', FILTER_VALIDATE_INT));
var_dump(filter_var('10,000', FILTER_VALIDATE_INT));
var_dump(filter_var('-5', FILTER_VALIDATE_INT));
var_dump(filter_var('+7', FILTER_VALIDATE_INT));
```

结果：

*(图片 `Image01063.jpg` 和 `Image01064.jpg` 已省略)*

如果你预期只有数字，可以使用正则表达式：

*(图片 `Image01065.jpg` 已省略)*

如果你将此值转换为整数，就不必进行此检查，因此可以使用 `filter_var`。

#### 第 46.9 节：验证整数是否落在某个范围内

验证整数是否落在某个范围内时，该检查包含最小值和最大值边界：

*(图片 `Image01066.jpg` 已省略)*

结果：

*(图片 `Image01067.jpg` 已省略)*

#### 第 46.10 节：验证 URL

### `filter_var`

当过滤 URL 时，`filter_var()` 将返回过滤后的数据（在此例中为 URL），如果找不到有效的 URL 则返回 `false`：

**URL：`example.com`**

```
var_dump(filter_var('example.com', FILTER_VALIDATE_URL));
var_dump(filter_var('example.com', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('example.com', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('example.com', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('example.com', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01069.jpg` 已省略)*

**URL：`http://example.com`**

```
var_dump(filter_var('http://example.com', FILTER_VALIDATE_URL));
var_dump(filter_var('http://example.com', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('http://example.com', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('http://example.com', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('http://example.com', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01071.jpg` 已省略)*

**URL：`http://www.example.com`**

```
var_dump(filter_var('http://www.example.com', FILTER_VALIDATE_URL));
var_dump(filter_var('http://www.example.com', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('http://www.example.com', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('http://www.example.com', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('http://www.example.com', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01073.jpg` 已省略)*

**URL：`http://www.example.com/path/to/dir/`**

```
var_dump(filter_var('http://www.example.com/path/to/dir/', FILTER_VALIDATE_URL));
var_dump(filter_var('http://www.example.com/path/to/dir/', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01075.jpg` 已省略)*

**URL：`http://www.example.com/path/to/dir/index.php`**

```
var_dump(filter_var('http://www.example.com/path/to/dir/index.php', FILTER_VALIDATE_URL));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01077.jpg` 已省略)*

**URL：`http://www.example.com/path/to/dir/index.php?test=y`**

```
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_VALIDATE_URL));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_VALIDATE_URL, FILTER_FLAG_SCHEME_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_VALIDATE_URL, FILTER_FLAG_HOST_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_VALIDATE_URL, FILTER_FLAG_PATH_REQUIRED));
var_dump(filter_var('http://www.example.com/path/to/dir/index.php?test=y', FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED));
```

结果：

*(图片 `Image01080.jpg` 已省略)*

> **警告**：你必须检查协议以防止 XSS 攻击：
>
> ```
> var_dump(filter_var('javascript://comment%0Aalert(1)', FILTER_VALIDATE_URL));
> // string(31) "javascript://comment%0Aalert(1)"
> ```

#### 第 46.11 节：清理浮点数

移除数字、`+-` 以及可选的 `.,eE` 以外的所有字符。

```
var_dump(filter_var(1, FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var(1.0, FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var(1.0000, FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var(1.00001, FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1.0', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1.0000', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1.00001', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1,000', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1,000.0', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1,000.0000', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1,000.00001', FILTER_SANITIZE_NUMBER_FLOAT));
var_dump(filter_var('1.8281e-009', FILTER_SANITIZE_NUMBER_FLOAT));
```

结果：

*(图片 `Image01083.jpg` 已省略)*

使用 `FILTER_FLAG_ALLOW_THOUSAND` 选项时：




#### 第 46.12 节：验证 IP 地址

验证一个值是否为有效的 IP 地址。

![](img/Image01089.jpg)
```
var_dump(filter_var('185.158.24.24', FILTER_VALIDATE_IP));
var_dump(filter_var('2001:0db8:0a0b:12f0:0000:0000:0000:0001', FILTER_VALIDATE_IP));
var_dump(filter_var('192.168.0.1', FILTER_VALIDATE_IP));
var_dump(filter_var('127.0.0.1', FILTER_VALIDATE_IP));
```
结果：

![](img/Image01090.jpg)

验证有效的 IPv4 IP 地址：

![](img/Image01091.jpg)
```
var_dump(filter_var('185.158.24.24', FILTER_VALIDATE_IP, FILTER_FLAG_IPV4));
var_dump(filter_var('2001:0db8:0a0b:12f0:0000:0000:0000:0001', FILTER_VALIDATE_IP, FILTER_FLAG_IPV4));
var_dump(filter_var('192.168.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_IPV4));
var_dump(filter_var('127.0.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_IPV4));
```
结果：

![](img/Image01092.jpg)

验证有效的 IPv6 IP 地址：

![](img/Image01093.jpg)
```
var_dump(filter_var('185.158.24.24', FILTER_VALIDATE_IP, FILTER_FLAG_IPV6));
var_dump(filter_var('2001:0db8:0a0b:12f0:0000:0000:0000:0001', FILTER_VALIDATE_IP, FILTER_FLAG_IPV6));
var_dump(filter_var('192.168.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_IPV6));
var_dump(filter_var('127.0.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_IPV6));
```
结果：

![](img/Image01094.jpg)

验证 IP 地址不在私有范围内：

![](img/Image01095.jpg)
```
var_dump(filter_var('185.158.24.24', FILTER_VALIDATE_IP, FILTER_FLAG_NO_PRIV_RANGE));
var_dump(filter_var('2001:0db8:0a0b:12f0:0000:0000:0000:0001', FILTER_VALIDATE_IP, FILTER_FLAG_NO_PRIV_RANGE));
var_dump(filter_var('192.168.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_NO_PRIV_RANGE));
var_dump(filter_var('127.0.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_NO_PRIV_RANGE));
```
结果：

![](img/Image01096.jpg)

验证 IP 地址不在保留范围内：

![](img/Image01097.jpg)
```
var_dump(filter_var('185.158.24.24', FILTER_VALIDATE_IP, FILTER_FLAG_NO_RES_RANGE));
var_dump(filter_var('2001:0db8:0a0b:12f0:0000:0000:0000:0001', FILTER_VALIDATE_IP, FILTER_FLAG_NO_RES_RANGE));
var_dump(filter_var('192.168.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_NO_RES_RANGE));
var_dump(filter_var('127.0.0.1', FILTER_VALIDATE_IP, FILTER_FLAG_NO_RES_RANGE));
```
结果：

![](img/Image01098.jpg)

#### 第 46.13 节：清理过滤器

我们可以使用过滤器根据需要清理变量。

##### 示例

![](img/Image01099.jpg)

以上代码将从 `$string` 变量中移除 HTML 标签。

## 第 47 章：生成器

#### 第 47.1 节：Yield 关键字

`yield` 语句类似于 `return` 语句，不同之处在于 `yield` 不会停止函数执行并返回，而是返回一个 [`Generator`](http://php.net/manual/en/class.generator.php) 对象并暂停生成器函数的执行。

下面是一个以生成器形式编写的 range 函数示例：

![](img/Image01100.jpg)

通过检查 `var_dump` 的输出，你可以看到该函数返回一个 [`Generator`](http://php.net/manual/en/class.generator.php) 对象：

![](img/Image01101.jpg)

### 生成值

然后可以像遍历数组一样遍历 [`Generator`](http://php.net/manual/en/class.generator.php) 对象。

![](img/Image01102.jpg)

以上示例将输出：

![](img/Image01103.jpg)

### 生成带键的值

除了生成值，还可以生成键/值对。

![](img/Image01104.jpg)

以上示例将输出：

![](img/Image01105.jpg)

#### 第 47.2 节：使用生成器读取大文件

生成器的一个常见用例是从磁盘读取文件并遍历其内容。下面是一个允许你遍历 CSV 文件的类。该脚本的内存使用量非常可预测，不会因 CSV 文件的大小而波动。

![](img/Image01106.jpg)

#### 第 47.3 节：为什么要使用生成器？

当你需要生成一个稍后要遍历的大型集合时，生成器非常有用。它们是创建实现 [`Iterator`](http://php.net/manual/en/class.iterator.php) 接口的类的更简单替代方案，后者往往大材小用。

例如，考虑下面的函数。

![](img/Image01107.jpg)

该函数所做的只是生成一个填充随机数字的数组。要使用它，我们可以调用 `randomNumbers(10)`，这将给我们一个包含 10 个随机数字的数组。如果我们要生成一百万个随机数字呢？`randomNumbers(1000000)` 可以做到，但会付出内存代价。在数组中存储一百万个整数大约使用 33 兆字节的内存。

![](img/Image01108.jpg)

这是因为一次性生成并返回了一百万个随机数字，而不是逐个生成。生成器是解决此问题的简便方法。

#### 第 47.4 节：使用 send() 函数向生成器传递值

`send()`




生成器编码快速，在许多情况下是繁重的迭代器实现的轻量级替代方案。随着快速实现而来的是，当生成器应该停止生成或应该生成其他内容时，控制力稍显不足。然而，这可以通过使用 `()` 函数来实现，使请求函数能够在每次循环后向生成器发送参数。

![](img/Image01109.jpg)

结果输出如下：

![](img/Image01110.jpg)

## 第 48 章：UTF-8

#### 第 48.1 节：输入

![](img/Image01111.jpg)在尝试存储或使用接收到的字符串之前，你应该验证每一个字符串是否为有效的 UTF-8。

| [mb_check_encoding](http://php.net/manual/en/function.mb-check-encoding.php) |
| --- |

PHP 的 `mb_check_encoding()` 可以完成这项工作，但你必须始终如一地使用它。这确实没有捷径，因为恶意客户端可以提交任何他们想要的编码的数据。

![](img/Image01112.jpg)

| accept | | \- | charset | 属性添加到你所有的 | `<form` |
| --- | --- | --- | --- | --- | --- |

以使用 UTF-8。唯一可靠的方法是像这样添加 `>` 标签：

![](img/Image01113.jpg)

#### 第 48.2 节：输出

| php | | . | ini | ，或手动发送 | Content | \- | Type |
| --- | --- | --- | --- | --- | --- | --- | --- |

![](img/Image01114.jpg)如果你的应用程序向其他系统传输文本，它们也需要知道字符编码。在 PHP 中，你可以在

中使用 `default_charset` 选项，或手动发送 MIME 头部。这是针对现代浏览器时的首选方法。

[HTML 元数据](http://stackoverflow.com/q/4696499/4245525) 。

![](img/Image01115.jpg)

![](img/Image01116.jpg)

#### 第 48.3 节：数据存储与访问

![](img/Image01117.jpg)本主题专门讨论 UTF-8 以及将其与数据库一起使用时的注意事项。如果你想了解更多关于在 PHP 中使用数据库的信息，请查看该主题。

在 MySQL 数据库中存储数据：

![](img/Image01118.jpg)在数据库的所有表和文本列上指定 `utf8mb4` 字符集。这使得 MySQL 以 UTF-8 原生编码物理存储和检索值。

| utf8mb4_ |
| --- |

![](img/Image01119.jpg)如果指定了 `*` 排序规则（不带任何显式字符集），MySQL 将隐式使用 `utf8mb4` 编码。

旧版本的 MySQL (< 5.5.3) 不支持 `utf8mb4`，因此你将被迫使用 `utf8`，它仅支持 Unicode 字符的一个子集。

在 MySQL 数据库中访问数据：

![](img/Image01120.jpg)在你的应用程序代码中（例如 PHP），无论你使用哪种数据库访问方法，都需要将连接字符集设置为 `utf8mb4`。这样，当 MySQL 将数据传递给你的应用程序时（反之亦然），不会从其原生 UTF-8 进行转换。

![](img/Image01121.jpg)某些驱动程序提供自己的机制来配置连接字符集，这既更新了其自身的内部状态，又通知 MySQL 连接上将使用的编码。这通常是首选方法。

例如（关于 `utf8mb4` / `utf8` 的相同考虑如上所述）：

如果你使用 [PDO](http://www.php.net/manual/en/book.pdo.php) 抽象层且 PHP ≥ 5.3.6，你可以在 [DSN](http://www.php.net/manual/en/ref.pdo-mysql.connection.php) 中指定字符集：

| [set_charset](http://www.php.net/manual/en/mysqli.set-charset.php) |
| --- |

```
$handle = new PDO('mysql:charset=utf8mb4');
```
如果你使用 [mysqli](http://www.php.net/manual/en/book.mysqli.php) ，可以调用 `mysqli_set_charset()` ：

```
$conn = mysqli_connect('localhost', 'my_user', 'my_password', 'my_db');
$conn->set_charset('utf8mb4');     // 面向对象风格
mysqli_set_charset($conn, 'utf8mb4'); // 过程化风格
```

![](img/Image01122.jpg)

如果你不得不使用旧版 [mysql](http://www.php.net/manual/en/book.mysql.php) 但碰巧运行 PHP ≥ 5.2.3，你可以调用 `mysql_set_charset()` 。

```
$conn = mysql_connect('localhost', 'my_user', 'my_password');
$conn->set_charset('utf8mb4');     // 面向对象风格
mysql_set_charset($conn, 'utf8mb4'); // 过程化风格
```

| [SET NAMES](http://dev.mysql.com/doc/en/charset-connection.html) ['utf8mb4'](http://dev.mysql.com/doc/en/charset-connection.html) |
| --- |

如果数据库驱动程序没有提供自己的机制来设置连接字符集，你可能不得不发出一个查询来告诉 MySQL 你的应用程序期望连接上的数据如何编码： .

## 第 49 章：PHP 中的 Unicode 支持

#### 第 49.1 节：使用 PHP 将 Unicode 字符转换为 “\uxxxx” 格式

你可以使用以下代码进行双向转换。

![](img/Image01123.jpg)

用法：

![](img/Image01124.jpg)

输出：

![](img/Image01125.jpg)

#### 第 49.2 节：使用 PHP 将 Unicode 字符转换为其数值和/或 HTML 实体

你可以使用以下代码进行双向转换。

![](img/Image01126.jpg)

![](img/Image01127.jpg)

用法：

![](img/Image01128.jpg)

输出：

![](img/Image01129.jpg)

![](img/Image01130.jpg)

#### 第 49.3 节：用于 Unicode 支持的 Intl 扩展

原生字符串函数映射到单字节函数，它们不能很好地处理 Unicode。`iconv` 和 `mbstring` 扩展为 Unicode 提供了一些支持，而 `Intl` 扩展提供完整支持。`Intl` 是事实标准 ICU 库的封装，详细信息请参阅 [`site.icu-project.org`](http://site.icu-project.org/) ，这些信息在 [`php.net/manual/en/book.intl.php`](http://php.net/manual/en/book.intl.php) 上不可用。如果你无法安装该扩展，请查看 [Symfony 框架提供的 Intl 替代实现](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) [an alternative](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) [implementation of Intl from the Symfony framework](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) 。

ICU 提供完整的国际化支持，Unicode 只是其中较小的一部分。你可以轻松进行转码：

![](img/Image01131.jpg)
```
\UConverter::transcode($sString, 'UTF-8', 'UTF-8');  // 针对攻击剥离坏字节
```

但是，不要轻易放弃 `iconv`，请考虑：

![](img/Image01132.jpg)

## 第 50 章：URL

#### 第 50.1 节：解析 URL

| [parse_url](http://php.net/parse_url) |
| --- |

要将 URL 分离为各个组成部分，请使用 `parse_url()` ：

![](img/Image01133.jpg)

执行上述代码后，`$parts` 的内容将为：

![](img/Image01134.jpg)

你也可以选择性地仅返回 URL 的一个组件。仅返回查询字符串：

![](img/Image01135.jpg)

接受以下任意常量：`PHP_URL_SCHEME` 、`PHP_URL_HOST` 、`PHP_URL_PORT` 、`PHP_URL_USER` 、`PHP_URL_PASS` 、`PHP_URL_PATH` 、`PHP_URL_QUERY` 和 `PHP_URL_FRAGMENT` 。

| [parse_str](http://php.net/parse_str) |
| --- |

要进一步将查询字符串解析为键值对，请使用 `parse_str()` ：

![](img/Image01136.jpg)

执行上述代码后，`$params` 数组将填充以下内容：

![](img/Image01137.jpg)

#### 第 50.2 节：从数组构建 URL 编码的查询字符串

| [http_build_query](http://php.net/manual/function.http-build-query.php) |
| --- |

`http_build_query()` 将从数组或对象创建查询字符串。这些字符串可以附加到 URL 以创建 GET 请求，或用于 POST 请求（例如配合 cURL）。

![](img/Image01138.jpg)

`$queryString` 将具有以下值：

![](img/Image01139.jpg)

![](img/Image01140.jpg)

![](img/Image01141.jpg)

这是以下内容的 URL 编码版本：

![](img/Image01142.jpg)

#### 第 50.3 节：重定向到另一个 URL

| header |
| --- |



## 第 51 章：如何拆解 URL

在编写 PHP 代码时，你很可能会遇到需要将 URL 拆分为若干部分的情况。显然，根据你的需求，有不止一种方法可以实现。本文将为你解释这些方法，以便你找到最适合你的方案。

#### 第 51.1 节：使用 `parse_url()`

你可以使用 `header()` 函数指示浏览器重定向到不同的 URL：

```
header("Location: http://www.example.com/"); /* 重定向浏览器 */
exit;
```

你也可以重定向到相对 URL（这不属于官方 HTTP 规范的一部分，但在所有浏览器中均可工作）：

```
header("Location: /path/to/page.php"); /* 重定向浏览器 */
exit;
```

如果头部信息已发送，你可以选择发送一个 meta refresh HTML 标签。

> **警告**：meta refresh 标签依赖于客户端正确处理 HTML，但某些客户端不会这样做。通常，它仅在 Web 浏览器中有效。此外，请考虑到如果头部信息已发送，你可能存在一个 Bug，这应该触发一个异常。

你也可以为用户打印一个可点击的链接，以供忽略 meta refresh 标签的客户端使用：

```php
$saveUrl = htmlspecialchars($url); // 防止浏览器将 url 视为 HTML
// 告诉浏览器在 0 秒后将页面重定向到 $saveUrl
print '<meta http-equiv="refresh" content="0; url=' . $saveUrl . '">' ;
// 为用户显示链接
print '<p>Please continue to <a href="' . $saveUrl . '">' . $saveUrl . '</a></p>' ;
exit;
```

如果你需要分离路径，可以使用 `explode()`：

```php
$url = 'http://username:password@hostname:9090/path/to/resource?arg=value#anchor';
$parts = parse_url($url);
print_r($parts);
```

如果你需要路径的最后一部分，可以像这样使用 `end()`：

```php
$path = $parts['path']; // /path/to/resource
$segments = explode('/', $path);
$lastSegment = end($segments); // resource
```

如果 URL 包含 GET 变量，你也可以检索它们：

```php
$query = $parts['query']; // arg=value
parse_str($query, $vars);
print_r($vars); // Array ( [arg] => value )
```

如果你想拆解查询变量，可以像这样使用 `parse_str()`：

```php
$str = "first=value&arr[]=foo+bar&arr[]=baz";
parse_str($str, $output);
print_r($output);
```

#### 第 51.2 节：使用 `explode()`

`explode()`：返回一个字符串数组，每个元素是由 string delimiter 分隔形成的字符串的子串。

此函数非常直观。

```php
$url = "http://www.example.com/path/to/page.php";
$parts = explode('/', $url);
print_r($parts);
```

你可以通过以下方式获取 URL 的最后一部分：

```php
$lastPart = end($parts); // page.php
```

你也可以结合 `sizeof()` 和数学运算符在数组中导航，如下所示：

```php
$secondToLast = $parts[sizeof($parts) - 2]; // to
```

#### 第 51.3 节：使用 `basename()`

`basename()`：给定一个包含文件或目录路径的字符串，此函数将返回路径中的文件名部分。

此函数将仅返回 URL 的最后一部分：

```php
$url = "http://www.example.com/path/to/page.php";
$file = basename($url); // page.php
```

```php
$url = "http://www.example.com/path/to/page.php?arg=value";
$file = basename($url); // page.php?arg=value
```

如果你的 URL 包含更多内容，而你需要的是包含文件的目录名，可以结合 `dirname()` 这样使用：

```php
$url = "http://www.example.com/path/to/page.php";
$dir = dirname($url); // http://www.example.com/path/to
```

## 第 52 章：对象序列化

#### 第 52.1 节：Serialize / Unserialize

| 函数 | 说明 |
| --- | --- |
| `serialize()` | 返回一个字符串，包含了可以在 PHP 中存储的任意值的字节流表示。 |
| `unserialize()` | 可以使用该字符串重新创建原始的变量值。 |

序列化一个对象：

```php
$serialized = serialize($object);
```

反序列化一个对象：

```php
$object = unserialize($serialized);
```

示例：

```php
class A {
    public $var = 'value';
}
$obj = new A();
$serialized = serialize($obj);
echo $serialized; // O:1:"A":1:{s:3:"var";s:5:"value";}
$unserialized = unserialize($serialized);
var_dump($unserialized);
```

#### 第 52.2 节：`Serializable` 接口

##### 简介

| 方法 | 说明 |
| --- | --- |
| `__sleep()` | |
| `__wakeup()` | |
| `__destruct()` | |
| `unserialize()` | |
| `__construct()` | |

实现此接口的类将不再支持 `__sleep()` 和 `__wakeup()`。每当一个实例需要被序列化时，`serialize()` 方法会被调用。除非在方法内部编程，否则这不会调用 `__sleep()` 或产生任何其他副作用。当数据被反序列化时，类是已知的，并且会调用适当的 `unserialize()` 方法作为构造函数，而不是调用 `__construct()`。如果你需要执行标准构造函数，可以在该方法中进行。

基本用法：

```php
class MyClass implements Serializable {
    private $data;

    public function __construct($data) {
        $this->data = $data;
    }

    public function serialize() {
        return serialize($this->data);
    }

    public function unserialize($data) {
        $this->data = unserialize($data);
    }
}
```

```php
$obj = new MyClass('some data');
$serialized = serialize($obj);
$unserialized = unserialize($serialized);
```

## 第 53 章：序列化

##### 参数详情

要序列化的值。`serialize()` 处理所有类型，除了 `resource` 类型。你甚至可以 `serialize()` 包含对自身引用的数组。你正在序列化的数组/对象中的循环引用也将被存储。任何其他引用将会丢失。序列化对象时，PHP 会尝试在序列化前调用成员函数 `__sleep()`。这是为了允许对象在被序列化前进行任何最后时刻的清理工作等。同样地，当使用 `unserialize()` 恢复对象时，会调用 `__wakeup()` 成员函数。对象的私有成员会在成员名前加上类名；受保护成员会在成员名前加上 `'*'`。这些前缀值的两侧都有空字节。

#### 第 53.1 节：不同类型的序列化

生成一个值的可存储表示。

这对于在不丢失类型和结构的情况下存储或传递 PHP 值非常有用。

要将序列化字符串转回 PHP 值，请使用 `unserialize()`。

```php
$double = 1.5;
echo serialize($double); // d:1.5;
```

序列化浮点数：

```php
$float = 1.5;
echo serialize($float); // d:1.5;
```

```php
$int = 123;
echo serialize($int); // i:123;
```

```php
$string = 'hello';
echo serialize($string); // s:5:"hello";
```

```php
$array = array('a', 'b', 'c');
echo serialize($array); // a:3:{i:0;s:1:"a";i:1;s:1:"b";i:2;s:1:"c";}
```

你也可以序列化对象。

序列化对象时，PHP 会尝试在序列化前调用成员函数 `__sleep()`。这是为了允许对象在被序列化前进行任何最后时刻的清理工作等。同样地，当使用 `unserialize()` 恢复对象时，会调用 `__wakeup()` 成员函数。

```php
class Test {
    public $prop = 'value';
}
$obj = new Test();
echo serialize($obj); // O:4:"Test":1:{s:4:"prop";s:5:"value";}
```

请注意，闭包不能被序列化：

```php
$closure = function() {};
echo serialize($closure); // Fatal error: Uncaught Exception: Serialization of 'Closure' is not allowed
```

#### 第 53.2 节：`unserialize` 的安全问题

使用 `unserialize` 函数反序列化来自用户输入的数据可能很危险。

### php.net 的警告

> **警告**：请勿将不可信的用户输入传递给 `unserialize()`。反序列化可能导致由于对象实例化和自动加载而加载并执行代码，恶意用户可能会利用这一点。如果你需要向用户传递序列化数据，请使用安全的标准数据交换格式，如 JSON（通过 `json_decode()` 和 `json_encode()`）。

### 可能的攻击

#### PHP 对象注入

PHP 对象注入是一种应用层漏洞，可能允许攻击者执行不同类型的恶意攻击，例如代码注入、SQL 注入、路径遍历和应用层拒绝服务，具体取决于上下文。当用户提供的输入在传递给 `unserialize()` PHP 函数之前未经过适当清理时，就会发生此漏洞。由于 PHP 允许对象序列化，攻击者可能将临时序列化字符串传递给易受攻击的 `unserialize()` 调用，导致任意 PHP 对象被注入到应用程序作用域中。

要成功利用 PHP 对象注入漏洞，必须满足两个条件：

| 条件 | 说明 |
| --- | --- |
| `unserialize()` | 应用程序必须有一个实现了 PHP 魔术方法（如 `__wakeup` 或 `__destruct`）的类，该方法可用于发动恶意攻击，或启动“POP 链”。 |
| 类可用性 | 攻击期间使用的所有类必须在调用易受攻击的 `unserialize()` 时已声明，否则必须支持这些类的对象自动加载。 |

#### 示例 1 - 路径遍历攻击

下面的示例展示了一个包含可利用的 `__destruct` 方法的 PHP 类：

```php
class Example1 {
    public $cache_file;

    public function __destruct() {
        unlink($this->cache_file);
    }
}
```

在本例中，攻击者可能通过路径遍历攻击删除任意文件，例如请求以下 URL：

```
http://testsite.com/vuln.php?data=O:8:"Example1":1:{s:10:"cache_file";s:15:"../../index.php";}
```

#### 示例 2 - 代码注入攻击




下面的示例展示了一个包含可利用的 `__wakeup` 方法的 PHP 类：

```
![](img/Image01179.jpg)
```

在这个示例中，攻击者可能能够通过发送如下 HTTP 请求来执行代码注入攻击：

```
![](img/Image01180.jpg)
```

其中 Cookie 参数 "data" 是由以下脚本生成的：

```
![](img/Image01181.jpg)
```

## 第 54 章：闭包

#### 第 54.1 节：闭包的基本用法

闭包是 PHP 中匿名函数的等价物，即没有名称的函数。即使从技术上讲这并不完全正确，但闭包的行为与函数保持一致，只是增加了一些额外功能。

闭包只不过是通过声明一个没有名称的函数而创建的 `Closure` 类的对象。例如：

```
![](img/Image01182.jpg)
```

请记住 `$myClosure` 是 `Closure` 的一个实例，这样您就知道实际上可以对它做什么（参见 [`fr2.php.net/manual/en/class.closure.php`](http://fr2.php.net/manual/en/class.closure.php)）。

您需要 `Closure` 的经典场景是当您必须给一个函数传递一个可调用对象时，例如 `usort`。

下面是一个按每个人兄弟姐妹数量对数组进行排序的示例：

```
![](img/Image01183.jpg)
```

#### 第 54.2 节：使用外部变量

可以在闭包内部使用特殊关键字 `use` 来使用外部变量。例如：

```
![](img/Image01184.jpg)
```

```
![](img/Image01185.jpg)
```

您可以通过创建“动态”闭包来进一步扩展。可以创建一个函数，根据您想要添加的数量返回一个特定的计算器。例如：

```
![](img/Image01186.jpg)
```

#### 第 54.3 节：基本闭包绑定

如前所述，闭包只不过是 `Closure` 类的一个实例，可以在它们上面调用不同的方法。其中之一是 `bindTo`，给定一个闭包，它将返回一个绑定到给定对象的新闭包。例如：

```
![](img/Image01187.jpg)
```

#### 第 54.4 节：闭包绑定与作用域

让我们考虑这个例子：

```
![](img/Image01188.jpg)
```

```
![](img/Image01189.jpg)
```

尝试将属性可见性更改为 `protected` 或 `private`。您会得到一个致命错误，提示您无法访问此属性。确实，即使闭包已绑定到该对象，但调用闭包的作用域并不是获得该访问权限所需的作用域。这就是 `bindTo` 的第二个参数的作用。

只有当从允许访问的作用域（即类的作用域）访问私有属性时，才能访问它。在刚才的代码示例中，未指定作用域，这意味着闭包是在创建闭包时所用的相同作用域中被调用的。让我们改变这一点：

```
![](img/Image01190.jpg)
```

正如刚才所说，如果不使用此第二个参数，则闭包是在创建闭包时所用的相同上下文中被调用的。例如，在类的方法内部创建并在对象上下文中调用的闭包将具有与该方法相同的作用域：

```
![](img/Image01191.jpg)
```

```
![](img/Image01192.jpg)
```

#### 第 54.5 节：为单次调用绑定闭包

自 PHP 7 起，可以通过 `call` 方法仅为一次调用绑定闭包。例如：

```
![](img/Image01193.jpg)
```

与 `bindTo` 方法不同，无需担心作用域。此次调用使用的作用域与访问或调用 `$myInstance` 的属性时使用的作用域相同。

#### 第 54.6 节：使用闭包实现观察者模式

通常，观察者是一个具有特定方法的类，当被观察对象上发生动作时会调用该方法。在某些情况下，闭包足以实现观察者设计模式。

下面是此类实现的详细示例。首先声明一个类，其目的是在其属性发生变化时通知观察者。

```
![](img/Image01194.jpg)
```

```
![](img/Image01195.jpg)
```

然后，声明将代表不同观察者的类。

```
![](img/Image01196.jpg)
```

最后，让我们测试一下：

```
![](img/Image01197.jpg)
```

```
![](img/Image01198.jpg)
```

请注意，此示例之所以有效，是因为观察者具有相同的性质（它们都是“命名观察者”）。

## 第 55 章：读取请求数据

#### 第 55.1 节：读取原始 POST 数据

通常，POST 请求中发送的数据是结构化的键/值对，MIME 类型为 `application/x-www-form-urlencoded`。然而，许多应用程序（如 Web 服务）要求发送原始数据，通常采用 XML 或 JSON 格式。可以使用以下两种方法之一来读取此数据。

`php://input` 是一个提供对原始请求主体访问权限的流。

```
![](img/Image01199.jpg)
```

**版本 < 5.6**

`$HTTP_RAW_POST_DATA` 是一个包含原始 POST 数据的全局变量。仅当 `php.ini` 中的 `always_populate_raw_post_data` 指令启用时才可用。

```
![](img/Image01200.jpg)
```

自 PHP 5.6 版本起，此变量已被弃用，并在 PHP 7.0 中被移除。

请注意，当内容类型设置为 `multipart/form-data`（用于文件上传）时，这两种方法均不可用。

#### 第 55.2 节：读取 POST 数据

POST 请求的数据以关联数组的形式存储在 [超全局变量](http://php.net/manual/en/language.variables.superglobals.php) `$_POST` 中。

请注意，访问不存在的数组项会产生通知，因此应始终使用 `isset()` 或 `empty()` 函数，或空合并运算符来检查是否存在。

示例：

```
![](img/Image01201.jpg)
```

**版本 ≥ 7.0**

```
![](img/Image01202.jpg)
```

#### 第 55.3 节：读取 GET 数据

GET 请求的数据以关联数组的形式存储在 [超全局变量](http://php.net/manual/en/language.variables.superglobals.php) `$_GET` 中。

请注意，访问不存在的数组项会产生通知，因此应始终使用 `isset()` 或 `empty()` 函数，或空合并运算符来检查是否存在。

示例：（针对 URL `/topics.php?author=alice&topic=php`）

```
![](img/Image01203.jpg)
```

**版本 ≥ 7.0**

```
![](img/Image01204.jpg)
```

#### 第 55.4 节：处理文件上传错误

`$_FILES["FILE_NAME"]['error']`（其中 "FILE_NAME" 是表单中文件输入的 name 属性的值）可能包含以下值之一：

1.  **UPLOAD_ERR_OK** - 没有错误，文件上传成功。
2.  **UPLOAD_ERR_INI_SIZE** - 上传的文件超过了 `php.ini` 中的 `upload_max_filesize` 指令。
3.  **UPLOAD_ERR_PARTIAL** - 上传的文件超过了 HTML 表单中指定的 `MAX_FILE_SIZE` 指令。
4.  **UPLOAD_ERR_NO_FILE** - 没有文件被上传。
5.  **UPLOAD_ERR_NO_TMP_DIR** - 缺少临时文件夹。（PHP 5.0.3 起）。
6.  **UPLOAD_ERR_CANT_WRITE** - 无法将文件写入磁盘。（PHP 5.1.0 起）。
7.  **UPLOAD_ERR_EXTENSION** - PHP 扩展阻止了文件上传。（PHP 5.2.0 起）。

检查错误的基本方法如下：

```
![](img/Image01205.jpg)
```

#### 第 55.5 节：通过 POST 传递数组

通常，提交给 PHP 的 HTML 表单元素会产生单个值。例如：

```
![](img/Image01206.jpg)
```

```
![](img/Image01207.jpg)
```

这将产生以下输出：

```
![](img/Image01208.jpg)
```

但是，有时您可能想要传递一个值数组。这可以通过向 HTML 元素的名称添加类似 PHP 的后缀来完成：

```
![](img/Image01209.jpg)
```

这将产生以下输出：

```
![](img/Image01210.jpg)
```

您也可以指定数组索引，无论是数字还是字符串：

```
![](img/Image01211.jpg)
```





这将返回以下输出：

![](img/Image01212.jpg)

此技术可用于避免对 `$_POST` 数组进行后处理循环，使您的代码更精简、更简洁。

#### 第 55.6 节：使用 HTTP PUT 上传文件

[PHP 提供支持](http://php.net/manual/en/features.file-upload.put-method.php)某些客户端用于在服务器上存储文件的 HTTP PUT 方法。PUT 请求比使用 POST 请求的文件上传简单得多，它们看起来类似这样：

![](img/Image01213.jpg)

在您的 PHP 代码中，您可以这样做：

![](img/Image01214.jpg)

此外，[这里](http://stackoverflow.com/questions/12005790/how-to-receive-a-file-via-http-put-with-php) 您可以阅读关于通过 HTTP PUT 接收文件的有趣 SO 问答。

## 第 56 章：类型转换与非严格比较问题

#### 第 56.1 节：什么是类型转换？

PHP 是一门弱类型语言。这意味着，默认情况下，它不要求表达式中的操作数类型相同（或兼容）。例如，您可以将数字追加到字符串后面，并期望它能正常工作。

![](img/Image01215.jpg)

输出将为：

![](img/Image01216.jpg) string(24) "This is example number 1"

PHP 通过自动将不兼容的变量类型转换为允许执行请求操作的类型来实现这一点。在上述情况下，它会将整数字面量 `1` 转换为字符串，从而使其可以连接到前面的字符串字面量上。这被称为类型转换。这是 PHP 一个非常强大的功能，但如果您不了解它，也可能导致您拔光头发，甚至引发安全问题。

请看下面的例子：

![](img/Image01217.jpg)

其意图似乎是程序员正在检查变量是否具有值 `1`。但如果 `$variable` 的值是 `"1 and a half"` 会怎样？答案可能会让您感到惊讶。

![](img/Image01218.jpg)

结果是：

![](img/Image01219.jpg) bool(true)

为什么会发生这种情况？因为 PHP 意识到字符串 `"1 and a half"` 不是整数，但为了将其与整数 `1` 进行比较，它需要是整数。PHP 不会报错，而是启动类型转换并尝试将变量转换为整数。它通过获取字符串开头所有可以转换为整数的字符并进行转换来实现这一点。一旦遇到无法作为数字处理的字符，就会停止。因此 `"1 and a half"` 被转换为整数 `1`.

诚然，这是一个非常牵强的例子，但它用于演示该问题。接下来的几个例子将涵盖我在真实软件中遇到的由类型转换引起的一些错误情况。

#### 第 56.2 节：从文件读取

当从文件读取时，我们想知道何时到达了文件末端。已知 `fgets()` 在文件末端返回 `false`，我们可能会将其用作循环的条件。然而，如果最后一次读取返回的数据恰好是某个评估为布尔值 `false` 的值，会导致我们的文件读取循环过早终止。

![](img/Image01220.jpg)

如果被读取的文件包含空行，`while` 循环将在该处终止，因为空字符串评估为布尔值 `false`。

相反，我们可以使用严格相等运算符显式检查布尔值 `false`：

![](img/Image01221.jpg)

注意这是一个牵强的例子；在实际生活中，我们会使用以下循环：

![](img/Image01222.jpg)

或者用以下代码替换整个内容：

![](img/Image01223.jpg)

#### 第 56.3 节：Switch 语句的惊喜

Switch 语句使用非严格比较来确定匹配。这可能导致一些 [令人不快的惊喜](http://stackoverflow.com/questions/4098104/odd-behaviour-in-a-switch-statement)。例如，考虑以下语句：

![](img/Image01224.jpg)

这是一个非常简单的语句，当 `$name` 是字符串时按预期工作，但在其他情况下可能会导致问题。

例如，如果 `$name` 是整数 `0`，则比较期间会发生类型转换。然而，被转换的是 `case` 语句中的字面量值，而不是 `switch` 语句中的条件。字符串 `"input 1"` 被转换为整数 `0`，这与输入值整数 `0` 匹配。结果是，如果您提供整数 `0` 的值，第一个 `case` 总是会执行。

此问题有几种解决方案：

**显式转换**

可以在比较前将值转换为字符串：

![](img/Image01225.jpg)

或者也可以使用已知返回字符串的函数：

![](img/Image01226.jpg)

这两种方法都能确保值的类型与 `case` 语句中的值类型相同。

**避免使用 switch**

使用 `if` 语句将使我们能够控制比较的方式，从而允许我们使用严格比较运算符：

![](img/Image01227.jpg)

#### 第 56.4 节：严格类型

自 PHP 7.0 起，可以通过 [严格类型](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict) 缓解类型转换的一些有害影响。通过将此 `declare` 语句作为文件的第一行包含进来，PHP 将通过抛出 `TypeError` 异常来强制执行参数类型声明和返回类型声明。

![](img/Image01228.jpg)

例如，这段使用参数类型定义的代码在运行时将抛出一个可捕获的 `TypeError` 类型异常：

![](img/Image01229.jpg)

同样，这段代码使用了返回类型声明；如果它尝试返回除整数以外的任何内容，也将抛出异常：

![](img/Image01230.jpg)

## 第 57 章：Sockets

#### 第 57.1 节：TCP 客户端 Socket

创建一个使用 TCP（传输控制协议）的 socket

```
$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
```

确保 socket 成功创建。`onSocketFailure` 函数来自本主题中的处理 socket 错误示例。

```
if (!is_resource($socket)) onSocketFailure("Failed to create socket");
```

将 socket 连接到指定地址。如果连接失败，第二行将优雅地处理失败。

```
socket_connect($socket, "chat.stackoverflow.com", 6667)
    or onSocketFailure("Failed to connect to chat.stackoverflow.com:6667", $socket);
```

向服务器发送数据

`socket_write` 函数通过 socket 发送字节。在 PHP 中，字节数组由字符串表示，通常不区分编码。

![](img/Image01234.jpg)

从服务器接收数据

以下片段使用 `socket_read` 函数从服务器接收一些数据。

将 `PHP_NORMAL_READ` 作为第三个参数传递，将读取直到遇到 `\r` / `\n` 字节，且该字节包含在返回值中。

相反，传递 `PHP_BINARY_READ` 将从流中读取所需数量的数据。

如果之前调用了 `socket_set_nonblock` 且使用了 `PHP_BINARY_READ`，`socket_read` 将立即返回 `false`。否则，该方法将阻塞，直到接收到足够的数据（达到第二个参数中的长度，或达到行尾），或 socket 关闭。

此示例从假设的 IRC 服务器读取数据。

![](img/Image01235.jpg)

关闭 Socket

关闭 socket 将释放 socket 及其相关资源。

![](img/Image01236.jpg)

#### 第 57.2 节：TCP 服务端 Socket

Socket 创建

创建一个使用 TCP 的 socket。这与创建客户端 socket 相同。

![](img/Image01237.jpg)

Socket 绑定

将来自给定网络（参数 2）的特定端口（参数 3）的连接绑定到 socket。

第二个参数通常是 `"0.0.0.0"`，它接受来自所有网络的连接。它也可以





![](img/Image01238.jpg)

`socket_bind` 报错的一个常见原因是[指定的地址已绑定到另一个进程](https://www.google.com.hk/search?q=site%3Astackexchange.com%20OR%20site%3Astackoverflow.com%20kill%20processes%20bound%20to%20address)。通常会终止其他进程（通常是手动终止，以防止意外终止关键进程），以便释放套接字。

```
socket_bind($socket, "0.0.0.0", 6667) or onSocketFailure("Failed to bind to 0.0.0.0:6667");
```

### 设置套接字监听

使用 `socket_listen` 使套接字监听传入的连接。第二个参数是在连接被接受之前允许排队的最大连接数。

![](img/Image01239.jpg)

```
socket_listen($socket, 5);
```

### 处理连接

TCP 服务器实际上是处理子连接的服务器。`socket_accept` 会创建一个新的子连接。

![](img/Image01240.jpg)

来自 `socket_accept` 的连接的数据传输与 TCP 客户端套接字的数据传输相同。

```
socket_close($conn);
```

当需要关闭此连接时，直接调用 `socket_close($conn);`。这不会影响原始的 TCP 服务器套接字。

### 关闭服务器

```
socket_close($socket);
```

另一方面，当服务器不再使用时，应调用 `socket_close($socket);`。这也会释放 TCP 地址，允许其他进程绑定到该地址。

#### 第 57.3 节：UDP 服务器套接字

UDP（用户数据报协议）服务器与 TCP 不同，不是基于流的。它是基于数据包的，即客户端以“数据包”为单位向服务器发送数据，并通过客户端的地址来识别客户端。没有内置函数关联来自同一客户端的不同数据包（与 TCP 不同，TCP 中来自同一客户端的数据由 `socket_accept` 创建的特定资源处理）。可以将其视为每当一个 UDP 数据包到达时，都会接受并关闭一个新的 TCP 连接。

### 创建 UDP 服务器套接字

![](img/Image01241.jpg)

### 将套接字绑定到地址

参数与 TCP 服务器相同。

![](img/Image01242.jpg)

```
socket_bind($socket, $address, $port);
```

### 发送数据包

此行将 `$data` 作为 UDP 数据包发送到 `$address:$port`。

![](img/Image01243.jpg)

```
socket_sendto($socket, $data, strlen($data), 0, $address, $port);
```

### 接收数据包

以下代码片段尝试以客户端索引的方式管理 UDP 数据包。

![](img/Image01244.jpg)

### 关闭服务器

`socket_close` 可用于 UDP 服务器套接字资源。这将释放 UDP 地址，允许其他进程绑定到该地址。

#### 第 57.4 节：处理套接字错误

`socket_last_error` 可用于获取套接字扩展中最后一个错误的错误 ID。`socket_strerror` 可用于将 ID 转换为人类可读的字符串。

![](img/Image01245.jpg)

## 第 58 章：PDO

[PDO](http://php.net/manual/en/book.pdo.php)（PHP 数据对象）扩展允许开发者连接到多种不同类型的数据库，并以统一的、面向对象的方式对它们执行查询。

#### 第 58.1 节：使用参数化查询防止 SQL 注入

SQL 注入是一种允许恶意用户修改 SQL 查询、向其中添加不需要的命令的攻击。例如，以下代码是脆弱的：

![](img/Image01246.jpg)

这允许该脚本的任何用户基本上随意修改我们的数据库。例如考虑以下查询字符串：

![](img/Image01247.jpg)

这会使我们的示例查询变成这样：

![](img/Image01248.jpg)

```
SELECT name, email, user_level FROM users WHERE userID = 0; TRUNCATE TABLE users;
```

虽然这是一个极端的例子（大多数 SQL 注入攻击并不旨在删除数据，而且大多数 PHP 查询执行函数不支持多查询），但这展示了由于查询组装不当，SQL 注入攻击是如何成为可能的。不幸的是，此类攻击非常常见，并且由于程序员未能采取适当的预防措施来保护数据，其效果极佳。

为了防止 SQL 注入的发生，预处理语句是推荐的解决方案。不直接将用户数据拼接到查询中，而是使用占位符。然后单独发送数据，这意味着 SQL 引擎没有机会将用户数据与一组指令混淆。

![](img/Image01249.jpg)

> 虽然此处的主题是 PDO，但请注意 PHP MySQLi 扩展也支持预处理语句。

PDO 支持两种占位符（占位符不能用于列名或表名，仅用于值）：

### 1. 命名占位符

一个冒号（`:`），后跟一个唯一的名称（例如 `:user`）。

```php
// 使用命名占位符
$sql = 'SELECT name, email, user_level FROM users WHERE userID = :user';
$prep = $conn->prepare($sql);
$prep->execute(['user' => $_GET['user']]); // 关联数组
$result = $prep->fetchAll();
```

### 2. 传统 SQL 位置占位符

表示为 `?`。

```php
// 使用问号占位符
$sql = 'SELECT name, user_level FROM users WHERE userID = ? AND user_level = ?';
$prep = $conn->prepare($sql);
$prep->execute([$_GET['user'], $_GET['user_level']]); // 索引数组
```

![](img/Image01252.jpg)

如果您确实需要动态更改表名或列名，请知晓这存在安全风险且属于不良实践。尽管如此，可以通过字符串拼接来完成。提高此类查询安全性的一种方法是设置一个允许值的表，并将要拼接的值与该表进行比较。

请注意，重要的是仅通过 DSN 设置连接字符集，否则如果使用了某些奇特的编码，您的应用程序可能容易受到[一个隐蔽的漏洞](https://stackoverflow.com/questions/134099/are-pdo-prepared-statements-sufficient-to-prevent-sql-injection/12202218#12202218)的影响。对于 5.3.6 之前的 PDO 版本，无法通过 DSN 设置字符集，因此唯一的选择是在连接创建后立即将 `PDO::ATTR_EMULATE_PREPARES` 属性设置为 false。

![](img/Image01253.jpg)

这会导致 PDO 使用底层 DBMS 的原生预处理语句，而不仅仅是模拟它。

但是，请注意 PDO 会[静默回退](https://github.com/php/php-src/blob/master/ext/pdo_mysql/mysql_driver.c#L210)到模拟 MySQL 无法原生预处理的语句：它能原生预处理的语句[在手册中列出](http://dev.mysql.com/doc/en/sql-syntax-prepared-statements.html)([来源](https://stackoverflow.com/questions/134099/are-pdo-prepared-statements-sufficient-to-prevent-sql-injection/12202218#12202218))。

#### 第 58.2 节：基本 PDO 连接与检索

自 PHP 5.0 起，[PDO](http://php.net/manual/en/intro.pdo.php) 作为数据库访问层可用。它与数据库无关，因此以下连接示例代码只需更改 DSN 即可适用于其[任何支持的数据库](http://php.net/manual/en/pdo.drivers.php)。

![](img/Image01254.jpg)

[`prepare`](http://php.net/manual/en/pdo.prepare.php) 函数从查询字符串创建一个 `PDOStatement` 对象。查询的执行和结果的检索在此返回的对象上执行。如果失败，该函数根据 PDO 连接的配置，要么返回 false，要么抛出异常。

#### 第 58.3 节：使用 PDO 进行数据库事务

数据库事务确保仅当每条语句都成功时，一组数据更改才会永久生效。事务期间发生的任何查询或代码失败都可以被捕获，随后您可以选择回滚尝试的更改。

PDO 提供了用于开始、提交和回滚事务的简单方法。

![](img/Image01255.jpg)

在事务期间进行的任何数据更改仅对活动连接可见。即使更改尚未提交到数据库，`SELECT` 语句也会返回更改后的数据。




> **注意：** 请参阅数据库供应商文档以了解事务支持的详细信息。某些系统完全不支持事务。某些支持嵌套事务，而其他系统则不支持。

# 使用 PDO 进行事务处理的实际示例

以下部分演示了一个实际的真实场景，其中事务的使用确保了数据库的一致性。

想象一下以下场景，假设你正在为一个电子商务网站构建购物车，并决定将订单保存在两个数据库表中。一个名为 `orders`，包含字段 `order_id`、`name`、`address`、`telephone` 和 `created_at`。另一个名为 `orders_products`，包含字段 `order_id`、`product_id` 和 `quantity`。第一个表包含订单的元数据，而第二个表包含实际订购的产品。

## 向数据库插入新订单

要向数据库插入新订单，你需要做两件事。首先，你需要向 `orders` 表 `INSERT` 一条新记录，该记录将包含订单的元数据（`name`、`address` 等）。然后，你需要为订单中包含的每个产品，向 `orders_products` 表 `INSERT` 一条记录。

你可以通过执行类似以下操作来实现：

![Image01256.jpg](img/Image01256.jpg)

这对于向数据库插入新订单效果很好，直到发生意外情况，导致第二个 `INSERT` 查询因某种原因失败。如果发生这种情况，你将在 `orders` 表中得到一个新订单，但它没有关联任何产品。幸运的是，修复方法非常简单，你只需将查询以单个数据库事务的形式执行即可。

## 使用事务向数据库插入新订单

要使用 PDO 开启事务，只需在执行任何数据库查询之前调用 `beginTransaction()` 方法。然后通过执行 `INSERT` 和/或 `UPDATE` 查询对数据进行任何想要的更改。最后调用 `PDO` 对象的 `commit()` 方法使更改永久生效。在调用 `commit()` 方法之前，你对数据所做的每一项更改都尚未永久生效，只需调用 `PDO` 对象的 `rollback()` 方法即可轻松撤销。

以下示例演示了使用事务向数据库插入新订单，同时确保数据的一致性。如果两个查询中的任何一个失败，所有更改都将被撤销。

![Image01257.jpg](img/Image01257.jpg)

#### 第 58.4 节：PDO：连接到 MySQL/MariaDB 服务器

根据你的基础设施，有两种连接到 MySQL/MariaDB 服务器的方式。

## 标准 (TCP/IP) 连接

```php
$dsn = 'mysql:dbname=demo;host=server;port=3306;charset=utf8';

$connection = new \PDO($dsn, $username, $password);

// 发生 SQL 错误时抛出异常
$connection->setAttribute(\PDO::ATTR_ERRMODE, \PDO::ERRMODE_EXCEPTION);

// 防止预处理语句模拟
$connection->setAttribute(\PDO::ATTR_EMULATE_PREPARES, false);
```

![Image01258.jpg](img/Image01258.jpg)

由于 PDO 设计为与旧版 MySQL 服务器兼容（这些版本不支持预处理语句），你必须显式禁用模拟。否则，你将失去使用预处理语句通常带来的防注入优势。

另一个需要注意的设计妥协是默认的错误处理行为。如果不另行配置，PDO 不会显示任何 SQL 错误的迹象。

强烈建议将其设置为“异常模式”，因为在编写持久化抽象层时（例如：违反 UNIQUE 约束时抛出异常），这能提供额外的功能。

## Socket 连接

```php
$dsn = 'mysql:unix_socket=/tmp/mysql.sock;dbname=demo;charset=utf8';

$connection = new \PDO($dsn, $username, $password);

// 发生 SQL 错误时抛出异常
$connection->setAttribute(\PDO::ATTR_ERRMODE, \PDO::ERRMODE_EXCEPTION);

// 防止预处理语句模拟
$connection->setAttribute(\PDO::ATTR_EMULATE_PREPARES, false);
```

![Image01259.jpg](img/Image01259.jpg)

在类 Unix 系统上，如果主机名是 `localhost`，则通过域套接字连接到服务器。

#### 第 58.5 节：PDO：获取查询影响的行数

| 方法 | 说明 |
| --- | --- |
| `rowCount()` | 返回由相应 `PDOStatement` 对象执行的最后一个 DELETE、INSERT 或 UPDATE 语句影响的行数。 |

我们从 `$db` 开始，它是 `PDO` 类的一个实例。执行查询后，我们通常想确定受其影响的行数。`PDOStatement` 的 `rowCount()` 方法非常适合这项工作：

```php
$query = $db->query("DELETE FROM table WHERE name = 'John'");
$count = $query->rowCount();
echo "Deleted $count rows named John";
```

> **注意：** 此方法仅应用于确定 `INSERT`、`DELETE` 和 `UPDATE` 语句影响的行数。虽然此方法对 `SELECT` 语句也可能有效，但并非在所有数据库中都一致。

#### 第 58.6 节：PDO::lastInsertId()

你经常可能需要获取刚插入数据库表中的行的自增 ID 值。你可以使用 `lastInsertId()` 方法实现这一点。

![Image01260.jpg](img/Image01260.jpg)

```php
// 1. 准备查询
$query = "INSERT INTO foo_user(pseudo, email) VALUES ('anonymous', 'anonymous@example.com')";

// 2. 执行查询
$query_success = $pdo->query($query);

// 3. 获取最后插入的 ID
$id = $pdo->lastInsertId(); // 返回值为整数
```

![Image01261.jpg](img/Image01261.jpg)

在 PostgreSQL 和 Oracle 中，存在 `RETURNING` 关键字，它返回当前插入/修改行的指定列。此处为插入一条记录的示例：

![Image01262.jpg](img/Image01262.jpg)

## 第 59 章：PHP MySQLi

[mysqli](http://php.net/manual/en/book.mysqli.php) 接口是 mysql 接口的改进版（意为“MySQL 改进扩展”），mysql 接口在 5.5 版本中被弃用，并在 7.0 版本中被移除。mysqli 扩展（有时称为 MySQL 改进扩展）的开发旨在利用 MySQL 4.1.3 及更新版本中发现的新功能。mysqli 扩展包含在 PHP 5 及更高版本中。

#### 第 59.1 节：关闭连接

当我们完成数据库查询后，建议关闭连接以释放资源。

### 面向对象风格

![Image01263.jpg](img/Image01263.jpg)

### 过程化风格

![Image01264.jpg](img/Image01264.jpg)

> **注意：** 除非通过显式调用关闭连接函数提前关闭，否则服务器连接将在脚本执行结束时立即关闭。

**用例：** 如果我们的脚本在获取结果后有大量处理要执行，且已检索完整个结果集，我们绝对应该关闭连接。如果不这样做，当 Web 服务器负载繁重时，MySQL 服务器有可能达到其连接限制。

#### 第 59.2 节：MySQLi 连接

### 面向对象风格

#### 连接到服务器

![Image01265.jpg](img/Image01265.jpg)

```php
$conn->select_db("my_db");
```

#### 连接到数据库

![Image01266.jpg](img/Image01266.jpg)

### 过程化风格

#### 连接到服务器

![Image01267.jpg](img/Image01267.jpg)

```php
mysqli_select_db($conn, "my_db");
```

#### 连接到数据库

```php
$conn = mysqli_connect("localhost", "my_user", "my_password", "my_db");
```

![Image01268.jpg](img/Image01268.jpg)

### 验证数据库连接

#### 面向对象风格

![Image01269.jpg](img/Image01269.jpg)

#### 过程化风格

![Image01270.jpg](img/Image01270.jpg)

#### 第 59.3 节：遍历 MySQLi 结果

PHP 使得从结果中获取数据并使用 `while` 语句循环遍历变得很容易。当无法获取下一行时，它返回 `false`，循环随之结束。这些示例适用于



# MySQLi 函数与预处理语句

## 获取结果

以下函数从结果集中检索行：

- `mysqli_fetch_assoc()` — 以列名为键的关联数组
- `mysqli_fetch_object()` — 以列名为变量的 `stdClass` 对象
- `mysqli_fetch_array()` — 关联和数字数组（可使用参数仅获取其中一种）
- `mysqli_fetch_row()` — 数字数组

### 面向对象风格
![Image01272.jpg](img/Image01272.jpg)

### 过程化风格
![Image01273.jpg](img/Image01273.jpg)

要从结果中获取确切信息，我们可以使用：
![Image01274.jpg](img/Image01274.jpg)

#### 第 59.4 节：MySQLi 中的预处理语句

请阅读 *使用参数化查询防止 SQL 注入*，以全面了解预处理语句为何能帮助您保护 SQL 语句免受 SQL 注入攻击。

此处的 `$conn` 变量是一个 `MySQLi` 对象。详情请参阅 *MySQLi 连接示例*。

对于两个示例，我们假设 `$sql` 为：
![Image01275.jpg](img/Image01275.jpg)

`?` 代表我们稍后将提供的值。请注意，无论类型如何，我们都不需要为占位符加引号。我们也只能在查询的数据部分提供占位符，即 `SET`、`VALUES` 和 `WHERE`。您不能在 `SELECT` 或 `FROM` 部分使用占位符。

### 面向对象风格
![Image01276.jpg](img/Image01276.jpg)

### 过程化风格
![Image01277.jpg](img/Image01277.jpg)

| `$stmt->bind_param` |
| --- |

`bind_param()` 的第一个参数或 `mysqli_stmt_bind_param()` 的第二个参数由 SQL 查询中相应参数的数据类型决定：

| 参数 | 绑定参数的数据类型 |
| --- | --- |
| i | integer（整数） |
| d | double（双精度浮点数） |
| s | string（字符串） |
| b | blob（二进制大对象） |

| `column_2` | `=` | `?` | `)` 是字符串，第二个参数（`column_3` | `>` | `?` |
| --- | --- | --- | --- | --- | --- |

您的参数列表顺序必须与查询中提供的顺序一致。在本例中 `si` 表示第一个参数是整数。

关于检索数据，请参阅 *如何从预处理语句获取数据*。

#### 第 59.5 节：转义字符串

转义字符串是一种较旧（且安全性较低）的方法，用于保护插入查询的数据。它通过使用 [MySQL 的函数 `mysql_real_escape_string()`](http://dev.mysql.com/doc/refman/5.7/en/mysql-real-escape-string.html) 来处理和清理数据（换句话说，是 MySQL 而非 PHP 在执行转义）。MySQLi API 提供了对该函数的直接访问：
![Image01278.jpg](img/Image01278.jpg)

此时，您拥有一个 MySQL 认为可安全用于直接查询的字符串：
![Image01279.jpg](img/Image01279.jpg)

那么为什么这不如预处理语句安全？存在欺骗 MySQL 生成其认为安全的字符串的方法。请考虑以下示例：
![Image01280.jpg](img/Image01280.jpg)

| OR |
| --- |

`1=1` 并不代表 MySQL 会转义的数据，但这仍然构成 SQL 注入。还有 [其他](http://stackoverflow.com/questions/5741187/sql-injection-that-gets-around-mysql-real-escape-string) [示例](http://stackoverflow.com/questions/5741187/sql-injection-that-gets-around-mysql-real-escape-string) 表明其会返回不安全数据。问题在于 MySQL 的转义函数旨在使数据符合 SQL 语法。它**并非**旨在确保 MySQL 不会将用户数据误认为 SQL 指令。

#### 第 59.6 节：MySQLi 中的 SQL 调试

因此您的查询失败了（关于如何创建 `$conn`，请参阅 *MySQLi 连接*）：

```php
$result = $conn->query('SELECT * FROM non_existent_table'); // 此查询将失败
```

我们如何查明发生了什么？`$result` 为 `false`，这无济于事。幸运的是，连接对象 `$conn` 可以告诉我们 MySQL 关于失败的报告：
![Image01282.jpg](img/Image01282.jpg)

或过程化风格：
![Image01283.jpg](img/Image01283.jpg)

您应该会得到类似以下的错误：
![Image01284.jpg](img/Image01284.jpg) Table 'my_db.non_existent_table' doesn't exist（表 'my_db.non_existent_table' 不存在）

#### 第 59.7 节：MySQLi 查询

`query()` 函数接受一个有效的 SQL 字符串并直接针对数据库连接 `$conn` 执行它。

### 面向对象风格
![Image01285.jpg](img/Image01285.jpg)
![Image01286.jpg](img/Image01286.jpg)

此处常见的问题是，人们直接执行查询并期望其生效（即返回一个 `mysqli_stmt` 对象）。由于此函数仅接受字符串，您需要先自行构建查询。如果 SQL 中存在任何错误，MySQL 编译器将失败，此时该函数将返回 `false`。

```php
$result = $conn->query('SELECT * FROM non_existent_table'); // 此查询将失败
$row = $result->fetch_assoc();
```

上述代码将产生 `E_FATAL` 错误，因为 `$result` 为 `false`，而非对象。

![Image01288.jpg](img/Image01288.jpg) PHP Fatal error: Call to a member function `fetch_assoc()` on a non-object（PHP 致命错误：调用非对象的成员函数 `fetch_assoc()`）

过程化风格的错误类似，但非致命，因为我们只是违反了函数的预期。
![Image01289.jpg](img/Image01289.jpg)

您将从 PHP 获得以下消息：
![Image01290.jpg](img/Image01290.jpg) mysqli_fetch_array() expects parameter 1 to be mysqli_result, boolean given（mysqli_fetch_array() 期望参数 1 为 mysqli_result，布尔值 given）

您可以通过先进行测试来避免此问题：
![Image01291.jpg](img/Image01291.jpg)

#### 第 59.8 节：如何从预处理语句获取数据

### 预处理语句
关于如何准备和执行查询，请参阅 *MySQLi 中的预处理语句*。

### 结果绑定

#### 面向对象风格
![Image01292.jpg](img/Image01292.jpg)

#### 过程化风格
![Image01293.jpg](img/Image01293.jpg)

使用 `bind_result()` 的问题在于，它要求语句指定将要使用的列。这意味着：

| `SELECT forename FROM users` |
| --- |

为了使上述代码工作，查询必须如下所示。要包含更多列，只需将它们作为参数添加到 `bind_result()` 函数中（并确保将它们添加到 SQL 查询中）。

在两种情况下，我们都将 `forename` 列赋值给 `$forename` 变量。这些函数接受的参数数量与您要赋值的列数相同。赋值仅执行一次，因为该函数通过引用绑定。

然后我们可以按如下方式循环：

#### 面向对象风格
![Image01294.jpg](img/Image01294.jpg)

#### 过程化风格
![Image01295.jpg](img/Image01295.jpg)

其缺点是您必须一次性分配大量变量。这使得跟踪大型查询变得困难。如果您安装了 [MySQL 原生驱动程序 (mysqlnd)](http://php.net/manual/en/book.mysqlnd.php)，则只需使用 `get_result()` 即可。

#### 面向对象风格
![Image01296.jpg](img/Image01296.jpg)

#### 过程化风格
![Image01297.jpg](img/Image01297.jpg)

这要容易得多，因为现在我们得到了一个 `mysqli_result` 对象。这与 `mysqli_query()` 返回的对象相同。这意味着您可以使用常规的结果循环来获取数据。

### 如果我无法安装 mysqlnd 怎么办？

如果是这种情况，@Sophivorus 为您提供了 [这个精彩的回答](http://stackoverflow.com/a/30551477/3578036)。

此函数可在服务器未安装 `get_result()` 的情况下执行其任务。它只是遍历结果并构建一个关联数组：
![Image01298.jpg](img/Image01298.jpg)

| `mysqli_fetch_assoc` |
| --- |

然后我们可以像使用 `get_result()` 一样使用该函数获取结果：
![Image01299.jpg](img/Image01299.jpg)

其输出将与使用 mysqlnd 驱动程序时相同，只是无需安装该驱动程序。如果您无法在系统上安装该驱动程序，这非常有用。只需实现此解决方案即可。

#### 第 59.9 节：MySQLi 插入 ID

检索在具有 `AUTO_INCREMENT` 列的表上执行 `INSERT` 查询生成的最后一个 ID。

### 面向对象风格
![Image01300.jpg](img/Image01300.jpg)
![Image01301.jpg](img/Image01301.jpg)

### 更新行时的插入 ID

| `INSERT ... ON DUPLICATE KEY UPDATE` |
| --- |




通常情况下，`UPDATE` 语句不会返回插入 ID，因为只有在保存（或插入）新行时才会返回 `AUTO_INCREMENT` ID。使更新能够获取新 ID 的一种方法是使用 `INSERT ... ON DUPLICATE KEY UPDATE` 语法进行更新。

后续示例的设置：

![](img/Image01302.jpg)

| LAST_INSERT_ID |
| --- |

`IODKU` 执行“更新”且 `LAST_INSERT_ID()` 检索相关 ID 的情况：

![](img/Image01303.jpg)

| LAST_INSERT_ID |
| --- |

`IODKU` 执行“插入”且 `LAST_INSERT_ID()` 检索新 ID 的情况：

![](img/Image01304.jpg)

生成的表内容：

![](img/Image01305.jpg)

## 第 60 章：SQLite3

#### 第 60.1 节：SQLite3 快速入门教程

这是一个包含所有常用 SQLite 相关 API 的完整示例。目的是让你能够非常快速地上手运行。你也可以获取该教程的 [可运行 PHP 文件](https://gist.github.com/bladeSk/6294d3266370868601a7d2e50285dbf5)。

### 创建/打开数据库

| sqlite |
| --- |

首先让我们创建一个新数据库。仅当文件不存在时创建它，并以读/写模式打开。文件扩展名由你决定，但 `.sqlite` 非常常见且不言自明。

![](img/Image01306.jpg)

```
$db = new SQLite3('analytics.sqlite', SQLITE3_OPEN_CREATE | SQLITE3_OPEN_READWRITE);
```

### 创建表

![](img/Image01307.jpg)

### 插入示例数据

建议将相关查询包裹在事务中（使用关键字 `BEGIN` 和 `COMMIT`），即使你不关心原子性。如果不这样做，SQLite 会自动将每个单独的查询包裹在事务中，这会极大地拖慢所有操作。如果你是 SQLite 新手，可能会惊讶于为什么 [INSERT 这么慢](http://stackoverflow.com/a/3852082/388994)。

![](img/Image01308.jpg)

使用预处理语句插入潜在的不安全数据。你可以使用命名参数来实现：

![](img/Image01309.jpg)

```
$statement = $db->prepare('INSERT INTO "visits" ("user_id", "url", "time")
     VALUES (:uid, :url, :time)');

$statement->bindValue(':uid', 1337);
$statement->bindValue(':url', '/test');
$statement->bindValue(':time', date('Y-m-d H:i:s'));
$statement->execute();
// 你可以使用不同的值重用该语句
```

### 获取数据

让我们获取用户 #42 今天的访问记录。我们将再次使用预处理语句，但这次使用编号参数，这更简洁：

![](img/Image01310.jpg)
![](img/Image01311.jpg)

释放内存——在脚本运行期间这不会自动完成。

![](img/Image01312.jpg)

### 简写方法

这是一个用于将单行作为关联数组获取的有用简写方法。第二个参数表示我们想要所有选定的列。

注意，此简写不支持参数绑定，但你可以转义字符串代替。值务必放在**单**引号中！双引号用于表名和列名（类似于 MySQL 中的反引号）。

![](img/Image01313.jpg)

另一个用于仅检索单个值的有用简写。

![](img/Image01314.jpg)

```
echo "\n";
```

### 清理工作

最后，关闭数据库。脚本结束时这会自动完成。

![](img/Image01315.jpg)

#### 第 60.2 节：查询数据库

![](img/Image01316.jpg)

另请参阅 http://stackoverflow.com/documentation/sql/topics

#### 第 60.3 节：仅检索一个结果

除了使用 `LIMIT` SQL 语句外，你还可以使用 `SQLite3::querySingle()` 函数来检索单行或第一列。

```php
<?php
$database = new SQLite3('mysqlitedb.db');

// 未将可选的第二个参数设置为 true 时，此查询将仅返回结果首行的第一列，类型与 columnName 相同
$database->querySingle('SELECT column1Name FROM table WHERE column2Name=1');

// 设置可选的 entire_row 参数时，此查询将返回查询结果首行完整数据的数组。
$database->querySingle('SELECT column1Name, column2Name FROM user WHERE column3Name=1', true);
?>
```

## 第 61 章：使用 MongoDB

#### 第 61.1 节：连接到 MongoDB

创建一个 MongoDB 连接，稍后可用于查询：

![](img/Image01318.jpg)

```
$manager = new \MongoDB\Driver\Manager('mongodb://localhost:27017');
```

在下一个示例中，你将学习如何查询连接对象。

此扩展会自动关闭连接；无需手动关闭。

#### 第 61.2 节：获取多个文档 - find()

搜索名为 "Mike" 的多个用户的示例：

![](img/Image01319.jpg)

#### 第 61.3 节：获取单个文档 - findOne()

搜索具有特定 ID 的单个用户的示例，你应该这样做：

![](img/Image01320.jpg)

#### 第 61.4 节：插入文档

添加文档的示例：

![](img/Image01321.jpg)

#### 第 61.5 节：更新文档

更新所有 name 等于 "John" 的文档的示例：

![](img/Image01322.jpg)

#### 第 61.6 节：删除文档

删除所有 name 等于 "Peter" 的文档的示例：

![](img/Image01323.jpg)

## 第 62 章：mongo-php

#### 第 62.1 节：MongoDB 与 Php 之间的一切

### 要求

![](img/Image01324.jpg)

*   MongoDB 服务器运行在通常为 27017 的端口上。（在命令提示符中输入 `mongod` 以运行 mongodb 服务器）
*   PHP 作为 cgi 或 fpm 安装并安装了 MongoDB 扩展（MongoDB 扩展不随默认 php 捆绑）

| php composer || . || phar require |
| --- | --- | --- |

![](img/Image01325.jpg)

*   Composer 库 (`mongodb/mongodb`)。（在项目根目录运行 `"mongodb/mongodb=¹.0.0"` 以安装 MongoDB 库）

如果一切正常，你就可以继续了。

### 检查 PHP 安装

| php |
| --- |

如果不确定，请通过在命令提示符运行 `-v` 来检查 PHP 安装，将返回类似如下内容：

```
PHP 7.0.6 (cli)
built: Apr 28 2016 14:12:14
ZTS
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
```

![](img/Image01327.jpg)
![](img/Image01328.jpg)

### 检查 MongoDB 安装

```
mongo --version
```
将返回：
```
MongoDB shell version: 3.2.6
```

通过运行 `mongo --version` 检查 MongoDB 安装。

### 检查 Composer 安装

```
php composer.phar --version
```
将返回：
```
Composer version 1.2-dev (3d09c17b489cd29a0c0b3b11e731987e7097797d) 2016-08-30 16:12:39
```

通过运行 `php composer.phar --version` 检查 Composer 安装。

### 从 php 连接到 MongoDB

![](img/Image01331.jpg)
![](img/Image01332.jpg)

| mongodb/mongodb | included as | vendor/autoload.php |
| --- | --- | --- |

上述代码将使用 MongoDB composer 库 (`mongodb/mongodb`) 连接到运行在端口 `27017` 上的 MongoDB 服务器。如果一切正常，它将连接并列出一个数组，如果连接 MongoDB 服务器时发生异常，将打印错误消息。

### CREATE（插入）到 MongoDB

![](img/Image01333.jpg)

| $result->getInsertedId() |
| --- |

在示例中，我们使用了“从 php 连接到 MongoDB”部分中先前使用的 `$mongo` 实例。MongoDB 使用 JSON 类型的数据格式，因此在 PHP 中我们将使用数组向 MongoDB 插入数据，数组到 JSON 以及反之的转换将由 mongo 库完成。MongoDB 中的每个文档都有一个名为 `_id` 的唯一 ID，在插入期间我们可以通过使用 `getInsertedId()` 获取它。

### READ（查找）在 MongoDB 中

![](img/Image01334.jpg)

### 在 MongoDB 中 Drop

![](img/Image01335.jpg)



可以对 `$collection` 执行许多方法，请参阅 MongoDB 的[官方文档](http://mongodb.github.io/mongo-php-library/api/index.html)

## 第 63 章：在 PHP 中使用 Redis

#### 第 63.1 节：连接到 Redis 实例

假设默认服务器运行在 localhost 上并使用默认端口，连接到该 Redis 服务器的命令如下：

![](img/Image01336.jpg)

#### 第 63.2 节：在 Ubuntu 上安装 PHP Redis

要在 Ubuntu 上安装 PHP，首先安装 Redis 服务器：

![](img/Image01337.jpg)

然后安装 PHP 模块：

![](img/Image01338.jpg)

并重启 Apache 服务器：

![](img/Image01339.jpg)

#### 第 63.3 节：在 PHP 中执行 Redis 命令

Redis PHP 模块提供了与 Redis CLI 客户端相同的命令访问权限，因此使用起来非常简单。

语法如下：

![](img/Image01340.jpg)

## 第 64 章：发送邮件

##### 参数详情

| 参数 | 描述 |
| --- | --- |
| `string $to` | 收件人邮箱地址 |
| `string $subject` | 邮件主题 |
| `string $message` | 邮件正文 |
| `string $additional_headers` | 可选：要添加到邮件中的标头 |
| `string $additional_parameters` | 可选：要在命令行中传递给配置的邮件发送应用程序的参数 |

#### 第 64.1 节：发送邮件 - 基础、更多详情和完整示例

一封典型的邮件有三个主要组成部分：

1.  收件人（以邮箱地址表示）
2.  主题
3.  邮件正文

在 PHP 中发送邮件可以简单到只需调用内置函数 `mail()`。`mail()` 最多接受五个参数，但前三个参数就是发送邮件所需的全部（尽管通常会使用第四个参数，如下所示）。前三个参数是：

1.  收件人的邮箱地址（字符串）
2.  邮件的主题（字符串）
3.  邮件的正文（字符串）（例如邮件的内容）

![](img/Image01341.jpg)

最小示例将类似于以下代码：

```
mail('recipient@example.com', 'Email Subject', 'This is the email message body');
```

上述简单示例在有限情况下效果很好，例如为内部系统硬编码邮件警报。但是，通常会将作为 `mail()` 参数传递的数据放在变量中，以使代码更整洁且易于管理（例如，从表单提交动态构建邮件）。

此外，`mail()` 接受第四个参数，允许您随邮件发送额外的邮件标头。这些标头允许您设置：

| 标头 | 描述 |
| --- | --- |
| `From` | 用户将看到的发件人姓名和邮箱地址 |
| `Reply-To` | 用户回复将发送到的邮箱地址 |
| `X-Mailer` | 额外的非标准标头，如 X-Mailer，可告知收件人此邮件是通过 PHP 发送的 |

```
$to       = 'recipient@example.com'; // 也可以是 $to = $_POST['recipient'];
$subject  = 'Email Subject';         // 也可以是 $subject = $_POST['subject'];
$message  = 'This is the email message body'; // 也可以是 $message = $_POST['message'];
$headers  = implode("\r\n", [
    'From: John Conde <webmaster@example.com>',
    'Reply-To: webmaster@example.com>',
    'X-Mailer: PHP/' . PHP_VERSION
]);
```

![](img/Image01342.jpg)

可选的第五个参数可用于将额外的标志作为命令行选项传递给配置用于发送邮件的程序，由 `sendmail_path` 配置设置定义。例如，这可以用于在使用带有 `-f` sendmail 选项的 sendmail/postfix 时设置信封发件人地址。

![](img/Image01343.jpg)

虽然使用 `mail()` 可能非常可靠，但绝不意味着调用 `mail()` 时一定会发送邮件。要查看发送邮件时是否存在潜在错误，您应该捕获 `mail()` 的返回值。如果邮件成功被接受投递，将返回 `TRUE`。否则，您将收到 `FALSE`。

![](img/Image01344.jpg)

**注意**：虽然 `mail()` 可能返回 `TRUE`，但这并不意味着邮件已发送或收件人将收到邮件。它仅表示邮件已成功移交给您系统的邮件系统。

如果您想发送 HTML 邮件，不需要做太多额外的工作。您需要：

1.  添加 `MIME-Version` 标头
2.  添加 `Content-Type` 标头
3.  确保您的邮件内容是 HTML

![](img/Image01345.jpg)
![](img/Image01346.jpg)
![](img/Image01347.jpg)

### 另请参阅

**官方文档**

*   [`mail`](http://php.net/manual/en/function.mail.php)
*   [`mail` 配置](http://php.net/manual/en/mail.configuration.php)

**相关 Stack Overflow 问题**

*   [PHP 邮件表单未完成发送电子邮件](http://stackoverflow.com/q/24644436/250259)
*   [如何确保您以编程方式发送的电子邮件不会被自动标记为垃圾邮件？](http://stackoverflow.com/q/371/250259)
*   [如何使用 SMTP 发送电子邮件](http://stackoverflow.com/questions/15965376/how-to-configure-xampp-to-send-mail-from-localhost/18185233#18185233)
*   [设置信封发件人地址](http://stackoverflow.com/a/5666682/2417031)

**替代邮件发送库**

*   [PHPMailer](https://github.com/Synchro/PHPMailer)
*   [SwiftMailer](http://swiftmailer.org/)
*   [PEAR::Mail](https://pear.php.net/package/Mail)

**邮件服务器**

*   [Mercury Mail (Windows)](http://www.pmail.com/overviews/ovw_mercury.htm)

**相关主题**

*   [Post/Redirect/Get](https://en.wikipedia.org/wiki/Post/Redirect/Get)

#### 第 64.2 节：使用 mail() 发送 HTML 邮件

![](img/Image01353.jpg)
![](img/Image01354.jpg)

这与发送纯文本邮件差别不大。关键区别在于内容正文的结构类似于 HTML 文档，并且必须包含两个额外的标头，以便邮件客户端知道将邮件作为 HTML 渲染。它们是：

```
MIME-Version: 1.0
Content-Type: text/html; charset=UTF-8
```

#### 第 64.3 节：使用 mail() 发送带附件的邮件

![](img/Image01356.jpg)
![](img/Image01357.jpg)

### Content-Transfer-Encodings（内容传输编码）

可用的编码有 `7bit`、`8bit`、`binary`、`quoted-printable`、`base64`、`ietf-token` 和 `x-token`。根据 RFC 2045 第 6.4 节所述，在这些编码中，当标头具有多部分 `Content-Type` 时，`Content-Transfer-Encoding` 的值不得为 `7bit`、`8bit` 或 `binary` 以外的任何其他值。

我们的示例为多部分标头选择了 `7bit` 编码，它代表 US-ASCII 字符，因为正如 RFC 2045 第 6 节所述，某些协议仅支持此编码。边界内的数据随后可以按部分进行编码（RFC 2046，第 5.1 节）。本示例正是如此。第一部分包含 `text/plain` 消息，被定义为 `8bit`，因为可能需要支持额外的字符。在这种情况下，使用的是 Latin1 (`iso-8859-1`) 字符集。第二部分是附件，因此被定义为 `base64` 编码的 `application/octet-stream`。由于 `base64` 将任意数据转换为 `7bit` 范围，因此它可以通过受限传输发送（RFC 2045，第 6.2 节）。

#### 第 64.4 节：使用 PHPMailer 发送纯文本邮件

### 基础文本邮件

![](img/Image01358.jpg)
![](img/Image01359.jpg)

### 添加额外收件人、抄送收件人、密送收件人

![](img/Image01360.jpg)

#### 第 64.5 节：使用 PHPMailer 发送 HTML 邮件

![](img/Image01361.jpg)



## 第 64 章：发送邮件

#### 第 64.6 节：使用 PHPMailer 发送带附件的邮件

![](img/Image01363.jpg)

#### 第 64.7 节：使用 Sendgrid 发送纯文本邮件

### 基础文本邮件

![](img/Image01364.jpg)

### 添加额外收件人、抄送收件人、密送收件人

![](img/Image01365.jpg)

#### 第 64.8 节：使用 Sendgrid 发送带附件的邮件

![](img/Image01366.jpg)

## 第 65 章：使用 SQLSRV

#### 第 65.1 节：检索错误消息

当查询出错时，获取驱动程序返回的错误消息以确定问题原因非常重要。语法如下：

![](img/Image01367.jpg)

这将返回一个包含以下内容的数组：

| 键 | 说明 |
| --- | --- |
| SQLSTATE | SQL Server / ODBC 驱动程序所处的状态 |
| code | SQL Server 错误代码 |
| message | 错误的描述 |

通常像下面这样使用上述函数：

![](img/Image01368.jpg)

#### 第 65.2 节：获取查询结果

从查询获取结果主要有 3 种方式：

### `sqlsrv_fetch_array()`

![](img/Image01369.jpg)

`sqlsrv_fetch_array()` 有一个可选的第二个参数，用于获取不同类型的数组：

可使用 `SQLSRV_FETCH_ASSOC`、`SQLSRV_FETCH_NUMERIC` 和 `SQLSRV_FETCH_BOTH`（默认）；分别返回关联数组、数字索引数组，或两者兼有的数组。

### `sqlsrv_fetch_object()`

![](img/Image01370.jpg)

`sqlsrv_fetch_object()` 将下一行作为对象检索。

### `sqlsrv_fetch()`

![](img/Image01371.jpg)

`sqlsrv_fetch()` 使下一行可供读取。

#### 第 65.3 节：创建连接

![](img/Image01372.jpg)

SQLSRV 也有 PDO 驱动程序。要使用 PDO 连接：

![](img/Image01373.jpg)

```
$conn = new PDO("sqlsrv:Server=localhost,1234;Database=db001", $dbUser, $dbPassword);
```

#### 第 65.4 节：执行简单查询

![](img/Image01374.jpg)

注意：使用方括号 `[]` 是为了转义单词 `table`，因为它是一个[保留字](https://msdn.microsoft.com/en-us/library/ms189822.aspx)。这些的工作方式与 MySQL 中的反引号 `` ` `` 相同。

#### 第 65.5 节：调用存储过程

要在服务器上调用存储过程：

![](img/Image01375.jpg)

![](img/Image01376.jpg)

#### 第 65.6 节：执行参数化查询

![](img/Image01377.jpg)

| `sqlsrv_prepare()` | | 和 | `sqlsrv_execute()` |
| --- | --- | --- | --- |

如果你打算多次使用同一查询语句但参数不同，可以使用以下函数实现相同目的，如下所示：

![](img/Image01378.jpg)

## 第 66 章：命令行界面 (CLI)

#### 第 66.1 节：处理程序选项

| `getopt()` |
| --- |

程序选项可以使用 `getopt()` 函数处理。它的语法与 POSIX `getopt` 命令类似，并额外支持 GNU 风格的长选项。

![](img/Image01379.jpg)

可以像下面这样测试此脚本：

![](img/Image01380.jpg)

![](img/Image01381.jpg)

| `v` |
| --- |

注意最后一种方法将不起作用，因为 `-5` 无效。

![](img/Image01382.jpg)

注意：自 PHP 5.3.0 起，`getopt` 与操作系统无关，在 Windows 上也能工作。

#### 第 66.2 节：参数处理

参数以类似于大多数 C 风格语言的方式传递给程序。`$argc` 是一个整数，包含包括程序名在内的参数数量，`$argv` 是一个包含传递给程序的参数的数组。`$argv` 的第一个元素是程序名称。

![](img/Image01383.jpg)

| `php example.php foo bar` |
| --- |

使用 `php example.php foo bar` 调用上述应用程序（其中 `example.php` 包含上述代码）将产生以下输出：

![](img/Image01384.jpg)

你使用 2 个参数调用了程序 `example.php`

参数 1 是 `foo`

参数 2 是 `bar`

注意 `$argc` 和 `$argv` 是全局变量，而非超全局变量。如果在函数中需要它们，必须使用 `global` 关键字将其导入局部作用域。

此示例展示了当使用 `""` 或 `\` 等转义字符时参数是如何分组的。

### 示例脚本

![](img/Image01385.jpg)

### 命令行

![](img/Image01386.jpg)

![](img/Image01387.jpg)

![](img/Image01388.jpg)

![](img/Image01389.jpg)

#### 第 66.3 节：输入和输出处理

当从 CLI 运行时，常量 `STDIN`、`STDOUT` 和 `STDERR` 是预定义的。这些常量是文件句柄，可视为运行以下命令的结果：

![](img/Image01390.jpg)

这些常量可用于任何标准文件句柄适用的地方：

![](img/Image01391.jpg)

| `php://stdin`、`php://stdout` 和 `php://stderr` |
| --- |

前面提到的内置流地址（`php://stdin`、`php://stdout`、`php://stderr`）在大多数上下文中可代替文件名使用：

![](img/Image01392.jpg)

![](img/Image01393.jpg)

作为替代，你也可以使用 [`readline()`](http://php.net/manual/en/function.readline.php) 进行输入，并使用 `echo` 或 `print` 或任何其他字符串打印函数进行输出。

![](img/Image01394.jpg)

#### 第 66.4 节：返回代码

`exit` 结构可用于向执行环境传递返回代码。

![](img/Image01395.jpg)

| `exit` |
| --- |

默认情况下，如果未提供返回代码，将返回退出代码 `0`，即 `exit` 等同于 `exit(0)`。由于 `exit` 不是函数，如果不传递返回代码则不需要括号。

返回代码必须在 `0` 到 `254` 范围内（`255` 由 PHP 保留，不应使用）。按照惯例，使用返回代码 `0` 退出会告诉调用程序 PHP 脚本成功运行。使用非零返回代码告诉调用程序发生了特定的错误条件。

#### 第 66.5 节：将脚本执行限制在命令行

| [`php_sapi_name()`](http://php.net/php_sapi_name) |
| --- |

函数 [`php_sapi_name()`](http://php.net/php_sapi_name) 和常量 `PHP_SAPI` 都返回 PHP 正在使用的接口类型（服务器 API）。它们可用于将脚本执行限制在命令行，方法是检查函数输出是否等于 `cli`。

![](img/Image01396.jpg)

| [`drupal_is_cli()`](https://api.drupal.org/api/drupal/includes!bootstrap.inc/function/drupal_is_cli/7.x) |
| --- |

[`drupal_is_cli()`](https://api.drupal.org/api/drupal/includes!bootstrap.inc/function/drupal_is_cli/7.x) 函数是一个检测脚本是否从命令行执行的函数示例：

![](img/Image01397.jpg)

#### 第 66.6 节：命令行上的行为差异

从 CLI 运行时，PHP 表现出一些与从 Web 服务器运行时不同的行为。应牢记这些差异，特别是在同一脚本可能在两种环境中运行的情况下。

| `require("./stuff.inc");` |
| --- |

![](img/Image01398.jpg)

**无目录更改** 从 Web 服务器运行脚本时，当前工作目录始终是脚本本身所在的目录。代码 `require("./stuff.inc");` 假设文件与脚本在同一目录中。在命令行上，当前工作目录是你调用脚本时所在的目录。将从命令行调用的脚本应始终使用绝对路径。（注意魔术常量 `__DIR__` 和 `__FILE__` 继续按预期工作，并返回脚本的位置。）

| `php.ini` |
| --- |

![](img/Image01399.jpg)

**无输出缓冲** 指令 `output_buffering` 和 `implicit_flush` 默认分别为 `false` 和 `true`。缓冲仍然可用，但必须显式启用，否则输出将始终实时显示。

| `php.ini` |
| --- |

| `php.ini` |
| --- |

| `php.ini` 可以被加载。当你从 cli 使用 php 时，它可以使用不同的 `php.ini` |
| --- |




#### 第 66.7 节：运行你的脚本

指令 `max_execution_time` 被设置为零，因此脚本默认不会超时。

如果你启用了指令 `html_errors`，它将在命令行中被忽略。

这与 Web 服务器的行为不同。你可以通过运行 `php --ini` 来了解正在使用哪个配置文件。

在 Linux/UNIX 或 Windows 上，脚本可以作为参数传递给 PHP 可执行文件，随后跟随该脚本的选项和参数：

```
php script.php arg1 arg2
```

这将 `foo` 和 `bar` 作为参数传递给 `script.php`。

在 Linux/UNIX 上，运行脚本的首选方法是在文件的第一行使用 [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix))（例如 `#!/usr/bin/env php`），并为该文件设置可执行位。假设脚本在你的路径中，你可以直接调用它：

```
/usr/bin/env php
```

```
/usr/bin/php or /usr/local/bin/php
```

```
/usr/bin/env
```

使用 `/usr/bin/env` 会使 PHP 可执行文件通过 `PATH` 环境变量被查找。根据 PHP 的安装方式，它可能不位于同一位置（例如 `/usr/bin/php`），这与 `env` 不同，后者通常可从 `/usr/bin/env` 获得。

在 Windows 上，你可以通过将 PHP 的目录和你的脚本添加到 `PATH` 并编辑 `PATHEXT` 以允许通过 `PATH` 检测 `.php` 来获得相同的结果。另一种可能是在你的 PHP 脚本同目录下添加一个名为 `example.bat` 的文件并写入以下行：

```
@php "%~dp0example.php" %*
```

或者，如果你将 PHP 的目录添加到了 `PATH` 中，为了方便使用：

```
example arg1 arg2
```

#### 第 66.8 节：getopt() 的边缘情况

此示例展示了当用户输入不常见时 `getopt` 的行为：

```
php script.php -a -b -c
```

Shell 命令行

```
php script.php -a -b -c
```

从这个示例中可以看出：

单个选项（无冒号）如果启用，始终携带布尔值 `false`。

如果一个选项被重复，`getopt` 输出中的相应值将变为一个数组。

必需参数选项（一个冒号）接受一个空格或无空格（像可选参数选项一样）作为分隔符。

在一个无法映射到任何选项的参数之后，其后的选项也不会被映射。

#### 第 66.9 节：运行内置 Web 服务器

从 5.4 版本开始，PHP 自带内置服务器。它可以用于运行应用程序，而无需安装其他 HTTP 服务器，如 nginx 或 apache。内置服务器仅设计用于开发和测试目的的受控环境中。

可以使用命令 `php -S` 运行它：

```
index.php
```

要测试它，请创建包含以下内容的 `index.php` 文件：

```
<?php echo "Hello World"; ?>
```

并运行命令：

```
php -S localhost:8080
```

现在你应该能在浏览器中看到内容。要检查这一点，请导航到 `http://localhost:8080`。

每次访问都会导致日志条目被写入终端：

```
[Mon Aug 15 18:20:19 2016] ::1:52622 [200]: /index.php
```

## 第 67 章：本地化

#### 第 67.1 节：使用 gettext() 本地化字符串

```
php.ini
```

GNU gettext 是 PHP 中的一个扩展，必须在 `php.ini` 中包含：`extension=php_gettext.dll` #Windows `extension=gettext.so` #Linux

gettext 函数实现了一个 NLS（本地语言支持）API，可用于国际化你的 PHP 应用程序。

可以通过设置区域设置、设置翻译表并对任何你想要翻译的字符串调用 `gettext()` 来在 PHP 中翻译字符串。

```
<?php
$locale = 'fr_FR';
putenv("LC_ALL=$locale");
setlocale(LC_ALL, $locale);
bindtextdomain("myPHPApp", "./locale");
textdomain("myPHPApp");
?>
```

`myPHPApp.po`

```
msgid "some string"
msgid "une chaîne"
```

`gettext()` 加载给定的后编译 `.po` 文件，一个 `.mo` 文件，它将你的待翻译字符串映射如上所示。

完成这小段设置代码后，翻译将在以下文件中查找：

```
./locale/fr_FR/LC_MESSAGES/myPHPApp.mo
```

每当你调用 `gettext('some string')` 时，如果 'some string' 已在 `.mo` 文件中翻译，则返回翻译。否则，将返回未翻译的 'some string'。

```
echo gettext("some string"); // outputs: une chaîne
```

## 第 68 章：Headers 操作

#### 第 68.1 节：Header 的基本设置

这是一个在点击按钮时更改 Header 以跳转到新页面的基本设置。

```
<?php
header("Location: newpage.php");
?>
```

## 第 69 章：编码规范

#### 第 69.1 节：PHP 标签

你应该始终使用 `<?php ?>` 标签或短回显标签 `<?= ?>`。其他变体（特别是短标签 `<? ?>`）不应使用，因为它们通常被系统管理员禁用。

当文件不需要产生输出时（整个文件均为 PHP 代码），应省略结束标签 `?>` 以避免意外输出，这可能导致客户端解析文档时出现问题，特别是某些浏览器无法识别 `<!DOCTYPE>` 标签并激活 [Quirks Mode](https://en.wikipedia.org/wiki/Quirks_mode)。

简单 PHP 脚本示例：

```
<?php
echo "Hello World";
```

类定义文件示例：

```
<?php
class MyClass {
    public function myMethod() {
        return "Hello";
    }
}
```

PHP 嵌入 HTML 示例：

```
<!DOCTYPE html>
<html>
<head>
    <title>PHP Test</title>
</head>
<body>
    <?php echo "Hello World"; ?>
</body>
</html>
```

## 第 70 章：异步编程

#### 第 70.1 节：生成器的优势

PHP 5.5 引入了生成器和 `yield` 关键字，这使我们能够编写看起来更像同步代码的异步代码。

`Generator::send()`

yield 表达式负责将控制权交还给调用代码，并在该处提供一个恢复点。可以沿着 yield 指令发送一个值。该表达式的返回值要么是 `null`，要么是传递给 `Generator::send()` 的值。

```
<?php
function generator() {
    $value = yield 1;
    echo $value; // 2
}
$gen = generator();
$gen->send(2);
```

这种机制可被协程实现用于等待生成器产出的 Awaitables（通过将自身注册为解析的回调），并在 Awaitable 解析后立即继续执行生成器。

#### 第 70.2 节：使用 Icicle 事件循环

[Icicle](https://github.com/icicleio/icicle) 使用 Awaitables 和生成器来创建协程。

```
<?php
require 'vendor/autoload.php';

use Icicle\Loop;
use Icicle\Awaitable;

$coroutine = function() {
    yield Awaitable\resolve(1);
    yield Awaitable\resolve(2);
};

Loop\run(function() use ($coroutine) {
    $result = yield $coroutine();
    var_dump($result);
});
```

```
<?php
use Icicle\Loop;
use Icicle\Awaitable\resolve;

Loop\run(function() {
    $promise = resolve(1);
    $promise->then(function($value) {
        echo $value; // 1
    });
});
```

#### 第 70.3 节：使用 proc_open() 生成非阻塞进程

除非你安装诸如 `pthread` 之类的扩展，否则 PHP 没有并发运行代码的支持。有时可以通过使用 `proc_open()` 和 `stream_set_blocking()` 并异步读取它们的输出来绕过此限制。

`stream_set_blocking()`

如果我们将代码拆分为更小的块，我们可以将其作为多个子进程运行。然后使用 `stream_set_blocking()` 函数，我们可以使每个子进程也变为非阻塞。这意味着我们可以生成多个子进程，然后在循环中检查它们的输出（类似于事件循环）并等待直到它们全部完成。




## 第 70.3 节：使用 Event 扩展进行子进程管理

作为示例，我们可以有一个小型子进程，它只是运行一个循环，并在每次迭代中随机休眠 100-1000ms（注意，对于同一个子进程，延迟始终相同）。

![Image01421.jpg](img/Image01421.jpg)

然后主进程将生成子进程并读取它们的输出。我们可以将其分解为更小的代码块：

![Image01422.jpg](img/Image01422.jpg)

![Image01423.jpg](img/Image01423.jpg)

输出随后包含来自所有三个子进程的混合数据，因为它们是由 `fread()` 读取的（注意，在这种情况下 proc1 比其他两个早得多地结束了）：

![Image01424.jpg](img/Image01424.jpg)

## 第 70.4 节：使用 Event 和 DIO 读取串口

`DIO` 流目前不被 `Event` 扩展识别。没有干净的方法来获取封装在 `DIO` 资源中的文件描述符。但有一个变通方法：

| 函数 / 方法 | 说明 |
| :--- | :--- |
| `fopen` | 为端口打开流 |
| `stream_set_blocking` | 使流变为非阻塞 |
| `EventUtil::getSocketFd` | 从流中获取数字文件描述符 |
| `dio_fdopen` | 传递数字文件描述符并获取 DIO 资源 |

![Image01425.jpg](img/Image01425.jpg)

1. 使用 `fopen()` 为端口打开流。
2. 使用 `stream_set_blocking()` 使流变为非阻塞。
3. 使用 `EventUtil::getSocketFd()` 从流中获取数字文件描述符。
4. 将数字文件描述符传递给 `dio_fdopen()`（目前未文档化）并获取 DIO 资源。
5. 添加一个带有回调的 Event，用于监听文件描述符上的读取事件。
6. 在回调中消耗可用数据，并根据应用程序的逻辑进行处理。

**dio.php**

![Image01426.jpg](img/Image01426.jpg)

![Image01427.jpg](img/Image01427.jpg)

### 测试

在终端 A 中运行以下命令：

```bash
$ socat -d -d pty,raw,echo=0 pty,raw,echo=0
```

```text
2016/12/01 18:04:06 socat[16750] N PTY is /dev/pts/5
2016/12/01 18:04:06 socat[16750] N PTY is /dev/pts/8
2016/12/01 18:04:06 socat[16750] N starting data transfer loop with FDs [5,5] and [7,7]
```

输出可能有所不同。使用前几行中的 PTY（特别是 `/dev/pts/5` 和 `/dev/pts/8`）。

在终端 B 中运行上述脚本。您可能需要 root 权限：

![Image01429.jpg](img/Image01429.jpg)

在终端 C 中向第一个 PTY 发送字符串：

![Image01430.jpg](img/Image01430.jpg)

输出：

![Image01431.jpg](img/Image01431.jpg)

## 第 70.5 节：基于 Event 扩展的 HTTP 客户端

这是一个基于 `Event` 扩展的示例 HTTP 客户端类。

该类允许调度多个 HTTP 请求，然后异步运行它们。

**http-client.php**

![Image01432.jpg](img/Image01432.jpg)

```php
/**
 * 调度所有待处理的请求（事件）
 * @return void
 */
public function run() {
    $this->base->dispatch();
}

public function __destruct() {
    // 显式销毁连接对象，不要等待 GC。
    // 否则，EventBase 可能会被更早地释放。
    $this->connections = null;
}

/**
 * @brief 添加一个待处理的 HTTP 请求
 * @param string $address 主机名，或 IP
 * @param int $port 端口号
 * @param array $headers 额外的 HTTP 头部
 * @param int $cmd 一个 EventHttpRequest::CMD_* 常量
 * @param string $resource HTTP 请求资源，例如 '/page?a=b&c=d'
 * @return EventHttpRequest|false
 */
public function addRequest($address, $port, array $headers,
    $cmd = EventHttpRequest::CMD_GET, $resource = '/'
) {
    $conn = new EventHttpConnection($this->base, null, $address, $port);
    $conn->setTimeout(5);
    $req = new EventHttpRequest([$this, '_requestHandler'], $this->base);
    foreach ($headers as $k => $v) {
        $req->addHeader($k, $v, EventHttpRequest::OUTPUT_HEADER);
    }
    $req->addHeader('Host', $address, EventHttpRequest::OUTPUT_HEADER);
    $req->addHeader('Connection', 'close', EventHttpRequest::OUTPUT_HEADER);
    if ($conn->makeRequest($req, $cmd, $resource)) {
        $this->connections[] = $conn;
        return $req;
    }
    return false;
}

/**
 * @brief 处理一个 HTTP 请求
 * @param EventHttpRequest $req
 * @param mixed $unused
 * @return void
 */
public function _requestHandler($req, $unused) {
    if (is_null($req)) {
        echo "Timed out\n";
    } else {
        $response_code = $req->getResponseCode();
        if ($response_code == 0) {
            // ...
        }
    }
}
```

![Image01433.jpg](img/Image01433.jpg)

**test.php**

这是一个服务端示例脚本。

![Image01434.jpg](img/Image01434.jpg)

### 用法

![Image01435.jpg](img/Image01435.jpg)

### 示例输出

![Image01436.jpg](img/Image01436.jpg)

![Image01437.jpg](img/Image01437.jpg)

（已截断。）

注意，该代码专为在 `CLI SAPI` 中进行长期处理而设计。

## 第 70.6 节：基于 Ev 扩展的 HTTP 客户端

这是一个基于 `Ev` 扩展的示例 HTTP 客户端。

`Ev` 扩展实现了一个简单而强大的通用事件循环。它不提供特定于网络的观察者，但其 `I/O 观察者` 可用于 `socket` 的异步处理。以下代码展示了如何调度 HTTP 请求以进行并行处理。

**http-client.php**

![Image01438.jpg](img/Image01438.jpg)

```php
$this->http_client = $client;
$this->host        = $host;
$this->resource    = $resource;
$this->method      = $method;
// 获取 WWW 服务的端口
$this->service_port = getservbyname('www', 'tcp');
// 获取目标主机的 IP 地址
$this->address     = gethostbyname($this->host);
// 创建一个 TCP/IP socket
$this->socket      = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
if (!$this->socket) {
    throw new RuntimeException("socket_create() failed: reason: " .
        socket_strerror(socket_last_error()));
}
// 设置 O_NONBLOCK 标志
socket_set_nonblock($this->socket);
$this->conn_watcher = $this->http_client->getLoop()
    ->timer(0, 0., [$this, 'connect']);
}

public function __destruct() {
    $this->close();
}

private function freeWatcher(&$w) {
    if ($w) {
        $w->stop();
        $w = null;
    }
}

/**
 * 释放请求的所有资源
 */
private function close() {
    if ($this->socket) {
        socket_close($this->socket);
        $this->socket = null;
    }
    $this->freeWatcher($this->timeout_watcher);
    $this->freeWatcher($this->read_watcher);
    $this->freeWatcher($this->write_watcher);
    $this->freeWatcher($this->conn_watcher);
}

/**
 * 在 socket 上初始化连接
 * @return bool
 */
public function connect() {
    $loop = $this->http_client->getLoop();
    $this->timeout_watcher = $loop->timer($this->timeout, 0., [$this, '_onTimeout']);
    $this->write_watcher   = $loop->io($this->socket, Ev::WRITE, [$this, '_onWritable']);
    return socket_connect($this->socket, $this->address, $this->service_port);
}
```




# 第 70 章：事件循环

## 第 70.7 节：使用 Amp 事件循环

[Amp](https://github.com/amphp/amp/tree/v1.x) 利用 Promise（Awaitable 的另一种叫法）和生成器来创建协程。

```php
public function _onTimeout(EvTimer $w) {
    $w->stop();
    $this->close();
}

/**
 * 当套接字变为可写时调用的回调
 */
public function _onWritable(EvIo $w) {
    $this->timeout_watcher->stop();
    $w->stop();
    $in = implode("\r\n", [
        "{$this->method} {$this->resource} HTTP/1.1",
        "Host: {$this->host}",
        'Connection: Close',
    ]) . "\r\n\r\n";
    if (!socket_write($this->socket, $in, strlen($in))) {
        trigger_error("Failed writing $in to socket", E_USER_ERROR);
        return;
    }
    $loop = $this->http_client->getLoop();
    $this->read_watcher = $loop->io($this->socket, Ev::READ, [$this, '_onReadable']);
    // 继续运行循环
    $loop->run();
}

/**
 * 当套接字变为可读时调用的回调
 */
public function _onReadable(EvIo $w) {
    // 在非阻塞模式下 recv() 20 字节
    $ret = socket_recv($this->socket, $out, 20, MSG_DONTWAIT);
    if ($ret) {
        // 仍有数据可读。将读取的块追加到缓冲区。
        $this->buffer .= $out;
    } elseif ($ret === 0) {
        // 全部读取完毕
        printf("\n <<<< \n %s \n >>>>", rtrim($this->buffer));
        fflush(STDOUT);
        $w->stop();
        $this->close();
        return;
    }
    // 捕获 EINPROGRESS、EAGAIN 或 EWOULDBLOCK
    if (in_array(socket_last_error(), static::$e_nonblocking)) {
        return;
    }
    $w->stop();
    $this->close();
}
```

测试

```http
http://my-host.local/test.php
```

假设脚本正在打印 `$_GET` 的转储：

```bash
php http-client.php
```

那么命令的输出将类似于以下内容：

(已裁剪)

注意，在 PHP 5 中，sockets 扩展可能会为 `EINPROGRESS`、`EAGAIN` 和 `EWOULDBLOCK` errno 值记录警告。可以通过以下方式关闭日志：

```php
error_reporting(E_ALL & ~E_WARNING);
```

```php
// 使用 Amp\resolve() 转换为协程
$promise = Amp\resolve(queryStackOverflow(Dns\Record::NS));
list($ns, $type, $ttl) = // 我们只需要一个 NS 结果，而不是全部
    current(yield Amp\timeout($promise, 2000 /* 毫秒 */));
echo "The result of the fastest server to reply to our query was $ns";

} catch (Amp\TimeoutException $e) {
    echo "We've heard no answer for 2 seconds! Bye!";

} catch (Dns\NoRecordException $e) {
    echo "No NS records there? Stupid DNS nameserver!";
});
```

## 第 71 章：如何检测客户端 IP 地址

#### 第 71.1 节：HTTP_X_FORWARDED_FOR 的正确用法

鉴于最新的 [httpoxy](https://httpoxy.org/) 漏洞，还有一个变量被广泛滥用。

`HTTP_X_FORWARDED_FOR` 常用于检测客户端 IP 地址，但如果不进行任何额外检查，这可能会导致安全问题，特别是当该 IP 稍后用于身份验证或在未经清理的情况下用于 SQL 查询时。

大多数可用的代码示例都忽略了这样一个事实：`HTTP_X_FORWARDED_FOR` 实际上可以被视为客户端自身提供的信息，因此它不是检测客户端 IP 地址的可靠来源。一些示例确实添加了关于可能滥用的警告，但代码本身仍然缺乏任何额外的检查。

因此，这里提供了一个用 PHP 编写的函数示例，说明如何检测客户端 IP 地址，前提是你知道客户端可能位于代理后面，并且你知道该代理是可信的。如果你不知道任何可信代理，可以直接使用 `$_SERVER['REMOTE_ADDR']`。

```php
function getClientIp(array $trustedProxies = []) {
    $ip = $_SERVER['REMOTE_ADDR'];
    if (in_array($ip, $trustedProxies)) {
        $forwarded = $_SERVER['HTTP_X_FORWARDED_FOR'] ?? '';
        $ips = array_map('trim', explode(',', $forwarded));
        $ip = array_shift($ips);
    }
    return $ip;
}
```

## 第 72 章：在 PHP 中创建 PDF 文件

#### 第 72.1 节：PDFlib 入门

此代码要求你使用 [PDFlib 库](http://php.net/manual/en/ref.pdf.php) 才能正常运行。

```php
$p = new PDFlib();
if ($p->begin_document("", "") == 0) {
    die("Error: " . $p->get_errmsg());
}
$p->set_info("Creator", "hello.php");
$p->set_info("Author", "Rainer Schaaf");
$p->set_info("Title", "Hello world (PHP)!");
$p->begin_page_ext(595, 842, "");
$font = $p->load_font("Helvetica-Bold", "unicode", "");
$p->setfont($font, 24.0);
$p->set_text_pos(50, 700);
$p->show("Hello world!");
$p->continue_text("says PHP");
$p->end_page_ext("");
$p->end_document("");
$buf = $p->get_buffer();
$len = strlen($buf);
header("Content-type: application/pdf");
header("Content-Length: $len");
header("Content-Disposition: inline; filename=hello.pdf");
echo $buf;
$p = 0;
```

## 第 73 章：PHP 中的 YAML

#### 第 73.1 节：安装 YAML 扩展

YAML 不随标准 PHP 安装提供，而是需要作为 PECL 扩展安装。在 linux/unix 上，可以通过简单的命令安装：

```bash
pecl install yaml
```

```text
libyaml-devel
```

请注意，系统上必须安装 `libyaml-devel` 包，因为 PECL 包只是对 libYAML 调用的简单封装。

Windows 机器上的安装方式不同——你可以下载预编译的 DLL 或从源代码构建。

#### 第 73.2 节：使用 YAML 存储应用程序配置

[YAML](http://www.yaml.org/) 提供了一种存储结构化数据的方式。数据可以是一组简单的名称-值对，也可以是值甚至为数组的复杂层级数据。

请考虑以下 YAML 文件：

```yaml
database:
  host: localhost
  port: 3306
  username: root
  password: secret
  name: myapp
debug: true
paths:
  - /var/www
  - /opt/app
```

```text
config.yaml
```

假设它保存为 `config.yaml`。然后可以使用以下代码在 PHP 中读取此文件：

```php
$config = yaml_parse_file('config.yaml');
```

`print_r` 将产生以下输出：

```text
Array
(
    [database] => Array
        (
            [host] => localhost
            [port] => 3306
            [username] => root
            [password] => secret
            [name] => myapp
        )
    [debug] => 1
    [paths] => Array
        (
            [0] => /var/www
            [1] => /opt/app
        )
)
```

现在可以通过简单地使用数组元素来使用配置参数：

```php
$host = $config['database']['host'];
$port = $config['database']['port'];
```

## 第 74 章：使用 GD 进行图像处理

#### 第 74.1 节：图像输出

| [image](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) |
| --- |

可以使用 [image*](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) [函数](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) 创建图像，其中 * 代表文件格式。

它们具有通用的语法：

```php
imagepng($image, $to = null, $quality = -1, $filters = -1);
```

### 保存到文件

如果要将图像保存到文件，可以将文件名或打开的文件流作为 `$to` 传递。如果传递流，则无需关闭它，因为 GD 会自动关闭它。

例如，保存 PNG 文件：

```php
imagepng($im, 'test.png');
```

使用 `fopen` 时，请确保使用 `b` 标志而不是 `t` 标志，因为该文件是二进制输出。

```php
fopen("php://temp", "wb", $f) or fopen("php://memory", "wb", $f)
```

不要尝试将 `fopen("php://output", "wb")` 传递给它。由于调用后函数会关闭流，你将无法进一步使用它，例如检索其内容。

### 作为 HTTP 响应输出

如果你想直接将此图像作为响应返回（例如创建动态徽章），则不需要传递任何内容（或传递 `null`）作为第二个参数。但是，在 HTTP 响应中，你需要指定内容类型：

```php
header('Content-Type: image/png');
imagepng($im);
```

```text
image/png, image/gif
```

`$mimeType` 是你返回的格式的 MIME 类型。示例包括 `image/png` 和 `image/gif`。

```text
image/jpeg
```

。

### 写入变量

有两种方法可以写入变量。

#### 使用 OB（输出缓冲）

```php
ob_start();
imagepng($im);
$png_data = ob_get_clean();
```

#### 使用流包装器

你可能有很多理由不想使用输出缓冲。例如，你可能已经开启了 OB。因此，需要一种替代方案。

使用 `stream_wrapper_register` 函数，可以注册一个新的流包装器。因此，你可以将流传递给图像输出函数，稍后再检索它。

```php
class GlobalStream {
    public $varname;
    public function stream_open($path, $mode, $options, &$opened_path) {
        $this->varname = parse_url($path, PHP_URL_HOST);
        return true;
    }
    public function stream_write($data) {
        $GLOBALS[$this->varname] .= $data;
        return strlen($data);
    }
    public function stream_eof() { return true; }
    public function stream_close() { return true; }
}
stream_wrapper_register('global', 'GlobalStream');
$png_data = '';
imagepng($im, 'global://png_data');
echo strlen($png_data);
```

在本例中，`GlobalStream` 类将任何输入写入引用变量（即间接写入给定名称的全局变量）。稍后可以直接检索全局变量。

有一些特别需要注意的事项：



# 第 74 章：GD 库

## 第 74.1 节：流包装器

![](img/Image01459.jpg)一个完全实现的流包装器类应如 [此处](http://php.net/manual/en/stream.streamwrapper.example-1.php) 所示，但根据使用 `__call` 魔术方法的测试，内部函数仅会调用 `stream_open`、`stream_write` 和 `stream_close`。

`fopen` 调用不需要标志，但你至少应传递一个空字符串。这是因为 `fopen` 函数期望该参数，即使你在 `stream_open` 实现中不使用它，仍需要一个虚拟参数。

![](img/Image01460.jpg)根据测试，`stream_write` 会被多次调用。请记住使用 `.=`（连接赋值），而非 `=`（直接变量赋值）。

### 示例用法

| <img | |

| --- | |

![](img/Image01461.jpg) 在 `>` HTML 标签中，可以直接提供图片，而无需使用外部链接：`echo '<img src="data:image/png;base64,' . base64_encode($binary) . '">';`

#### 第 74.2 节：创建图片

要创建一张空白图片，请使用 `imagecreatetruecolor` 函数：

![](img/Image01462.jpg)

`$img` 现在是一个资源变量，代表一张宽 `$width` 像素、高 `$height` 像素的图片资源。注意宽度从左向右计算，高度从上向下计算。

图片资源也可以通过 [图片创建函数](http://php.net/manual/en/ref.image.php) 创建，例如：

![](img/Image01463.jpg)`imagecreatefrompng`、`imagecreatefromjpeg`

| imagecreatefrom | |

| --- | |

![](img/Image01464.jpg)其他 `*` 函数。

| imagedestroy | |

| --- | |

当不再有对图片资源的引用时，它们稍后可能会被释放。然而，为了立即释放内存（如果你正在处理许多大图片，这可能很重要），在图片不再使用时使用 `imagedestroy()` 可能是个好习惯。 ![](img/Image01465.jpg)`imagedestroy($image);`

### 转换图片

图片转换创建的图片在输出之前不会修改原图。因此，图片转换器可以简单到只需三行代码：

![](img/Image01466.jpg)

#### 第 74.3 节：图片裁剪与缩放

如果你有一张图片，想要创建一张具有新尺寸的新图片，可以使用 `imagecopyresampled` 函数：首先创建一张具有所需尺寸的新图片：

![](img/Image01467.jpg)

| createimagefrom | |

| --- | |

并将原始图片存储到一个变量中。为此，你可以使用其中一个 `*` 函数，其中 `*` 代表：

![](img/Image01468.jpg)
- jpeg
- gif
- png
- string

例如：

![](img/Image01469.jpg)

现在，通过 `imagecopyresampled` 将原始图片 (`src_img`) 的全部（或部分）复制到新图片 (`dst_img`) 中：

![](img/Image01470.jpg)

| src_ | | * and | | dst_ |

| --- | --- | --- | --- | --- |

要设置 `*` 尺寸，请使用下图：

![](img/Image01471.jpg)

现在，如果你想将整个源（初始）图片复制到整个目标区域（无裁剪）：

```
$src_x = $src_y = $dst_x = $dst_y = 0;
$dst_width = $width; // 新图片的宽度
$dst_height = $height; // 新图片的高度
$src_width = imagesx($src_img); // 初始图片的宽度
```
![](img/Image01472.jpg) `$src_height = imagesy($src_img); // 初始图片的高度`

## 第 75 章：Imagick

#### 第 75.1 节：第一步

### 安装

#### 在基于 Debian 的系统上使用 apt

![](img/Image01473.jpg)

#### 在 OSX/macOS 上使用 Homebrew

![](img/Image01474.jpg)

要查看使用 brew 方法安装的依赖项，请访问 [brewformulas.org/Imagemagick](http://brewformulas.org/Imagemagick)。

#### 使用二进制发行版

请参阅 [ImageMagick 网站](https://www.imagemagick.org/script/binary-releases.php#macosx) 上的说明。

### 用法

![](img/Image01475.jpg)

#### 第 75.2 节：将图片转换为 Base64 字符串

此示例展示如何将图片转换为 Base64 字符串（即可直接用于 `img` 标签 `src` 属性的字符串）。此示例专门使用 [Imagick](http://php.net/manual/en/intro.imagick.php) 库（也有其他可用库，如 [GD](http://php.net/manual/en/intro.image.php)）。

![](img/Image01476.jpg)

![](img/Image01477.jpg)

## 第 76 章：SOAP 服务端

#### 第 76.1 节：基础 SOAP 服务端

![](img/Image01478.jpg)

## 第 77 章：机器学习

#### 第 77.1 节：使用 PHP-ML 进行分类

机器学习中的分类问题是识别新观测值属于哪组类别的问题。分类属于监督式机器学习范畴。

![](img/Image01479.jpg)任何实现分类的算法都称为分类器。

PHP-ML 支持的分类器有：

![](img/Image01480.jpg)
- SVC（支持向量分类）
- k-近邻算法
- 朴素贝叶斯

所有分类器的 `train` 和 `predict` 方法相同。唯一的区别在于所用的底层算法。

### SVC（支持向量分类）

在开始预测新观测值之前，我们需要训练分类器。请看以下代码：

![](img/Image01481.jpg)

代码非常直观。上述使用的 `$cost` 是衡量我们多大程度上希望避免错误分类每个训练样本的指标。较小的 `$cost` 值可能导致误分类样本。默认值设为 `1.0`。

现在我们已经训练好分类器，可以开始进行实际预测。请看以下用于预测的代码：

![](img/Image01482.jpg)

上述分类器可以接收未分类的样本并预测其标签。`predict` 方法可以接收单个样本，也可以接收样本数组。

### k-近邻算法

该算法的分类器接受两个参数，可按如下方式初始化：

`$classifier = new KNearestNeighbors($neighbor_num = 4);`

![](img/Image01483.jpg) `$classifier = new KNearestNeighbors($neighbor_num = 3, new Minkowski($lambda = 4));`

`$neighbor_num` 是 [knn](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) 算法中要扫描的最近邻居数量，而第二个参数是距离度量，在第一种情况下默认为 `Euclidean`。更多关于 Minkowski 的信息请见 [此处](https://en.wikipedia.org/wiki/Minkowski_distance)。以下是如何使用此分类器的简短示例：

![](img/Image01484.jpg)

### NaiveBayes 分类器

| 贝叶斯定理 | |

| --- | |

NaiveBayes 分类器基于贝叶斯定理，构造函数不需要任何参数。

以下代码演示了一个简单的预测实现：

![](img/Image01485.jpg)

### 实际案例

到目前为止，我们在所有案例中只使用了整数数组，但实际情况并非如此。因此让我尝试描述一个如何使用分类器的实际场景。

| mm | | , | | 10 mm |

| --- | --- | --- | --- | --- |

| 10 mm | | , | | 20 mm |

| --- | --- | --- | --- | --- |

![](img/Image01486.jpg) ![](img/Image01487.jpg)假设你有一个存储自然界花卉特征的应用程序。为简单起见，我们可以考虑花瓣的颜色和长度。这两个特征将用于训练数据。颜色较简单，你可以为每种颜色分配一个整数值；对于长度，你可以定义范围，如 `(0)=1`、`()=2`。用初始数据训练你的分类器。现在，你的某位用户需要识别他后院生长的花卉种类。他所做的就是选择花的颜色并添加花瓣长度。你运行的分类器可以检测出花的类型（“上述示例中的标签”）。

#### 第 77.2 节：回归

| PHP | | - | | ML |

| --- | --- | --- | --- | --- |

在使用 PHP-ML 进行分类时，我们为新观测值分配标签。回归几乎相同，区别在于输出值不是类别标签，而是连续值。它广泛用于预测和预报。PHP-ML 支持以下回归算法：

![](img/Image01488.jpg)
- 支持向量回归
- 最小二乘线性回归

回归具有与分类中相同的 `train` 和 `predict` 方法。

### 支持向量回归

这是 SVM（支持向量机）的回归版本。第一步与分类一样，是训练模型：

![](img/Image01489.jpg)




# 回归

在回归中，`targets` 不是类标签，这与分类相反。这是两者的区别因素之一。使用数据训练模型后，我们可以开始进行实际预测。

![](img/Image01490.jpg)

注意，预测返回的值在目标范围之外。

## 最小二乘线性回归

该算法使用最小二乘法来近似解。以下演示了训练和预测的简单代码：

![](img/Image01491.jpg)

PHP-ML 还提供了多元线性回归选项。示例代码如下：

```
$samples = [[73676, 1996], [77006, 1998], [10565, 2000], [146088, 1995], [15000, 2001], [65940, 2000], [9300, 2000], [93739, 1996], [153260, 1994], [17764, 2002], [57000, 1998], [15000, 2000]];

$targets = [2000, 2750, 15500, 960, 4400, 8800, 7100, 2550, 1025, 5900, 4600, 4400];

$regression = new LeastSquares();

$regression->train($samples, $targets);

$regression->predict([60000, 1996]) // return 4094.82
```

当多个因素或特征共同决定结果时，多元线性回归特别有用。

## 实际案例

现在让我们看一个回归在现实场景中的应用。

![](img/Image01493.jpg)

假设你运营一个非常受欢迎的网站，但流量不断变化。你需要一种解决方案，能在任何给定时间预测所需部署的服务器数量。假设你的托管提供商提供了一个用于生成服务器的 API，且每台服务器需要 15 分钟启动。基于以往的流量数据和回归分析，你可以预测任何时刻将访问你应用程序的流量。利用该知识，你可以在流量激增前 15 分钟启动服务器，从而防止应用程序离线。

#### 第 77.3 节：聚类

聚类是将相似对象归类在一起。它广泛用于模式识别。聚类属于无监督机器学习，因此不需要训练。PHP-ML 支持以下聚类算法：

![](img/Image01494.jpg)

- `k-Means`
- `dbscan`

### k-Means

`k-Means` 将数据分成 `n` 个方差相等的组。这意味着我们需要传入一个数字 `n`，即我们需要的聚类数量。以下代码将有助于更清晰地理解：

![](img/Image01495.jpg)

注意，输出包含 3 个数组，因为 `KMeans` 构造函数中 `n` 的值为 3。构造函数中还可以有一个可选的第二个参数，即初始化方法。例如：

![](img/Image01496.jpg)

`INIT_RANDOM` 在尝试确定聚类时放置完全随机的质心。但为了防止质心离数据太远，它受数据空间边界的限制。

默认构造函数的初始化方法是 [kmeans++](https://en.wikipedia.org/wiki/K-means%2B%2B)，它以智能方式选择质心以加快进程。

### DBSCAN

与 `KMeans` 不同，`DBSCAN` 是一种基于密度的聚类算法，这意味着我们不需要传入决定结果中聚类数量的 `n`。相反，它需要两个参数才能工作：

1. `$minSamples`：一个聚类中应存在的最小对象数量
2. `$epsilon`：两个样本被视为同一聚类的最大距离

快速示例如下：

![](img/Image01497.jpg)

代码基本上是不言自明的。一个主要区别是，无法像 `KMeans` 那样知道输出数组中的元素数量。

## 实际案例

让我们看看在现实场景中使用聚类的情况。

![](img/Image01498.jpg)

聚类广泛用于模式识别和数据挖掘。假设你有一个内容发布应用程序。为了留住用户，他们应该看到自己喜欢的内容。为简单起见，假设如果他们在特定网页上停留超过一分钟并滚动到底部，则表示他们喜欢该内容。你的每个内容都将有一个唯一标识符，用户也是如此。基于此进行聚类，你将了解哪些用户群体具有相似的内容偏好。这反过来可用于推荐系统：如果同一聚类中的某些用户喜欢该文章，那么其他用户也会喜欢，并可在你的应用程序中作为推荐展示。

## 第 78 章：缓存

#### 第 78.1 节：使用 Memcache 进行缓存

| key | | - | | value |
| --- | --- | --- | --- | --- |

Memcache 是一个分布式对象缓存系统，用于存储小数据。在将 Memcache 代码调用到 PHP 之前，你需要确保它已安装。这可以使用 PHP 中的 `class_exists` 方法完成。一旦验证模块已安装，你就可以开始连接到 Memcache 服务器实例。

![](img/Image01499.jpg)

这将验证 Memcache PHP 驱动程序已安装，并连接到在 localhost 上运行的 Memcache 服务器实例。

![](img/Image01500.jpg)

Memcache 作为守护进程运行，称为 `memcached`。

在上面的示例中，我们只连接到单个实例，但你也可以使用以下方式连接到多个服务器：

![](img/Image01501.jpg)

注意，在这种情况下，与 `connect` 不同，直到你尝试存储或获取值时才会有活动连接。

在缓存中，有三个重要的操作需要实现：

1. **存储数据**：向 Memcached 服务器添加新数据
2. **获取数据**：从 Memcached 服务器获取数据
3. **删除数据**：从 Memcached 服务器删除已存在的数据

### 存储数据

`$cache` 或 `memcached` 类对象有一个 `set` 方法，它接受键、值和保存值的时间（ttl）。

![](img/Image01502.jpg)

这里 `$ttl` 或生存时间是你希望 Memcache 在服务器上存储键值对的时间（以秒为单位）。

### 获取数据

`$cache` 或 `memcached` 类对象有一个 `get` 方法，它接受一个键并返回相应的值。

![](img/Image01503.jpg)

### 删除数据

有时你可能需要删除某些缓存值。`$cache` 或 `memcache` 实例有一个可用于此目的的 `delete` 方法。

![](img/Image01504.jpg)

### 缓存小场景

假设一个简单的博客。登录页面将有多个帖子，每次页面加载都从数据库获取。为了减少 SQL 查询，我们可以使用 Memcached 缓存帖子。这是一个非常小的实现：

![](img/Image01505.jpg)

#### 第 78.2 节：使用 APC Cache 进行缓存

Alternative PHP Cache (APC) 是一个免费开放的 PHP 操作码缓存。其目标是为缓存和优化 PHP 中间代码提供一个免费、开放且健壮的框架。[安装](http://php.net/manual/en/apc.installation.php)

![](img/Image01506.jpg)

### 添加缓存：

![](img/Image01507.jpg)

### 删除缓存：

![](img/Image01508.jpg)

### 设置缓存示例：

![](img/Image01509.jpg)

![](img/Image01510.jpg)

### 性能：

APC 比 Memcached 快近 [5 倍](https://www.percona.com/blog/2006/09/27/apc-or-memcached/)。

## 第 79 章：自动加载入门

#### 第 79.1 节：作为框架解决方案一部分的自动加载

![](img/Image01511.jpg)

得益于我们的通用自动加载器，我们可以访问任何遵循我们自动加载命名约定的类。在本例中，我们的约定很简单：所需的类必须在同一目录下有一个以类命名并以 ".php" 结尾的文件。请注意，类名与文件名完全匹配。

如果没有自动加载，我们将不得不手动 `require` 基类。如果我们建立了一个完整的动物园，我们将有成千上万个 `require` 语句，这些语句可以更容易地被单个自动加载器替换。




# PHP 自动加载与 SPL 数据结构

## PHP 自动加载概述

归根结底，PHP 自动加载是一种帮助你编写更少机械代码、从而专注于解决业务问题的机制。你只需定义一种将类名映射到文件名的策略。你可以像这里一样实现自己的自动加载策略。或者，你可以使用 PHP 社区采用的标准策略：[PSR-0](http://www.php-fig.org/psr/psr-0/) 或 [PSR-4](http://www.php-fig.org/psr/psr-4/)。又或者，你可以使用 [composer](http://www.getcomposer.org/) 来通用地定义和管理这些依赖。

#### 第 79.2 节：内联类定义，无需加载

![](img/Image01512.jpg)

![](img/Image01513.jpg)

| new Animal |
| --- |

PHP 在执行前就知道 `Animal` 是什么，因为 PHP 是自上而下读取源文件的。但如果我们想在许多地方创建新的 `Animal` 对象，而不仅仅是在定义它的源文件中，该怎么办？为此，我们需要加载类定义。

#### 第 79.3 节：使用 require 手动加载类

![](img/Image01514.jpg)

这里有三个文件。一个文件 (`Animal.php`) 定义了类。除了定义类之外，该文件没有副作用，并将关于 "Animal" 的所有知识整齐地保存在一个地方。它易于版本控制，也易于复用。

| new Animal |
| --- |

两个文件通过手动 `require` 来使用 `Animal.php` 文件。同样，PHP 自上而下读取源文件，因此 `require` 会去查找 `Animal.php` 文件，并在调用 `new Animal` 之前使 `Animal` 类定义可用。

| new Animal |
| --- |

现在想象一下，如果我们有几十或几百种情况想要执行 `new Animal`。那将需要许多许多 `require` 语句（双关语，原文 "require" 既是函数名也是“需要”之意），编写起来非常繁琐。

#### 第 79.4 节：自动加载替代手动类定义加载

![](img/Image01515.jpg)

![](img/Image01516.jpg)

| require "Animal.php" |
| --- |

将其与其他示例进行比较。注意 `require "Animal.php"` 是如何被 `require "autoload.php"` 替换的。我们仍然在运行时包含一个外部文件，但包含的不再是特定的类定义，而是能够包含*任意*类的逻辑。这是一种间接层，简化了我们的开发。我们不再为每个需要的类编写一个 `require`，而是为所有类编写一个 `require`。我们可以用 1 个 `require` 替换 N 个 `require`。

神奇之处在于 [`spl_autoload_register`](http://php.net/manual/en/function.spl-autoload-register.php)。此 PHP 函数接受一个闭包，并将该闭包添加到闭包队列中。当 PHP 遇到一个没有定义的类时，PHP 将类名传递给队列中的每个闭包。如果调用闭包后类存在，PHP 将恢复之前的业务。如果尝试完整个队列后类仍不存在，PHP 会崩溃并报错 "Class 'Whatever' not found."（找不到类 'Whatever'）。

#### 第 79.5 节：使用 Composer 进行自动加载

| vendor | / | autoload | . | php |
| --- | --- | --- | --- | --- |

Composer 会生成一个 `vendor/autoload.php` 文件。

你只需包含此文件，即可免费获得自动加载功能。

```
require __DIR__ . '/vendor/autoload.php';
```

这使得处理第三方依赖变得非常容易。

| composer | . | json |
| --- | --- | --- |

你也可以通过在 `composer.json` 中添加 autoload 部分，将自己的代码添加到自动加载器中。

![](img/Image01517.jpg)

在此部分中定义自动加载映射。在本例中，它是一个 [PSR-4](http://www.php-fig.org/psr/psr-4/) 映射，将命名空间映射到项目根文件夹下的 `src` 目录，该目录与 `vendor` 目录处于同一级别：即 `src` 目录。示例文件名为 `src/Foo.php`，其中包含 `YourApplicationNamespace\Foo` 类。

| dump | - | autoload |
| --- | --- | --- |

| vendor | / | autoload | . | php |
| --- | --- | --- | --- | --- |

**重要提示：** 向 autoload 部分添加新条目后，必须重新运行命令 `dump-autoload`，以便使用新信息重新生成并更新 `vendor/autoload.php` 文件。

| PSR | -4 autoloading, Composer also supports | PSR |
| --- | --- | --- |

除了 `PSR-0`，Composer 还支持 classmap 和 files 自动加载。详见 [autoload reference](https://getcomposer.org/doc/04-schema.md#autoload) 了解更多信息。

| vendor | / | autoload | . | php |
| --- | --- | --- | --- | --- |

当你包含 `vendor/autoload.php` 文件时，它将返回一个 Composer Autoloader 实例。你可以将 include 调用的返回值存储在变量中，并添加更多命名空间。例如，这对于在测试套件中自动加载类非常有用。

![](img/Image01518.jpg)

## 第 80 章：SPL 数据结构

#### 第 80.1 节：SplFixedArray

### 与 PHP 数组的区别

PHP 默认的 Array 类型实际上是作为有序哈希映射实现的，它允许我们创建由键/值对组成的数组，其中值可以是任意类型，键可以是数字或字符串。然而，这并非数组的传统创建方式。

![](img/Image01519.jpg)

因此，正如你从该图解中所见，普通 PHP 数组更像是一个有序的键/值对集合，其中每个键可以映射到任意值。请注意，在这个数组中，键既有数字也有字符串，值也有不同类型，且键与元素的顺序无关。

![](img/Image01520.jpg)

![](img/Image01521.jpg)

因此，上述代码将给出我们完全预期的结果。

```
9 => foo
1 => 4.2
bar =>
```

普通 PHP 数组也是动态调整大小的。当我们向数组推入或弹出值时，它们会自动增长和收缩。

然而，在传统数组中，大小是固定的，且完全由同一类型的值组成。此外，不是通过键，而是通过索引来访问每个值，该索引可通过其在数组中的偏移量推断得出。

![](img/Image01522.jpg)

| type size | * | n |
| --- | --- | --- |

既然我们知道给定类型的大小和数组的固定大小，偏移量就是 `type size * n`，其中 n 代表值在数组中的位置。因此，在上面的示例中，`$arr[0]` 给我们 1（数组中的第一个元素），`$arr[1]` 给我们 2，依此类推。

然而，`SplFixedArray` 并不限制值的类型。它仅将键限制为数字类型。它也是固定大小的。

这使得 `SplFixedArray` 在一个特定方面比普通 PHP 数组更高效。它们更紧凑，因此占用更少的内存。

### 实例化数组

```
count($arr)
```

```
foreach ($arr as $k => $v)
```

`SplFixedArray` 作为对象实现，但由于它实现了 `ArrayAccess` 接口，因此可以使用与访问普通 PHP 数组相同的熟悉语法来访问。它还实现了 `Countable` 和 `Iterator` 接口，因此其行为与你习惯的 PHP 数组行为相同（即 `count($arr)` 和 `foreach ($arr as $k => $v)` 等在 `SplFixedArray` 中的工作方式与普通 PHP 数组完全相同）。

`SplFixedArray` 构造函数接受一个参数，即数组的大小。

![](img/Image01523.jpg)

![](img/Image01524.jpg)

这将给你预期的结果。

```
0 => foo
1 => bar
2 => baz
3 =>
```

这也如预期般工作。

![](img/Image01525.jpg)

给我们……

```
int(4)
```

请注意，在 `SplFixedArray` 中，与普通 PHP 数组不同，键确实描绘了元素在数组中的顺序，因为它是真正的索引，而不仅仅是一个映射。

### 调整数组大小

```
unset($arr[1]) will result in $arr[1] === null, count($arr)
```

只需记住，因为数组大小固定，count 将始终返回相同的值。所以虽然执行 `unset($arr[1])`，`count($arr)` 仍然是 4。

因此，要调整数组大小，你需要调用 `setSize` 方法。

![](img/Image01526.jpg)



现在我们得到... `int(3) 0 => foo 1 => 2 => baz` 导入到 `SplFixedArray` 并从 `SplFixedArray` 导出

你也可以使用 `fromArray` 和 `toArray` 方法将普通的 PHP 数组导入到 `SplFixedArray` 中并从中导出。

![](img/Image01527.jpg)

1 2 3 4 5

反向操作。

![](img/Image01528.jpg)

![](img/Image01529.jpg)

1 2 3 4 5

## 第 81 章：IMAP

#### 第 81.1 节：连接到邮箱

要对 IMAP 账户执行任何操作，首先需要连接到它。为此，你需要指定一些必需的参数：

- 邮件服务器的服务器名称或 IP 地址
- 你希望连接的端口

| 协议 | 端口 |
| --- | --- |
| IMAP | 143 或 993 (安全) |
| POP | 110 或 995 (安全) |
| SMTP | 25 或 465 (安全) |
| NNTP | 119 或 563 (安全) |

- 连接标志（见下文）

| 标志 | 说明 | 选项 |
| --- | --- | --- |
| `service` | 使用哪种服务 | `imap`, `pop3`, `nntp`, `smtp` |
| `user` | 用于在服务器上登录的远程用户名 | |
| `authuser` | 远程认证用户；如果指定了此项，则使用该用户名的密码（例如管理员） | |
| `anonymous` | 作为匿名用户远程访问 | |
| `debug` | 在应用程序的调试日志中记录协议遥测数据 | |
| `secure` | 不要通过网络传输明文密码 | |
| `norsh` | 不要使用 rsh 或 ssh 来建立预认证的 IMAP 会话 | |
| `ssl` | 使用安全套接字层加密会话 | |
| `validate-cert` | 验证来自 TLS/SSL 服务器的证书 | 启用 |
| `novalidate-cert` | 不验证来自 TLS/SSL 服务器的证书，如果服务器使用自签名证书则需要此项。谨慎使用 | 禁用 |
| `tls` | 强制使用 start-TLS 加密会话，并拒绝连接到不支持它的服务器 | |
| `notls` | 不要使用 start-TLS 加密会话，即使服务器支持它 | |
| `readonly` | 请求以只读模式打开邮箱（仅限 IMAP；在 NNTP 上被忽略，在 SMTP 和 POP3 上会报错） | |

你的连接字符串看起来会像这样：

![](img/Image01531.jpg)

请注意，如果连接字符串中的任何字符是非 ASCII 字符，则必须使用 `utf7_encode($string)` 对其进行编码。

要连接到邮箱，我们使用 `imap_open` 命令，它返回一个指向流的资源值：

![](img/Image01532.jpg)

#### 第 81.2 节：安装 IMAP 扩展

要在 PHP 中使用 [IMAP 函数](http://www.php.net/imap)，你需要安装 IMAP 扩展：

**Debian/Ubuntu 与 PHP5**

![](img/Image01533.jpg)

**Debian/Ubuntu 与 PHP7**

![](img/Image01534.jpg)

**基于 YUM 的发行版**

![](img/Image01535.jpg)

**Mac OS X 与 php5.6**

![](img/Image01536.jpg)

#### 第 81.3 节：列出邮箱中的所有文件夹

一旦你连接到了邮箱，你会想看看里面的内容。第一个有用的命令是 `imap_list`。第一个参数是从 `imap_open` 获取的资源，第二个是你的邮箱字符串，第三个是模糊搜索字符串（`*` 用于匹配任何模式）。

![](img/Image01537.jpg)

输出应该看起来类似于这样：

![](img/Image01538.jpg)

你可以使用第三个参数来过滤这些结果，如下所示：

![](img/Image01539.jpg)

```
$folders = imap_list($mailbox, "{imap.example.com:993/imap/tls/secure}", "*.Sent");
```

| Sent |
| --- |

现在结果只包含名称中带有 `.` 的条目：

![](img/Image01540.jpg)

**注意**：使用 `*` 作为模糊搜索将递归返回所有匹配项。如果你使用 `%`，它将仅返回当前指定文件夹中的匹配项。

#### 第 81.4 节：在邮箱中查找消息

你可以使用 `imap_headers` 返回邮箱中所有消息的列表。

![](img/Image01541.jpg)

结果是一个字符串数组，具有以下模式：

![](img/Image01542.jpg)

```
[标志] [消息-ID])[DD-MM-YYYY] [发件人地址] [主题截断至 25 字符] ([大小] 字符)
```

以下是每行可能的样子示例：

```
A       1)19-Aug-2016 someone@example.com Message Subject (1728 chars)
D       2)19-Aug-2016 someone@example.com RE: Message Subject (22840 chars)
U       3)19-Aug-2016 someone@example.com RE: RE: Message Subject (1876 chars)
N       4)19-Aug-2016 someone@example.com RE: RE: RE: Message Subje (1741 chars)
```

| 符号 | 标志 | 含义 |
| --- | --- | --- |
| A | Answered | 消息已回复 |
| D | Deleted | 消息已删除（但未移除） |
| F | Flagged | 消息被标记/加星以引起注意 |
| N | New | 消息是新的且未被查看 |
| R | Recent | 消息是新的且已被查看 |
| U | Unread | 消息未读 |
| X | Draft | 消息是草稿 |

请注意，此调用可能需要相当长的时间来运行，并可能返回一个非常大的列表。

```
imap_num_msg($mailbox)
```

另一种方法是根据需要单独加载消息。你的每封电子邮件都会被分配一个从 1（最旧）到 `imap_num_msg($mailbox)` 值的 ID。

有许多函数可以直接访问电子邮件，但最简单的方法是使用 `imap_header`，它返回结构化的头部信息：

![](img/Image01544.jpg)

![](img/Image01545.jpg)

## 第 82 章：HTTP 认证

在本主题中，我们将制作一个 HTTP 头部认证脚本。

#### 第 82.1 节：简单认证

**请注意：仅将此代码放在页面的头部，否则将无法工作！**

![](img/Image01546.jpg)

## 第 83 章：WebSockets

Socket 扩展的使用实现了基于流行的 BSD sockets 的套接字通信函数的低级接口，提供了作为套接字服务器和客户端的可能性。

#### 第 83.1 节：简单的 TCP/IP 服务器

基于 PHP 手册中找到的示例的最小示例：[`php.net/manual/en/sockets.examples.php`](http://php.net/manual/en/sockets.examples.php)

```
telnet 127.0.0.1 5000
```

创建一个监听 5000 端口的 websocket 脚本。使用 putty、终端运行（localhost）。

此脚本会回复你发送的消息（作为 ping-back）。

![](img/Image01547.jpg)

![](img/Image01548.jpg)

## 第 84 章：BC Math（二进制计算器）

| 函数 | 说明 | 参数 |
| --- | --- | --- |
| `bcadd` | 将两个任意精度数字相加。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |
| `bccomp` | 比较两个任意精度数字。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：比较中使用的小数点后位数。 |
| `bcdiv` | 将两个任意精度数字相除。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |
| `bcmod` | 获取任意精度数字的模数。 | `left_operand` (string)：左操作数。<br>`modulus` (string)：模数。 |
| `bcmul` | 将两个任意精度数字相乘。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |




# BCMath 函数参考

## 函数参数

### `bcpow`
将任意精度数字提升到另一个数字的幂。

| 参数 | 描述 |
| --- | --- |
| `left_operand` | 左操作数，以字符串形式表示。 |
| `right_operand` | 右操作数，以字符串形式表示。 |
| `scale` | 可选参数，用于设置结果中小数点后的位数。 |

### `bcpowmod`
将任意精度数字提升到另一个数字的幂，并按指定模数取模。

| 参数 | 描述 |
| --- | --- |
| `left_operand` | 左操作数，以字符串形式表示。 |
| `right_operand` | 右操作数，以字符串形式表示。 |
| `modulus` | 模数，以字符串形式表示。 |
| `scale` | 可选参数，用于设置结果中小数点后的位数。 |

### `bcscale`
为所有 BC 数学函数设置默认的 scale 参数。

| 参数 | 描述 |
| --- | --- |
| `scale` | 比例因子。 |

### `bcsqrt`
获取任意精度数字的平方根。

| 参数 | 描述 |
| --- | --- |
| `operand` | 操作数，以字符串形式表示。 |
| `scale` | 可选参数，用于设置结果中小数点后的位数。 |

### `bcsub`
从一个任意精度数字中减去另一个。

| 参数 | 描述 |
| --- | --- |
| `left_operand` | 左操作数，以字符串形式表示。 |
| `right_operand` | 右操作数，以字符串形式表示。 |
| `scale` | 可选参数，用于设置结果中小数点后的位数。 |

## 概述
二进制计算器可用于计算任意大小和精度的数字，精度高达 2147483647-1 位小数，以字符串格式表示。二进制计算器比 PHP 的浮点数计算更精确。

#### 第 84.1 节：在 32 位系统上使用 bcmath 读/写二进制长整型

在 32 位系统上，大于 `0x7FFFFFFF` 的整数无法以原始方式存储，而介于 `0x0000000080000000` 和 `0x7FFFFFFFFFFFFFFF` 之间的整数可以在 64 位系统上以原始方式存储（有符号长长整型），但不能在 32 位系统上存储。然而，由于 64 位系统和许多其他语言支持存储有符号长长整型，有时有必要按精确值存储此范围的整数。有几种方法可以做到这一点，例如创建一个包含两个数字的数组，或将整数转换为其十进制人类可读形式。这有几个优点，例如方便向用户展示，以及能够直接使用 bcmath 对其进行操作。

[`pack`](https://php.net/pack) / [`unpack`](https://php.net/unpack) 方法可用于在数字的二进制字节和十进制形式（均为字符串类型，但一个是二进制，一个是 ASCII）之间转换，但它们在 32 位系统上总会尝试将 ASCII 字符串转换为 32 位整数。以下代码片段提供了一种替代方案：

```php
/** 64 位系统使用 pack("J") 或 pack("p") */
function writeLong(string $ascii): string {
    if (bccomp($ascii, "0") === -1) { // if $ascii < 0
        // 18446744073709551616 等于 (1 << 64)
        // 记得加上引号，否则该数字会被解析为浮点数字面量
        $ascii = bcadd($ascii, "18446744073709551616");
    }
    // "n" 是大端序 16 位无符号短整型。小端序使用 "v"。
    return pack("n", bcmod(bcdiv($ascii, "281474976710656"), "65536")) .
           pack("n", bcmod(bcdiv($ascii, "4294967296"), "65536")) .
           pack("n", bcdiv($ascii, "65536"), "65536")) .
           pack("n", bcmod($ascii, "65536"));
}

function readLong(string $binary): string {
    $result = "0";
    $result = bcadd($result, unpack("n", substr($binary, 0, 2)));
    $result = bcmul($result, "65536");
    $result = bcadd($result, unpack("n", substr($binary, 2, 2)));
    $result = bcmul($result, "65536");
    $result = bcadd($result, unpack("n", substr($binary, 4, 2)));
    $result = bcmul($result, "65536");
    $result = bcadd($result, unpack("n", substr($binary, 6, 2)));
    // if $binary is a signed long long
    // 9223372036854775808 等于 (1 << 63) （注意该表达式甚至在 64 位系统上也无法工作）
    if (bccomp($result, "9223372036854775808") !== -1) { // if $result >= 9223372036854775807
        $result = bcsub($result, "18446744073709551616"); // $result -= (1 << 64)
    }
    return $result;
}
```

#### 第 84.2 节：BCMath 与浮点数算术运算的比较

### `bcadd` 对比 float+float
```php
var_dump('10' + '-9.99');         // float(0.0099999999999998)
var_dump(10 + -9.99);             // float(0.0099999999999998)
var_dump(10.00 + -9.99);          // float(0.0099999999999998)
var_dump(bcadd('10', '-9.99', 20)); // string(22) "0.01000000000000000000"
```

### `bcsub` 对比 float-float
```php
var_dump('10' - '9.99');         // float(0.0099999999999998)
var_dump(10 - 9.99);             // float(0.0099999999999998)
var_dump(10.00 - 9.99);          // float(0.0099999999999998)
var_dump(bcsub('10', '9.99', 20)); // string(22) "0.01000000000000000000"
```

### `bcmul` 对比 int*int
```php
var_dump('5.00' * '2.00');       // float(10)
var_dump(5.00 * 2.00);           // float(10)
var_dump(bcmul('5.0', '2', 20));   // string(4) "10.0"
var_dump(bcmul('5.000', '2.00', 20)); // string(8) "10.00000"
var_dump(bcmul('5', '2', 20));     // string(2) "10"
```

### `bcmul` 对比 float*float
```php
var_dump('1.6767676767' * '1.6767676767'); // float(2.8115498416259)
var_dump(1.6767676767 * 1.6767676767);     // float(2.8115498416259)
var_dump(bcmul('1.6767676767', '1.6767676767', 20)); // string(22) "2.81154984162591572289"
```

### `bcdiv` 对比 float/float
```php
var_dump('10' / '3.01');         // float(3.3222591362126)
var_dump(10 / 3.01);             // float(3.3222591362126)
var_dump(10.00 / 3.01);          // float(3.3222591362126)
var_dump(bcdiv('10', '3.01', 20)); // string(22) "3.32225913621262458471"
```

## 第 85 章：Docker 部署

[Docker](http://www.docker.com/) 是一种非常流行的容器解决方案，广泛用于在生产环境中部署代码。它使管理和扩展 Web 应用程序和微服务变得更加容易。

#### 第 85.1 节：获取 PHP 的 docker 镜像

为了在 docker 上部署应用程序，首先我们需要从注册表获取镜像。

```bash
docker pull php:7.0-apache
```

这将从官方 PHP 仓库获取最新版本的镜像。一般来说，PHP 通常用于部署 Web 应用程序，因此我们需要一个 HTTP 服务器来配合镜像。该镜像预装了 apache，使部署变得轻松无忧。

#### 第 85.2 节：编写 Dockerfile

`Dockerfile` 用于配置我们将用 Web 应用程序代码构建的自定义镜像。在项目根文件夹中创建一个新文件 `Dockerfile`，然后放入以下内容：

```dockerfile
FROM php:7.0-apache
COPY php.ini /usr/local/etc/php/
COPY . /var/www/html/
EXPOSE 80
```

第一行非常直观，用于描述构建新镜像时应使用哪个基础镜像。该行也可以更改为注册表中的任何其他特定 PHP 版本。

第二行只是将 `php.ini` 文件上传到我们的镜像中。你可以随时将该文件更改为其他自定义文件位置。

第三行会将当前目录中的代码复制到 `/var/www/html/`，这是我们的网站根目录。请记住镜像内部的 `/var/www/html/`。

最后一行只会在 docker 容器内打开 80 端口。

### 忽略文件

创建 `.dockerignore` 文件以从构建上下文中排除文件。




在某些情况下，可能会有一些你不想放到服务器上的文件，比如环境配置等。假设我们的环境配置在 `.env` 中。现在，为了忽略此文件，我们只需将其添加到代码库根文件夹下的 `.dockerignore` 中即可。

## 第 85.3 芄：构建镜像

构建镜像并非 PHP 特有，但为了构建上述描述的镜像，我们可以简单地使用：

```
docker build -t my-php-app .
```

镜像构建完成后，你可以使用以下命令进行验证：

```
docker images
```

这将列出你系统中安装的所有镜像。

#### 第 85.4 节：启动应用容器

镜像准备就绪后，我们可以启动并运行它。要从镜像创建容器，请使用：

```
docker run -p 80:80 -d my-php-app
```

| 参数 | 说明 |
| --- | --- |
| `-p 80:80` | 将服务器的 80 端口转发到容器的 80 端口。 |
| `-d` | 指示容器应作为后台任务运行。 |
| `my-php-app` | 指定用于构建容器的镜像。 |

### 检查容器

要检查正在运行的容器，只需使用：

```
docker ps
```

这将列出 Docker 守护进程上所有正在运行的容器。

### 应用日志

日志对于调试应用程序至关重要。要查看日志，请使用：

```
docker logs <container_id>
```

## 第 86 章：APCu

APCu 是 PHP 的共享内存键值存储。内存由同一池的 PHP-FPM 进程共享。存储的数据在请求之间持久化。

#### 第 86.1 节：遍历条目

[`APCUIterator`](http://php.net/manual/en/class.apcuiterator.php) 允许遍历缓存中的条目：

```php
$iterator = new APCUIterator();
foreach ($iterator as $entry) {
    // ...
}
```

迭代器可以使用可选的正则表达式进行初始化，以仅选择键匹配的条目：

```php
$iterator = new APCUIterator('/^user_/');
```

可以通过以下方式获取单个缓存条目的信息：

```php
apcu_entry('key', function($key) {
    return 'value';
});
```

#### 第 86.2 节：简单的存储与检索

[`apcu_store`](http://php.net/manual/de/function.apcu-store.php) 可用于存储，[`apcu_fetch`](http://php.net/manual/de/function.apcu-fetch.php) 用于检索值：

```php
apcu_store('key', 'value');
$value = apcu_fetch('key');
```

#### 第 86.3 节：存储信息

[`apcu_cache_info`](http://php.net/manual/en/function.apcu-cache-info.php) 提供关于存储及其条目的信息：

```php
$info = apcu_cache_info();
print_r($info);
```

## 第 87 章：PHP 内置服务器

| 选项 | 说明 |
| --- | --- |
| `-S` | 告诉 PHP 我们要启动一个 Web 服务器。 |
| `<hostname>:<port>` | 要使用的主机名和端口。 |
| `-t` | 公共目录（文档根目录）。 |
| `<filename>` | 路由脚本。 |

了解如何使用内置服务器来开发和测试你的应用程序，而无需 XAMPP、WAMP 等其他工具。

#### 第 87.1 节：运行内置服务器

```
php -S localhost:80
```

```
PHP 7.1.7 Development Server started at Fri Jul 14 15:11:05 2017
Listening on http://localhost:80
Document root is C:\projetos\repgeral
Press Ctrl-C to quit.
```

这是启动一个响应发送到 localhost 80 端口请求的 PHP 服务器的最简单方法。

`-S` 表示我们正在启动一个 Web 服务器。

`localhost:80` 指示我们要响应的主机和端口。你可以使用其他组合，如：

*   `mymachine:80` - 将在 mymachine 地址和 80 端口监听；
*   `127.0.0.1:8080` - 将在 127.0.0.1 地址和 8080 端口监听；

#### 第 87.2 节：带有特定目录和路由脚本的内置服务器

```
php -S localhost:80 -t project/public router.php
```

```
PHP 7.1.7 Development Server started at Fri Jul 14 15:22:25 2017
Listening on http://localhost:80
Document root is /home/project/public
Press Ctrl-C to quit.
```

# 第 88 章：PSR

[PSR](http://www.php-fig.org/psr/)（PHP 标准建议）是由 [FIG](http://www.php-fig.org/)（框架互操作小组）汇总的一系列建议。

> “该小组的初衷是让项目代表们交流项目间的共性，并寻找合作方式” - [FIG FAQ](http://www.php-fig.org/faqs/)

PSR 可以处于以下状态：已接受、审查中、草案或已弃用。

## 第 88.1 节：PSR-4：自动加载器

[PSR-4](http://www.php-fig.org/psr/psr-4/) 是一项已接受的建议，概述了通过文件名自动加载类的标准。建议将其作为早期（现已弃用）[PSR-0](http://www.php-fig.org/psr/psr-0/) 的替代方案。

完全限定类名应符合以下结构：

```
\<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>
```

示例路径结构：

```
path/to/src/Alphabet/Google/AdWord/KeywordPlanner.php
```

因此最终的类名将是 `Alphabet\Google\AdWord\KeywordPlanner`。完全限定类名也应转化为有意义的文件路径，因此 `Alphabet\Google\AdWord\KeywordPlanner` 将位于 `path/to/src/Alphabet/Google/AdWord/KeywordPlanner.php`。

从 PHP 5.3.0 开始，可以定义一个[自定义自动加载函数](http://php.net/manual/en/function.spl-autoload-register.php)，根据你定义的路径和文件名模式来加载文件。

```php
// 编辑你的 php 以包含类似内容：
spl_autoload_register(function ($class) {
    include 'classes/' . $class . '.class.php';
});
```

将位置（`'classes/'`）和文件扩展名（`'.class.php'`）替换为适用于你结构的值。

Composer 包管理器[支持 PSR-4](https://getcomposer.org/doc/01-basic-usage.md#autoloading)，这意味着，如果你遵循该标准，可以使用 Composer 的 vendor 自动加载器自动加载项目中的类。

```json
{
    "autoload": {
        "psr-4": {
            "Alphabet\\Google\\AdWord\\": "src/"
        }
    }
}
```

重新生成自动加载文件：

```
composer dump-autoload
```

现在在你的代码中可以执行以下操作：

```php
require __DIR__ . '/vendor/autoload.php';
$KeywordPlanner = new Alphabet\Google\AdWord\KeywordPlanner();
```

## 第 88.2 节：PSR-1：基本编码标准

[PSR-1](http://www.php-fig.org/psr/psr-1/) 是一项已接受的建议，概述了代码编写的基本标准建议。

*   它规定了类、方法和常量的命名约定。
*   它要求采用 PSR-0 或 PSR-4 建议。
*   它指明了要使用的 PHP 标签：`<?php` 和 `<?=`，但不包括 `<?`。
*   它指定了要使用的文件编码（UTF-8）。
*   它还规定文件要么声明新符号（类、函数、常量等）且不产生其他副作用，要么执行带有副作用的逻辑但不定义符号，但不能两者兼顾。

# 第 89 章：PHPDoc

#### 第 89.1 节：描述变量

| 标签 | 说明 |
| --- | --- |
| `@var` | `@var` 关键字可用于描述变量的类型和用法。 |

类型可以是内置 PHP 类型之一，或用户定义的类，包括命名空间。

应包含变量名，但如果文档块仅适用于一项，则可以省略。

#### 第 89.2 节：为函数添加元数据

函数级别的注解有助于 IDE 识别返回值或潜在的危险代码。

```php
/**
 * @return int
 */
function getInt() {
    return 1;
}
```

```php
/**
 * @deprecated 请改用 getInt()
 * @return mixed
 */
function oldFunction() {
    // ...
}
```

#### 第 89.3 节：描述参数

```php
/**
 * @param string $name 用户的名称
 * @param int $id 用户 ID
 */
function setUser($name, $id) {
    // ...
}
```

```php
/**
 * @param array<string, int> $data 关联数据数组
 */
function processData(array $data) {
    // ...
}
```

#### 第 89.4 节：集合

[PSR-5](https://github.com/php-fig/fig-standards/blob/211063eed7f4d9b4514b728d7b1810d9b3379dd1/proposed/phpdoc.md#collections) 提出了一种泛型风格的集合表示法。

### 泛型语法

```php
/**
 * @param array<int, string> $strings
 */
function foo(array $strings) {}
```

### 集合中的值甚至可以是另一个数组，甚至是另一个集合。

```php
/**
 * @param array<int, array<int, string>> $multiDimArray
 */
function bar(array $multiDimArray) {}
```

##### 示例

```php
/** @var array<int, string> $strings */
$strings = ['a', 'b'];

/** @var array<string, int> $map */
$map = ['a' => 1, 'b' => 2];
```

```php
/**
 * @return array<string, \MyClass>
 */
function getObjects(): array {
    return [];
}
```

#### 第 89.5 节：为文件添加元数据

文件级别的元数据适用于文件内的所有代码，应放在文件顶部：

```php
<?php
/**
 * @package MyPackage
 * @author  John Doe <john@example.com>
 * @license MIT
 */
```

#### 第 89.6 节：从父结构继承元数据

`@inheritDoc` 标签可用于继承父级的 DocBlock。

```php
class ParentClass {
    /**
     * 执行某些操作。
     * @return void
     */
    public function doSomething() {}
}

class ChildClass extends ParentClass {
    /**
     * @inheritDoc
     */
    public function doSomething() {}
}
```




| @ inheritDoc |
| --- |

如果一个类继承自另一个类并将使用相同的元数据，提供它是使用相同文档的一种简单方法。如果多个类继承自一个基类，则只需更改基类即可影响子类。

![](img/Image01587.jpg)

![](img/Image01588.jpg)

## 第 90 章：设计模式

本主题提供了在 PHP 中实现的知名设计模式示例。

#### 第 90.1 节：PHP 中的方法链

方法链是 [Martin Fowler 的书](http://rads.stackoverflow.com/amzn/click/0321712943) [Domain Specific Languages](http://rads.stackoverflow.com/amzn/click/0321712943) 中解释的一种技术。方法链总结如下：

![](img/Image01589.jpg) [让修饰方法返回宿主对象，以便可以在单个表达式中调用多个修饰符](http://martinfowler.com/dslCatalog/methodChaining.html)。

请看这段非链式/常规代码（从上述书籍移植到 PHP）：

![](img/Image01590.jpg)

方法链将允许您以更紧凑的方式编写上述语句：

![](img/Image01591.jpg)

| return $this |
| --- |

要使其工作，您只需在想要链式调用的方法中 `return $this`：

![](img/Image01592.jpg)

### 何时使用

利用方法链的主要用例是在构建内部领域特定语言时。方法链是 [Expression Builders](http://martinfowler.com/bliki/ExpressionBuilder.html)（表达式构建器）和 [Fluent Interfaces](http://martinfowler.com/bliki/FluentInterface.html)（流式接口）的基础构建块。[但它并不等同于它们](http://stackoverflow.com/a/17940086/208809)。方法链仅仅是启用了它们。引用 Fowler 的话：

![](img/Image01593.jpg)

![](img/Image01594.jpg) 我还注意到一个常见的误解——许多人似乎将流式接口等同于方法链。当然，链式调用是流式接口常用的技术，但真正的流畅性远不止于此。

话虽如此，仅为了避免书写宿主对象而使用方法链，被许多人视为一种 [code](http://martinfowler.com/bliki/CodeSmell.html) [smell](http://martinfowler.com/bliki/CodeSmell.html)（代码异味）。它会导致不明显的 API，特别是在与非链式 API 混合使用时。

### 附加说明

#### 命令查询分离

[命令查询分离是由 Bertrand Meyer 提出的设计原则](http://martinfowler.com/bliki/CommandQuerySeparation.html)。它规定：改变状态的方法（命令）不应返回任何内容，而返回内容的方法（查询）不应改变状态。这使得系统更易于推理。方法链违反了这一原则，因为我们在改变状态的同时返回了值。

#### Getter 方法

当使用实现了方法链的类时，调用 getter 方法（即返回 `$this` 以外内容的方法）时要特别注意。由于 getter 必须返回除 `$this` 以外的值，因此在 getter 后链式调用额外的方法会使该调用作用于获取到的值，而不是原始对象。虽然链式 getter 有一些用例，但它们可能会降低代码的可读性。

#### 迪米特法则及对测试的影响

如上所述的方法链不违反 [迪米特法则](https://en.wikipedia.org/wiki/Law_of_Demeter)。也不影响测试。这是因为我们返回的是宿主实例，而不是某个协作者。这是一个常见的误解，源于人们将单纯的方法链与流式接口和表达式构建器混淆。只有当方法链返回除宿主对象以外的其他对象时，才会违反迪米特法则，并导致测试中出现大量 Mock 对象。

# 第 91 章：编译 PHP 扩展

## 第 91.1 节：在 Linux 上编译

要在典型的 Linux 环境中编译 PHP 扩展，需要满足一些先决条件：

*   基本的 Unix 技能（能够操作 `make` 和 C 编译器）
*   ANSI C 编译器
*   您想要编译的 PHP 扩展的源代码

通常有两种编译 PHP 扩展的方法。您可以将扩展静态编译到 PHP 二进制文件中，或者将其编译为由 PHP 二进制文件在启动时加载的共享模块。共享模块更常见，因为它们允许您在不重新构建整个 PHP 二进制文件的情况下添加或删除扩展。本示例侧重于共享模块选项。

```
apt-get install php5-dev or php7-dev
```

如果您通过包管理器安装了 PHP（apt, yum install 等），您将需要安装 PHP 的开发包，其中将包含构建环境所需的 PHP 头文件和 `phpize` 脚本。该包可能命名为 `php5-dev` 之类，但请务必使用您的包管理器搜索您发行版仓库中合适的名称。它们可能有所不同。

```
/usr/include
```

如果您从源代码构建了 PHP，则头文件很可能已经存在于您的系统上（通常在 `/usr/include` 或 `/usr/local/include`）。

### 编译步骤

在检查确认您具备编译所需的所有先决条件后，您可以前往 [pecl.php.net](http://pecl.php.net/)，选择您想要编译的扩展，并下载压缩包。

```
tar xfvz yaml-2.0.0RC8.tgz
```

1.  解压压缩包（例如 `tar xfvz yaml-2.0.0RC8.tgz`）
2.  进入解压后的目录并运行 `phpize`
3.  如果一切顺利，您现在应该会看到一个新创建的 `configure` 脚本，运行它 `./configure`
4.  现在您需要运行 `make`，这将编译扩展
5.  最后，`make install` 会将编译好的扩展二进制文件复制到您的扩展目录中

```
/usr/lib/, 例如它可能类似于 /usr/lib/php5/20131226/yaml.so
```

```
--with-prefix
```

`make install` 步骤通常会为您提供扩展被复制到的安装路径。这通常在 `/usr/lib/` 中。但这取决于您的 PHP 配置（即 `--with-prefix`）和特定的 API 版本。API 编号包含在路径中，以将为不同 API 版本构建的扩展保存在单独的位置。

### 在 PHP 中加载扩展

```
extension=yaml.so
```

要在 PHP 中加载扩展，请找到适用于相应 SAPI 的已加载 `php.ini` 文件，并添加行 `extension=yaml.so`（当然，请将 `yaml.so` 更改为您实际安装的扩展名称）。

对于 Zend 扩展，您确实需要提供共享对象文件的完整路径。但是，对于普通的 PHP 扩展，此路径源自您加载的配置中的 `extension_dir` 指令，或初始设置期间的 `$PATH` 环境变量。

## 第 92 章：常见错误

## 第 92.1 节：在布尔值上调用 fetch_assoc

如果您遇到如下错误：

![](img/Image01596.jpg) Fatal error: Call to a member function `fetch_assoc()` on boolean in `C:\xampp\htdocs\stack\index.php` on line 7

![](img/Image01597.jpg) 其他变体包括类似：`mysql_fetch_assoc()` expects parameter 1 to be resource, boolean given ...

这些错误意味着您的查询（这是一个 PHP/MySQL 错误）或您的引用出了问题。上述错误由以下代码产生：

![](img/Image01598.jpg)

为了“修复”此错误，建议让 mysql 抛出异常：

![](img/Image01599.jpg)

这将抛出一个异常，并显示更有帮助的消息：




# 第 92 章：SQL 和解析错误

## 第 92.1 节：SQL 语法错误

![](img/Image01600.jpg)

您的 SQL 语法有误；请查阅与您的 MariaDB 服务器版本对应的手册，以获取在 `'SELCT * FROM db'` 附近第 1 行处使用的正确语法。

另一个会产生类似错误的示例是您只是向 `mysql_fetch_assoc()` 函数或类似函数提供了错误的信息：

![](img/Image01601.jpg)

## 第 92.2 节：Unexpected $end（意外的文件结束）

![](img/Image01602.jpg)

解析错误：语法错误，在 `C:\xampp\htdocs\stack\index.php` 第 4 行遇到意外的文件结束。

| unexpected $end |
| --- |

如果您遇到此类错误（有时根据 PHP 版本不同），您需要确保已匹配所有的引号、所有的圆括号、所有的花括号、所有的方括号等。

以下代码产生了上述错误：

![](img/Image01603.jpg)

请注意缺少的花括号。另请注意，此错误显示的行号无关紧要——它始终显示文档的最后一行。

## 第 93 章：错误和警告汇编

## 第 93.1 节：解析错误：语法错误，意外的 T_PAAMAYIM_NEKUDOTAYIM

**外观**

"Paamayim Nekudotayim" 在希伯来语中意为“双冒号”；因此此错误指的是双冒号运算符（`::`）的不当使用。该错误通常是由尝试调用一个实际上并非静态的静态方法引起的。

**可能的解决方案**

![](img/Image01604.jpg)

如果上述代码导致此错误，您很可能只需更改调用该方法的方式：

![](img/Image01605.jpg)

| `doMethod()` |
| --- |

后一个示例假设 `$classname` 是一个类的实例，且该方法不是该类的静态方法。

## 第 93.2 节：Notice: Undefined index（未定义索引）

**外观**

尝试使用数组中不存在的键来访问数组。

**可能的解决方案**

在访问前检查其可用性。使用：

| `isset()` |
| --- |

| `array_key_exists()` |
| --- |

1. `isset()`
2. `array_key_exists()`

## 第 93.3 节：Warning: Cannot modify header information - headers already sent（无法修改标头信息 - 标头已发送）

**外观**

当您的脚本尝试向客户端发送 HTTP 标头，但在此之前已有输出，导致标头已发送给客户端时发生。

**可能的原因**

1. **Print, echo**：来自 `print` 和 `echo` 语句的输出将终止发送 HTTP 标头的机会。必须重构应用程序流程以避免这种情况。

| `header()` |
| --- |

2. **原始 HTML 区域**：`.php` 文件中未解析的 HTML 部分也是直接输出。将触发 `header()` 调用的脚本条件必须置于任何原始块之前。

![](img/Image01606.jpg)

3. **`<?php` 前的空白字符导致 "script.php line 1" 警告**：如果警告指的是第 1 行的输出，则主要是开头标记 `<?php` 之前的前导空白、文本或 HTML。

![](img/Image01607.jpg)

参考来自 SO [answer](http://stackoverflow.com/a/8028987/5447994) by [Mario](http://stackoverflow.com/users/345031/mario)。

## 第 94 章：异常处理和错误报告

#### 第 94.1 节：设置错误报告及显示位置

如果在 `php.ini` 中尚未完成，错误报告可以动态设置，并应设置为允许显示大多数错误。

**语法**

![](img/Image01608.jpg)

**示例**

![](img/Image01609.jpg)

错误默认会由 PHP 记录，通常在与运行脚本同级的 `error.log` 文件中。在开发环境中，也可以在屏幕上显示它们：

![](img/Image01610.jpg)

然而在生产环境中，应该：

![](img/Image01611.jpg)

并通过使用异常或错误处理程序显示友好的问题提示信息。

#### 第 94.2 节：记录致命错误

在 PHP 中，致命错误是一种无法被捕获的错误；即程序在经历致命错误后不会恢复执行。但是，要记录此错误或以某种方式处理崩溃，可以使用 `register_shutdown_function()` 来注册一个关闭处理程序。

![](img/Image01612.jpg)

![](img/Image01613.jpg)

**参考**

![](img/Image01614.jpg)
- [`php.net/manual/en/function.register-shutdown-function.php`](http://php.net/manual/en/function.register-shutdown-function.php)
- [`php.net/manual/en/function.error-get-last.php`](http://php.net/manual/en/function.error-get-last.php)
- [`php.net/manual/en/errorfunc.constants.php`](http://php.net/manual/en/errorfunc.constants.php)

## 第 95 章：调试

#### 第 95.1 节：转储变量

[`var_dump()`](http://php.net/manual/en/function.var-dump.php) 函数允许您转储变量的内容（类型和值）以进行调试。

**示例**

![](img/Image01615.jpg)

**输出**

![](img/Image01616.jpg)

#### 第 95.2 节：显示错误

| `php.ini` |
| --- |

如果您希望 PHP 在页面上显示运行时错误，必须启用 [`display_errors`](http://php.net/manual/en/errorfunc.configuration.php#ini.display-errors)，无论是在 `php.ini` 中还是使用 [`ini_set()`](http://php.net/manual/en/function.ini-set.php) 函数。

| `E_*` |
| --- |

您可以使用 `error_reporting()` 函数（或在 ini 中）选择要显示的错误，它接受 [常量](http://php.net/manual/en/errorfunc.constants.php)，并使用 [位运算符](http://php.net/manual/en/language.operators.bitwise.php) 组合。

PHP 可以根据 [`html_errors`](http://php.net/manual/en/errorfunc.configuration.php#ini.html-errors) 设置以文本或 HTML 格式显示错误。

**示例**

![](img/Image01617.jpg)

![](img/Image01618.jpg)

**纯文本输出**（HTML 格式因实现而异）：

![](img/Image01619.jpg)

处理 `error_reporting` 的常用方法是在开发期间使用 `E_ALL` 常量完全启用它，而在生产阶段使用 `display_errors` 禁用公开显示，以隐藏脚本的内部细节。

## 第 95.3 节：phpinfo()

**警告**

必须仅在开发环境中使用 `phpinfo()`。切勿将包含 `phpinfo()` 的代码发布到生产环境。

**简介**

话虽如此，它在理解您正在使用的 PHP 环境（操作系统、配置、版本、路径、模块）方面可能是一个有用的工具，尤其是在追踪 Bug 时。它是一个简单的内置函数：

![](img/Image01620.jpg)

它有一个参数 `$what`，允许自定义输出。默认值为 `INFO_ALL`，这会导致其显示所有信息，且在开发期间常用于查看 PHP 的当前状态。

| `INFO_*` |
| --- |

您可以传递参数 [常量](http://php.net/manual/en/function.phpinfo.php#refsect1-function.phpinfo-parameters)，并结合位运算符，以查看自定义列表。

您可以在浏览器中运行它以获得格式良好的详细视图。它也适用于 PHP CLI，您可以将其通过管道传输给 `less` 以便于查看。

**示例**

![](img/Image01621.jpg)

这将显示 PHP 指令列表 ([`ini_get()`](http://php.net/manual/en/function.ini-get.php))、环境 ([`$_ENV`](http://php.net/manual/en/reserved.variables.environment.php)) 和 [预定义](http://php.net/manual/en/language.variables.predefined.php) 变量。

## 第 95.4 节：Xdebug

[Xdebug](https://xdebug.org/) 是一个 PHP 扩展，提供调试和分析功能。它使用 DBGp 调试协议。

此工具有一些不错的功能：

![](img/Image01622.jpg) 错误堆栈跟踪。

| `var_dump()` |
| --- |




# Xdebug 功能特性

Xdebug 提供以下功能：

- 最大嵌套层级保护和时间追踪
- 标准 `var_dump()` 函数的实用替代品，用于显示变量
- 允许将所有函数调用（包括参数和返回值）以不同格式记录到文件中
- 代码覆盖率分析
- 性能分析信息
- 远程调试（为与运行中的 PHP 脚本交互的调试器客户端提供接口）

正如你所见，该扩展非常适合开发环境。特别是远程调试功能，可以帮助你在不使用大量 `var_dump()` 调用的情况下调试 PHP 代码，并像在 C 或 Java 语言中一样使用标准的调试流程。

## 安装

通常安装此扩展非常简单：

![安装步骤 1](img/Image01624.jpg)

并在你的 `php.ini` 中激活它：

![php.ini 配置](img/Image01625.jpg)

更复杂的情况请参阅这些[说明](https://xdebug.org/docs/install)。

> **警告：** [XDebug 不适用于生产环境](http://stackoverflow.com/a/3522356/2253302)

# 第 95 章：错误报告与版本检查

## 第 95.5 节：错误报告（两者都用上）

![错误报告配置](img/Image01626.jpg)

## 第 95.6 节：phpversion()

##### 简介

在使用各种库及其相关依赖时，通常需要知道当前 PHP 解析器或其某个包的版本。

### 语法

```php
phpversion(string $extension = null): string|false
```

该函数接受一个可选参数，形式为扩展名称。如果相关扩展已安装，函数将返回包含版本值的字符串。但是，如果扩展未安装，将返回 `false`。如果未提供扩展名称，函数将返回 PHP 解析器本身的版本。

##### 示例

![phpversion 示例](img/Image01627.jpg)

## 第 96 章：单元测试

#### 第 96.1 节：测试类规则

假设我们有一个简单的 `LoginForm` 类，带有一个 `rules()` 方法（用于登录页面作为框架模板）：

![LoginForm 类](img/Image01628.jpg)

为了对该类执行测试，我们使用单元测试（检查源代码以查看是否符合我们的预期）：

![单元测试设置](img/Image01629.jpg)

单元测试究竟如何在此提供帮助（不包括通用示例）？例如，当我们得到意外结果时，它们非常合适。让我们看看之前的这条规则：

![正确规则](img/Image01630.jpg)

相反，如果我们遗漏了一个重要的东西并写成了这样：

![错误规则](img/Image01631.jpg)

面对数十条不同的规则（假设我们不仅使用邮箱和密码），很难发现错误。这个单元测试：

```php
// 初始化为有效值并测试
$this->loginForm->email = "valid@email.com";
$this->loginForm->password = "password";
$this->loginForm->rememberMe = true;

$this->assertTrue($this->loginForm->validate($rules), "Should be valid as nothing is invalid");
```

![测试执行](img/Image01632.jpg)

将通过我们的第一个示例，但无法通过第二个。为什么？因为在第 2 个示例中，我们编写的模式有一个拼写错误（漏掉了 `+` 号），意味着它只接受一个字母/数字。

### 运行测试

```bash
phpunit [path_to_file]
```

单元测试可以在控制台使用上述命令运行。如果一切正常，我们应该能看到所有测试都处于 OK 状态；否则我们将看到 Error（语法错误）或 Fail（该方法中至少有一行未通过）。

```bash
phpunit --coverage [path_to_file]
```

使用 `--coverage` 等附加参数，我们还可以直观地看到后端代码中有多少行被测试了，以及哪些通过/失败了。这适用于任何安装了 [PHPUnit](https://phpunit.de/) 的框架。

PHPUnit 测试在控制台中的样子示例（通用外观，非针对本示例）：

![PHPUnit 控制台输出](img/Image01633.jpg)

## 第 96.2 节：PHPUnit 数据提供者

测试方法通常需要被测试的数据。要完整测试某些方法，你需要为每种可能的测试条件提供不同的数据集。当然，你可以使用循环手动完成，如下所示：

![手动数据循环](img/Image01634.jpg)

有人可能会觉得这很方便。但这种方法有一些缺点：

1. 如果你的测试函数接受多个参数，你将不得不执行额外的操作来提取数据。
2. 如果没有额外的消息和调试，在失败时很难区分是哪个数据集失败了。
3. PHPUnit 使用[数据提供者](https://phpunit.de/manual/current/en/writing-tests-for-phpunit.html#writing-tests-for-phpunit.data-providers)提供了一种自动处理测试数据集的方法。

数据提供者是一个应为你的特定测试用例返回数据的函数。

![数据提供者示例](img/Image01635.jpg)

数据提供者方法必须是公共的，并且返回一个数组的数组，或一个实现了 `Iterator` 接口并在每次迭代步骤中生成一个数组的对象。对于集合中的每个数组，测试方法将使用该数组的内容作为其参数被调用。

### 使用数据提供者

要将数据提供者与你的测试一起使用，请使用 `@dataProvider` 注解并指定数据提供者函数的名称：

![DataProvider 注解](img/Image01636.jpg)

![DataProvider 用法](img/Image01637.jpg)

每个数据集可以为了方便而命名。这将更容易检测失败的数据：

![命名数据集](img/Image01638.jpg)

### 迭代器

![迭代器实现](img/Image01639.jpg)

![迭代器用法](img/Image01640.jpg)

正如你所见，简单的迭代器也能工作。

> **注意：** 即使对于单个参数，数据提供者也必须返回一个数组 `[]`。因为如果我们将 `current()` 方法（实际上在每次迭代时返回数据）更改为这样：

![错误的单值返回](img/Image01641.jpg)

或更改实际数据：

![数据更改示例 1](img/Image01642.jpg)

![数据更改示例 2](img/Image01643.jpg)

### 生成器

手册中未明确注明和展示，但你也可以使用生成器作为数据提供者。注意 `Generator` 类实际上实现了 `Iterator` 接口。

所以这里是一个结合使用 `DirectoryIterator` 和生成器的示例：

![生成器数据提供者](img/Image01645.jpg)

#### 第 96.3 节：测试异常

假设你想测试一个抛出异常的方法：

![抛出异常的方法](img/Image01646.jpg)

![测试类结构](img/Image01647.jpg)

你可以通过将方法调用包裹在 `try/catch` 块中并对异常对象的属性进行断言来实现，但更方便的是使用异常断言方法。自 [PHPUnit 5.2](https://github.com/sebastianbergmann/phpunit/wiki/Release-Announcement-for-PHPUnit-5.2.0) 起，你可以使用 `expectException()` 方法来断言异常类型、消息和代码：

![expectException 方法](img/Image01648.jpg)

如果你使用的是较早版本的 PHPUnit，可以使用 `setExpectedException()` 方法代替 `expectException()` 方法，但请记住它已被弃用，并将在版本 6 中移除。

![setExpectedException 方法](img/Image01649.jpg)

## 第 97 章：性能

## 第 97.1 节：使用 Xdebug 进行性能分析

一个名为 Xdebug 的 PHP 扩展可用于协助[分析 PHP 应用程序](https://xdebug.org/docs/profiler)以及运行时调试。运行分析器时，输出会以一种称为 "cachegrind" 的二进制格式写入文件。每个平台都有可用的应用程序来分析这些文件。

要启用分析，请安装扩展并调整 `php.ini` 设置。在我们的示例中，我们将根据请求参数有选择地运行分析器。这允许我们保持设置静态，仅在需要时开启分析器。

```ini
; 设置为 1 即可为每个请求开启
xdebug.profiler_enable = 0

; 让我们使用 GET/POST 参数来开启分析器
xdebug.profiler_enable_trigger = 1

; 我们将传递的 GET/POST 值；为空则表示任意值
xdebug.profiler_enable_trigger_value = ""

; 将 cachegrind 文件输出到 /tmp，以便系统稍后清理
xdebug.profiler_output_dir = "/tmp"

xdebug.profiler_output_name = "cachegrind.out.%p"
```

![分析器配置](img/Image01650.jpg)

接下来，使用 Web 客户端向你想要分析的应用程序 URL 发起请求，例如：

```bash
curl "http://localhost/your-app?XDEBUG_PROFILE=1"
```

![分析请求](img/Image01651.jpg)

随着页面处理，它将写入一个名称类似于以下内容的文件：

```
cachegrind.out.12345
```

![Cachegrind 输出](img/Image01652.jpg)




请注意，它将为每个执行的 PHP 请求/进程写入一个文件。因此，例如，如果您想分析表单提交，将为显示 HTML 表单的 GET 请求写入一个性能分析文件。`XDEBUG_PROFILE` 参数需要传递给后续的 POST 请求，以分析处理表单的第二个请求。因此，在进行性能分析时，有时直接运行 `curl` 来 POST 表单会更容易。

写入后，可以使用 KCachegrind 等应用程序读取性能分析缓存。

![](img/Image01653.jpg)

这将显示包括以下信息在内的内容：

![](img/Image01654.jpg)

*   执行的函数
*   调用时间，包括其自身时间以及包含后续函数调用的时间
*   每个函数被调用的次数
*   调用图
*   源代码链接

显然，性能调优非常具体，取决于每个应用程序的用例。通常情况下，建议寻找：

![](img/Image01655.jpg)

*   对同一函数的重复调用，而这些调用是你意料之外的。对于处理和查询数据的函数，这些可能是您的应用程序进行缓存的绝佳机会。
*   运行缓慢的函数。应用程序将大部分时间花在哪里了？性能调优中回报最大的做法是专注于消耗时间最多的那些应用程序部分。

**注意**：Xdebug，特别是其性能分析功能，非常消耗资源并会拖慢 PHP 执行速度。建议不要在生产服务器环境中运行这些功能。

#### 第 97.2 节：内存使用

| php | | . | ini |
| --- | --- | --- | --- |

PHP 的运行时内存限制通过 INI 指令 `memory_limit` 设置。此设置可防止任何单次 PHP 执行占用过多内存，导致其他脚本和系统软件内存耗尽。内存限制默认为 128M，可在 `php.ini` 文件中或运行时更改。可以将其设置为无限制，但这通常被视为不良实践。

| `memory_get_usage` |
| --- |

运行时使用的确切内存量可以通过调用 `memory_get_usage()` 来确定。它返回当前正在运行的脚本所分配的内存字节数。自 PHP 5.2 起，它有一个可选的布尔参数，用于获取总分配的系统内存，而不是 PHP 正在活跃使用的内存。

![](img/Image01656.jpg)

| `memory_get_peak_usage` |
| --- |

`memory_get_usage` 给出的是运行那一刻的内存使用量。在对该函数的调用之间，您可能会在内存中分配和释放其他内容。要获取截至某一时刻使用的最大内存量，请调用 `memory_get_peak_usage()`。

![](img/Image01657.jpg)

请注意，该值只会增加或保持不变。

## 第 97.3 节：使用 XHProf 进行性能分析

[XHProf](https://github.com/phacility/xhprof) 是一个 PHP 性能分析器，最初由 Facebook 编写，旨在为 XDebug 提供一个更轻量级的替代方案。

安装 xhprof PHP 模块后，可以从 PHP 代码中启用/禁用性能分析：

![](img/Image01658.jpg)

| `doSlowOperation` |
| --- |

返回的数组将包含有关在 `doSlowOperation()` 内部访问的每个函数的调用次数、CPU 时间和内存使用量的数据。

| `xhprof_sample_enable` | | `()` / | `xhprof_sample_disable` |
| --- | --- | --- | --- |

`xhprof_sample_enable()` 可用作更轻量级的选项，它仅记录一小部分请求的性能分析信息（且格式不同）。

XHProf 有一些（大多未记录在案的）辅助函数来显示数据（[参见示例](https://github.com/phacility/xhprof/blob/master/examples/sample.php)），或者您可以使用其他工具来可视化它（platform.sh 博客[有一个示例](https://platform.sh/2015/07/29/flamegraphs/)）。

# 第 98 章：多进程处理

#### 第 98.1 节：使用内置 fork 函数进行多进程处理

您可以使用内置函数将 PHP 进程作为 fork 运行。如果不需要线程之间相互通信，这是实现并行工作的最简单方法。

这允许您将耗时的任务（如将文件上传到另一台服务器或发送电子邮件）放到另一个线程中，以便您的脚本加载得更快并能利用多核，但请注意，这不是真正的多线程，主线程无法知晓子线程在做什么。

请注意，在 Windows 下，这将为您启动的每个 fork 弹出另一个命令提示符窗口。

**master.php**

![](img/Image01659.jpg)

**worker.php**

![](img/Image01660.jpg)

## 第 98.2 节：使用 fork 创建子进程

PHP 拥有用于创建子进程的内置函数 `pcntl_fork`。`pcntl_fork` 与 Unix 中的 fork 相同。它不接受任何参数，并返回一个整数，可用于区分父进程和子进程。

请参考以下代码进行说明：

![](img/Image01661.jpg)

正如您所见，`-1` 表示 fork 出错，子进程未被创建。子进程创建后，我们有两个具有独立 PID 的进程在运行。

| `pcntl_wait` | | `(` | `$status` |
| --- | --- | --- | --- |

此处的另一个考虑因素是僵尸进程或失效进程，即父进程在子进程之前结束。为防止僵尸子进程，只需在父进程末尾添加 `pcntl_wait($status)`。![](img/Image01662.jpg) `pcntl_wait` 会挂起父进程的执行，直到子进程退出。

还值得注意的是，僵尸进程无法使用 SIGKILL 信号杀死。

#### 第 98.3 节：进程间通信

进程间通信允许程序员在不同进程之间进行通信。例如，假设我们需要编写一个可以运行 bash 命令并打印输出的 PHP 应用程序。我们将使用 `proc_open`，它将执行命令并返回一个可用于通信的资源。以下代码展示了一个从 PHP 在 bash 中运行 `pwd` 的基本实现：

![](img/Image01663.jpg)

`proc_open` 使用 `$descriptor` 作为描述符规范来运行 bash 命令。之后，我们使用 `is_resource` 来验证进程。完成后，我们可以根据描述符规范生成的 `$pipes` 开始与子进程交互。

之后，我们可以简单地使用 `fwrite` 写入子进程的 stdin。在本例中是 `pwd` 后跟回车符。

最后，使用 `stream_get_contents` 读取子进程的 stdout。

![](img/Image01664.jpg) 请始终记得使用 `proc_close()` 关闭子进程，这将终止子进程并返回退出状态码。

## 第 99 章：多线程扩展

#### 第 99.1 节：入门

| `pthreads` - ext |
| --- |

要开始多线程编程，您需要 PHP 的 `pthreads` 扩展，可以通过以下方式安装：

![](img/Image01665.jpg)

| php | . | ini |
| --- | --- | --- |

并将条目添加到 `php.ini`。

一个简单的示例：

![](img/Image01666.jpg)

## 第 99.2 节：使用池和工作者

![](img/Image01667.jpg) 池化提供了 Worker 功能的更高层抽象，包括 pthreads 所需方式的引用管理。来源：[`php.net/manual/en/class.pool.php`](http://php.net/manual/en/class.pool.php)

池和工作者提供了更高层级的控制，并简化了多线程的创建。

![](img/Image01668.jpg)

![](img/Image01669.jpg)

# 第 100 章：安全的“记住我”功能

我一直在寻找这个主题，直到发现了 ircmaxell 的这篇帖子 [`stackoverflow.com/a/17266448/4535386`](https://stackoverflow.com/a/17266448/4535386)，我认为它值得更多的关注。

## 第 100.1 节：“保持登录状态” - 最佳方法

存储包含三部分的 cookie。

![](img/Image01670.jpg)

然后，进行验证：

![](img/Image01671.jpg)

## 第 101 章：安全

由于大多数网站运行在 PHP 上，应用程序安全是 PHP 开发人员保护其网站、数据和客户的重要课题。本主题涵盖 PHP 中的最佳安全实践，以及常见漏洞和弱点，并附带 PHP 示例修复方案。

## 第 101.1 节：PHP 版本泄露

默认情况下，PHP 会向外界透露您正在使用的 PHP 版本，例如：

![](img/Image01672.jpg)

要修复此问题，您可以更改 `php.ini`：

![](img/Image01673.jpg)

或者更改 header：




# 第 101.2 节：跨站脚本攻击 (XSS)

## 问题

跨站脚本攻击是指 Web 客户端非预期地执行远程代码。如果 Web 应用程序接受用户输入并直接将其输出到网页上，则可能会暴露于 XSS 攻击之下。如果输入包含 HTML 或 JavaScript，当 Web 客户端渲染此内容时，远程代码即可被执行。

例如，如果第三方网站包含一个 JavaScript 文件：

![](img/Image01677.jpg)

而某 PHP 应用程序直接输出传入给它的字符串：

![](img/Image01678.jpg)

| `<script src = "http://example.com/runme.js"> </script>` |
| --- |

如果未经检查的 GET 参数包含 `>`，则 PHP 脚本的输出将变为：

![](img/Image01679.jpg)

第三方 JavaScript 将会运行，用户将在网页上看到 "I'm running"（我正在运行）。

## 解决方案

作为一条通用规则，**永远不要信任来自客户端的输入**。每一个 GET、POST 和 Cookie 值都可能是任意内容，因此都应当经过验证。在输出这些值中的任何一个时，请对其进行转义，以免它们以意想不到的方式被解析执行。

请记住，即使在最简单的应用程序中，数据也会被四处移动，很难追踪所有来源。因此，**始终转义输出**是一项最佳实践。

PHP 提供了几种根据上下文转义输出的方法。

### 过滤函数

[PHP 的过滤函数](http://php.net/manual/en/ref.filter.php)允许以[多种方式](http://php.net/manual/en/filter.filters.php)对传入 PHP 脚本的输入数据进行[清理](http://php.net/manual/en/filter.filters.sanitize.php)或[验证](http://php.net/manual/en/filter.filters.validate.php)。它们在保存或输出客户端输入时非常有用。

### HTML 编码

`htmlspecialchars` 会将任何 "HTML 特殊字符" 转换为其 HTML 实体编码，这意味着它们随后不会被作为标准 HTML 处理。使用此方法修复我们之前的示例：

![](img/Image01680.jpg)

将输出：

![](img/Image01681.jpg)

```
<div> &lt; script src= &quot; http://example.com/runme.js &quot;&gt;&lt; /script &gt; </div>
```

| `<div>` |
| --- |

`>` 标签内的所有内容将不会被浏览器解释为 JavaScript 标签，而是作为简单的文本节点。用户将安全地看到：

![](img/Image01682.jpg)

### URL 编码

当输出动态生成的 URL 时，PHP 提供了 `urlencode` 函数以安全地输出有效的 URL。因此，例如，如果用户输入的数据成为另一个 GET 参数的一部分：

![](img/Image01683.jpg)

任何恶意输入都将被转换为编码后的 URL 参数。

### 使用专业的外部库或 OWASP AntiSamy 列表

有时您可能希望允许发送 HTML 或其他类型的代码输入。您将需要维护一个授权词汇列表（白名单）和一个未授权词汇列表（黑名单）。

您可以从 [OWASP AntiSamy 网站](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) 下载标准列表。每个列表都适用于特定类型的交互（eBay API、tinyMCE 等）。并且它们是开源的。

存在一些库可用于过滤 HTML 并防止一般情况下的 XSS 攻击，其表现至少与 AntiSamy 列表相当，且使用非常简便。例如 [HTML Purifier](http://htmlpurifier.org/)。

#### 第 101.3 节：跨站请求伪造

## 问题

| `delete.php?accnt=12` |
| --- |

跨站请求伪造 (CSRF) 可强制最终用户在不知情的情况下向 Web 服务器生成恶意请求。此攻击向量可在 POST 和 GET 请求中均被利用。假设 URL 端点 `/delete.php` 根据 GET 请求的 `accnt` 参数删除账户。现在，如果一位已认证用户在任何其他应用程序中遇到以下脚本：

![](img/Image01684.jpg)

```
<img src = "http://domain.com/delete.php?accnt=12" width = "0" height = "0" border = "0" >
```

该账户将被删除。

## 解决方案

解决此问题的常用方法是使用 CSRF 令牌。CSRF 令牌被嵌入请求中，以便 Web 应用程序能够信任该请求来自预期来源，且属于应用程序正常工作流的一部分。首先，用户执行某项操作（如查看表单），触发创建一个唯一令牌。

实现此功能的示例表单可能如下所示：

![](img/Image01685.jpg)

随后，服务器可在表单提交后根据用户会话验证该令牌，从而排除恶意请求。

### 示例代码

以下是基本实现的示例代码：

![](img/Image01686.jpg)
![](img/Image01687.jpg)

已有许多库和框架提供了各自的 CSRF 验证实现。虽然这是 CSRF 的简单实现，但您需要编写一些代码以动态重新生成 CSRF 令牌，防止 CSRF 令牌被窃取和固定。

#### 第 101.4 节：命令行注入

## 问题

正如 SQL 注入允许攻击者在数据库上执行任意查询一样，命令行注入允许某人在 Web 服务器上运行不受信任的系统命令。如果服务器安全配置不当，这将使攻击者完全控制系统。

假设某脚本允许用户列出 Web 服务器上的目录内容。

![](img/Image01688.jpg)

（在实际应用中，应使用 PHP 的内置函数或对象来获取路径内容。此示例仅用于简单的安全演示。）

| `tmp`。但由于允许任意输入，路径可能是 `; rm -fr` |
| --- |

人们期望获得的路径参数类似于 `//tmp`。

Web 服务器将执行命令：

![](img/Image01689.jpg)

并尝试从服务器根目录删除所有文件。

## 解决方案

| `escapeshellarg()` 或 `escapeshellcmd()` |
| --- |

所有命令参数必须使用 `escapeshellarg()` 进行转义。这会使参数变得不可执行。对于每个参数，输入值也应经过验证。

在最简单的情况下，我们可以用以下方式保护示例：

![](img/Image01690.jpg)
![](img/Image01691.jpg)

沿用之前尝试删除文件的示例，执行的命令变为：

![](img/Image01692.jpg)

该字符串仅作为参数传递给 `ls`，而不是终止 `ls` 命令并运行 `rm`。

应注意，上述示例现在虽免受命令注入攻击，但**不**防目录遍历。要修复此问题，应检查规范化路径是否以期望的子目录开头。

PHP 提供了多种执行系统命令的函数，包括 `exec`、`passthru`、`proc_open`、`shell_exec` 和 `system`。所有这些函数的输入都必须经过仔细验证和转义。

#### 第 101.5 节：剥离标签

如果您知道如何使用，[`strip_tags`](http://php.net/manual/en/function.strip-tags.php) 是一个非常强大的函数。作为预防跨站脚本攻击的方法，有更好的方法，如字符编码，但在某些情况下剥离标签很有用。

## 基本示例

![](img/Image01693.jpg)

原始输出：

![](img/Image01694.jpg)

## 允许标签

| `<b>` |
| --- |

假设您想允许某个特定标签但不允许其他标签，则可在函数的第二个参数中指定。此参数是可选的。在我的示例中，我只希望 `>` 标签被保留通过。

![](img/Image01695.jpg)

原始输出：

![](img/Image01696.jpg)

##### 注意事项





# HTML 注释和 PHP 标签

HTML 注释和 PHP 标签也会被剥离。这是硬编码的，无法通过 `allowable_tags` 更改。

| `<br>` | `>` | `<br/>` |
| --- | --- | --- |

在 PHP 5.3.4 及更高版本中，自闭合 XHTML 标签会被忽略，因此在 `allowable_tags` 中应仅使用非自闭合标签。例如，要同时允许 `<br>` 和 `<br/>`，应使用：

```
allowable_tags = "<br><br/>"
```

## 第 101 章：安全

#### 第 101.6 节：文件包含

### 远程文件包含

远程文件包含（也称为 RFI）是一种允许攻击者包含远程文件的漏洞类型。

此示例注入了一个包含恶意代码的远程托管文件：

```
include($_GET['file']);
```

### 本地文件包含

本地文件包含（也称为 LFI）是通过 Web 浏览器在服务器上包含文件的过程。

```
include("includes/" . $_GET['page'] . ".php");
```

### RFI 和 LFI 的解决方案

建议仅允许包含你批准的文件，并仅限于这些文件。

```
$allowed = array('page1', 'page2', 'page3');
if (in_array($_GET['page'], $allowed)) {
    include($_GET['page'] . '.php');
}
```

#### 第 101.7 节：错误报告

默认情况下，如果脚本中发生意外情况，PHP 会直接在页面上输出错误、警告和通知消息。这对于解决脚本的特定问题很有用，但同时也会输出你不想让用户知道的信息。

因此，在生产环境中，避免显示那些会泄露服务器信息（例如目录树）的消息是一种良好的实践。在开发或测试环境中，这些消息可能仍然有利于显示以进行调试。

### 快速解决方案

你可以将它们关闭，使消息完全不显示，但这会使调试脚本变得更难。

```
ini_set('display_errors', 0);
```

或直接在 `php.ini` 中更改它们：

```
display_errors = 0
```

### 错误处理

一个更好的选择是将这些错误消息存储在一个更有用的地方，比如数据库：

```
set_error_handler(function ($errno, $errstr, $errfile, $errline) {
    // 记录到数据库
    $db->query("INSERT INTO error_log (message, file, line) VALUES (?, ?, ?)", [$errstr, $errfile, $errline]);
    return true; // 阻止默认处理程序
});
```

此方法将消息记录到数据库，如果失败则记录到文件，而不是直接回显到页面中。这样你可以追踪用户在你网站上遇到的问题，并在出错时立即收到通知。

#### 第 101.8 节：上传文件

如果你想让用户向你的服务器上传文件，在实际将上传的文件移动到 Web 目录之前，你需要进行一些安全检查。

### 上传的数据

`$_FILES` 数组包含用户提交的数据，并非文件本身的信息。虽然通常这些数据由浏览器生成，但可以使用软件轻松地向同一表单发起 POST 请求。

```
$_FILES['userfile']['name']
$_FILES['userfile']['type']
$_FILES['userfile']['tmp_name']
$_FILES['userfile']['error']
$_FILES['userfile']['size']
```

### 利用文件名

通常操作系统不允许文件名中包含特定字符，但通过伪造请求可以添加这些字符，从而导致意外情况发生。例如，将文件命名为：

```
../script.php%00.png
```

仔细观察该文件名，你应该会注意到几点。

1.  首先注意到的是 `../`，这在文件名中是完全非法的，但如果你要将文件从一个目录移动到另一个目录，这却完全没问题，对吧？
2.  你可能认为你在脚本中正确验证了文件扩展名，但此漏洞利用依赖于 URL 解码，将 `%00` 转换为空字符，基本上告诉操作系统字符串到此结束，从而从文件名中剥离 `.png`。

所以现在我已将 `script.php` 上传到另一个目录，绕过了简单的文件扩展名验证。它还绕过了禁止在上传目录中执行脚本的 `.htaccess` 文件。

### 安全地获取文件名和扩展名

你可以使用 `pathinfo()` 以安全的方式推断名称和扩展名，但首先我们需要替换文件名中的不需要字符：

```
$filename = basename($_FILES['userfile']['name']);
$filename = preg_replace('/[^a-zA-Z0-9._-]/', '', $filename);
$pathinfo = pathinfo($filename);
$extension = $pathinfo['extension'];
```

虽然现在我们有了可用于存储的文件名和扩展名，但我仍然倾向于将该信息存储在数据库中，并给该文件一个生成的名称，例如 `md5(uniqid() . microtime())`：

```
$newFilename = md5(uniqid() . microtime());
move_uploaded_file($_FILES['userfile']['tmp_name'], '/uploads/' . $newFilename);
```

| id | title | extension | mime | size | filename | time |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | myfile | txt | text/plain | 1020 | 5bcdaeddbfbd2810fa1b6f3118804d66 | 2017-03-11 00:38:54 |

这将解决重复文件名和文件名中不可预见的漏洞问题。这也会导致攻击者必须猜测文件存储在哪里，因为他或她无法专门针对该文件进行执行。

### MIME 类型验证

检查文件扩展名以确定文件类型是不够的，因为文件可能命名为 `image.png`，但很可能包含 PHP 脚本。通过将上传文件的 MIME 类型与文件扩展名进行对比，可以验证文件是否包含其名称所指的内容。

你甚至可以更进一步来验证图像，即实际打开它们：

```
$imageInfo = getimagesize($_FILES['userfile']['tmp_name']);
if ($imageInfo === false) {
    die('Not a valid image');
}
```

你可以使用内置的 `mime_content_type()` 函数或 `finfo` 类来获取 MIME 类型。

### 为上传文件建立白名单

最重要的是，你应该根据每个表单对文件扩展名和 MIME 类型建立白名单。

```
$allowedMimes = ['image/jpeg', 'image/png', 'image/gif'];
$allowedExts = ['jpg', 'jpeg', 'png', 'gif'];

$finfo = new finfo(FILEINFO_MIME_TYPE);
$mime = $finfo->file($_FILES['userfile']['tmp_name']);
$ext = strtolower(pathinfo($_FILES['userfile']['name'], PATHINFO_EXTENSION));

if (!in_array($mime, $allowedMimes) || !in_array($ext, $allowedExts)) {
    die('Invalid file type');
}
```

## 第 102 章：密码学

## 第 102.1 节：使用 OpenSSL 对大文件进行对称加密和解密

PHP 缺少用于加密和解密大文件的内置函数。`openssl_encrypt()` 可用于加密字符串，但将巨大的文件加载到内存中是个坏主意。

所以我们必须编写一个用户空间函数来实现。此示例使用对称 AES-128-CBC 算法加密大文件的较小块，并将它们写入另一个文件。

### 加密文件

```
function encryptFile($source, $dest, $password) {
    $method = "aes-128-cbc";
    $ivLength = openssl_cipher_iv_length($method);
    $iv = openssl_random_pseudo_bytes($ivLength);
    $key = hash('sha256', $password, true);
    
    $fpSource = fopen($source, 'rb');
    $fpDest = fopen($dest, 'wb');
    
    fwrite($fpDest, $iv);
    
    while (!feof($fpSource)) {
        $buffer = fread($fpSource, 8192);
        $encrypted = openssl_encrypt($buffer, $method, $key, OPENSSL_RAW_DATA, $iv);
        fwrite($fpDest, $encrypted);
    }
    
    fclose($fpSource);
    fclose($fpDest);
}
```

### 解密文件

要解密使用上述函数加密的文件，可以使用此函数。

```
function decryptFile($source, $dest, $password) {
    $method = "aes-128-cbc";
    $ivLength = openssl_cipher_iv_length($method);
    $key = hash('sha256', $password, true);
    
    $fpSource = fopen($source, 'rb');
    $fpDest = fopen($dest, 'wb');
    
    $iv = fread($fpSource, $ivLength);
    
    while (!feof($fpSource)) {
        $buffer = fread($fpSource, 8192);
        $decrypted = openssl_decrypt($buffer, $method, $key, OPENSSL_RAW_DATA, $iv);
        fwrite($fpDest, $decrypted);
    }
    
    fclose($fpSource);
    fclose($fpDest);
}
```

### 如何使用

如果你需要一小段代码片段来了解其工作原理或测试上述函数，请查看以下代码。

```
$password = 'secret_password';
$plainFile = 'testfile.txt';
$encryptedFile = 'testfile.txt.enc';
$decryptedFile = 'testfile.txt.dec';

file_put_contents($plainFile, 'This is a test file content.');

encryptFile($plainFile, $encryptedFile, $password);
decryptFile($encryptedFile, $decryptedFile, $password);

echo file_get_contents($decryptedFile); // Should output: This is a test file content.
```

这将创建三个文件：

1.  `testfile.txt` 包含明文
2.  `testfile.txt.enc` 包含加密文件
3.  `testfile.txt.dec` 包含解密文件。其内容应与 `testfile.txt` 相同

#### 第 102.2 节：对称密码

此示例演示了 CBC 模式下的 AES 256 对称密码。需要初始化向量，因此我们使用 openssl 函数生成一个。变量 `$strong` 用于确定生成的 IV 是否具有加密学强度。

### 加密

```
$method = "aes-256-cbc"; // 密码方法
$iv_length = openssl_cipher_iv_length($method); // 获取所需的 IV 长度
$strong = false; // 设为 false 供下一行使用
$iv = openssl_random_pseudo_bytes($iv_length, $strong); // 生成初始化向量

/* 注意：稍后需要检索 IV，因此将其存储在数据库中。但是，不要重复使用相同的 IV 来再次加密数据。 */

if (!$strong) { // 如果 IV 不具备加密学强度则抛出异常
    throw new Exception("IV not cryptographically strong!");
}

$data = "This is a message to be secured."; // 我们的秘密消息
$pass = "Stack0verfl0w"; // 我们的密码

/* 注意：密码应通过 HTTPS 会话以 POST 方式提交。 */
```




这里，它被存储在一个变量中用于演示目的。 \*/

`$enc_data = openssl_encrypt($data, $method, $password, true, $iv);` // 加密

## 解密

/\* 从数据库检索 IV，并从 POST 请求获取密码 \*/

![](img/Image01713.jpg)
`$dec_data = openssl_decrypt($enc_data, $method, $pass, true, $iv);` // 解密

## Base64 编码与解码

| `base64_encode()` | | `base64_decode()` |
| --- | --- | --- |

如果加密数据需要以可打印文本的形式发送或存储，则应分别使用 `base64_encode()` 和 `base64_decode()` 函数。

![](img/Image01714.jpg)

## 第 103 章：密码哈希函数

随着更安全的 Web 服务避免以明文格式存储密码，PHP 等语言提供了各种（不可解密的）哈希函数来支持更安全的行业标准。本主题提供了在 PHP 中正确哈希的文档。

#### 第 103.1 节：创建密码哈希

| `password_hash()` |
| --- |

使用 `password_hash()` 创建密码哈希，以采用当前行业最佳实践标准的哈希或密钥派生。在撰写本文时，标准是 [bcrypt](https://en.wikipedia.org/wiki/Bcrypt)，这意味着 `PASSWORD_DEFAULT` 包含相同的值。

![](img/Image01715.jpg)

第三个参数不是强制性的。

'cost' 值应根据您的生产服务器硬件来选择。增加它将使密码生成的成本更高。生成成本越高，任何试图破解它的人生成它所需的时间也就越长。成本理想情况下应尽可能高，但在实践中，应设置为不会使所有操作过度变慢。0.1 到 0.4 秒之间是可以接受的。如果不确定，请使用默认值。

### 版本 < 5.5

| `password_*` |
| --- |

在低于 5.5.0 的 PHP 版本中，`password_*` 函数不可用。您应该使用 [兼容包](https://github.com/ircmaxell/password_compat) 来替代这些函数。请注意，兼容包需要 PHP 5.3.7 或更高版本，或已回移植 `$2y` 修复的版本（如 RedHat 提供的版本）。

| `crypt()` | | 作为 `password_hash()` |
| --- | --- | --- |

| `crypt()` |
| --- |

如果您无法使用那些函数，可以使用 `crypt()` 实现密码哈希。由于 `password_hash()` 是作为 `crypt()` 函数的封装器实现的，因此您无需损失任何功能。

```php
// 这是一个简单的 bcrypt 哈希实现，其他方面与
// `password_hash()` 兼容
// 不保证保持完整 `password_hash()`
// 实现的相同加密强度
// 如果 `CRYPT_BLOWFISH` 为 1，意味着 bcrypt（使用 blowfish）
// 在您的系统上可用
if (CRYPT_BLOWFISH == 1) {
    $salt = mcrypt_create_iv(16, MCRYPT_DEV_URANDOM);
    $salt = base64_encode($salt);
    // crypt 使用一种修改过的 base64 变体
    $source = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
    $dest = './ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    $salt = strtr(rtrim($salt, '='), $source, $dest);
    $salt = substr($salt, 0, 22);

    // `crypt()` 通过传入的 salt 字符串的形式
    // 来确定使用哪种哈希算法
    $hashedPassword = crypt($plaintextPassword, '$2y$10$' . $salt . '$');
}
```

![](img/Image01716.jpg)

### 密码哈希的 Salt

尽管 crypt 算法可靠，但仍然容易受到 [彩虹表](https://en.wikipedia.org/wiki/Rainbow_table) 攻击。这就是为什么建议使用 salt 的原因。

Salt 是在哈希前附加到密码上的某些数据，以使源字符串唯一。给定两个相同的密码，由于它们的 salt 是唯一的，因此生成的哈希也将是唯一的。

随机 salt 是您密码安全最重要的组成部分之一。这意味着即使拥有已知密码哈希的查找表，攻击者也无法将您用户的密码哈希与数据库中的密码哈希匹配，因为使用了随机 salt。您应该始终使用随机且加密安全的 salt。[阅读更多](http://www.springer.com/us/book/9781484221198)

| `password_hash()` |
| --- |

使用 `password_hash()` 的 bcrypt 算法，明文 salt 会与生成的哈希一起存储，这意味着哈希可以在不同的系统和平台间传输，仍然可以针对原始密码进行验证。

### 版本 < 7.0

尽管不鼓励这样做，但您可以使用 salt 选项来定义您自己的随机 salt。

![](img/Image01717.jpg)

**重要。** 如果省略此选项，`password_hash()` 将为每个哈希密码生成一个随机 salt。这是预期的操作模式。

### 版本 ≥ 7.0

自 PHP 7.0.0 起，salt 选项已被[弃用](http://php.net/manual/ru/function.password-hash.php)。现在首选直接使用默认生成的 salt。

## 第 103.2 节：确定现有密码哈希是否可以升级为更强的算法

如果您使用 `PASSWORD_DEFAULT` 方法让系统选择最佳算法来哈希您的密码，随着默认算法强度的增加，您可能希望在用户登录时重新哈希旧密码。

![](img/Image01718.jpg)

如果您的系统上没有 `password_*` 函数（并且您无法使用下方备注中链接的兼容包），您可以通过类似以下的方法来确定创建原始哈希所使用的算法和 cost：

![](img/Image01719.jpg)

## 第 103.3 节：根据哈希验证密码

| `password_verify()` |
| --- |

`password_verify()` 是（自 PHP 5.5 起）提供的内置函数，用于根据已知哈希验证密码的有效性。

![](img/Image01720.jpg)

所有支持的哈希算法都在哈希本身中存储了标识所用哈希的信息，因此无需指明您用于编码明文密码的算法。

| `crypt()` |
| --- |

如果您的系统上没有 `password_*` 函数（并且您无法使用下方备注中链接的兼容包），您可以使用 `crypt()` 函数实现密码验证。请注意，必须采取特定预防措施以避免 [时序攻击](https://en.wikipedia.org/wiki/Timing_attack)。

![](img/Image01721.jpg)

# 第 104 章：为 PHP 手册做贡献

PHP 手册提供了函数参考和语言参考，以及对 PHP 主要特性的解释。与大多数语言的文档不同，PHP 手册鼓励 PHP 开发者向文档的每一页添加他们自己的示例和注释。本主题解释了向 PHP 手册做贡献的方法，以及最佳实践的提示、技巧和指南。

#### 第 104.1 节：改进官方文档

PHP 已经在 [`php.net/manual/`](http://php.net/manual/) 拥有了出色的官方文档。PHP 手册记录了几乎所有语言特性、核心库和大多数可用扩展。有大量示例可供学习。

PHP 手册提供多种语言和格式。

最重要的是，文档可供任何人免费编辑。

PHP 文档组在 [`edit.php.net`](https://edit.php.net/) 为 PHP 手册提供了一个在线编辑器。它支持多种单点登录服务，包括使用您的 Stack Overflow 账户登录。您可以在 [`wiki.php.net/doc/editor`](https://wiki.php.net/doc/editor) 找到编辑器的介绍。





对 PHP 手册的修改需要由拥有 Doc Karma 的 PHP 文档组成员批准。Doc Karma 有点像声望，但更难获得。这种同行评审流程确保只有事实正确的信息才能进入 PHP 手册。

PHP 手册是用 DocBook 编写的，这是一种易于学习的、用于撰写书籍的标记语言。乍一看可能有点复杂，但有模板可以帮你入门。你肯定不需要成为 DocBook 专家就能做出贡献。

#### 第 104.2 节：为手册做贡献的技巧

以下是为那些希望为 PHP 手册做贡献的人提供的技巧列表：

遵循手册的风格指南。确保始终遵循[手册的风格指南](http://doc.php.net/tutorial/style.php)，以保持一致性。

执行拼写和语法检查。确保使用正确的拼写和语法——否则所呈现的信息可能更难以吸收，且内容看起来会不够专业。

解释要简练。避免啰嗦，以便清晰简洁地向希望快速查阅的开发者呈现信息。

将代码与其输出分开。这能为开发者提供更整洁、不那么繁杂的代码示例以供理解。

检查页面章节顺序。确保被编辑的手册页面的所有章节都按正确的顺序排列。手册的统一性使其更易于快速阅读和查找信息。

移除 PHP 4 相关内容。考虑到 PHP 4 现在已经非常古老，具体提及 PHP 4 的内容已不再相关。应从手册中移除对它的提及，以防止用不必要的信息使手册变得繁杂。

正确设置文件版本。在文档中创建新文件时，确保文件的修订 ID 设置为空，如下所示：

```
<!-- $Revision$ -->
```

将有用的评论合并到手册中。一些评论贡献了手册可受益的有用信息。这些应被合并到主页面的内容中。

不要破坏文档构建。在提交更改前，始终确保 PHP 手册能正确构建。

# 第 105 章：为 PHP 核心做贡献

## 第 105.1 节：设置基本开发环境

PHP 的源代码托管在 [GitHub](https://github.com/php/php-src) 上。要从源代码构建，你首先需要检出一份工作副本。

如果你想添加功能，最好创建你自己的分支。

最后，配置并构建 PHP。

如果因缺少依赖项而导致配置失败，你将需要使用操作系统的包管理系统来安装它们（例如 `yum`、`apt` 等），或者下载并从源代码编译它们。

# 附录 A：在 Windows 上安装 PHP 环境

## 第 A.1 节：下载、安装和使用 WAMP

WampServer 是一个 Windows Web 开发环境。它允许你使用 Apache2、PHP 和 MySQL 数据库创建 Web 应用程序。此外，PhpMyAdmin 允许你轻松管理数据库。

WampServer 有两个不同的版本可免费获得（基于 GPML 许可证）：32 位和 64 位。WampServer 2.5 与 Windows XP 不兼容，无论是否带 SP3，也不兼容 Windows Server 2003。旧版本的 WampServer 可在 [SourceForge](https://sourceforge.net/projects/wampserver/files/) 上找到。

WampServer 版本：

*   [WampServer (64 位) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x64_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)
*   [WampServer (32 位) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x86_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)

当前提供：

*   Apache: 2.4.18
*   MySQL: 5.7.11
*   PHP: 5.6.19 & 7.0.4

安装很简单，只需运行安装程序，选择位置并完成即可。

完成后，你可以启动 WampServer。然后它会在系统托盘（任务栏）中启动，最初为红色，服务器启动后变为绿色。

你可以打开浏览器并输入 `localhost` 或 `127.0.0.1` 以获取 WAMP 的索引页面。从现在起，你可以通过将文件存储在 `PATH_TO_WAMP/www/<php_or_html_file>` 中，并在 `http://localhost/<php_or_html_file_name>` 上查看结果，在本地处理 PHP 文件。

## 第 A.2 节：安装 PHP 并配合 IIS 使用

首先，你需要在机器上安装并运行 IIS（Internet Information Services）；IIS 默认不可用，你必须从控制面板 -> 程序 -> Windows 功能 中添加该特性。

1.  从 [`windows.php.net/download/`](http://windows.php.net/download/) 下载你喜欢的 PHP 版本，并确保下载 PHP 的非线程安全（NTS）版本。
2.  将文件解压到 `C:\PHP\`。
3.  打开 Internet Information Services (IIS) 管理器。
4.  在左侧面板中选择根项目。
5.  双击“处理程序映射”。
6.  在右侧面板点击“添加模块映射”。
7.  按如下方式设置值：
    *   安装 `vcredist_x64.exe` 或 `vcredist_x86.exe`（Visual C++ 2012 可再发行组件），从 [`www.microsoft.com/en-US/download/details.aspx?id=30679`](https://www.microsoft.com/en-US/download/details.aspx?id=30679)
8.  设置你的 `C:\PHP\php.ini`，特别是设置 `extension_dir = "C:\PHP\ext"`。
9.  重置 IIS：在 DOS 命令控制台中输入 `IISRESET`。

你也可以选择安装 [PHP Manager for IIS](https://phpmanager.codeplex.com/)，它对设置 ini 文件和跟踪错误日志很有帮助（在 Windows 10 上不工作）。

记得将 `index.php` 设置为 IIS 的默认文档之一。

如果你遵循了安装指南，现在你已经准备好测试 PHP 了。

就像 Linux 一样，IIS 在服务器上有一个目录结构，这棵树的根目录是 `C:\inetpub\wwwroot\`，这是所有公共文件和 PHP 脚本的入口点。

现在使用你喜欢的编辑器，或者只是 Windows 记事本，输入以下内容：

```
<?php phpinfo(); ?>
```

将文件以 UTF-8 格式（无 BOM）保存到 `C:\inetpub\wwwroot\index.php`。

然后在浏览器中使用此地址打开你全新的网站：[`localhost/index.php`](http://localhost/index.php)

## 第 A.3 节：下载并安装 XAMPP

什么是 XAMPP？

XAMPP 是最流行的 PHP 开发环境。XAMPP 是一个完全免费、开源且易于安装的 Apache 发行版，包含 MariaDB、PHP 和 Perl。

我应该从哪里下载？

从[他们的下载页面](http://www.apachefriends.org/download.html)下载合适的稳定 XAMPP 版本。根据操作系统类型（32 位或 64 位及操作系统版本）以及它必须支持的 PHP 版本选择下载。

当前最新版本为 [XAMPP for Windows 7.0.8 / PHP 7.0.8](http://www.apachefriends.org/xampp-files/7.0.8/xampp-win32-7.0.8-0-VC14-installer.exe)。

或者你可以遵循以下方式：

XAMPP for Windows 有三种不同的形式：

*   exe 格式
*   zip 格式
*   7zip 格式

*   [安装程序](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14-installer.exe/download)（可能是安装 XAMPP 最简单的方法）
*   [ZIP](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.zip/download)（给纯粹主义者：作为普通 ZIP 归档的 XAMPP）





# XAMPP Windows 安装指南

## 下载选项
- **[7zip](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.7z/download)**：适合带宽较低的纯粹主义者（XAMPP 7zip 压缩包）。

## 如何安装以及将 PHP/HTML 文件放在哪里？

### 方法 1：使用提供的安装程序安装
1. 双击下载的 `.exe` 文件执行 XAMPP 服务器安装程序。

### 方法 2：从 ZIP 压缩包安装
1. 将 zip 压缩包解压到您选择的文件夹中。
2. XAMPP 将解压到所选目标目录下的 `\xampp` 子目录中。
3. 现在启动文件 `setup_xampp.bat` 以将 XAMPP 配置调整为您的系统。

> **注意：** 如果您选择根目录 `C:\` 作为目标，则不得启动 `setup_xampp.bat`。

## 安装后
使用 **“XAMPP 控制面板”** 执行其他任务，如启动/停止 Apache、MySQL、FileZilla 和 Mercury，或将这些安装为服务。

## 文件处理
安装过程非常简单。完成后，您可以将要在服务器上托管的 HTML/PHP 文件添加到 `XAMPP\root\htdocs\` 中。然后启动服务器并在浏览器中打开 `http://localhost/file.php` 以查看页面。

> **注意：** Windows 中默认的 XAMPP 根目录是 `C:\xampp\htdocs`。

在您喜爱的 Web 浏览器中输入以下 URL 之一：
- `http://localhost`
- `http://127.0.0.1`

现在您应该能看到 XAMPP 启动页面。

---

# 附录 B：在 Linux/Unix 环境中安装

## 第 B.1 节：使用 APT 通过命令行安装 PHP 7

```bash
sudo add-apt-repository ppa:ondrej/php
```

> **注意：** 这将仅安装 PHP。如果您希望向 Web 提供 PHP 文件，还需要安装 Web 服务器，例如 [Apache](http://www.apache.org/)、[Nginx](https://www.nginx.com/)，或使用 [PHP 内置 Web 服务器](http://php.net/manual/en/features.commandline.webserver.php)（PHP 5.4+ 版本）。

如果您使用的是 16.04 以下版本的 Ubuntu 但仍想使用 PHP 7，可以通过以下方式添加 [Ondrej 的 PPA 仓库](https://launchpad.net/~ondrej/+archive/ubuntu/php/)：

确保您所有的 [软件仓库](https://en.wikipedia.org/wiki/Software_repository) 都是最新的：

```bash
sudo apt-get update
```

更新系统仓库后，安装 PHP：

```bash
sudo apt-get install php7.0
```

让我们通过检查 PHP 版本来测试安装：

```bash
php -v
```

这应该输出类似如下内容（您的输出会略有不同）：

```
PHP 7.0.8-0ubuntu0.16.04.1 (cli) ( NTS )
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.8-0ubuntu0.16.04.1, Copyright (c) 1999-2016, by Zend Technologies
    with Xdebug v2.4.0, Copyright (c) 2002-2016, by Derick Rethans
```

您现在已经具备了从命令行运行 PHP 的能力。

## 第 B.2 节：在企业级 Linux 发行版中安装（CentOS、Scientific Linux 等）

在基于企业级 Linux 的操作系统中使用 `yum` 命令管理软件包：

```bash
yum install php
```

这将安装包含一些常用功能的最小化 PHP。如果您需要额外的模块，则需要单独安装。您同样可以使用 `yum` 来搜索这些软件包：

```bash
yum search php-
```

**示例输出：**
```
php-bcmath.x86_64 : 用于 PHP 应用程序使用 bcmath 库的模块
php-cli.x86_64    : PHP 的命令行界面
php-common.x86_64 : PHP 的通用文件
php-dba.x86_64    : 用于 PHP 应用程序的数据库抽象层模块
php-devel.x86_64  : 构建 PHP 扩展所需的文件
php-embedded.x86_64 : 用于嵌入应用程序的 PHP 库
php-enchant.x86_64 : 人类语言和字符编码支持
php-gd.x86_64     : 用于 PHP 应用程序使用 gd 图形库的模块
php-imap.x86_64   : 用于使用 IMAP 的 PHP 应用程序的模块
```

安装 `gd` 库：

```bash
yum install php-gd
```

企业级 Linux 发行版在更新方面一向保守，通常不会更新到超出其发布时的版本。许多第三方仓库提供当前版本的 PHP：
- [IUS](https://ius.io/)
- [Remi Colette](http://www.remirepo.net/)
- [Webtatic](https://webtatic.com/)

