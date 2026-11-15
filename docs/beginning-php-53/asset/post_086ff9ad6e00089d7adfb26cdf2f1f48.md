
## Providing an Alternative Choice with the else Statement

As you've seen, the if statement allows you to run a block of code if an expression evaluates to true. If the expression evaluates to false, the code is skipped.

You can enhance this decision-making process by adding an else statement to an if construction. This lets you run one block of code if an expression is true, and a different block of code if the expression is false. For example:

```php
if ( $widgets >= 10 ) {
echo "We have plenty of widgets in stock.";
} else {
echo "Less than 10 widgets left. Time to order some more!";
}
```

If $widgets is greater than or equal to 10, the first code block is run, and the message “We have plenty of widgets in stock.” is displayed. However, if $widgets is less than 10, the second code block is run, and the visitor sees the message: “Less than 10 widgets left. Time to order some more!”

You can even combine the else statement with another if statement to make as many alternative choices as you like:

```php
if ( $widgets >= 10 ) {
echo "We have plenty of widgets in stock.";
} else if ( $widgets >= 5 ) {
echo "Less than 10 widgets left. Time to order some more!";
} else {
echo "Panic stations: Less than 5 widgets left! Order more now!";
}
```

If there are 10 or more widgets in stock, the first code block is run, displaying the message: “We have plenty of widgets in stock.” However, if $widgets is less than 10, control passes to the first else statement, which in turn runs the second if statement: if ( $widgets >= 5 ). If this is true the second message — “Less than 10 widgets left. Time to order some more!” — is displayed. However, if the result of this second if expression is false, execution passes to the final else code block, and the message “Panic stations: Less than 5 widgets left! Order more now!” is displayed.

PHP even gives you a special statement — elseif — that you can use to combine an else and an if statement. So the preceding example can be rewritten as follows:

```php
if ( $widgets >= 10 ) {
echo "We have plenty of widgets in stock.";
} elseif ( $widgets >= 5 ) {
echo "Less than 10 widgets left. Time to order some more!";
} else {
echo "Panic stations: Less than 5 widgets left! Order more now!";
}
```

## Testing One Expression Many Times with the switch Statement

Sometimes you want to test an expression against a range of different values, carrying out a different task depending on the value that is matched. Here's an example, using the `if`, `elseif`, and `else` statements:

```php
if ( $userAction == "open" ) {
// Open the file
} elseif ( $userAction == "save" ) {
// Save the file
} elseif ( $userAction == "close" ) {
// Close the file
} elseif ( $userAction == "logout" ) {
// Log the user out
} else {
print "Please choose an option";
}
```

As you can see, this script compares the same variable, over and over again, with different values. This can get quite cumbersome, especially if you later want to change the expression used in all of the tests.

PHP provides a more elegant way to run these types of tests: the `switch` statement. With this statement, you include the expression to test only once, then provide a range of values to test it against, with corresponding code blocks to run if the values match. Here's the preceding example rewritten using `switch`:

```php
switch ( $userAction ) {
case "open":
// Open the file
break;
case "save":
// Save the file
break;
case "close":
// Close the file
break;
case "logout":
// Log the user out
break;
default:
print "Please choose an option";
}
```

As you can see, although the second example has more lines of code, it's a cleaner approach and easier to maintain.

Here's how it works. The first line features the `switch` statement, and includes the condition to test — in this case, the value of the `$userAction` variable — in parentheses. Then, a series of `case` statements test the expression against various values: "open", "save", and so on. If a value matches the expression, the code following the `case` line is executed. If no values match, the `default` statement is reached, and the line of code following it is executed.

Note that each case construct has a break statement at the end of it. Why are these break statements necessary? Well, when the PHP engine finds a case value that matches the expression, it not only executes the code block for that case statement, but it then also continues through each of the case statements that follow, as well as the final default statement, executing all of their code blocks in turn. What's more, it does this regardless of whether the expression matches the values in those case statements! Most of the time, you don't want this to happen, so you insert a break statement at the end of each code block. break exits the entire switch construct, ensuring that no more code blocks within the switch construct are run.

For example, if you didn't include break statements in this example script, and $userAction was equal to "open", the script would open the file, save the file, close the file, log the user out and, finally, display "Please choose an option", all at the same time!

Sometimes, however, this feature of switch statements is useful, particularly if you want to carry out an action when the expression matches one of several different values. For example, the following script asks the users to confirm their action only when they're closing a file or logging out:

```php
switch ( $userAction ) {
case "open":
    // Open the file
    break;
case "save":
    // Save the file
    break;
case "close":
case "logout":
    print "Are you sure?";
    break;
default:
    print "Please choose an option";
}
```

If $userAction equals "open" or "save", the script behaves like the previous example. However, if $userAction equals "close", both the (empty) "close" code block and the following "logout" code block are executed, resulting in the "Are you sure?" message. And, of course, if $userAction equals "logout", the "Are you sure?" code is also executed. After displaying "Are you sure?" the script uses a break statement to ensure that the default code block isn't run.

## Compact Coding with the Ternary Operator

Although you looked at the most common PHP operators in the previous chapter, there is another operator, called the ternary operator, that is worth knowing about. The symbol for the ternary operator is ?.

Unlike other PHP operators, which work on either a single expression (for example, !$x) or two expressions (for example, $x == $y), the ternary operator uses three expressions:

```
( expression1 ) ? expression2 : expression3;
```

The ternary operator can be thought of as a compact version of the if . . . else construct. The preceding code reads as follows: If expression1 evaluates to true, the overall expression equals expression2; otherwise, the overall expression equals expression3.

Here’s a “real world” example to make this concept clearer:

```php
$widgets = 23;
$plenty = "We have plenty of widgets in stock.";
$few = "Less than 10 widgets left. Time to order some more!";
echo ( $widgets >= 10 ) ? $plenty : $few;
```

This code is functionally equivalent to the example in the else statement section earlier in this chapter. Here’s how it works.

Three variables are created: the $widgets variable, with a value of 23, and two variables, $plenty and $few, to hold text strings to display to the user. Finally, the ternary operator is used to display the appropriate message. The expression $widgets >= 10 is tested; if it’s true (as it will be in this case), the overall expression evaluates to the value of $plenty. If the test expression happens to be false, the overall expression will take on the value of $few instead. Finally, the overall expression — the result of the ternary operator — is displayed to the user using echo().

Code that uses the ternary operator can be hard to read, especially if you’re not used to seeing the operator. However, it’s a great way to write compact code if you just need to make a simple if . . . else type of decision.

## Try It Out Use Decisions to Display a Greeting

Here’s a simple example that demonstrates the if, elseif, and else statements, as well as the ? (ternary) operator. Save the script as greeting.php in your document root folder.

This script (and most of the other scripts in this book) link to the common.css style sheet file listed in Chapter 2, so make sure you have common.css in your document root folder too.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Greetings</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<?php
$hour = date( "G" );
$year = date( "Y" );
if ( $hour >= 5 && $hour < 12 ) {
echo "<h1>Good morning!</h1>";
} elseif ( $hour >= 12 && $hour < 18 ) {
echo "<h1>Good afternoon!</h1>";
} elseif ( $hour >= 18 && $hour < 22 ) {
```
