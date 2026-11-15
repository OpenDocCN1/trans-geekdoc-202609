
Constants are useful for any situation where you want to make sure a value does not change throughout the running of your script. Common uses for constants include configuration files and storing text to display to the user.

## Try It Out Calculate the Properties of a Circle

Save this simple script as circle_properties.php in your Web server’s document root folder, then open its URL (for example, http://localhost/circle_properties.php) in your Web browser to run it:

```php
<?php
$radius = 4;

$diameter = $radius * 2;
$circumference = M_PI * $diameter;
$area = M_PI * pow( $radius, 2 );

echo "This circle has...<br />";
echo "A radius of " . $radius . "<br />";
echo "A diameter of " . $diameter . "<br />";
echo "A circumference of " . $circumference . "<br />";
echo "An area of " . $area . "<br />";
?>
```

When you run the script, you should see something like Figure 3-1.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_86_0.png)

Figure 3-1

### How It Works

First, the script stores the radius of the circle to test in a $radius variable. Then it calculates the diameter — twice the radius — and stores it in a $diameter variable. Next it works out the circle’s circumference, which is π (pi) times the diameter, and stores the result in a $circumference variable. It uses the built-in PHP constant, M_PI, which stores the value of π. Then the script calculates the circle’s area, which is π times the radius squared, and stores it in an `$area` variable. To get the value of the radius squared, the script uses the built-in `pow()` function, which takes a base number, `base`, followed by an exponent, `exp`, and returns `base` to the power of `exp`.

Finally, the script outputs the results of its calculations, using the string concatenation operator (`.`) to join strings together.

## Summary

This chapter took you through some fundamental building blocks of the PHP language. You learned the following concepts:

- Variables: What they are, how you create them, and how to name them
- The concept of data types, including the types available in PHP
- Loose typing in PHP; a feature that gives you a lot of flexibility with variables and values
- How to test the type of a variable with `gettype()`, and how to change types with `settype()` and casting
- The concepts of operators, operands, and expressions
- The most common operators used in PHP
- Operator precedence — all operators are not created equal
- How to create constants that contain non-changing values

Armed with this knowledge, you’re ready to move on and explore the next important concepts of PHP: decisions, loops, and control flow. You learn about these in the next chapter. Before you read it, though, try the two exercises that follow to ensure that you understand variables and operators. You can find the solutions to these exercises in Appendix A.

## Exercises

- 1. Write a script that creates a variable and assigns an integer value to it, then adds 1 to the variable’s value three times, using a different operator each time. Display the final result to the user.

- 2. Write a script that creates two variables and assigns a different integer value to each variable. Now make your script test whether the first value is
  - a. equal to the second value
  - b. greater than the second value
  - c. less than or equal to the second value
  - d. not equal to the second value
  and output the result of each test to the user.

## Decisions and Loops

So far, you've learned that PHP lets you create dynamic Web pages, and you've explored some fundamental language concepts such as variables, data types, operators, expressions, and constants.

However, all the scripts you've written have worked in a linear fashion: the PHP engine starts at the first line of the script, and works its way down until it reaches the end. Things get a lot more interesting when you start introducing decisions and loops.

A *decision* lets you run either one section of code or another, based on the results of a specific test. Meanwhile, a *loop* lets you run the same section of code over and over again until a specific condition is met.

By using decisions and loops, you add a lot of power to your scripts, and you can make them truly dynamic. Now you can display different page content to your visitors based on where they live, or what buttons they've clicked on your form, or whether or not they're logged in to your site.

In this chapter you explore the various ways that you can write decision-making and looping code in PHP. You learn about:

- Making decisions with the `if`, `else`, and `switch` statements
- Writing compact decision code with the ternary operator
- Looping with the `do`, `while`, and `for` statements
- Altering loops with the `break` and `continue` statements
- Nesting loops inside each other
- Using decisions and looping to display HTML

Once you've learned the concepts in this chapter, you'll be well on your way to building useful, adaptable PHP scripts.

## Making Decisions

Like most programming languages, PHP lets you write code that can make decisions based on the result of an expression. This allows you to do things like test if a variable matches a particular value, or if a string of text is of a certain length. In essence, if you can create a test in the form of an expression that evaluates to either `true` or `false`, you can use that test to make decisions in your code.

You studied expressions in Chapter 3, but you might like to quickly review the “Operators and Expressions” section in that chapter to give yourself an idea of the kinds of expressions you can create. You can see that, thanks to the wide range of operators available in PHP, you can construct some pretty complex expressions. This means that you can use almost any test as the basis for decision-making in your code.

PHP gives you a number of statements that you can use to make decisions:

- The `if` statement
- The `else` and `elseif` statements
- The `switch` statement

You explore each of these statements in the coming sections.

### Simple Decisions with the if Statement

The easiest decision-making statement to understand is the `if` statement. The basic form of an `if` construct is as follows:

```
if ( expression ) {
// Run this code
}
// More code here
```

If the expression inside the parentheses evaluates to `true`, the code between the braces is run. If the expression evaluates to `false`, the code between the braces is skipped. That’s really all there is to it.

It’s worth pointing out that any code following the closing brace is always run, regardless of the result of the test. So in the preceding example, if `expression` evaluates to `true`, both the Run this code and More code here lines are executed; if `expression` evaluates to `false`, Run this code is skipped but More code here is still run.

Here’s a simple real-world example:

```
$widgets = 23;
if ( $widgets == 23 ) {
    echo "We have exactly 23 widgets in stock!";
}
```

The first line of the script creates a variable, `$widgets`, and sets its value to 23. Then an `if` statement uses the `==` operator to check if the value stored in `$widgets` does indeed equal 23. If it does — and it should! — the expression evaluates to `true` and the script displays the message: “We have exactly 23 widgets in stock!” If `$widgets` doesn’t hold the value 23, the code between the parentheses — that is, the `echo()` statement — is skipped. (You can test this for yourself by changing the value in the first line of code and re-running the example.)

Here’s another example that uses the `>=` (greater than or equal) and `<=` (less than or equal) comparison operators, as well as the `&&` (and) logical operator:

```
$widgets = 23;

if ( $widgets >= 10 && $widgets <= 20 ) {
    echo "We have between 10 and 20 widgets in stock.";
}
```

This example is similar to the previous one, but the test expression inside the parentheses is slightly more complex. If the value stored in `$widgets` is greater than or equal to 10, and it’s also less than or equal to 20, the expression evaluates to `true` and the message “We have between 10 and 20 widgets in stock.” is displayed. If either of the comparison operations evaluates to `false`, the overall expression also evaluates to `false`, the `echo()` statement is skipped, and nothing is displayed.

The key point to remember is that, no matter how complex your test expression is, if the whole expression evaluates to `true` the code inside the braces is run; otherwise the code inside the braces is skipped and execution continues with the first line of code after the closing brace.

You can have as many lines of code between the braces as you like, and the code can do anything, such as display something in the browser, call a function, or even exit the script. In fact, here’s the previous example rewritten to use an `if` statement inside another `if` statement:

```
$widgets = 23;
if ( $widgets > 10 ) {
    if ( $widgets <= 20 ) {
        echo "We have between 10 and 20 widgets in stock.";
    }
}
```

The code block between the braces of the first `if` statement is itself another `if` statement. The first `if` statement runs its code block if `$widgets >= 10`, whereas the inner `if` statement runs its code block — the `echo()` statement — if `$widgets <= 20`. Because both `if` expressions need to evaluate to `true` for the `echo()` statement to run, the end result is the same as the previous example.

If you only have one line of code between the braces you can, in fact, omit the braces altogether:

```
$widgets = 23;
if ( $widgets == 23 )
    echo "We have exactly 23 widgets in stock!";
```

However, if you do this, take care to add braces if you later add additional lines of code to the code block. Otherwise, your code will not run as expected!
