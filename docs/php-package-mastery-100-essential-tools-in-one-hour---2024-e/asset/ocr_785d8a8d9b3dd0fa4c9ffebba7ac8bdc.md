# 4. PHP dotenv

PHP dotenv is a library that loads environment variables from a .env file into the PHP environment. It is useful for managing application settings separate from code, which enhances security and flexibility across different deployment environments.

Ex:PHP dotenv

```
```php
require 'vendor/autoload.php';
$dotenv = Dotenv\Dotenv::createImmutable(__DIR__);
$dotenv->load();
echo 'Database password: ' . $_ENV['DB_PASSWORD'];
?>
```
```

Displays the database password stored in the .env file.

This example begins with the inclusion of the Composer autoload file through require 'vendor/autoload.php';. Composer is a tool for dependency management in PHP, allowing you to declare the libraries your project depends on and it will manage (install/update) them for you.The Dotenv\Dotenv::createImmutable(__DIR__) method creates an immutable dotenv object, pointing to the directory where the .env file is located. The