# Using PHP 7 High Performance Features

In a slight twist, however, instead of using the f* functions directly, instead we will use the SplFileObject class, which is included in the SPL (Standard PHP Library):

+   1. First, we define a Application\Iterator\LargeFile class with the appropriate properties and constants:

```
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
```

+   2. We then define a __construct() method that accepts a filename as an argument and populates the $file property with an SplFileObject instance. This is also a good place to throw an exception if the file does not exist:

```
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

+   3. Next we define a method fileIteratorByLine() method which uses fgets() to read one line of the file at a time. It's not a bad idea to create a complimentary fileIteratorByLength() method that does the same thing but uses fread() instead. The method that uses fgets() would be suitable for text files that include linefeeds. The other method could be used if parsing a large binary file:

```
protected function fileIteratorByLine()
{
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgets();
        $count++;
```