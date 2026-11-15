# # Autoloading

PHP doesn’t need to load up all your app and dependencies on every request. Each request will use only a small fraction of the code. In modern PHP we split our code into multiple files, usually one class per file, and then only include the files we need to deal with the current task in hand. To make this process easier for the developer PHP has an autoloading mechanism. It means you don’t have to specify which files to include for each request. PHP will use the autoloader to work out which files to include when they are needed. Composer creates an autoloader for us based on the configuration in our composer.json file.

Use the composer install command to download dependencies and create the autoloader.

```
$ composer install
```

We have not specified any required packages yet, so nothing is downloaded to our project. Composer just creates the autoloader in the vendor/composer folder. We load this in our app by including the vendor/autoload.php file.