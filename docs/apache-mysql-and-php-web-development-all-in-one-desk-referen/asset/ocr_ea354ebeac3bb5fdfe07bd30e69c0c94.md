This code saves the string henry in the variable $username and then compares $username to the string henry. If the condition is true, the program writes out a friendly message. If the condition isn't true (that is, if the name doesn't equal henry), the program compares $username to maude. If this comparison matches, the program prints out a message. If it fails, the program prints out a generic message.

Another way to do consecutive if statements is to use a switch statement, which I describe next.

# switch

The switch statement is available starting with Perl version 5.8. You can find out your version of Perl by typing the following statement at the command prompt:

```
perl -v
```

If your version number is lower than 5.8, you have to use an if statement followed by several elsif statements, as described in the preceding section.

The example in the preceding section isn't particularly useful because I saved the string henry in the variable and immediately started comparing it. As a better example, first let me show you how to obtain the current day of the week. Look at this line of code:

```
$day = (localtime())[6];
```

This code saves the day of the week as a number in the $day variable. (For details on the localtime() function, see the “Getting the time” sidebar, elsewhere in this chapter.) If the current day is Sunday, $day is 0. If it’s Monday, $day is 1, and so on.

Here's an example of the switch statement:

```
use Switch;
$day = (localtime())[6];
switch ($day) {
 case 0 {
 print "Sunday, I love eating sundaes";
 }
 case 1 {
 print "Monday is a slow day";
 }
 case 2 {
 print "Two for Tuesday";
```