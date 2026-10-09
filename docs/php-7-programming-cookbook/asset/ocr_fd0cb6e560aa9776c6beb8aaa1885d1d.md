# Hinting at data types

In many cases when developing functions, you might reuse the same library of functions in other projects. Also, if you work with a team, your code might be used by other developers. In order to control the use of your code, it might be appropriate to make use of a **type hint**. This involves specifying the data type your function expects for that particular parameter.

# How to do it...

+   1. Parameters in functions can be prefixed by a type hint. The following type hints are available in both PHP 5 and PHP 7:

* Array
* Class
* Callable

+   2. If a call to the function is made, and the wrong parameter type is passed, a TypeError is thrown. The following example requires an array, an instance of DateTime, and an anonymous function:

```
function someTypeHint(Array $a, DateTime $t, Callable $c)
{
    $message = '';
    $message .= 'Array Count: ' . count($a) . PHP_EOL;
    $message .= 'Date: ' . $t->format('Y-m-d') . PHP_EOL;
    $message .= 'Callable Return: ' . $c() . PHP_EOL;
    return $message;
}
```

> You don't have to provide a type hint for every single parameter. Use this technique only where supplying a different data type would have a negative effect on the processing of your function. As an example, if your function uses a `foreach()` loop, if you do not supply an array, or something which implements Traversable, an error will be generated.

+   3. In PHP 7, presuming the appropriate declare() directive is made, **scalar** (that is, integer, float, boolean, and string) type hints are allowed. Another function demonstrates how this is accomplished. At the top of the code library file which contains the function in which you wish to use scalar type hinting, add this declare() directive just after the opening PHP tag:

```
declare(strict_types=1);
```