# PHP7 336

This represents a significant challenge. If we type hint for a parameter that supports the ArrayAccess interface, PHP will complain when we fail to give it one. If we type hint for a scalar value, PHP7 will only complain if it can't perform the type cast internally.

Given that we're perfectly capable of explicitly casting from one scalar to another if we truly needed to, i.e. $int = (int) "31.25"; I think it's preferable to have PHP complain when we have a method expecting one type but getting a different type passed in.

Can this be achieved? The answer is yes, but the solution is rather a clunky one in my opinion.

We can tell PHP7 to turn on strict checking by adding a statement to the top of every file that needs it. The format of that statement is this.

```
<?php
declare(strict_types=1);
```

It should be noted at this stage that declare() statement must be the first directive in each file that requires strict type checking. When declaration is in place at the top of the file, then our scalar type hinting will work as we expect it to. That to say, PHP will raise an error if we tried to pass a float as a parameter that was hinted as an integer. Equally, we'll also get an error when we try to pass a numeric string when the hint requires a float or an integer.

> Just to confuse matters, when strict checking is turned on, you can still present an integer to a method expecting a float. This is a "feature" since integers can be readily cast to floats without any loss or corruption. Integer 42 simply becomes float 42.0.

This is what is needed. Rather than type casting happening silently in the background, if we we have a string and it needs to be either of the numeric types, we will be required to explicitly perform the cast in our code instead. This significantly improves the visibility of any errors that we make when performing the type casts manually and as such, will give us an easier time of it identifying and fixing the bugs as a result.