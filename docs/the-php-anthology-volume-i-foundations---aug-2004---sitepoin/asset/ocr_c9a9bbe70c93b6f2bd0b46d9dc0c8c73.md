```
```php
<?php
// Include PEAR::Archive_Tar
require_once 'Archive/Tar.php' ;

// Instantiate Archive_Tar
$tar = new Archive_Tar('demo/demo.tar.gz', 'gz');

// An array of files to archive
$files = array(
  'demo/example.ini',
  'demo/writeSecureScripts.html'
);

// Create the archive file
$tar->create($files);

echo 'Archive created';
?>
```
```

It's pretty simple. When instantiating the class, the second argument tells Archive_Tar what type of compression to use—the alternative to gz (for gzip) is bz2 (for bzip2). You can simply omit the second argument if you don't require compression. The array of file names needs to be specified when you use the create method, the file paths being relative to the location where the above script is executed. That's it.

To extract the file again, we could use the following code:

```
```php
<?php
// Include PEAR::Archive_Tar
require_once 'Archive/Tar.php';

// Instantiate Archive_Tar
$tar = new Archive_Tar('demo/demo.tar.gz');

// Create the archive file
$tar->extract('extract');

echo 'Archive extracted';
?>
```
```