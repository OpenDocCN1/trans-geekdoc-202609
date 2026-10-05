# Adding Tests

It is easy to add test code for the Ctof() method, because Ctof() is just the opposite of FtoC(). We can reuse the data provider from the test_FtoC() method.

# Exercise

Please stop here and think about how you would write the test method.

Update the test_FtoC() method:

```
application/tests/libraries/temperature_converter_test.php
/**
 * @dataProvider provide_temperature_data
 */
public function test_FtoC($expected, $degree) {
    $obj = new Temperature_converter();
    $actual = $obj->FtoC($degree);
    $this->assertEquals($expected, $actual, '', 0.01);
}
```

The order of the test_FtoC() parameters is reversed.
This test class is okay, but we can still improve it a bit with PHPUnit's setUp() method.

# Fixtures

A fixture is a state for an application. If you run tests, you must set the world up in a known state before running tests, because any difference in the state may change the test results.
PHPUnit has methods for defining fixtures. In this test case, we don't need to do anything, because the class under has no dependencies except for PHP's internal function, round(). The round() also has no dependencies, it returns a calculated value.
However, we can still improve our test code by setting up our environment.

# setUp()

setUp() is a method which is called before a test method is run. In other words, PHPUnit calls setUp() before running each test method. If you use it, you can share the setup code and the state over multiple test methods.