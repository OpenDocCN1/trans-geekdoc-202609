
1. 首先，我们定义一个 `Application\Web\Access` 类。在构造函数中，我们接受一个文件名作为参数。日志文件以 `SplFileObject` 打开，并赋值给 `$this->log:`

```php
namespace Application\Web;

use Exception;
use SplFileObject;

class Access
{
    const ERROR_UNABLE = 'ERROR: unable to open file';
    protected $log;
    public $frequency = array();
    
    public function __construct($filename)
    {
        if (!file_exists($filename)) {
            $message = __METHOD__ . ' : ' . self::ERROR_UNABLE . PHP_EOL;
            $message .= strip_tags($filename) . PHP_EOL;
            throw new Exception($message);
        }
        $this->log = new SplFileObject($filename, 'r');
    }
}
```

2. 接下来，我们定义一个生成器，逐行遍历文件：

```php
public function fileIteratorByLine()
{
    $count = 0;
    while (!$this->log->eof()) {
        yield $this->log->fgets();
        $count++;
    }
    return $count;
}
```

3. 最后，我们定义一个方法，查找 IP 地址并将其作为子匹配项提取出来：

```php
public function getIp($line)
{
    preg_match('/(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/', $line, $match);
    return $match[1] ?? '';
}
```

## 工作原理...

首先，我们定义一个调用程序 `chap_02_performance_using_php7_enhancement_call.php`，它利用*第 1 章，奠定基础*中定义的自动加载类，获取 `Application\Web\Access` 的实例：

```php
define('LOG_FILES', '/var/log/apache2/*access*.log');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
```

接下来我们定义匿名函数，该函数处理日志文件中的一行。如果检测到 IP 地址，它将成为 `$frequency` 数组中的一个键，并且该键的当前值将递增：

```php
// define functions
$freq = function ($line) {
    $ip = $this->getIp($line);
    if ($ip) {
        echo '.';
        $this->frequency[$ip] =
            (isset($this->frequency[$ip])) ? $this->frequency[$ip] + 1 : 1;
    }
};
```

然后我们遍历找到的每个日志文件中的每一行迭代，处理 IP 地址：

```php
foreach (glob(LOG_FILES) as $filename) {
    echo PHP_EOL . $filename . PHP_EOL;
    // access class
    $access = new Application\Web\Access($filename);
    foreach ($access->fileIteratorByLine() as $line) {
        $freq->call($access, $line);
    }
}
```

实际上你可以在 PHP 5 中做同样的事情，但是需要两行代码：

```
$func = $freq->bindTo($access);
$func($line);
```

与在 PHP 7 中使用 `call()` 相比，性能要慢**20% 到 50%**。

最后，我们对数组进行逆序排序，但保留键。输出在一个简单的 `foreach()` 循环中产生：

```
arsort($access->frequency) ;
foreach ($access->frequency as $key => $value) {
    printf('$16s : %6d' . PHP_EOL, $key, $value);
}
```

输出将根据你处理的哪个 `access.log` 而有所不同。以下是一个示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_61_0.png)

## 更多...

许多 PHP 7 的性能改进与新特性和函数无关。相反，它们以内部改进的形式出现，直到你开始运行程序前都是*不可见的*。以下是属于此类别的一些改进的简短列表：

| 特性 | 更多信息 | 备注 |

| :--- | :--- | :--- |

| 快速参数解析 | [https://wiki.php.net/rfc/fast_zpp](https://wiki.php.net/rfc/fast_zpp) | 在 PHP 5 中，提供给函数的参数必须在每次函数调用时都进行解析。参数是以`string`形式传入，并以类似于`scanf()`函数的方式进行解析。在 PHP 7 中，此过程已得到优化，效率大大提高，从而带来了显著的性能提升。这种改进很难衡量，但似乎约为 6%。 |

| PHP NG | [https://wiki.php.net/rfc/phpng](https://wiki.php.net/rfc/phpng) | PHP **NG (下一代)** 计划代表对 PHP 语言大部分内容的重写。它保留了现有功能，但涉及所有可想象的节省时间和提高效率的措施。数据结构已得到压缩，内存使用更加高效。例如，仅仅一个影响数组处理的更改，就带来了显著的性能提升，同时大大减少了内存使用。 |

| 去除无用负载 | [https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts) | 约有二十多个扩展属于以下类别之一：已弃用、不再维护、依赖项不再维护，或尚未移植到 PHP 7。核心开发小组的投票决定移除“短名单”上约 2/3 的扩展。这减少了开销，并加快了 PHP 语言未来的整体开发速度。 |

## 遍历大文件

诸如 `file_get_contents()` 和 `file()` 之类的函数使用起来简单快捷，然而，由于内存限制，在处理大文件时很快就会引发问题。`php.ini` 中 `memory_limit` 设置的默认值为**128 兆字节**。因此，任何大于此大小的文件都不会被加载。

解析大文件时的另一个考虑因素是你的函数或类方法产生输出的速度有多快？例如，在产生用户输出时，乍一看似乎将输出累积在数组中会更好。然后一次性输出以提高效率。不幸的是，这可能会对用户体验产生不利影响。最好创建一个**生成器**，并使用 `yield` 关键字立即产生结果。

## 操作方法...

如前所述，做一个小小的改变，我们不直接使用 `f*` 函数，而是使用包含在 SPL（标准 PHP 库）中的 `SplFileObject` 类：

1. 首先，我们定义一个 `Application\Iterator\LargeFile` 类，并设置相应的属性和常量：

```php
namespace Application\Iterator;

use Exception;
use InvalidArgumentException;
use SplFileObject;
use NoRewindIterator;

class LargeFile
{
    const ERROR_UNABLE = 'ERROR: Unable to open file';
    const ERROR_TYPE   = 'ERROR: Type must be "ByLength",
                         "ByLine" or "Csv"';
    protected $file;
    protected $allowedTypes = ['ByLine', 'ByLength', 'Csv'];
}
```

2. 然后我们定义一个 `__construct()` 方法，它接受文件名作为参数，并使用 `SplFileObject` 实例填充 `$file` 属性。如果文件不存在，这也是抛出异常的好地方：

```php
public function __construct($filename, $mode = 'r')
{
    if (!file_exists($filename)) {
        $message = __METHOD__ . ': ' . self::ERROR_UNABLE . PHP_EOL;
        $message .= strip_tags($filename) . PHP_EOL;
        throw new Exception($message);
    }
    $this->file = new SplFileObject($filename, $mode);
}
```

3. 接下来我们定义一个方法 `fileIteratorByLine()`，该方法使用 `fgets()` 一次读取文件中的一行。创建一个互补的 `fileIteratorByLength()` 方法也是一个不错的主意，该方法做同样的事情，但使用 `fread()` 代替。使用 `fgets()` 的方法适合包含换行符的文本文件。另一个方法可以用于解析大型二进制文件：

```php
protected function fileIteratorByLine()
{
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgets();
        $count++;
    }
}
```

```php
     }
     return $count;
  }

protected function fileIteratorByLength($NumBytes = 1024)
{
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fread($NumBytes);
        $count++;
    }
    return $count;
}
```

4. 最后，我们定义一个 `getIterator()` 方法，该方法返回一个 `NoRewindIterator()` 实例。此方法接受 `ByLine` 或 `ByLength` 作为参数，指的是前一步定义的两个方法。如果调用 `ByLength`，该方法还需要接受 `$numBytes` 参数。我们需要一个 `NoRewindIterator()` 实例是为了强制执行如下事实：在本示例中，我们只是单向读取文件：

```php
public function getIterator($type = 'ByLine', $NumBytes = NULL)
{
    if (!in_array($type, $this->allowedTypes)) {
        $message = __METHOD__ . ': ' . self::ERROR_TYPE . PHP_EOL;
        throw new InvalidArgumentException($message);
    }

    $iterator = 'fileIterator' . $type;
    return new NoRewindIterator($this->$iterator($NumBytes));
}
```

## 工作原理…

首先，我们利用第 1 章*构建基础*中定义的自动加载类，在调用程序 `chap_02_iterating_through_a_massive_file.php` 中获取 `Application\Iterator\LargeFile` 的实例：

```php
define('MASSIVE_FILE', '/../data/files/war_and_peace.txt');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
```

接下来，在一个 **try** {...} **catch** {...} 块中，我们获取一个 `ByLine` 迭代器的实例：

```php
try {
    $largeFile = new Application\Iterator\LargeFile(__DIR__ . MASSIVE_FILE);
    $iterator = $largeFile->getIterator('ByLine');
```

然后，我们提供了一个有用的操作示例，在这种情况下，定义每行的平均单词数：

```php
$words = 0;
foreach ($iterator as $line) {
    echo $line;
    $words += str_word_count($line);
}
echo str_repeat('-', 52) . PHP_EOL;
printf("%-40s : %8d\n", 'Total Words', $words);
printf("%-40s : %8d\n", 'Average Words Per Line',
    ($words / $iterator->getReturn()));
echo str_repeat('-', 52) . PHP_EOL;
```

然后结束 **catch** 块：

```php
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

预期输出（此处因过大无法展示！）显示，在 Project Gutenberg 版本的*战争与和平*中有 566,095 个单词。此外，我们发现每行的平均单词数为 8。

## 将电子表格上传到数据库

虽然 PHP 不具备读取特定电子表格格式（即 XLSX、ODS 等）的直接功能，但它确实具备读取 **CSV 逗号分隔值** 文件的能力。因此，为了处理客户提供的电子表格，您需要要求他们以 CSV 格式提供文件，或者您需要自行执行转换。

## 准备工作…

在将电子表格（即 CSV 文件）上传到数据库时，有三个主要考虑因素：

- 遍历（可能）巨大的文件

- 将每个电子表格行提取到 PHP 数组中

- 将 PHP 数组插入到数据库中

巨大文件的遍历将使用前述配方处理。我们将使用 `fgetcsv()` 函数将 CSV 行转换为 PHP 数组。最后，我们将使用 **PDO PHP 数据对象** 类来建立数据库连接并执行插入操作。

## 具体操作...

1. 首先，我们定义一个 `Application\Database\Connection` 类，该类根据提供给构造函数的参数集创建 PDO 实例：

```php
<?php
namespace Application\Database;

use Exception;
use PDO;

class Connection
{
    const ERROR_UNABLE = 'ERROR: Unable to create database connection';
    public $pdo;

    public function __construct(array $config)
    {
        if (!isset($config['driver'])) {
            $message = __METHOD__ . ' : ' . self::ERROR_UNABLE . PHP_EOL;
            throw new Exception($message);
        }
        $dsn = $config['driver']
            . ':host=' . $config['host']
            . ';dbname=' . $config['dbname'];
        try {
            $this->pdo = new PDO($dsn,
                $config['user'],
                $config['password'],
                [PDO::ATTR_ERRMODE => $config['errmode']]);
        } catch (PDOException $e) {
            error_log($e->getMessage());
        }
    }
}
```

## 使用 PHP 7 高性能特性

2. 然后，我们将 `Application\Iterator\LargeFile` 的实例整合进来。我们向该类添加一个新方法，旨在遍历 CSV 文件：
