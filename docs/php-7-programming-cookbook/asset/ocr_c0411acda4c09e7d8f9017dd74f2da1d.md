Best Practices, Testing, and Debugging

# # Running simple tests

Next, define a chap_13_unit_test_simple.php program file with a series of simple functions, such as add(), sub() and so on, as discussed in step 1. You can then define a simple test class contained in SimpleTest.php as mentioned in steps 2 and 3.

Assuming phpunit is in your PATH, from a terminal window, change to the directory containing the code developed for this recipe, and run the following command:

```
phpunit SimpleTest SimpleTest.php
```

You should see the following output:

![](bbox=[0.23, 0.37, 0.76, 0.46])

Make a change in SimpleTest.php so that the test will fail (step 4):

```
```php
public function testDiv()
{
    $this->assertEquals(2, div(4, 2));
    $this->assertEquals(99, div(4, 0));
}
```
```

Here is the revised output:

![](bbox=[0.23, 0.64, 0.76, 0.81])