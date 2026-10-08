
## Chapter 1. PHP Crash Course

![](img/654520c37415debd4290b9b4aa2c03f2_53_0.png)

Figure 1.4 The variables the user typed in are easily accessible in processor.php

The following sections describe a couple of interesting elements of this example.

## String Concatenation

In the sample script, echo prints the value the user typed in each form field, followed by some explanatory text. If you look closely at the echo statements, you can see that the variable name and text have a pattern (.) between them, such as:

```php
echo htmlspecialchars($tirety) . $tires<br/>;
```

This period is the string concatenation operator, which adds strings (pieces of text) together. You will often use it when sending output to the browser with echo. This can avoid writing multiple echo commands.

You can also place simple variables inside a double-quoted string to be echoed. (Arrays are somewhat complicated, so we look at combining arrays and strings in Chapter 4.) Consider this example:

```php
$tirety = htmlspecialchars($tirety);
echo "$tirety$tires<br/>";
```

This is equivalent to the first statement shown in this script. Either format is valid, and which one you use is a matter of personal taste. This process, replacing a variable with its contents within a string, is known as interpolation.

Note that interpolation is a feature of double-quoted strings only. You cannot place variable names inside a single-quoted string like this. Running the following line of code

```php
echo '$tirety$tires<br/>;
```

simply sends $tirety$tires<br/> to the browser. Within double quotation marks, the variable name is replaced with its value. Within single quotation marks, the variable name or any other text is unaltered.

## Variables and Literals

The variables and strings concatenated together in each of the echo statements in the sample script are different types of things. Variables are symbols for data. The strings are data elements. When we use a piece of raw data in a program like this, we call it a literal to distinguish it from a variable. $tireqty is a symbol that represents what the customer typed in. On the other hand, "<br/>" is a literal. You can take it at face value. Almost, remember the second example in the preceding section. PHP replaced the variable $tireqty in the string with the value stored in the variable.

Remember the two kinds of strings mentioned already: with double quotation marks and with single quotation marks. PHP tries to evaluate strings in double quotation marks, resulting in the behavior shown earlier. Single-quoted strings are treated as true literals.

There is also a third way of specifying strings using the heredoc syntax (<<), which will be familiar to Perl. Heredoc syntax allows you to specify long strings tidily, by specifying an end marker that will be used to terminate the heredoc. The following example creates a three-line string and echoes it:

```php
echo <<theEnd
line 1
line 2
line 3
theEnd
```

The token end is entirely arbitrary. It just needs to be guaranteed not to appear in the text. To close a heredoc string, place a closing token at the start of a line.

Heredoc strings are interpolated, like double-quoted strings.

## Understanding Identifiers

Identifiers are the names of variables. They are also identifiers; we look at functions and classes in Chapter 5, "Reusing Code and Writing Functions," and Chapter 6, "Object-Oriented PHP." You need to be aware of the simple rules defining valid identifiers:

- Identifiers can be of any length and consist of letters, numbers, and underscores.
- Identifiers cannot begin with a digit.
- In PHP, identifiers are case sensitive. $tireqty is not the same as $TireQty. Trying to use them interchangeably is a common programming error. Functions are an exception to this rule: Their names can be used in any case.
- A variable can have the same name as a function. This usage is confusing, however, and should be avoided. Also, you cannot create a function with the same name as another function.

You can declare and use your own variables in addition to the variables you are passed from the HTML form.

One of the features of PHP is that it does not require you to declare variables before using them. A variable is created when you assign a value to it. See the next section for details.

You assign values to variables using the assignment operator.

## Type Strength

PHP is called a weakly typed or dynamically typed language. In most programming languages, variables can hold only one type of data, and that type must be declared before the variable can be used, as in C. The type of a variable is determined by the value assigned to it.

For example, when you created $tireqty and $totalamount, their initial types were:

```php
$tireqty = 0;
$totalamount = 0;
```

Because you assigned 0, an integer, to $tireqty, this is now an integer. Similarly, $totalamount is now a float.

Strangely enough, you could now add a line to your script:

```php
$totalamount = 'Hello';
```

The variable $totalamount would then be a string. PHP changes the variable type according to what is stored in it any given time.

This ability to change types transparently on the fly can be extremely useful. Remember PHP "automatically" knows what data type you put into your variable. It returns the data with the same data type that you retrieve from the variable.

## Type Casting

You can pretend that a variable or value is of a different type by using a type cast. This feature works identically to the way it works in C. You simply put the temporary type in parentheses before the variable you want to cast.

For example, you could have declared the two variables from the preceding section using a cast:

```php
$tireqty = 0;
$totalamount = (float)$tireqty;
```

The second line means "Take the value stored in $tireqty, interpret it as a float, and store it in $totalamount." The $totalamount variable will be a float. The variable does not change types, so $tireqty remains an integer type.

## Variable Variables

PHP provides one other type of variable: the variable. Variable variables enable you to change the name of a variable dynamically.

As you can, PHP allows a lot of freedom in this area. All languages enable you to change the value of a variable, but not many allow you to change the variable's type, and even fewer allow you to change the variable's name.
