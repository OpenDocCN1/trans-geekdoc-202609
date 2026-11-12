In other words, the replacement is the second backreference (that is, the second item found in parentheses), followed by a comma, then a space, and finally the first backreference. And it works!

When you put parentheses around part of an expression, the text that matches that part of the expression gets put in a backreference called \1. In the preceding example, the first set of parentheses matches up with the word Ingelbert, meaning \1 becomes Ingelbert.

The next step is to expand the little program to replace all names. That's easy, with just a few changes. But to make this example more interesting, suppose the file I'm reading is a text file with newlines, and a name can be split in the middle with the first name at the end of one line, and the last name at the beginning of the next. Here's the sample input file I will use:

Hello friends, this is Ingelbert Inguishable. Thank you for coming to our meeting. A special thanks to Salvador Dalmatian for his outstanding help. Zamamon Ziggly also helped out considerably.

When I started putting together this program, I realized that in the original expression, I have the first and last name always separated by a space. But in this example, I have one instance where they are separated by a newline. If I treat the whole thing as a single-line string (rather than a multiline string), the newlines are considered whitespace, just as spaces are. Thus, I'll modify the expression to use whitespace instead of a single space.

However, when I print out the name in last name, first name format, I want to print out the first and last names with whatever was in between them to preserve the formatting; if a newline was between them, I want to print a newline, not a space. Thus, I'm going to use another backreference, this time for the whitespace between them.

Here's the final program, which I called backref.pl:

```
undef $/;
$_ = <>;
s/([A-Z]\w+)\b(\s+)([A-Z]\w+)\b\/\3,\2\1/g;
print $_;
```

To run this program, save the preceding sample text in a file called backref.txt. Then run the program like this:

```
perl backref.pl backref.txt
```

Each name is converted to last name, first name format.