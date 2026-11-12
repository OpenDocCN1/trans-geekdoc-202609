How do you put a tab in your output? You use a \t, like so:

```
print "Hi\tthere";
```

This prints the following:

```
Hi     there
```

You can use the special characters \n and \t to line up text so it looks nice and neat. Look at this example:

```
print "Name\tage\n";
print "Hank\t28\n";
print "Sue\t29\n";
print "Mary\t30\n";
```

Look closely at the \t and \n characters embedded in the strings. The first line has the characters Name followed by a tab, followed by the characters age, followed by a newline. Here's the output that you see:

```
Name    age
Hank    28
Sue     29
Mary    30
```

But what if you want to actually print the characters \n or \t or just a backslash? The key is to use two backslashes. The reason is that Perl treats the backslash as a special character; every time it encounters the backslash, Perl does something special, depending on the character that follows the backslash. These combinations are called escape sequences. Backslash-n produces a newline. Backslash-t produces a tab. And backslash-backslash produces a backslash. Got all that?

Here's an example:

```
print "\\";
```

This code prints a single backslash:

```
\
```

If you want to print \n and \t, you would use this:

```
print "\\n\\t";
```

Here's the output:

```
\n\t
```