
```php
protected function fileIteratorCsv() {
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgetcsv();
        $count++;
    }
    return $count;
}
```

### 3. 我们还需要将 `Csv` 添加到允许的迭代方法列表中：

```php
const ERROR_UNABLE = 'ERROR: Unable to open file';
const ERROR_TYPE   = 'ERROR: Type must be "ByLength", "ByLine" or "Csv"';

protected $file;
protected $allowedTypes = ['ByLine', 'ByLength', 'Csv'];
```

## 工作原理...

首先，我们定义一个配置文件，`/path/to/source/config/db.config.php`，其中包含数据库连接参数：

```php
<?php
return [
    'driver'   => 'mysql',
    'host'     => 'localhost',
    'dbname'   => 'php7cookbook',
    'user'     => 'cook',
    'password' => 'book',
    'errmode'  => PDO::ERRMODE_EXCEPTION,
];
```

接下来，我们利用第 1 章*构建基础*中定义的自动加载类，获取 `Application\Database\Connection` 和 `Application\Iterator\LargeFile` 的实例，并定义调用程序 `chap_02_uploading_csv_to_database.php`：

```php
define('DB_CONFIG_FILE', '/…/data/config/db.config.php');
define('CSV_FILE', '…/data/files/prospects.csv');
require __DIR__ . '…/Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
```

然后，我们设置一个 `try {...} catch (...)` 块，该块捕获 `Throwable`。这允许我们捕获异常和错误：

```php
    try {
        // code goes here
    } catch (Throwable $e) {
        echo $e->getMessage();
    }
```

在 `try {...} catch (...)` 块内部，我们获取连接和大文件迭代器类的实例：

```php
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $iterator = (new Application\Iterator\LargeFile(__DIR__ . CSV_FILE))
        ->getIterator('Csv');
```

然后，我们利用 PDO 的 prepare/execute 功能。预编译语句中的 SQL 使用 `?` 来表示在循环中提供的值：

```php
    $sql = 'INSERT INTO `prospects` '
        . '("id","first_name","last_name","address","city","state_province",'
        . '"postal_code","phone","country","email","status","budget",'
        . '"last_updated") '
        . ' VALUES (?,?,?,?,?,?,?,?,?,?,?,?)';
    $statement = $connection->pdo->prepare($sql);
```

然后，我们使用 `foreach()` 遍历文件迭代器。每个 `yield` 语句生成一个值数组，代表数据库中的一行。然后，我们可以使用这些值与 `PDOStatement::execute()` 一起执行预编译语句，将值行插入到数据库中：

```php
    foreach ($iterator as $row) {
        echo implode(',', $row) . PHP_EOL;
        $statement->execute($row);
    }
```

然后，您可以检查数据库以验证数据是否成功插入。

## 递归目录迭代器

获取目录中的文件列表非常容易。传统上，开发人员使用 `glob()` 函数来实现此目的。从目录树中的特定点递归获取所有文件和目录的列表则更具挑战性。此配方利用了 **(SPL 标准 PHP 库)** 类 `RecursiveDirectoryIterator`，它可以出色地完成这一任务。

该类的作用是解析目录树，找到第一个子节点，然后跟随分支，直到没有更多子节点为止，然后停止！不幸的是，这不是我们想要的。我们需要想办法让 `RecursiveDirectoryIterator` 从给定的起点继续解析每个树和分支，直到没有更多文件或目录为止。恰好有一个出色的类 `RecursiveIteratorIterator` 可以做到这一点。通过将 `RecursiveDirectoryIterator` 包装在 `RecursiveIteratorIterator` 中，我们可以完成对任何目录树的完全遍历。

> **警告！**
>
> 请非常小心文件系统遍历的起始位置。如果您从根目录开始，递归过程可能会在所有文件和目录都被定位之前不会停止，从而导致服务器崩溃！

## 具体操作...

1. 首先，我们定义一个 `Application\Iterator\Directory` 类，该类定义适当的属性和常量，并使用外部类：

```php
namespace Application\Iterator;

use Exception;
use RecursiveDirectoryIterator;
use RecursiveIteratorIterator;
use RecursiveRegexIterator;
use RegexIterator;

class Directory
{

    const ERROR_UNABLE = 'ERROR: Unable to read directory';

    protected $path;
    protected $rdi;
    // recursive directory iterator
```

2. 构造函数基于目录路径在 `RecursiveIteratorIterator` 内部创建一个 `RecursiveDirectoryIterator` 实例：

```php
public function __construct($path)
{
    try {
        $this->rdi = new RecursiveIteratorIterator(
            new RecursiveDirectoryIterator($path),
```

# 3

## 使用 PHP 函数式编程

本章将涵盖以下主题：

- 开发函数
- 提示数据类型
- 使用返回值数据类型
- 使用迭代器
- 使用生成器编写自己的迭代器

### 简介

在本章中，我们将介绍利用 PHP **函数式编程** 特性的配方。函数式或**过程式**编程是 PHP 4 版本引入首个**面向对象编程 (OOP)** 实现之前，传统上编写 PHP 代码的方式。在函数式编程中，程序逻辑被封装到一系列离散的**函数**中，这些函数通常存储在单独的 PHP 文件中。然后，该文件可以被包含在任何未来的脚本中，从而允许随时调用所定义的函数。

### 开发函数

最困难的方面在于决定如何将程序逻辑拆分为函数。另一方面，在 PHP 中开发函数的机制相当简单。只需使用 `function` 关键字，给它一个名称，并在后面加上括号。

#### 实现方法...

1. 代码本身放在花括号内，如下所示：

```php
function someName ($parameter)
{
    $result = 'INIT';
    // one or more statements which do something
    // to affect $result
    $result .= ' and also ' . $parameter;
    return $result;
}
```

2. 你可以定义一个或多个**参数**。要使其中一个变为可选参数，只需为其分配一个默认值。如果你不确定要分配什么默认值，请使用 `NULL`：

```php
function someOtherName ($requiredParam, $optionalParam = NULL)
{
    $result = 0;
    $result += $requiredParam;
    $result += $optionalParam ?? 0;
    return $result;
}
```

你不能重新定义函数。唯一的例外是当重复的函数在不同的命名空间中定义时。以下定义将产生错误：

```php
function someTest ()
{
    return 'TEST';
}
function someTest ($a)
{
    return 'TEST: ' . $a;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_76_0.png)

3. 如果你不知道将为你的函数提供多少个参数，或者你想允许无限数量的参数，请使用 `...` 后跟变量名。所有提供的参数将以数组形式出现在该变量中：

```php
function someInfinite(...$params)
{
    // any params passed go into an array $params
    return var_export($params, TRUE);
}
```

4. 函数可以调用自身。这被称为**递归**。以下函数执行递归目录扫描：

```php
function someDirScan($dir)
{
    // uses "static" to retain value of $list
    static $list = array();
    // get a list of files and directories for this path
    $list = glob($dir . DIRECTORY_SEPARATOR . '*');
    // loop through
    foreach ($list as $item) {
        if (is_dir($item)) {
            $list = array_merge($list, someDirScan($item));
        }
    }
    return $list;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_77_0.png)

> 在函数内部使用 **static** 关键字的功能已在语言中存在了 12 年多。**static** 的作用是在**static** 声明时初始化变量一次，然后在同一请求中的函数调用之间保持该值的保留。

如果你需要在 HTTP 请求之间保留变量的值，请确保 PHP 会话已启动，并将值存储在 `$_SESSION` 中。

5. 在 PHP **命名空间**内部定义时，函数会受到约束。你可以利用这一特性，在函数库之间提供额外的逻辑分离。为了*锚定*命名空间，你需要添加 **use** 关键字。以下示例放置在不同的命名空间中。请注意，即使函数名称相同，由于它们彼此不可见，因此没有冲突。

6. 我们在命名空间 `Alpha` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_alpha.php` 中：

```php
<?php
namespace Alpha;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

7. 然后我们在命名空间 `Beta` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_beta.php` 中：

```php
<?php
namespace Beta;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

8. 然后我们可以通过在函数名称前加上命名空间名称来调用 `someFunction()`：

```php
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_alpha.php');
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_beta.php');
Alpha\someFunction();
Beta\someFunction();
```

> **最佳实践**
>
> 将函数库（以及类！）放入单独的文件中通常被认为是最佳实践：每个命名空间一个文件，每个文件一个类或函数库。
>
> 可以在单个命名空间中定义许多类或函数库。你开发到单独命名空间中的唯一原因是如果你希望促进功能的逻辑分离。

## 工作原理……

最佳实践是将所有逻辑相关的函数放入一个单独的 PHP 文件中。创建一个名为 `chap_03_developing_functions_library.php` 的文件，并将这些函数（前文已描述）放入其中：

- someName()
- someOtherName()
- someInfinite()
- someDirScan()
- someTypeHint()

然后，在调用这些函数的代码中引入该文件。

```php
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_library.php');
```

若要调用 `someName()` 函数，请使用该函数名称并提供参数。

```php
echo someName('TEST');    // 返回 "INIT" 以及 TEST"
```

你可以使用一个或两个参数来调用 `someOtherName()` 函数，如下所示：

```php
echo someOtherName(1);     // 返回  1
echo someOtherName(1, 1);  //  返回 2
```

`someInfinite()` 函数接受无限（或可变）数量的参数。以下是调用此函数的几个示例：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

## 使用 PHP 函数式编程

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_0.png)

我们可以按照以下方式调用 `someDirScan()`：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_1.png)

## 提示数据类型

在许多开发函数的场景中，你可能需要在其他项目中重用相同的函数库。此外，如果你在一个团队中工作，你的代码可能会被其他开发人员使用。为了控制代码的使用，采用**类型提示**可能更为合适。这涉及指定你的函数对特定参数所期望的数据类型。

### 如何实现……

1. 函数中的参数可以加上类型提示前缀。以下类型提示在 PHP 5 和 PHP 7 中均可用：
   - Array
   - Class
   - Callable

2. 如果调用函数时传递了错误的参数类型，则会抛出 TypeError。以下示例要求一个数组、一个 DateTime 实例以及一个匿名函数：
