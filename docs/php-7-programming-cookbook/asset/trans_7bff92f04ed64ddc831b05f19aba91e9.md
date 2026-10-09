

## 工作原理...

首先，请继续定义前面提到的 `Application\Web\Deep` 类，以及上一道菜中定义的 `Application\Web\Hoover` 类。

接下来，从 `chap_01_deep_scan_website.php` 中定义一段设置自动加载的代码（如本章前面所述）：

```php
<?php
// 根据需要修改
define('DEFAULT_URL', 'unlikelysource.com');
define('DEFAULT_TAG', 'img');

require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../../');
```

接下来，获取我们新类的实例：

```php
$deep = new Application\Web\Deep();
```

此时，你可以从 URL 参数中获取 URL 和标签信息。PHP 7 的 null 合并运算符对于建立回退值非常有用：

```php
$url = strip_tags($_GET['url']) ?? DEFAULT_URL;
$tag = strip_tags($_GET['tag']) ?? DEFAULT_TAG;
```

一些简单的 HTML 将显示结果：

```php
foreach ($deep->scan($url, $tag) as $item) {
    $src = $item['attributes']['src'] ?? NULL;
    if ($src && (stripos($src, 'png') || stripos($src, 'jpg'))) {
        printf('<br><img src="%s"/>' , $src);
    }
}
```

## 参见

关于生成器和 yield from 的更多信息，请参见 http://php.net/manual/en/language.generators.syntax.php 上的文章。

## 创建一个 PHP 5 到 PHP 7 代码转换器

在大多数情况下，PHP 5.x 代码可以在 PHP 7 上无更改地运行。然而，有一些变化被归类为**向后不兼容**。这意味着，如果你的 PHP 5 代码以特定方式编写，或者使用了已被移除的函数，你的代码将会崩溃，你会遇到一个棘手的错误。

### 准备就绪

**PHP 5 到 PHP 7 代码转换器** 做两件事：

- 扫描你的代码文件并将已移除的 PHP 5 功能转换为 PHP 7 中的等价物
- 在语言用法发生变化但无法重写代码的地方添加 `// WARNING` 注释

![](img/39390f6d56c5a83b28db083a8bd5185c_40_0.png)

> 请注意，运行转换器后，你的代码不保证能在 PHP 7 中正常工作。你仍然需要检查添加的 `// WARNING` 标签。至少，这个食谱能让你在将 PHP 5 代码转换为 PHP 7 兼容代码时有一个良好的开端。

这个食谱的核心是新的 PHP 7 `preg_replace_callback_array()` 函数。这个神奇的函数允许你呈现一个以正则表达式为键的数组，其值代表独立的回调。然后你可以将字符串通过一系列转换。不仅如此，回调数组的主题本身*可以*是一个数组。

### 具体操作...

1. 在一个新的类 `Application\Parse\Convert` 中，我们从 `scan()` 方法开始，该方法接受一个文件名作为参数。它检查文件是否存在。如果存在，它调用 PHP 的 `file()` 函数，该函数将文件加载到数组中，每个数组元素代表一行：

```php
public function scan($filename)
{
    if (!file_exists($filename)) {
        throw new Exception(
            self::EXCEPTION_FILE_NOT_EXISTS);
    }
    $contents = file($filename);
    echo 'Processing: ' . $filename . PHP_EOL;

    $result = preg_replace_callback_array( [
```

2. 接下来，我们开始传递一系列键/值对。键是一个正则表达式，该表达式针对字符串进行处理。任何匹配项都会传递给回调，回调由键/值对的值部分表示。我们检查已从 PHP 7 中移除的开启和关闭标签：

```php
    // 替换不再支持的开启标签
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php' . $match[1];
        },
    
    // 替换不再支持的开启标签
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php echo ' . $match[1];
        },
    
    // 替换不再支持的关闭标签
    '!\$>!' =>
        function ($match) {
            return '?>';
        },
```

3. 接下来是一系列警告，当检测到某些操作且在 PHP 5 与 PHP 7 中处理这些操作的方式存在潜在代码破坏时发出警告。在所有这些情况下，代码不会被重写。相反，会添加一个包含 WARNING 字样的内联注释：

```php
    // $$$$xx 插值处理方式的变更
    '!(.*)\$\$!!' =>
        function ($match) {
            return '// WARNING: 变量插值
                ' . ' 现在从左到右进行' . PHP_EOL
                . '// 参见: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        },
    
    // list() 运算符处理方式的变更
    '!(.*?)list\(*?\)(?!' =>
        function ($match) {
            return '// WARNING: list() 运算符
                ' . ' 的处理方式已发生变更。'
                . ' 参见: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        };
```

```php
        },

        // \u{ 的实例
        '!(.*)?\\u{(!' =>
        function ($match) {
            return '// WARNING: \u{xxx} 现在被认为是 '
                . 'unicode 转义语法' . PHP_EOL
                . '// 参见: http://php.net/manual/en/'
                . 'migration70.new-features.php'
                . '#migration70.new-features.unicode-'
                . 'codepoint-escape-syntax' . PHP_EOL
                . $match[0];
        },

        // 依赖 set_error_handler()
        '!(.*)?set_error_handler(\s*?\)\.*(!' =>
        function ($match) {
            return '// WARNING: 可能无法 '
                . '捕获所有错误'
                . '// 参见: http://php.net/manual/en/'
                . '// language.errors.php7.php'
                . $match[0];
        },

        // session_set_save_handler(xxx)
        '!(.*)?session_set_save_handler(\s*?\)\(.*)\)' =>
        function ($match) {
            if (isset($match[3])) {
                return '// WARNING: PHP 5.4 中引入的'
                    . ' 一个影响 session_set_save_handler() 分配的处理程序 '
                    . ' 且 ignore_user_abort() 为 TRUE 的 '
                    . ' bug 已在 PHP 7 中修复。'
                    . ' 这可能会在 '
                    . ' 某些情况下 '
                    . ' 破坏你的代码。' . PHP_EOL
                    . '参见: http://php.net/manual/en/'
                    . 'migration70.incompatible.php'
                    . $match[0];
            } else {
                return $match[0];
            }
        },
```

4. 任何尝试使用 `<<` 或 `>>` 配合负运算符，或超出 64 的情况，都会被包裹在一个 `try { xxx } catch ( { xxx }` 块中，以查找抛出的 `ArithmeticError`：

```php
// 将位移操作包裹在 try / catch 中
'!(<(.*)?(\\d\*s*(\\<|\\>\\>\*?-?\[d+] (.*)?)$' =>
function ($match) {
    return '// WARNING: 负数和 '
    . '超范围的按位 '
    . '移位操作现在将 '
    . '抛出 ArithmeticError' . PHP_EOL
    . '参见: http://php.net/manual/en/'
    . 'migration70.incompatible.php'
    . 'try {' . PHP_EOL
    . "\t" . $match[0] . PHP_EOL
    . '}' catch (\ArithmeticError $e) {'
    . "\t" . 'error_log("File:" '
    . $e->getFile()
    . " Message:" . $e->getMessage());'
    . '}' . PHP_EOL;
},
```

> PHP 7 改变了错误处理方式。在某些情况下，错误被移动到与异常类似的分类中，并且可以被捕获！`Error` 和 `Exception` 类都实现了 `Throwable` 接口。如果你想捕获 `Error` 或 `Exception`，就捕获 `Throwable`。

5. 接下来，转换器重写任何对 `call_user_method*()` 的使用，这些功能已在 PHP 7 中被移除。它们被替换为使用 `call_user_func*()` 的等价物：

```php
// 将 "call_user_method()" 替换为
// "call_user_func()"
'!call_user_method\( (.*)?, (.*)?\) (\b|;) !' =>
function ($match) {
    $params = $match[3] ?? '';
    return '// WARNING: call_user_method() 已 '
    . '从 PHP 7 中移除' . PHP_EOL
    . "call_user_func(['" . trim($match[2]) . "','"
    . trim($match[1]) . '] ' . $params . ');';
},
```

```php
// 将 "call_user_method_array()"
// 替换为 "call_user_func_array()"
'!call_user_method_array\( (.*)?, (.*)?, (.*)?\) (\b|;) !' =>
```

