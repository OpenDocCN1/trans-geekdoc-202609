
## How it works...

First of all, go ahead and define the `Application\Web\Deep` class defined previously, as well as the `Application\Web\Hoover` class defined in the previous recipe.

Next, define a block of code from `chap_01_deep_scan_website.php` that sets up autoloading (as described earlier in this chapter):

```php
<?php
// modify as needed
define('DEFAULT_URL', 'unlikelysource.com');
define('DEFAULT_TAG', 'img');

require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../../');
```

Next, get an instance of our new class:

```php
$deep = new Application\Web\Deep();
```

At this point, you can retrieve URL and tag information from URL parameters. The PHP 7 null coalesce operator is useful for establishing fallback values:

```php
$url = strip_tags($_GET['url']) ?? DEFAULT_URL;
$tag = strip_tags($_GET['tag']) ?? DEFAULT_TAG;
```

Some simple HTML will display results:

```php
foreach ($deep->scan($url, $tag) as $item) {
    $src = $item['attributes']['src'] ?? NULL;
    if ($src && (stripos($src, 'png') || stripos($src, 'jpg'))) {
        printf('<br><img src="%s"/>' , $src);
    }
}
```

## See also

For more information on generators and yield from, please see the article at http://php.net/manual/en/language.generators.syntax.php.

## Creating a PHP 5 to PHP 7 code converter

For the most part, PHP 5.x code can run unchanged on PHP 7. There are a few changes, however, that are classified as **backwards incompatible**. What this means is that if your PHP 5 code is written in a certain way, or uses functions that have been removed, your code will break, and you'll have a nasty error on your hands.

### Getting ready

The **PHP 5 to PHP 7 Code Converter** does two things:

- Scans your code file and converts PHP 5 functionality that has been removed to its equivalent in PHP 7
- Adds comments with `// WARNING` where changes in language usage have occurred, but where a re-write is not possible

![](img/39390f6d56c5a83b28db083a8bd5185c_40_0.png)

> Please note that after running the converter, your code is not guaranteed to work in PHP 7. You will still have to review the `// WARNING` tags added. At the least, this recipe will give you a good head start converting your PHP 5 code to work in PHP 7.

The core of this recipe is the new PHP 7 `preg_replace_callback_array()` function. What this amazing function allows you to do is to present an array of regular expressions as keys, with the value representing an independent callback. You can then pass the string through a series of transformations. Not only that, the subject of the array of callbacks can *itself* be an array.

### How to do it...

1. In a new class `Application\Parse\Convert`, we begin with a `scan()` method, which accepts a filename as an argument. It checks to see if the file exists. If so, it calls the PHP `file()` function, which loads the file into an array, with each array element representing one line:

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

2. Next, we start passing a series of key/value pairs. The key is a regular expression, which is processed against the string. Any matches are passed to the callback, which is represented as the value part of the key/value pair. We check for opening and closing tags that have been removed from PHP 7:

```php
    // replace no-longer-supported opening tags
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php' . $match[1];
        },
    
    // replace no-longer-supported opening tags
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php echo ' . $match[1];
        },
    
    // replace no-longer-supported closing tag
    '!\$>!' =>
        function ($match) {
            return '?>';
        },
```

3. Next is a series of warnings when certain operations are detected and there is a potential code-break between how they're handled in PHP 5 versus PHP 7. In all these cases, the code is not re-written. Instead, an inline comment with the word WARNING is added:

```php
    // changes in how $$$$xx interpolation is handled
    '!(.*)\$\$!!' =>
        function ($match) {
            return '// WARNING: variable interpolation
                ' . ' now occurs left-to-right' . PHP_EOL
                . '// see: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        },
    
    // changes in how the list() operator is handled
    '!(.*?)list\(*?\)(?!' =>
        function ($match) {
            return '// WARNING: changes have been made
                ' . ' in list() operator handling.'
                . ' See: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        };
```

```php
        },

        // instances of \u{
        '!(.*)?\\u{(!' =>
        function ($match) {
            return '// WARNING: \u{xxx} is now considered '
                . 'unicode escape syntax' . PHP_EOL
                . '// see: http://php.net/manual/en/'
                . 'migration70.new-features.php'
                . '#migration70.new-features.unicode-'
                . 'codepoint-escape-syntax' . PHP_EOL
                . $match[0];
        },

        // relying upon set_error_handler()
        '!(.*)?set_error_handler(\s*?\)\.*(!' =>
        function ($match) {
            return '// WARNING: might not '
                . 'catch all errors'
                . '// see: http://php.net/manual/en/'
                . '// language.errors.php7.php'
                . $match[0];
        },

        // session_set_save_handler(xxx)
        '!(.*)?session_set_save_handler(\s*?\)\(.*)\)' =>
        function ($match) {
            if (isset($match[3])) {
                return '// WARNING: a bug introduced in'
                    . 'PHP 5.4 which '
                    . 'affects the handler assigned by '
                    . 'session_set_save_handler() and '
                    . 'where ignore_user_abort() is TRUE '
                    . 'has been fixed in PHP 7.'
                    . 'This could potentially break '
                    . 'your code under '
                    . 'certain circumstances.' . PHP_EOL
                    . 'See: http://php.net/manual/en/'
                    . 'migration70.incompatible.php'
                    . $match[0];
            } else {
                return $match[0];
            }
        },
```

4. Any attempts to use `<<` or `>>` with a negative operator, or beyond 64, is wrapped in a `try { xxx } catch ( { xxx }` block, looking for an `ArithmeticError` to be thrown:

```php
// wraps bit shift operations in try / catch
'!(<(.*)?(\\d\*s*(\\<|\\>\\>\*?-?\[d+] (.*)?)$' =>
function ($match) {
    return '// WARNING: negative and '
    . 'out-of-range bitwise '
    . 'shift operations will now '
    . 'throw an ArithmeticError' . PHP_EOL
    . 'See: http://php.net/manual/en/'
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

> PHP 7 has changed how errors are handled. In some cases, errors are moved into a similar classification as exceptions, and can be caught! Both the `Error` and the `Exception` class implement the `Throwable` interface. If you want to catch either an `Error` or an `Exception`, catch `Throwable`.

5. Next, the converter rewrites any usage of `call_user_method*()`, which has been removed in PHP 7. These are replaced with the equivalent using `call_user_func*():`

```php
// replaces "call_user_method()" with
// "call_user_func()"
'!call_user_method\( (.*)?, (.*)?\) (\b|;) !' =>
function ($match) {
    $params = $match[3] ?? '';
    return '// WARNING: call_user_method() has '
    . 'been removed from PHP 7' . PHP_EOL
    . "call_user_func(['" . trim($match[2]) . "','"
    . trim($match[1]) . '] ' . $params . ');';
},
```

```php
// replaces "call_user_method_array()"
// with "call_user_func_array()"
'!call_user_method_array\( (.*)?, (.*)?, (.*)?\) (\b|;) !' =>
```
