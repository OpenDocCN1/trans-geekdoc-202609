# Defining Functions

In addition to the built-in functions, PHP allows you to define your own. There are advantages to using your own function. Not only do you have to type less when the same piece of code has to be executed several times but a custom-defined function also makes your script easier to maintain. If you want to change the way a task is performed, you only need to update the program code once in the function definition rather than fix it every place it appears in your script.

> **Modular Code** Grouping tasks into functions is the first step toward *modularizing* your codesomething that is especially important to keep your scripts manageable as they grow in size and become more complex.

The following is a simple example that shows how a function is defined and used in PHP:

```
```php
function add_tax($amount) {
   $total = $amount * 1.09;
   return $total;
}

$price = 16.00;
echo "Price before tax: $price <br>";
echo "Price after tax: ";
echo add_tax($price);
```
```

The `function` keyword defines a function called `add_tax` that will execute the code block that follows. The code that makes up a function is always contained in braces. Putting `$amount` in parentheses after the function name stipulates that `add_tax` takes a single argument that will be stored in a variable called `$amount` inside the function.

The first line of the function code is a simple calculation that multiplies `$amount` by 1.09which is equivalent to adding 9% to that valueand assigns the result to `$total` . The `return` keyword is followed by the value that is to be returned when the function is called from within the script.

Running this example produces the following output:

```
Price before tax: 16
Price after tax: 17.44
```

This is an example of a function that you might use in many places in a web page; for instance, on a page that lists all the products available in an online store, you would call this function once