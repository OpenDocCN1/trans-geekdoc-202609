# 10. DATA PROVIDERS

One of the earliest lessons I learned when I started writing comprehensive test suites was to always look for duplication in your tests. Here’s an example of a situation where this can happen.

You might be familiar with the FizzBuzz problem[1] problem, if only because it is sometimes presented as a problem to be solved as part of an interview. It is a good problem because it touches on a lot of really elementary basics of programming—you need to understand loops, collections, and conditional statements.

When you write tests for FizzBuzz, what you want to do is pass it a set of values and verify they are FizzBuzzed correctly. This could result in you having multiple tests that are the same, except for the values you are testing with. Data providers give you a way to simplify that process.

A data provider is a way to create multiple sets of testing data which can be passed in as parameters to your test method. You create a method that is available to the class your tests are in that returns an array of values matching the parameters you are passing into your test.

It sounds more complicated than it really is; let’s look at an example.

# Look at All Those Tests

If you didn’t know about data providers, what might your FizzBuzz tests look like?

```
```php
<?php
class FizzBuzzTest extends PHPUnit\Framework\TestCase
{
    public function setup()
    {
        $this->fb = new FizzBuzz();
    }

    public function testGetFizz()
    {
        $expected = 'Fizz';
        $input = 3;
        $response = $this->fb->check($input);
        $this->assertEquals($expected, $response);
    }
}
```
```

[1] FizzBuzz problem: <http://en.wikipedia.org/wiki/FizzBuzz>