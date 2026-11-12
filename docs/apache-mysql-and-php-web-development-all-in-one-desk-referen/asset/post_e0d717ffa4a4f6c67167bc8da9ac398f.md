
This example uses the more complex forms of the if statement. First, I call into some of the internal PHP functions that let me get information about the date. The first line calls the getdate() function, which gets the current date in the form of an array keyed by various words such as month and weekday. The second line calls the mktime() function to convert the date to a Unix time, which is the number of seconds since January 1, 1970. The third line prints out the date information. The line setting the $expiration variable calls mktime for December 31, 2003, which is when the hot dogs I'm selling expire. The next line converts that date to a string.

Then the fun begins. In the expressions in the if statements, I use only the Unix times, because comparing them is easy. First, I check if today's date and time match the expiration date and time. (Notice how I compared these two numbers: I used two equal signs in a row, as in ==.) So if, I print a message stating the food is about to expire.

But if this first evaluation fails (meaning the expression evaluated to false), then I use the elseif statement, which performs another comparison. (The PHP processor performs this second comparison only if the first comparison failed.) This second comparison checks if the current date and time are greater than the expiration date and time. Check if, So, the PHP program prints a message stating the food is expired.

Finally, if the second comparison also fails, I use an else block, which the PHP processor runs only if the previous comparisons all failed. From a logical standpoint, if the expression ($todayastime == $expiration) failed (that is, if it evaluated to false), and the expression ($todayastime >= $expiration) also failed, the only possibility left is that ($todayastime < $expiration; that is, today is before the expiration date. Thus, if today is before the expiration date, the PHP processor will make it to the final else block.

In summary, this if-elseif-else block of code works like so:

- 1. If the expiration date and time is right now, print a message telling the person to hurry up and eat the hot dogs ...
- 2. ...else if the expiration date has passed, print a message warning the person not to eat the hot dogs ...
- 3. ...else the expiration has not passed, tell the person to enjoy the hot dogs.

I uploaded this sample if statement to my server. If you want to see it in action, visit www.jeffcogswell.com/hotdog.php.

If you have an expression that tests for equality, use two equal signs, as in if ($a == $b). This is different from a variable assignment, where you always use a single equal sign, as in $a = 10;. But if you want to test for inequality, use an exclamation point (called a bang) followed by an equal sign, as in if ($a != $b). Other languages (including Perl and C++) use this same syntax.

## Looping with while

If you have some code that you want repeated over and over while a certain condition is true, and want the code to stop after the condition is no longer true, you can use a while loop.

Here's a quick example of a while loop:

```html
<html><title>While Your Power Bill Runs</title>
<body>
    Welcome to your power bill. The following
    numbers represent your expected bill for
    the next several months. Be sure to pay
    up or we'll shut it off.<br>
<?php
    $power = 2;
    while ($power < 10000) {
        print "$". $power .".00<br>\n";
        $power *= 2;
    }
?>
</body>
</html>
```

This example initializes the variable $power to 2 and then begins calculating powers of 2, representing your power bill. The loop runs as long as $power is less than 10,000. First, it prints out the value, formatted to look like a dollar amount, and then it multiplies the value by 2. It then repeats the process — printing and then multiplying — as long as the value is less than 10,000.

If the condition in a while loop is never true, the code inside the while loop never executes. Thus, in the following code, the print statement never runs:

```php
$x = 10;
while ($x < 5) {
    print "oops\n";
}
```

For example, suppose you're reading weather data and you want to print out data as long as the temperature is below 95 degrees. If the temperature is 95 degrees or higher, you don't want to print out any data. In that case, you can be assured that the code in your while loop will not execute the first time. (This is not true in some languages and can be a concern among programmers.)

If you have a situation where you always want the code inside the loop to execute at least once, and then to check the condition after each iteration, you can use a slightly modified form of the while loop, called the do-while loop.

## The do-while loop looks like this:

```html
<html><title></title>
<?php

$number = 20;
do {
    print "$number<br>\n";
    $number++;
} while ($number < 30);

?>
</html>
```

This example starts a counter called $number at 20, and continues counting up to, but not including, 30. Now look at the following code, where I changed the final while condition:

```html
<html><title></title>
<?php

$number = 20;
do {
    print "$number<br>\n";
    $number++;
} while ($number < 0);

?>
</html>
```

The value in $number will never be less than 0. If this were a standard while loop, the code inside the curly braces would never execute. But because I used the do-while loop, the code executes once. Here’s the resulting HTML:

```html
<html><title></title>
20<br>
</html>
```

## Doing for Loops

If you have a block of code and you know the exact number of times you want to execute the block of code, or if you know specific beginning and ending conditions, you can use a for loop.

Here is a simple example of a for loop:

```php
for ($counter = 10; $counter<20; $counter++) {
    print "$counter<br>\n";
}
?>
```

The for statement contains three expressions inside parentheses. The first expression, $counter = 10, sets the initial conditions. Before the code inside the curly brackets starts, the PHP processor stores 10 in the variable called $counter. (If the variable doesn't already exist, PHP creates it at this time.)

Next, the PHP processor tests whether the second expression inside the for line is true. If so, the PHP processor runs the code inside the curly brackets. After the code is finished, the PHP processor performs the code in the third expression, $counter++. That is, the PHP processor adds 1 to $counter.

If, at the end of any iteration, after incrementing $counter, the middle expression $counter < 20 is no longer true, the for loop finishes.

Think of the parts like this:

- The first expression is the initial condition.
- The middle expression is the while condition.
- The final expression is what the PHP processor does at the end of each iteration.

Thus, this for loop runs a counter that changes like this: 10, 11, 12, 13, 14, 15, 16, 17, 18, and 19.

![](img/3f967ab8a8fddc723173059f56621648_419_0.png)

If you prefer the syntax of the while loop, you can code the preceding for loop by using a while loop as follows:

```php
$counter = 10;
while ($counter < 20) {
    print "$counter<br>\n";
    $counter++;
}
?>
```

## Looping with concurrent expressions

The syntax of the `for` loop in PHP allows you to include multiple expressions for each of the three parts of a `for` loop. Take a peek at the following code:

```php
for ($height = 10, $width=20; $height < 20; $height++,
    $weight++)
{
    $area = $height * $width;
    print "$area<br>\n";
}
?>
```

Look carefully at the three parts of the `for` statement, and you’ll see that some of them have more than one expression:

- $height = 10, $width=20 These are the initial conditions. Before executing the `for` loop, PHP sets both of these initial conditions: $height is set to 10, and $width is set to 20.
- $height < 20 This is the while condition for the `for` loop. Note that you can have only one expression here. If you want multiple expressions, use a logical operator, such as $height < 20 && $width < 25. Because logical operators are common to most languages, I talk about logical operators in the book about Perl; see Book III, Chapter 3, for details. (However, you often find redundancies in doubled-up conditions. For example, this “and” condition has the same effect as simply using $width < 25, because width will reach 25 before height reaches 20.)
- $height++, $weight++ This is the statement that the `for` loop executes prior to each iteration. $height increases by 1, and $weight increases by 1.

If you think about it, you could break up the final part — $height++, $weight++ — and put one or both of these expressions inside the loop; whether you do so is personal preference. Thus, you could transform your `for` loop like so:

```php
for ($height = 10, $width=20; $height < 20; $height++) {
    $area = $height * $width;
    print "$area<br>\n";
    $weight++;
}
```
