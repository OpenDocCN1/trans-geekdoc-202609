Note that for the first of these two Tcl examples I had to delimit the string with quotes so the tclsh program would know that the big space is part of the string. Without the quotes, the program thinks the stuff past the spaces is some other word and ignores it. With the second example, I have no whitespace, so Tcl knows that this is all one string.

![](bbox=[0.13, 0.2, 0.22, 0.27])

You may want to match only a single space character or a single tab character. In these cases, you don't use the \s whitespace character because that will match either the space or tab.

To match a space character specifically, use a space in your regular expression, as in the following lines. First, here's a Perl example:

```
if ("Hi there" =~ /Hi there/) {
    print "I need space!\n";
}
```

And next is a Tcl example:

```
% regexp {Hi there} "Hi\tthere"
0
```

The first line matches and prints a 1. The second line doesn't match because a tab character doesn't match a space. Thus, the second line prints nothing.

Similarly, for a tab, put \t in your regular expression, as in Hi\tthere.

# Matching digits and numbers

A common need in regular expressions is to match digits and numbers. If you want to match a single digit, use the \d expression. Here's a Tcl example:
% regexp {\d} 3
1
If you need to match a whole string of digits (that is, a number), use \d+. The + means "1 or more," so \d+ means 1 or more digits. But what if you want an optional minus sign? Use a minus sign, followed by a question mark, -?. (The question mark means 0 or 1, meaning optional.) Thus, a regex for a whole number could be this:

-?\d+
In Perl, you may use this expression like so:
if ("-500" =~ /-?\d+/) {
    print "This is a whole
    number.\n";
}
But if you want to use this regular expression in Tcl, the - symbol is a special character, so you need to put a backslash in front of it. (Rules, rules, rules...) Here's an example:
% regexp {-\?\d+} -100
1