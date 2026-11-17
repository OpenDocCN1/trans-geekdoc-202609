```
ok 10 - objects of class myObject do have a myMethod method
ok 11 - the first and the second array are the same
not ok 12 - the fooBar.php file was properly included
#       Failed test (./test/unit/testTest.php at line 27)
#       Tried to include './fooBar.php'
ok 13 - exception caught successfully
ok 14 # SKIP skipping one test to keep the test count exact in the
condition
ok 15 # TODO one test left to do
# Looks like you planned 16 tests but only ran 15.
# Looks like you failed 1 tests of 16.
```

The diag() method doesn't count as a test. Use it to show comments, so that your test output stays organized and legible. On the other hand, the todo() and skip() methods count as actual tests. A pass()/fail() combination inside a try/catch block counts as a single test.

A well-planned test strategy must contain an expected number of tests. You will find it very useful to validate your own test files—especially in complex cases where tests are run inside conditions or exceptions. And if the test fails at some point, you will see it quickly because the final number of run tests won't match the number given during initialization.

# The test:unit Task

The test:unit task, which launches unit tests from the command line, expects either a list of test names or a file pattern. See Listing 15-5 for details.

Listing 15-5 - Launching Unit Tests

```
// Test directory structure
test/
  unit/
    myFunctionTest.php
    mySecondFunctionTest.php
    foo/
      barTest.php

$ php symfony test:unit myFunction    # Run
myFunctionTest.php
$ php symfony test:unit myFunction mySecondFunction   # Run both tests
$ php symfony test:unit foo/*        # Run barTest.php
$ php symfony test:unit *          # Run all tests
     (recursive)
```

# Stubs, Fixtures, and Autoloading

In a unit test, the autoloading feature is not active by default. Each class that you use in a test must be either defined in the test file or required as an external dependency. That's why many test files start with a group of include lines, as Listing 15-6 demonstrates.

Listing 15-6 - Including Classes in Unit Tests

```
<?php

include dirname(__FILE__).'/../bootstrap/unit.php';
require_once sfConfig::get('sf_symfony_lib_dir').'/util/
sfToolkit.class.php';

$t = new lime_test(7);
```