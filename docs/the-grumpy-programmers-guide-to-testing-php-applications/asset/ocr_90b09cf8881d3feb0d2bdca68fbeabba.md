# Building Further Test Cases

The implementation I did for the test case that proves 2 and 3 are converted correctly has me feeling like I should just continue to extend my code to handle other situations in a similar way. I'll add a test case which verifies 4, 5, and 9 are handled correctly. These represent behavior that is outside the norm.

First, the failing test.

```
```php
/**
 * @dataProvider exceptionDataSets
 * @test
 */
public function convertsSingleDigitExceptions($input, $expected)
{
    $this->assertTrue(false);
}
```
```

It fails as I expect it to.

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53
```

There are three failures because I'm using three data sets.

Then, I modify the code to handle this new behavior correctly.

```
```php
1. public function arabicToRoman($value) : string
2. {
3.     $currentValue = $value;
4.     $result = '';
5. 
6.     while ($currentValue > 0) {
7.         switch ($currentValue) {
8.             case $currentValue % 9 === 0:
9.                 $result .= 'IX';
10.                $currentValue -= 9;
11.                break;
```
```