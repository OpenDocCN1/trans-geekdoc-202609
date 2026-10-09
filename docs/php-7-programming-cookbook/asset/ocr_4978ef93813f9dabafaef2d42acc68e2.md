+   Now you can define a function that includes scalar type hints:

```
function someScalarHint (bool $b, int $i, float $f, string $s) {
    return sprintf ("\n%20s : %5s\n%20s : %5d\n%20s " .
                    ": %5.2f\n%20s : %20s\n\n",
                    'Boolean', ($b ? 'TRUE' : 'FALSE') ,
                    'Integer' , $i,
                    'Float' , $f,
                    'String', $s);
}
```

+   In PHP 7, assuming strict type hinting has been declared, boolean type hinting works a bit differently from the other three scalar types (that is, integer, float, and string). You can supply any scalar as an argument and no TypeError will be thrown! However, the incoming value will automatically be converted to the boolean data type once passed into the function. If you pass any data type other than scalar (that is, array or object) a TypeError will be thrown. Here is an example of a function that defines a boolean data type. Note that the return value will be automatically converted to a boolean:

```
function someBoolHint (bool $b)
{
    return $b;
}
```

# How it works...

First of all, you can place the three functions, someTypeHint(), someScalarHint(), and someBoolHint(), into a separate file to be included. For this example, we will name the file chap_03_developing_functions_type_hints_library.php. Don't forget to add declare(strict_types=1) at the top!

In our calling code, you would then include the file:

```
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_
functions_type_hints_library.php');
```

To test someTypeHint(), call the function twice, once with the correct data types, and the second time with incorrect types. This will throw a TypeError, however, so you will need to wrap the function calls in a try { ... } catch ( ) { ... } block:

```
try {
    $callable = function () { return 'Callback Return'; };
    echo someTypeHint ([1,2,3], new DateTime(), $callable);
    echo someTypeHint ('A', 'B', 'C');
```