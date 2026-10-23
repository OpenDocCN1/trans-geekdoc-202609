# 23. Carbon

Carbon is an extension for DateTime that simplifies the work with dates in PHP, providing a more intuitive interface and additional functionalities.

Ex:Carbon

```
```php
require 'vendor/autoload.php';
use Carbon\Carbon;
printf("Right now is %s", Carbon::now()->toDateTimeString());
printf("\nJust a day more is %s", Carbon::now()->addDay()->toDateTimeString());
```
```

Right now is 12:34:56
Just a day more is 2024-03-21 12:34:56

In this code we're using the Carbon library to work with dates in PHP. First, we include the Carbon library using Composer's autoload mechanism (require 'vendor/autoload.php';). Then, we make use of the Carbon class by importing it with the use statement.The Carbon::now()