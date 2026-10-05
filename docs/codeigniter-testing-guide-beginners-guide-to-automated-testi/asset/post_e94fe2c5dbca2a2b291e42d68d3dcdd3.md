
## Unit Testing CLI Controllers

- $this->seeder (Seeder object)

The glob() function uses the hard-coded argument `APPPATH.'database/seeds/*Seeder.php'`. basename() is a simple function and has no side-effects, so we use it as is. We don't have to mock it.

`glob()`² depends on the file system and has a hard-coded argument. We should mock it.

We can create mock objects, but how do we mock a global function? In this case, we can use Monkey Patching in ci-phpunit-test, but it has some limitations. Monkey patch functions may cause errors if you attempt to replace them, see the documentation³ for details.

By default, only some global functions, like `mt_uniq()`, `md5()`, `time()`, and `date()`, can be patched. To patch the `glob()` function, we use the monkey patching configuration in `application/tests/Bootstrap.php`.

```
--- a/CodeIgniter/application/tests/Bootstrap.php
+++ b/CodeIgniter/application/tests/Bootstrap.php
@@ -316,6 +316,7 @@ MonkeyManager::init[
  // Additional functions to patch
  'functions_to_patch' => [
    //'random_string',
    'glob',
  ],
  'exit_exception_classname' => 'PHPUnitTestException',
]);
```

> The listing above is in a format unified diff. It shows the difference between two files. In short, add the green line starting with + to the original file, to get the new file. See Conventions In This Book for details.

We can patch the `glob()` function with the `MonkeyPatch::patchFunction()` method. The first argument is the name of the function to patch. The second argument is the return value. The third argument is the class and method name in which to apply this patch.

## Unit Testing CLI Controllers

```
MonkeyPatch::patchFunction('glob', [
    '/application/database/seeds/NewsSeeder.php',
    '/application/database/seeds/BookSeeder.php',
    '/application/database/seeds/ShopSeeder.php',
], 'Dbfixture::seed');
```

The glob function will be patched only in the `Dbfixture::seed()` method, and it will return the array passed to the `MonkeyPatch::patchFunction()` method's second argument.

- If you call `MonkeyPatch::patchFunction()` without the third argument, all of the functions (located in include_paths and not in exclude_paths in the monkey patching configuration in the `application/tests/Bootstrap.php` file) called during the test execution will be replaced.

Using `MonkeyPatch::patchFunction()`, we can write a test method like the following:
`application/tests/controllers/Dbfixture_test.php`

```php
public function test_when_run_seed_Then_seeders_are_called() {
    // Patch on glob() function
    MonkeyPatch::patchFunction('glob', [
        '/application/database/seeds/NewsSeeder.php',
        '/application/database/seeds/BookSeeder.php',
        '/application/database/seeds/ShopSeeder.php',
        'Dbfixture::seed';
    ]);

    // Create mock object for CI_Loader
    $loader = $this->getDouble(
        'CI_Loader',
        'library' => null,
    );

    // Create mock object for Seeder
    $seeder = $this->getDouble('Seeder', ['call' => null]);
    $this->verifyInvokedMultipleTimes($seeder, 'call', 3, [
        ['NewsSeeder'],
        ['BookSeeder'],
        ['ShopSeeder'],
    ]);
}
```

## Unit Testing CLI Controllers

```php
// Inject mock objects
$this->obj->load = $loader;
$this->obj->seeder = $seeder;

$this->obj->seed();
```

`$this->verifyInvokedMultipleTimes()` method is a helper method for PHPUnit Mock Objects in ci-phpunit.

```php
$this->verifyInvokedMultipleTimes($seeder, 'call', 3, [
    ['NewsSeeder'],
    ['BookSeeder'],
    ['ShopSeeder'],
]);
```

The above code is equivalent to following:

```php
$seeder->expects($this->exactly(3))
->method('call')
->withConsecutive(
    ['NewsSeeder'],
    ['BookSeeder'],
    ['ShopSeeder'],
);
```

The `withConsecutive()` method can take any number of arrays arguments, depending on the calls you want to test against. Each array is a list of constraints corresponding to the arguments of the method being mocked, when calling with().

Run the phpunit command and execute the tests.

## Patching Class Methods

You can patch user-defined class methods with `MonkeyPatch::patchMethod()`. The first argument is the class name. The second argument is an array containing the method name and its return value:

## Unit Testing CLI Controllers

```php
MonkeyPatch::patchMethod('Dbfixture', [
    'migrate' => null,
    'seed' => null,
]);
```

With the code above, the `migrate()` and `seed()` methods of the `Dbfixture` class will return null. We can write test code for the `all()` method of the `Dbfixture` class like this:

`application/tests/controllers/Dbfi_test.php`

```php
public function test_when_run_all_Then_migrate_and_seed_are_called() {
    MonkeyPatch::patchMethod('Dbfixture', [
        'migrate' => null,
        'seed' => null,
    ]);
    MonkeyPatch::verifyInvokedOnce('Dbfixture::migrate');
    MonkeyPatch::verifyInvokedOnce('Dbfixture::seed');

    $this->obj->all();
}
```

`MonkeyPatch::verifyInvokedOnce()` verifies that a patched class method or a patched function was invoked only once.

In addition to `verifyInvokedOnce()`, there are other methods to verify the number of times a monkey-patched method or function has been invoked:

- `MonkeyPatch::verifyInvokedOnce($class_method, $params)` ... at least once
- `MonkeyPatch::verifyInvokedOnce($class_method, $params)` ... only once
- `MonkeyPatch::verifyInvokedMultipleTimes($class_method, $count, $params)` ... exactly count times
- `MonkeyPatch::verifyNeverInvoked($class_method, $params)` ... never

Run the phpunit command and verify that the tests pass.

## 8.7 Checking Code Coverage

Before checking code coverage, remove the `controllers/Dbfixture.php` line in phpunit.

```
--- a/CodeIgniter/application/tests/phpunit.xml
+++ b/CodeIgniter/application/tests/phpunit.xml
@@ -17,7 +17,6 @@
  <directory suffix=".php">hooks</directory>
  <exclude>
    <file>controllers/Dbfi.php</file>
    <file>libraries/Seeder.php</file>
  </exclude>
```

The listing above is in a format unified diff. It shows the difference between two files. In short, remove the red line starting with - from the original file and add the green line starting with +, to get the new file. See Conventions in This Book for details.

## 9.1 CodeIgniter Rest Server

**CodeIgniter Rest Server** is a fully RESTful implementation for CodeIgniter.
Download the latest version (in this book v2) by https://github.com/chaceris/codeigniter-restserver and unzip it. Copy the following files into your CodeIgniter directory.

```
CodeIgniter/
└── application/
    ├── config/
    │   └── rest.php
    ├── controller/
    │   └── api/
    │       └── Example.php
    ├── libraries/
    │   └── Format.php
    └── REST_Controller.php
```

CodeIgniter Rest Server is licensed under the MIT License. See the [License Agreement for CodeIgniter Rest](https://github.com/chaceris/codeigniter-restserver/blob/master/LICENSE).

## Fixing the CodeIgniter Rest Server

Up to the present we never modified code to write tests. However, we have to modify CodeIgniter Rest Server in order to be able to test.

> **Testing Tip: Untestable Code**
If you can't write tests or it is hard to write tests, it is a sign that your application design should be improved.

First, replace `require` with `require_once` in the Example controller. If there is more than one REST controller, we load them at the same time, which will result in *Fatal error: Cannot redeclare class REST_Controller* if require is used.

## Testing Rest Controllers

```php
--- a/CodeIgniter/application/controllers/api/Example.php
+++ b/CodeIgniter/application/controllers/api/Example.php
@@ -3,7 +3,7 @@
defined('BASEPATH') OR exit('No direct access allowed');
```

// This can be removed if you use __autoload() in config.php OR Modular Extensions
-require APPPATH.'libraries/REST_Controller.php';
require_once APPPATH.'libraries/REST_Controller.php';

/**
* This is example of a few user interaction methods you could use

The listing above is in a format unified diff. It shows the difference between two files. In short, remove the red line starting with - from the original file and add the green line starting with +, to get the new file. See Conversions in This Book for details.

Second, add the catch block below REST_Controller.php. CodeIgniter Rest Server calls exit() and monkey patching by ci-phpunit-test converts it to an exception, but the Rest Server catches it by default. We want to catch the exception thrown by the monkey patch and re-throw it.

```php
--- a/CodeIgniter/application/libraries/REST_Controller.php
+++ b/CodeIgniter/application/libraries/REST_Controller.php
@@ -653,6 +653,11 @@ abstract class REST_Controller extends CI_Controller {
    call_user_func_array([$this, $controller_method], $arguments);
+ catch (PHPUnitTestExitException $ex) {
+
    // This block is for ci-phpunit-test
+    throw $ex;
+ }
 catch (Exception $ex) {
{
    // If the method doesn't exist, then the error will be caught and a error response shown
```

## 9.2 Testing GET Requests

Let's access the web API using the curl command.
