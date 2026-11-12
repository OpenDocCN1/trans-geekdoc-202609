we call the function addition(5,10);, we pass two integers, which is consistent with the declared types. Consequently, the function additions these two integers and returns an integer result stored in variable $result1, which is then displayed.

However, in the following call addition(5, "10");, we pass an integer and a string, which does not correspond to the declared type **int**. As **strict** typing is enabled, this generates a fatal error, as the data type supplied does not match the type expected by the function. As a result, the script stops and displays an error rather than automatically converting the string to an integer, as would be the case in the absence of strict typing.

Finally, note that from PHP 8 onwards, you can specify multiple types for the same parameter using the new type union operator |(vertical bar). This allows you to define that a parameter can accept several different data types. For example, if a parameter can be either an integer or a string, you can declare it as follows:

```
<?php

function example(int|string $parameter1, float|int $parameter2) {
    // Body of function
}

?>
```

In this example, $parameter1 can be either an integer or a string. As for $parameter2, it can be either a decimal number or an integer. This offers greater flexibility when defining parameter types for functions.

# Scope of variables