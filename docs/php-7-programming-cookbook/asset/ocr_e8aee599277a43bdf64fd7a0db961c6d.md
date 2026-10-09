# See also

PHP 7.1 introduced a new type hint `iterable` which allows arrays, `Iterators` or `Generators` as arguments. See this for more information:

+   - https://wiki.php.net/rfc/iterable

For a background discussion on the rationale behind the implementation of scalar type hinting, have a look at this article:

+   - https://wiki.php.net/rfc/scalar_type_hints_v5

# Using return value data typing

PHP 7 allows you to specify a data type for the return value of a function. Unlike scalar type hinting, however, you don’t need to add any special declarations.

# How to do it...

+   1.  This example shows you how to assign a data type to a function return value. To assign a return data type, first define the function as you would normally. After the closing parenthesis, add a space, followed by the data type and a colon:

```
```
function returnsString(DateTime $date, $format) : string
{
    return $date->format($format);
}
```
```

![](bbox=[0.19, 0.57, 0.27, 0.62])

> PHP 7.1 introduced a variation on return data typing called **nullable types**. All you need to do is to change `string` to `?string`. This allows the function to return either `string` or NULL.

+   2.  Anything returned by the function, regardless of its data type inside the function, will be converted to the declared data type as a return value. Notice, in this example, the values of `$a`, `$b`, and `$c` are added together to produce a single sum, which is returned. Normally you would expect the return value to be a numeric data type. In this case, however, the return data type is declared as `string`, which overrides PHP’s type-juggling process:

```
```
function convertsToString($a, $b, $c) : string

    return $a + $b + $c;
}
```
```