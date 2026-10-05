# Enabling Monkey Patching

Next, we enable Monkey Patching, because we will need it later.

> Monkey Patching is a method used to replace code on the fly without modifying the original code. The Monkey Patching provided by ci-phpunit-test can replace exit() or die(), as well as some functions and methods of user-defined classes, to prevent unwanted behavior in the code being tested.

To enable monkey patching, open application/tests/Bootstrap.php in your editor and remove the comment marks below. Remove the lines 298 and 323.

```
/*
* Enabling Monkey Patching
* If you want to use monkey patching, uncomment below code and configure
* for your application.
*/
// Remove this line.
require DIR_ . . '/_ci_phpunit_test/patcher/bootstrap.php';
MonkeyPatchManager::init([
    'cache_dir' => APPATH . '/tests/_ci_phpunit_test/tmp/cache',
    // Directories to patch on source files
    'include_paths' => [
        APPPATH,
        BASEPATH,
    ],
    // Excluding directories to patch
    'exclude_paths' => [
        APPPATH . '/tests/',
    ],
    // All patches you use.
    'patcher_list' => [
        'ExitPatcher',
        'FunctionPatcher',
        'MethodPatcher',
    ],
    // Additional functions to patch
    'functions_to_patch' => [
```