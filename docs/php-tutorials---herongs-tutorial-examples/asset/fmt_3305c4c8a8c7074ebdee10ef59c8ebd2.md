
# Function Declaration, Arguments, and Return Values

## Function Call Operations

This section describes the function call operation, which triggers the execution of the called function with arguments provided on the call.

Calling a function in PHP is simple. All you have to do is to just use the function name with an argument list in any expression:

```
... function_name(argument_1, argument_2, ...) ...
```

When the execution reaches this function call operation, it will:

* Evaluate all calling arguments to values or variable references.
* Assign argument values and references to argument variables defined in the `function` statement.
* Start to execute the first statement of the function body.
* Continue to execute the function body until the end of the function body or a `return` statement.
* If a `return` statement is reached with a value specified, that value is returned as this function call operation.
* If a `return` statement is reached with no value specified, `NULL` is returned as this function call operation.
* If no `return` statement is reached, `NULL` is returned as this function call operation.

Here is a simple example script showing us how to use function call operations:

```php
<?php
#  FunctionCallOperations.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

#  Defining a function that returns a value
   function f2c($fahrenheit) {
      $celsius = ($fahrenheit - 32.0 ) / 1.8;
      return $celsius;
   }

#  Defining a function that returns NULL
   function showAnyFooter($author) {
      print("    Copyright: $author\n");
      print("    Last Modified: 2015\n");
   }

   print("\n Function call as a standalone expression:\n");
   showAnyFooter("Herong Yang");

   print("\n Function call as an operand of another operation:\n");
   if (f2c(20.0)<0.0) print("    It's cold here!\n");

   print("\n Function call as an argument of another call:\n");
   print("    How is the temperature? ");
   print(f2c(110.0));
?>
```

If you run this sample script, you should get:

```
herong> \php\php FunctionCallOperations.php

 Function call as a standalone expression:
    Copyright: Herong Yang
    Last Modified: 2019

 Function call as an operand of another operation:
    It's cold here!

 Function call as an argument of another call:
    How is the temperature? 43.3333333333
```

## Passing Arguments to Functions

This section describes rules on how arguments can be passed from the calling code into the called function by value (the default) or by reference.

As shown in examples in previous sections, passing arguments to a function seems to be a simple job. But it may cause confusion if you don't follow the rules. PHP has the following rules on passing arguments to function and subroutine procedures:

1. By default, a function argument is passed by value. In this case, the argument variable contains a copy of the data provided by the calling code.
2. But, a function argument can be passed by reference, if you define the argument variable as `&$variable_name`. In this case, the argument variable contains a reference of the original variable in the calling code. In another word, the argument variable is an alias of the original variable.
3. A pass-by-value argument variable is safer to use, because it will be assigned with a copy of the data from the calling code at the time of call. If the argument variable is re-assigned with a new data in the function, there will be no impact to the calling code.
4. A pass-by-reference argument variable offers an advantage and a risk. The advantage is that it can be used as an output channel for the function to send data back to the calling code. The risk is that if the argument variable is re-assigned with a new data in the function by a mistake, there will be some negative impact on the calling code.
5. An argument variable can be defined with a default value. Arguments with default values must be positioned at the end of the argument list.
6. If you want to use the default value of an argument variable, you can skip that argument in the function call operation.
7. Arguments passed in the function call can be retrieved without using argument variables. You can use `func_num_args()`, `func_get_arg()`, and `func_get_args()` functions to access arguments. This feature can be used to support variable-length argument lists.
8. If an array is passed by value, a copy of the original array will be passed to the function. If an array is passed by reference, the function and the calling code is sharing the same array.
9. If a reference of a variable is passed by value, a copy of the reference will be passed to the function. But the copy and the reference are both referring to the same original variable. So passing a reference by value is equivalent to passing a variable by reference.

## Example of Passing Arguments by Values

This section provides a tutorial example on how to use pass-by-value arguments, which allows the function to re-assign new values to original variables in the calling code.

As we learned from the previous section, PHP functions use pass-by-value arguments by default. If an argument is defined as a pass-by-value argument, the calling operation can provide an expression for this argument. That expression will be assigned to this argument variable when the function is called. For example, if we have `function f($var) {...}` defined, `f(exp)` is equivalent to `{$var=exp; ...}`.

To see how passing arguments by values works, I wrote this tutorial example, `PassByValue.php`:
