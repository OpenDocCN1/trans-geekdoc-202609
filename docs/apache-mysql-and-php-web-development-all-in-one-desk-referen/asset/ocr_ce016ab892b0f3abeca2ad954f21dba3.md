which is ASCII code 13, to end its lines. When you're writing code, you may have seen \r or \n or \r\n inside a string. The \r refers to a carriage return character, or ASCII code 13. The \n refers to the line feed character, which is ASCII code 10. Thus, \r\n generates ASCII code 13 and then 10.

For the purpose of this discussion, I say “a newline” or “the newline character” to refer to whatever end-of-line character (or two) your operating system uses.

# Processing Multiline Strings

Why distinguish between multiline and single-line strings? It all comes down to how you want the regular expression engine to interpret the three magical characters ^, $, and . (the dot). By default, these first two characters mean start of string and end of string, respectively, and the dot character matches any character except newline characters. But if you switch to multiline mode, the ^ and $ suddenly mean start of line and end of line. In multiline mode, the regular expression engine watches for the newline characters and matches up ^ and $ on a per-line basis. You can also specify a specialized single-line mode, in which case the . matches all characters including newlines. (Normally, as I stated, the dot character doesn’t match newlines.)

Here’s a good example. To make my point, I’m going to stuff several lines of text into a single string. Here’s the Perl code:

```
```perl
$a = "Don't eat my computer \nyet. cook it first.\n";
print $a;
print "=========\n";
$a =~ s/^(.*)(c.*)$/$1$2/mg;
print $a;
```
```

Look closely at the string. I put a couple \n characters in it; therefore, when you run this, first you’ll see the original string print on multiple lines. And to help organize the output, I put a bunch of equal signs on a line by itself to separate the original from the modified string.

Look closely at the regular expression. Remember, as usual, take these things in pieces. The regular expression starts with an s, which means search and replace, and at the end is a g modifier, which means the search and replace will happen as many times as possible. But notice I also put an m after the closing slash in the expression. (They call the m an m modifier.) That’s the key to magically transforming the search and replace into a multiline format.

The search pattern starts with ^, which in this case means start of line. Next comes a (.*), a c, and then another (.*). This will search for the last