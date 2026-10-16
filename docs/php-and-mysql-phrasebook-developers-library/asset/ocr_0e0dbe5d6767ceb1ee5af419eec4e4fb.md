![](bbox=[0.04, 0.08, 0.86, 0.56])

Figure 7.4 The contents of php.ini as a multidimensional array (parse_ini_file.php; excerpt).

TIP: If you want to avoid the grouping by sections in the INI file, just omit the second parameter parse_ini_file(); then, you get all settings at once.

`parse_ini_file('php.ini');`

# Retrieving File Information

```
<?php
$filename = __FILE__;
$data = array(
    'fileatime' => fileatime($filename),
    'filegroup' => filegroup($filename),
```