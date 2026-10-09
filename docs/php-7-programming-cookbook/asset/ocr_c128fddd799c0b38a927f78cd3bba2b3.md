# Using PHP 7 High Performance Features

+   2. We then incorporate an instance of Application\Iterator\LargeFile. We add a new method to this class that is designed to iterate through CSV files:

```PHP
protected function fileIteratorCsv() {
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgetcsv();
        $count++;
    }
    return $count;
}
```

3. We also need to add Csv to the list of allowed iterator methods:

```PHP
const ERROR_UNABLE = 'ERROR: Unable to open file';
const ERROR_TYPE   = 'ERROR: Type must be "ByLength", "ByLine" or "Csv"';

protected $file;
protected $allowedTypes = ['ByLine', 'ByLength', 'Csv'];
```

# How it works...

First we define a config file,/path/to/source/config/db.config.php, that contains database connection parameters:

```
```PHP
<?php
return [
    'driver'   => 'mysql',
    'host'     => 'localhost',
    'dbname'   => 'php7cookbook',
    'user'     => 'cook',
    'password' => 'book',
    'errmode'  => PDO::ERRMODE_EXCEPTION,
];
```
```

Next, we take advantage of the autoloading class defined in Chapter 1, Building a Foundation, to obtain an instance of Application\Database\Connection and Application\Iterator\LargeFile, defining a calling program, chap_02_uploading_csv_to_database.php:

```
```PHP
define('DB_CONFIG_FILE', '/…/data/config/db.config.php');
define('CSV_FILE', '…/data/files/prospects.csv');
require __DIR__ . '…/Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
```
```