
# PHP 与 MySQL：从入门到精通的完整指南 —— 详解 PHP 编程掌握之道

## 第 88 章：`PSR`

### 第 88.1 节：`PSR-4`：自动加载器

### 第 88.2 节：`PSR-1`：基础编码标准

## 第 89 章：`PHPDoc`

### 第 89.1 节：描述变量

### 第 89.2 节：为函数添加元数据

### 第 89.3 节：描述参数

### 第 89.4 节：集合

### 第 89.5 节：为文件添加元数据

### 第 89.6 节：从父结构继承元数据

## 第 90 章：设计模式

### 第 90.1 节：PHP 中的方法链

## 第 91 章：编译 `PHP` 扩展

### 第 91.1 节：在 `Linux` 上编译

## 第 92 章：常见错误

### 第 92.1 节：在布尔值上调用 `fetch_assoc`

### 第 92.2 节：意外的 `$end`

## 第 93 章：错误和警告汇编

### 第 93.1 节：解析错误：语法错误，意外的 `T_PAAMAYIM_NEKUDOTAYIM`

### 第 93.2 节：通知：未定义索引

### 第 93.3 节：警告：无法修改标头信息 - 标头已发送

## 第 94 章：异常处理和错误报告

### 第 94.1 节：设置错误报告及显示位置

### 第 94.2 节：记录致命错误

## 第 95 章：调试

### 第 95.1 节：转储变量

### 第 95.2 节：显示错误

### 第 95.3 节：`phpinfo()`

### 第 95.4 节：`Xdebug`

### 第 95.5 节：错误报告（两者皆用）

### 第 95.6 节：`phpversion()`

## 第 96 章：单元测试

### 第 96.1 节：测试类规则

### 第 96.2 节：`PHPUnit` 数据提供者

### 第 96.3 节：测试异常

## 第 97 章：性能

### 第 97.1 节：使用 `Xdebug` 进行性能分析

### 第 97.2 节：内存使用

### 第 97.3 节：使用 `XHProf` 进行性能分析

## 第 98 章：多进程

### 第 98.1 节：使用内置 fork 函数进行多进程处理

### 第 98.2 节：使用 `fork` 创建子进程

### 第 98.3 节：进程间通信

## 第 99 章：多线程扩展

### 第 99.1 节：入门

### 第 99.2 节：使用池和工作进程

## 第 100 章：安全的记住我功能

### 第 100.1 节：“保持登录状态” - 最佳实践

## 第 101 章：安全

### 第 101.1 节：`PHP` 版本泄露

### 第 101.2 节：跨站脚本攻击 (`XSS`)

### 第 101.3 节：跨站请求伪造

### 第 101.4 节：命令行注入

### 第 101.5 节：剥离标签

### 第 101.6 节：文件包含

### 第 101.7 节：错误报告

### 第 101.8 节：上传文件

## 第 102 章：密码学

### 第 102.1 节：使用 `OpenSSL` 对大文件进行对称加密和解密

### 第 102.2 节：对称密码

## 第 103 章：密码哈希函数

### 第 103.1 节：创建密码哈希

### 第 103.2 节：确定现有密码哈希是否可升级至更强算法

### 第 103.3 节：验证密码是否匹配哈希值

## 第 104 章：为 `PHP` 手册做贡献

### 第 104.1 节：改进官方文档

### 第 104.2 节：为手册做贡献的技巧

## 第 105 章：为 `PHP` 核心做贡献

### 第 105.1 节：搭建基础开发环境

## 附录 A：在 `Windows` 上安装 `PHP` 环境

### 第 A.1 节：下载、安装和使用 `WAMP`

### 第 A.2 节：安装 `PHP` 并配合 `IIS` 使用

### 第 A.3 节：下载并安装 `XAMPP`

## 附录 B：在 `Linux/Unix` 环境上安装

### 第 B.1 节：使用 `APT` 通过命令行安装 `PHP 7`

### 第 B.2 节：在企业级 `Linux` 发行版中安装（`CentOS`、`Scientific Linux` 等）

## 致谢

## 您可能还喜欢

## 第 1 章：`PHP` 入门

### 第 1.1 节：Web 服务器的 `HTML` 输出

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

另请参阅：字符串和 `PSR-1`，其中描述了最佳实践，包括短标签的正确使用。

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

使用 `header()` 时，其输出必须是服务器发送的第一个字节。因此，在 PHP 开启标签 `<?php` 之前，文件开头不得有空行或空格。出于同一原因，最佳实践（见 `PSR-2`）建议省略仅包含 PHP 的文件或文件末尾 PHP 代码块的关闭标签 `?>`。

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

通常建议始终使用分号，并为每个 PHP 代码块使用结束标签，最后一个 PHP 代码块除外（如果该 PHP 代码块后面没有更多代码）。

因此，你的代码基本上应该如下所示：

### 第 1.7 节：PHP 标签

文件中有三种标签用于标记 PHP 代码块。PHP 解析器会寻找开始标签和（如果存在）结束标签，以界定需要解析的代码。

### 标准标签

这些标签是在文件中嵌入 PHP 代码的标准方法。

```php
<?php
// code
?>
```

**PHP 5.x 版本 ≥ 5.4**

### Echo 标签

这些标签在所有 PHP 版本中均可用，且自 PHP 5.4 起始终启用。在早期版本中，echo 标签只能结合短标签一起启用。

```php
<?= "Hello World" ?>
```

### 短标签

你可以使用选项 `short_open_tag` 来禁用或启用这些标签。

```php
<?
// code
?>
```

短标签：

- 在所有主要的 PHP [编码标准](http://www.php-fig.org/psr/psr-1/) 中均被禁止
- [官方文档](https://secure.php.net/manual/en/language.basic-syntax.phptags.php) 不建议使用
- 在大多数发行版中默认禁用
- 会干扰内联 XML 的处理指令
- 大多数开源项目的代码提交不接受短标签

### PHP 5.x 版本 ≤ 5.6 ASP 标签

通过启用 `asp_tags` 选项，可以使用 ASP 风格的标签。

```php
<%
// code
%>
```

这是一种历史遗留的怪癖，**永远不应该**使用。它们已在 PHP 7.0 中移除。

## 第 2 章：变量

### 第 2.1 节：按名称动态访问变量（变量变量）

变量可以通过动态变量名来访问。变量的名称可以存储在另一个变量中，从而允许动态访问。这种变量被称为变量变量。

要将一个变量转变为变量变量，你需要在变量前加上一个额外的 `$`。

```php
$variableName = 'foo';
$foo = 'bar';
echo $$variableName; // 输出 'bar'
```

变量变量对于映射函数/方法调用很有用：

```php
$func = 'myFunction';
$func(); // 调用 myFunction()
```

这在 PHP 类中变得特别有用：

```php
$methodName = 'myMethod';
$object->$methodName(); // 调用 $object->myMethod()
```

将 `$variableName` 放在 `{}` 之间是可能的，但不是必须的：

```php
echo ${$variableName};
```

以下两个示例是等效的，都输出 "baz"：

```php
$foo = 'bar';
$bar = 'baz';
echo $$foo; // 输出 'baz'
```

```php
$foo = 'bar';
$bar = 'baz';
echo ${$foo}; // 输出 'baz'
```

仅当变量名本身是一个表达式时，使用 `{}` 才是强制性的，如下所示：

```php
echo ${$variableName . 'Suffix'};
```

不过，仍然建议始终使用 `{}`，因为它的可读性更好。

虽然不建议这样做，但可以链式调用此行为：

```php
$$$$$$$$DoNotTryThisAtHomeKids = $value;
```

```php
$DoNotTryThisAtHomeKids = 'value';
$$$$$$$$DoNotTryThisAtHomeKids = 'test';
echo $value; // 输出 'test'
```

重要的是要注意，许多开发人员认为过度使用变量变量是一种不良实践。因为它们不适合现代 IDE 进行静态分析，包含许多变量变量（或动态方法调用）的大型代码库会迅速变得难以维护。

##### PHP5 和 PHP7 之间的差异

始终使用 `{}` 或 `()` 的另一个原因是，PHP5 和 PHP7 处理动态变量的方式略有不同，这在某些情况下会导致不同的结果。

在 PHP7 中，动态变量、属性和方法现在将严格按从左到右的顺序求值，这与 PHP5 中的特殊情况混合处理形成对比。以下示例展示了求值顺序是如何改变的。

##### 情况 1：`$$foo['bar']['baz']`
