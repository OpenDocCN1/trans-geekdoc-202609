# PHPUnit Basics

Fortunately, PHPUnit includes functionality to repeat tests like this. One method of doing so is with a Data Provider. Using this, we can write tests like the following:

application/tests/libraries/Temperature_converter_test.php

```
<?php
class Temperature_converter_test extends TestCase {
  /**
   * @dataProvider provide_temperature_data
   */
  public function test_FtoC($degree, $expected) {
    $obj = new Temperature_converter();
    $actual = $obj->FtoC($degree);
    $this->assertEquals($expected, $actual, '', 0.01);
  }

  public function provide_temperature_data() {
    return [
      // [Fahrenheit, Celsius]
      [-40, -40.0],
      [ 0, -17.8],
      [ 32, 0.0],
      [100, 37.8],
      [212, 100.0],
    ];
  }
}
```

First, the provide_temperature_data() method was added. This is the method to provide data for testing. It returns an array of arrays.

Second, the @dataProvider tag was added to the docblock of the test_FtoC() method. This sets a data provider method for the test method.

```
/**
 * @dataProvider provide_temperature_data
 */
```