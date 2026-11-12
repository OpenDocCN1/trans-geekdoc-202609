
```
}
case 3 {
   print "It's midweek!!!!";
}
case 4 {
   print "Thirsty on Thursday";
}
case 5 {
   print "French fries for Friday";
}
else {
   print "Fly to Saturn on Saturday";
}
}
```

The first line, `use Switch;`, is a special line that tells the Perl system to make use of an extra language add-in called `Switch`. You need this line because the `switch` statement isn't a built-in part of the language. By including the `use Switch;` line, you are adding the `switch` capabilities to the language. (This type of add-in is called a _module._)

The next line grabs the day of the week, as I described earlier. Then comes the `switch` statement. Think of the `switch` statement as a shorthand version of an `if` block. The `switch` statement in this case checks the value of the `$day` variable. At the top of the `switch` statement, you place the variable you want to check inside parentheses. (Or you can place a function there, and the `switch` statement will use the result of the function.) Next comes an open brace, and at the end of the `switch` block is a closed brace.

Inside the `switch` block, you list several `case` statements. Each `case` statement begins with the word `case` followed by the value you want to compare the variable against. In this example, I compare the `$day` variable against 0 (on the line starting with `case 0`), then against 1 (on the line starting with `case 1`), and so on.

If `$day` is 0, I print the string Sunday. I love eating sundaes. Otherwise, if `$day` is 1, I print the string Monday is a slow day. This continues on through the value of 5, which represents Friday. If none of the cases satisfies the condition, I follow these `case` statements with an `else` block. For this example, because the only remaining possibility is 6, which represents Saturday, I print out a message for Saturday.

![](img/3f967ab8a8fddc723173059f56621648_161_0.png)

The `switch` statement is useful if you have a single item and you want to compare it to several things and execute code for each particular situation. The item inside parentheses can be a variable; an expression, such as (`$day + 1`); or the result of a function. Further, you don't have to compare the item against just numbers. You can compare it against strings or even regular expressions. (I discuss regular expressions in Book VII.)

## Getting the time

Perl measures the current time in seconds. The current time is given as the number of seconds since sometime around 1970. (I say "sometime" because different operating systems use a different start date, which is near January 1, 1970.) You can use the `localtime` function to figure out information about a specific time, such as the day, month, and year. For example, the time 1000000000 corresponds to sometime on September 8, 2001.

The `localtime` function creates a list of nine items. Here's what these nine items represent, in order:

- The seconds portion of the time. This first item is index 0.
- The minutes portion of the time. This second item is index 1.
- The hours.
- The date in the month.
- A number representing the month.
- The year. (The year is strange; 99 means the year 1999, 100 means the year 2000, 101 means 2001, and so on.)
- A number for the day of the week. (0 means Sunday, 1 means Monday, and so on.)
- The number of the day within the year. (1 is January 1, 200 is June 20 on non-leap years, and 365 is December 31 on non-leap years.)
- 1 if the time is during daylight-savings time; 0 otherwise.

To use the `localtime` function, you either pass a number representing a time in seconds, or don't pass anything to get information about the current time.

The number representing the current time isn't consistent across different computers and especially operating systems. Therefore, after you get the current time, I recommend running it through `localtime` to get a list that will be the same across systems.

## Comparing in Different Ways

You can use several different comparison operators. To test if two numbers are equal, you use two equal signs together, as in `==`. To test if the numbers are not equal, you use a bang followed by an equal sign, as in `!=`. You can test numbers or strings. Here are a couple of examples:

```
$num = 10;
$another = 20;
if ($num != $another) {
    print "$num does not equal $another.\n";
}
```

This sample code stores numbers in the two variables. Then the code tests if the numbers are not equal. If they are not equal, it prints out a message stating that fact. When you run this code, you see the following output:

```
10 does not equal 20.
```

Table 3-1 lists the available comparisons.

| Operator | Function |
|---|---|
| == | Tests if two numbers are equal. |
| != | Tests if two numbers are not equal. |
| eq | Tests if two strings are equal. |
| ne | Tests if two strings are not equal. |
| < | Tests if the first item is less than the second item. This works for numbers and for strings containing only numbers. |
| > | Tests if the first item is greater than the second item. As with less than, this works for numbers and for strings containing only numbers. |
| >= | Tests if the first item is greater than or equal to. |
| <= | Tests if the first item is less than or equal to. |
| ! | Reverses the results of a test. See the text that follows for more on this operator. |

Most of these comparison operators are pretty straightforward, but a few require some additional explanation.

The >, <, >=, and <= operators, as described in Table 3-1, work with both numbers and with strings containing only numbers. Here's an example of such a comparison:

```
$a = "10";
$b = "20";
if ($a < $b) {
  print "$a is less than $b\n";
}
```

The final operator in Table 3-1 may be confusing if you're new to programming. Take a look at this example:

```
$num = 10;
if (!($num > 100)) {
  print "$num is NOT greater than 100!\n";
}
```

In this example, the ! character takes the comparison $num > 100 and reverses it. Thus, the code inside braces runs if $num is not greater than 100.

One more interesting comparison operator is `<=>`, which is a less-than sign followed by an equal sign, followed by a greater-than sign. I didn't include this operator in Table 3-1 because you use it in a slightly different way than the other operators. You use the `<=>` operator to compare two numbers. (It doesn't apply to strings.) But instead of putting it in an if statement, you save its results in a variable, and then test if the variable is negative, 0, or positive, like so:

```
$num = 10;
$another = 20;
$compare = $num <=> $another;
if ($compare < 0 ) {
    print "$num is less than $another\n";
}
elseif ($compare == 0) {
    print "$num equals $another\n";
}
else {
    print "$num is greater than $another\n";
}
```

Here's how the `<=>` operator works. As you can see in this example, first I stored numbers in two variables, called $num and $another. Then I did the comparison, storing the results in the variable called $compare. At this point, $compare will contain -1 if the first variable is less than the second (that is, if 10 is less than 20, which it is), $compare will contain 0 if the two numbers are equal, or $compare will contain 1 if the first variable is greater than the second.

Then I begin the if statement. The first if statement checks if $compare is less than 0, which is true if the first variable is less than the second. The second comparison checks if $compare is 0, which means the two numbers are equal, and the third checks if $compare is greater than 0, meaning the first number is greater.

Mathematically speaking, you can accomplish the same thing as the `<=>` operator by doing a simple subtraction and then testing whether the result is negative, zero, or positive. However, the `<=>` operator is simpler because instead of returning just any negative number, it will return -1, or instead of returning just any positive number, it will return 1.

![](img/3f967ab8a8fddc723173059f56621648_164_0.png)
