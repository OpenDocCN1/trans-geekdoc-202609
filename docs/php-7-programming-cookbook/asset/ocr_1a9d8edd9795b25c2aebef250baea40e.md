Here is the expected result:

![](bbox=[0.2, 0.17, 0.78, 0.33])

Next, create a directory called uploads from /path/to/source/for/this/chapter. Go ahead and define another calling program, chap_09_middleware_value_objects_file_upload.php, that sets up autoloading and uses the appropriate classes:

```
```php
<?php
define('TARGET_DIR', __DIR__ . '/uploads');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\MiddleWare\UploadedFile;
```
```

Inside a try...catch block, check to see whether any files were uploaded. If so, loop through $ FILES and create UploadedFile instances where tmp_name is set. You can then use the moveTo() method to move the files to TARGET_DIR:

```
```php
try {
    $message = '';
    $uploadedFiles = array();
    if (isset($_FILES)) {
        foreach ($_FILES as $key => $info) {
            if ($info['tmp_name']) {
                $uploadedFiles[$key] = new UploadedFile(
                    $key, $info, TRUE);
                $uploadedFiles[$key]->moveTo(TARGET_DIR);
            }
        }
    }
} catch (Throwable $e) {
    $message = $e->getMessage();
}
?>
```
```