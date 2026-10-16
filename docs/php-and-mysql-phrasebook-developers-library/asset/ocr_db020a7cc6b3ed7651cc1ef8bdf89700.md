```
```php
}

file_put_bzip2_contents('file.txt.bz2', "\n--> This text file contains\nsome random text. <--");
echo 'Data written to file.';
?>
```
```

*Zipping a File with Bzip2 (bzip2write.php)*

The other direction (reading a file from a BZip2 archive) works analogously to reading a regular file. Instead of fopen(), fread(), and fclose(), you use bzopen(), bzread(), and bzclose(), as shown in the following code, which writes a function file_get_bzip2_contents():

```
```php
<?php
function file_get_bzip2_contents($filename) {
    $result = '';
    if ($fp = @bzopen($filename, 'wb')) {
        while ($data = bzread($fp, 4096)) {
            $result .= $data;
        }
        bzclose($fp);
        return $result;
    } else {
        return false;
    }
}

echo nl2br(htmlspecialchars(
    file_get_bzip2_contents('file.txt.bz2')
));
?>
```
```

*Unzipping a File with Bzip2 (bzip2read.php)*