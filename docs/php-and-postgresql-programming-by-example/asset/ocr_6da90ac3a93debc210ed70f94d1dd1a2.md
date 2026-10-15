![](bbox=[0.096, 0.06, 0.898, 0.409])

For database connection configuration, I created a PHP file, called **dbinfo.php**. The following is a content of dbinfo.php.

```
```php
<?php

$dbServer = "localhost";
$username = "user_db";
$password = "user_pass";
$database = "postgres";

$connString = "host=$dbServer dbname=$database user=$username password=$
```
```

Please change database parameter values based on your configuration.

You can modify this database configuration. The next step is to create a PHP class, called **CRUDDemo**. This class provides several functions to execute CRUD operations. Let’s start. Create PHP file, called **CRUDDemo.php**. Then write this script.

```
```php
<?php

include('dbinfo.php');

class CRUDDemo {
    private $msg = "";

    public function getMsg()
    {
```
```