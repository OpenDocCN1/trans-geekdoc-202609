```
% regexp {cd*r} cdddr
1
% regexp {cd*r} cdddddddddr
1
% regexp {cd*r} cr
1
```

Here's a Perl example that demonstrates the use of braces for providing an exact number or range of numbers:

```
if ("aaabc" =~ /a{2,5}bc/) {
    print "...aaaand we haaave a maaatch!\n";
}
```

This pattern says that you must have two, three, four, or five a characters in a row, followed by bc to match. Thus, the preceding string matches, and you see the drawn out message. But the following example will not result in a message:

```
if ("abc" =~ /a{2,5}bc/) {
    print "...aaaand we haaave a maaatch!\n";
}
```

In this example, you have only one a, and the expression requires that 2 to 5 a's match. This expression also works in Tcl:

```
% regexp {a{2,5}bc} aaabc
1
%
```

# Matching Special Characters

If you read Book VII, Chapter 1, you know that the dot (or what we used to call a period or decimal point) is a special character, and that to match the dot itself you must precede the dot with a backslash.

Here's an example in Perl:

```
if ("abc" =~ /a.c/) {
    print "match!\n";
}
```

And here's the same example in Tcl:

```
% regexp {a.c} abc
0
```