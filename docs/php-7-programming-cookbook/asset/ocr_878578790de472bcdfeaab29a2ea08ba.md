# Building a Foundation

> You will notice that the methods and properties in this class are static. This gives us greater flexibility when registering the autoloading method, and also lets us treat the Loader class like a **Singleton**.

+   Next, we define the method that calls loadFile() and actually performs the logic to locate the file based on the namespaced classname. This method derives a filename by converting the PHP namespace separator \ into the directory separator appropriate for this server and appending .php:

```
public static function autoLoad($class)
{
    $success = FALSE;
    $fn = str_replace('\\', DIRECTORY_SEPARATOR, $class)
        . '.php';
    foreach (self::$dirs as $start) {
        $file = $start . DIRECTORY_SEPARATOR . $fn;
        if (self::loadFile($file)) {
            $success = TRUE;
            break;
        }
    }
    if (!$success) {
        if (!self::loadFile(__DIR__
            . DIRECTORY_SEPARATOR . $fn)) {
            throw new \Exception(
                self::UNABLE_TO_LOAD . ' ' . $class);
        }
    }
    return $success;
}
```

+   Next, the method loops through an array of directories we call self::$dirs, using each directory as a starting point for the derived filename. If not successful, as a last resort, the method attempts to load the file from the current directory. If even that is not successful, an Exception is thrown.

+   Next, we need a method that can add more directories to our list of directories to test. Notice that if the value provided is an array, array_merge() is used. Otherwise, we simply add the directory string to the self::$dirs array:

```
public static function addDirs($dirs)
{
    if (is_array($dirs)) {
        self::$dirs = array_merge(self::$dirs, $dirs);
    } else {
```