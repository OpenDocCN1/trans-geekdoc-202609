
# Union Types

It is generally preferable to restrict parameters to accept only one specific data type, but sometimes you may want a parameter to allow calls to pass values of different data types. This is possible by specifying the acceptable data types in the function definition as a “union type”. This is pipe-separated list of PHP data types before the parameter name with this syntax:

`function function_name ( type|type|type $arg )`

Similarly, multiple acceptable data types of the value returned from a function can be specified as a union type with a pipe-separated list in a function definition:

`function function_name ( type|type $arg ) : type|type`

Union types support all the PHP data types except for `void`, but does support the special `null` type. This means that a function can return a value of a specific data type or `null`. This is a fairly common requirement known as a “nullable union”. It can be specified as a pipe-separated list or with a shorthand notation:

`type|null` or `?type`

![image](images/hot.jpg)

Union types is a great new feature introduced in PHP 8.

The shorthand version can only be used with a single data type, not with a union type, and the `null` type can only be used as part of a union type.

PHP also has a `mixed` pseudo type that allows a parameter or return value to be of any type except for `void`. It is equivalent to a union type that looks like this:

`string|int|float|bool|null|array|object|callable|resource`

The `mixed` pseudo type cannot be used in union with other types because it already represents all acceptable types. When no data type is explicitly specified for a parameter, PHP assumes the type to be `mixed`. When no data type is explicitly specified for a function’s return value, PHP assumes the type to be `mixed` or `void`.

![image](images/hot.jpg)

The `callable` type is simply a type hint. It may be specified for a parameter that accepts a callable function.

## Example

![image](images/1o.jpg)Begin a PHP script by defining a function that can accept an integer or floating-point number as its argument, and can return either an integer or floating-point number

```php
<?php
function half( int|float $arg ) : int|float
{
    // Statements to be inserted here.
}
```

![image](images/commono.jpg)

`union.php`

![image](images/2o.jpg)Next, insert statements to call another function to describe the argument, and return half of its value

```php
echo desc ( '<dt>Argument' , $arg ) ;
return $arg/2 ;
```

![image](images/3o.jpg)Now, add the other function that will return a string describing the numerical argument value it receives

```php
function desc( string $str, mixed $val ) : string
{
    return $str.' '.$val.' - '.gettype( $val ) ;
}
```

![image](images/4o.jpg)Finally, add statements to call the functions, passing integer and floating-point values

```php
echo desc( '<dd>Return', half( 100 ) ).'<hr>' ;
echo desc( '<dd>Return', half( 33 ) ).'<hr>' ;
echo desc( '<dd>Return', half( 3.142 ) ) ;
?>
```

![image](images/5o.jpg)Save the document in your web server’s `/htdocs` directory as `union.php` then open the page via HTTP to see the integer and floating-point argument and return values

![image](images/pg87_1.jpg)

![image](images/hot.jpg)

Union types can be used in all places where types can be specified – for parameters, return types, and for class properties in Object Oriented Programming (see [Chapter 7](#chapter07.xhtml)).

# Calling back

![image](images/pg88_1.jpg)

PHP allows you to create “anonymous” functions that have no name specified in the function definition. Like other functions, these can accept arguments if parameters are specified and they can optionally return a value when called. Unlike other function definitions, which are code constructs, an anonymous function definition is an expression. This means that each anonymous function definition must be terminated by a semicolon, like this:

```php
function ( )
{
    statement-to-be-executed ;
    statement-to-be-executed ;
    return value ;
} ;
```

![image](images/snake.jpg)

Don’t forget to add a terminating `;` semicolon after each anonymous function definition.

On its own an anonymous function is of little use as, without a name, it cannot be called, but it can be useful in other ways:

•Assigned to a variable, an anonymous function can be called using the variable name.
•Passed as a callable argument to another function, an anonymous function can be called later as a “callback”.
•Returned from a function, an anonymous function retains access to the returning function’s variables in “closure”.

By assigning an anonymous function to a variable you do, in effect, give the function a name and can call it and pass it arguments as you would any other function – using the variable name. Similarly, when you pass an anonymous function to another function it can be called back and passed arguments as you would any other function – using the parameter name. The PHP `use` keyword and `&` ampersand prefix allow an anonymous function to reference a local variable in the returning function.

## Example

![image](images/1o.jpg)Begin a PHP script by assigning to a variable an anonymous function that accepts a single argument

```php
<?php
$hello \= function ( $user ) { echo “Hello $user!<br>” ; } ;
```

![image](images/commono.jpg)

`callback.php`

![image](images/2o.jpg)Next, add a statement that calls the anonymous function and passes a single argument

```php
$hello( ‘Mike’ ) ;
```

![image](images/3o.jpg)Now, define a regular function that accepts a single callable argument and calls that function passing a string

```php
function greet( callable $anon )
{
    $anon( ‘Carole Anne’ ) ;
}
```

![image](images/4o.jpg)Add a statement to call the function, defined in the previous step, passing the anonymous function that was assigned to a variable in the first step

```php
greet( $hello ) ;
```

![image](images/5o.jpg)Next, define another regular function that has one local variable and returns an anonymous function that references the local variable value

```php
function meet() : callable
{
    $time \= ‘morning’ ;
    return function( $name ) use( &$time )
    { return “Good $time, $name!” ; } ;
}
```

![image](images/6o.jpg)Assign to a variable the function defined in the previous step then call that function, passing a string argument

```php
$meeting \= meet() ;
echo $meeting( ‘Susan’ ) ;
?>
```

![image](images/7o.jpg)Save the document in your web server’s `/htdocs` directory as `callback.php` then open the page via HTTP to see the returned values from anonymous functions

![image](images/pg75_1.jpg)

![image](images/forget.jpg)

Remember to include the `&` ampersand prefix to create a reference to the variable value.

![image](images/hot.jpg)

Notice that the final function call gets the `'morning'` string from the parent scope.

# Summary

•Custom functions allow PHP scripts to be modularized into sections of code that are easier to understand and maintain.
•Function names must begin with a letter or underscore character and are not case-sensitive.
•A function is defined by stating its name after the `function` keyword, then parentheses and braces containing statements.
•A function accepting arguments is defined by including a comma-separated list of parameters within the parentheses.
•Optionally, a function definition can specify the type of data to be passed from the caller before the parameter name.
•Argument data is normally passed by value but can be passed by reference if the parameter name is given an `&` prefix.
•Default argument values can optionally be specified in a function definition by assignment to the parameter name.
•The `...` splat operator allows multiple arguments to be passed to a parameter in order to create an array.
•Named parameters allow a caller to pass argument values to the function in any order.
