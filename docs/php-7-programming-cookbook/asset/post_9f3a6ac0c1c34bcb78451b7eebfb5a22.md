
## How it works...

Add these code examples to a single PHP file, chap_02_foreach.php. Run the script under PHP 5 from the command line. The expected output is as follows:

```
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter02$
PHP VERSION: 5.6.22
unset() in foreach()
1
2
3
unset() in foreach() after assignment by reference
1
3
current() in foreach()
1 - 2
2 - 3
3 - 0
adding new element in foreach()
1
array_pop() in foreach()
1
2
1
1
reference in foreach()
0 - 0
0 - 1
0 - 3
ed@ed:~/Desktop/Repos/php7_recipes/source/chapter02$
```

Run the same script under PHP 7 and notice the difference:

| PHP 5 | PHP 7 |
| :--- | :--- |
| **0 - 0** | **0 - 0** |
| **0 - 1** | **0 - 1** |
| **0 - 3** | **0 - 3** |
| **3 - 0** | |
| **3 - 3** | |

![](img/39390f6d56c5a83b28db083a8bd5185c_58_0.png)

### See also

For more information, consult the RFC addressing this issue, which was accepted. A write-up on this RFC can be found at <https://wiki.php.net/rfc/php7_foreach>.

## Improving performance using PHP 7 enhancements

One trend that developers are taking advantage of is the use of **anonymous functions**. One classic problem, when dealing with anonymous functions, is to write them in such a way that any object can be bound to `$this` and the function will still work. The approach used in PHP 5 code is to use `bindTo()`. In PHP 7, a new method, `call()`, was added, which offers similar functionality, but vastly improved performance.

### How to do it...

To take advantage of `call()`, execute an anonymous function in a lengthy loop. In this example, we will demonstrate an anonymous function, that scans through a log file, identifying IP addresses sorted by how frequently they appear:

1. First, we define a `Application\Web\Access` class. In the constructor, we accept a filename as an argument. The log file is opened as an `SplFileObject` and assigned to `$this->log:`

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

2. Next, we define a generator that iterates through the file, line by line:

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

3. Finally, we define a method that looks for, and extracts as a sub-match, an IP address:

```php
public function getIp($line)
{
    preg_match('/(\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}\\.\\d{1,3})/', $line, $match);
    return $match[1] ?? '';
}
```

### How it works...

First of all, we define a calling program, chap_02_performance_using_php7_enhancement_call.php, that takes advantage of the autoloading class defined in *Chapter 1, Building a Foundation*, to obtain an instance of Application\Web\Access:

```php
define('LOG_FILES', '/var/log/apache2/*access*.log');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
```

Next we define the anonymous function, which processes one line in the log file. If an IP address is detected, it becomes a key in the $frequency array, and the current value for this key is incremented:

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

We then loop through the iteration of lines in each log file found, processing IP addresses:

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

You can actually do the same thing in PHP 5. Two lines of code are required, however:

```
$func = $freq->bindTo($access);
$func($line);
```

Performance is **20% to 50%** slower than using `call()` in PHP 7.

Finally, we reverse-sort the array, but maintain the keys. The output is produced in a simple `foreach()` loop:

```
arsort($access->frequency) ;
foreach ($access->frequency as $key => $value) {
    printf('$16s : %6d' . PHP_EOL, $key, $value);
}
```

The output will vary depending on which `access.log` you process. Here is a sample:

![](img/39390f6d56c5a83b28db083a8bd5185c_61_0.png)

## There's more...

Many of the PHP 7 performance improvements have nothing to do with new features and functions. Rather, they take the form of internal improvements, which are *invisible* until you start running your programs. Here is a short list of improvements that fall into this category:

| Feature | More info | Notes |
| :--- | :--- | :--- |
| Fast parameter parsing | [https://wiki.php.net/rfc/fast_zpp](https://wiki.php.net/rfc/fast_zpp) | In PHP 5, parameters provided to functions have to be parsed for every single function call. The parameters were passed in as a `string`, and parsed in a manner similar to the `scanf()` function. In PHP 7 this process has been optimized and made much more efficient, resulting in a significant performance improvement. The improvement is difficult to measure, but seems to be in the region of 6%. |
| PHP NG | [https://wiki.php.net/rfc/phpng](https://wiki.php.net/rfc/phpng) | The PHP **NG (Next Generation)** initiative represents a rewrite of most of the PHP language. It retains existing functionality, but involves any and all time-savings and efficiency measures imaginable. Data structures have been compacted, and memory is used more efficiently. Just one change, which affects array handling, for example, has resulted in a significant performance increase, while at the same time greatly reducing memory usage. |
| Removing dead weight | [https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts) | There were approximately two dozen extensions that fell into one of these categories: deprecated, no longer maintained, unmaintained dependencies, or not ported to PHP 7. A vote by the group of core developers determined to remove about 2/3 or the extensions on the "short list". This results in reduced overhead and faster overall future development of the PHP language. |

## Iterating through a massive file

Functions such as `file_get_contents()` and `file()` are quick and easy to use however, owing to memory limitations, they quickly cause problems when dealing with massive files. The default setting for the `php.ini` `memory_limit` setting is **128 megabytes**. Accordingly, any file larger than this will not be loaded.

Another consideration when parsing through massive files is how quickly does your function or class method produce output? When producing user output, for example, although it might at first glance seem better to accumulate output in an array. You would then output it all at once for improved efficiency. Unfortunately, this might have an adverse impact on the user experience. It might be better to create a **generator**, and use the `yield` keyword to produce immediate results.

### How to do it...

As mentioned before, in a slight twist, however, instead of using the `f*` functions directly, instead we will use the SplFileObject class, which is included in the SPL (Standard PHP Library):

1. First, we define an `Application\Iterator\LargeFile` class with the appropriate properties and constants:

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

2. We then define a `__construct()` method that accepts a filename as an argument and populates the `$file` property with an `SplFileObject` instance. This is also a good place to throw an exception if the file does not exist:

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

3. Next we define a method `fileIteratorByLine()` which uses `fgets()` to read one line of the file at a time. It's not a bad idea to create a complimentary `fileIteratorByLength()` method that does the same thing but uses `fread()` instead. The method that uses `fgets()` would be suitable for text files that include linefeeds. The other method could be used if parsing a large binary file:

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
