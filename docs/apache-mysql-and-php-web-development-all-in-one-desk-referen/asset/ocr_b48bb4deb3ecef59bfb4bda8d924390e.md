![](bbox=[0.045, 0.105, 0.135, 0.165])

Although you use the word eq to compare strings, you don't use it to compare numbers. For comparing numbers, you use two equal signs, ==. Here's an example:

```
```
$num = 10;
$another = 10;
if ($num == $another) {
    print "We're equal in all regards.\n";
}
```
```

This compares the number stored in $num to the number stored in $another. If you want Perl to remind you if you accidentally use the == operator to compare two strings, run Perl with the -W option. (See Book III, Chapter 1, for more information on -W.)

Here's some sample code that will cause a problem:

```
```
$username = "jeff";
if ($username == "jeff") {
    print "Hello jeff, welcome back\n";
}
```
```

I used == when I should have used eq. Here's the warning that you'll see:

```
```
Argument "jeff" isn't numeric in
numeric eq (==) at warning.pl line 2.
```
```

![](bbox=[0.045, 0.545, 0.135, 0.605])

Use two equal signs in a row when you want to test for equality between numbers. If you forget and accidentally use one equal sign, your program will behave strangely. For example, look at this line:

```
```
$favorite = 10;
if ($favorite = 20) { # wrong
    print $favorite;
}
```
```

The first line stores the number 10 in the variable $favorite. Then the program attempts to compare the $favorite variable to the number 20. However, this code has a mistake in it; it has only one equal sign. So when Perl encounters the statement $favorite = 20 inside the if block, it sees the statement as a variable assignment and stores the number 20 in the variable $favorite. And because a storage statement such as this always returns true, the if statement succeeds, and the line inside the if block runs, printing out the following:

20