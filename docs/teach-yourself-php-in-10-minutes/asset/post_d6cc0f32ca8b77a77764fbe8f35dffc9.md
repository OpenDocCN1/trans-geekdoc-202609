
to check that the value is between 12 and 17 because the initial `if` condition ensures that PHP will not get as far as the `elseif` if `$hour` is less than 12.

The code in the `else` clause is executed if all else fails. For values of `$hour` that are 17 or higher, neither the `if` nor the `elseif` condition will be true.

**elseif Versus else if** In PHP you can also write `elseif` as two words: `else if`. The way PHP interprets this variation is slightly different, but its behavior is exactly the same.

## The `switch` Statement

An `if` statement can contain as many `elseif` clauses as you need, but including many of these clauses can often create cumbersome code, and an alternative is available. `switch` is a conditional statement that can have multiple branches in a much more compact format.

The following example uses a `switch` statement to check `$name` against two lists to see whether it belongs to a friend:

```
switch ($name) {
case "Damon":
case "Shelley":
    echo "Welcome, $name, you are my friend";
    break;
case "Adolf":
case "Saddam":
    echo "You are no friend of mine, $name";
    break;
default:
    echo "I do not know who you are, $name";
}
```

Each `case` statement defines a value for which the next block of PHP code will be executed. If you assign your first name to `$name` and run this script, you will be greeted as a friend if your name is Damon or Shelley, and you will be told that you are not a friend if your name is either Adolf or Saddam. If you have any other name, the script will tell you it does not know who you are.

There can be any number of `case` statements preceding the PHP code to which they relate. If the value that is being tested by the `switch` statement (in this case `$name` ) matches any one of them, any subsequent PHP code will be executed until a `break` command is reached.

Breaking Out The `break` statement is important in a `switch` statement. When a `case` statement has been matched, any PHP code that follows will be executed even if there is another `case` statement checking for a different value. This behavior can sometimes be useful, but mostly it is not what you want so remember to put a `break` after every `case`.

Any other value for `$name` will cause the `default` code block to be executed. As with an `else`

## Loops

PHP offers three types of loop constructs that all do the same thing repeat a section of code a number of times in slightly different ways.

### The while Loop

The while keyword takes a condition in parentheses, and the code block that follows is repeated while that condition is true. If the condition is false initially, the code block will not be repeated at all.

> **Infinite Loops** The repeating code must perform some action that affects the condition in such a way that the loop condition will eventually no longer be met; otherwise, the loop will repeat forever.

The following example uses a while loop to display the square numbers from 1 to 10:

```
$count = 1;
while ($count <= 10) {
    $square = $count * $count;
    echo "$count squared is $square <br>";
    $count++;
}
```

The counter variable $count is initialized with a value of 1. The while loop calculates the square of that number and displays it, then adds one to the value of $count. The ++ operator adds one to the value of the variable that precedes it.

The loop repeats while the condition $count <= 10 is true, so the first 10 numbers and their squares are displayed in turn, and then the loop ends.

### The do Loop

The do loop is very similar to the while loop except that the condition comes after the block of repeating code. Because of this variation, the loop code is always executed at least once even if the condition is initially false.

The following do loop is equivalent to the previous example, displaying the numbers from 1 to 10, with their squares:

```
$count = 1;
do {
  $square = $count * $count;
  echo "$count squared is $square <br>";
  $count++;
} while ($count <= 10);
```

### The **for** Loop

The for loop provides a compact way to create a loop. The following example performs the same loop as the previous two examples:

```
for ($count = 1; $count <= 10; $count++) {
  $square = $count * $count;
  echo "$count squared is $square <br>";
}
```

As you can see, using **for** allows you to use much less code to do the same thing as with **while** and **do**.

A **for** statement has three parts, separated by semicolons:

- The first part is an expression that is evaluated once when the loop begins. In the preceding example, you initialized the value of $count.
- The second part is the condition. While the condition is true, the loop continues repeating. As with a **while** loop, if the condition is false to start with, the following code block is not executed at all.
- The third part is an expression that is evaluated once at the end of each pass of the loop. In the previous example, $count is incremented after each line of the output is displayed.

### Nesting Conditions and Loops

So far you have only seen simple examples of conditions and loops. However, you can nest these constructs within each other to create some quite complex rules to control the flow of a script.

> **Remember to Indent** The more complex the flow control in your script is, the more important it becomes to indent your code to make it clear which blocks of code correspond to which constructs.

## Breaking Out of a Loop

You have already learned about using the keyword `break` in a `switch` statement. You can also use `break` in a loop construct to tell PHP to immediately exit the loop and continue with the rest of the script.

The `continue` keyword is used to end the current pass of a loop. However, unlike with `break`, the script jumps back to the top of the same loop and continues execution until the loop condition fails.

## Summary

In this lesson you have learned how to vary the flow of your PHP script by using conditional statements and loops. In the next lesson you will see how to create reusable functions from blocks of PHP code.

## Lesson 4. Functions

*In this lesson you will learn how frequently used sections of code can be turned into reusable functions.*

## Using Functions

A function is used to make a task that might consist of many lines of code into a routine that can be called using a single instruction.

PHP contains many functions that perform a wide range of useful tasks. Some are built in to the PHP language; others are more specialized and are available only if certain extensions are activated when PHP is installed.

The online PHP manual (www.php.net) is an invaluable reference. As well as documentation for every function in the language, the manual pages are also annotated with user-submitted tips and examples, and you can even submit your own comments if you want.

**Online Reference** To quickly pull up the PHP manual page for any function, use this shortcut: www.php.net/function_name.

You have already used the date function to generate a string that contains a formatted version of the current date. Let’s take a closer look at how that example from Lesson 1, "Getting to Know PHP," works. The example looked like this:

```
echo date('j F Y');
```

The online PHP manual gives the prototype for date as follows:

```
string date (string format [, int timestamp])
```

This means that date takes a string argument called format and, optionally, the integer timestamp. It returns a string value. This example sends j F Y to the function as the format argument, but timestamp is omitted. The echo command displays the string that is returned.

**Prototypes** Every function has a prototype that defines how many arguments it takes, the arguments' data types, and what value is returned. Optional arguments are shown in square brackets ([ ]).

## Defining Functions

In addition to the built-in functions, PHP allows you to define your own. There are advantages to using your own function. Not only do you have to type less when the same piece of code has to be executed several times but a custom-defined function also makes your script easier to maintain. If you want to change the way a task is performed, you only need to update the program code once in the function definition rather than fix it every place it appears in your script.

> **Modular Code** Grouping tasks into functions is the first step toward *modularizing* your code—something that is especially important to keep your scripts manageable as they grow in size and become more complex.

The following is a simple example that shows how a function is defined and used in PHP:

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

The `function` keyword defines a function called `add_tax` that will execute the code block that follows. The code that makes up a function is always contained in braces. Putting `$amount` in parentheses after the function name stipulates that `add_tax` takes a single argument that will be stored in a variable called `$amount` inside the function.

The first line of the function code is a simple calculation that multiplies `$amount` by 1.09 which is equivalent to adding 9% to that value and assigns the result to `$total`. The `return` keyword is followed by the value that is to be returned when the function is called from within the script.

Running this example produces the following output:

```
Price before tax: 16
Price after tax: 17.44
```

This is an example of a function that you might use in many places in a web page; for instance, on a page that lists all the products available in an online store, you would call this function once
