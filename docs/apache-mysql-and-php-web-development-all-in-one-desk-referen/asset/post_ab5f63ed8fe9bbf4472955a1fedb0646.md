
occurrence of the letter c, and store everything on the line before the c in $1 and everything on the line after the c in $2. (Why does it search for the last occurrence of c? Because the first (.*) is greedy, as all * patterns are unless you follow the * with a ?.)

The next part is the replacement pattern. It is $1M$2. This just spits out the $1 (the stuff before the m), then a capital M, and then the $2 (the stuff after the m). In other words, this expression replaces the last m in each string with a capital M.

When you run the program, you see the following output:

```
Don't eat my cold computer
yet. cook it first.
======
Don't eat my cold Computer
yet. Cook it first.
```

![](img/3f967ab8a8fddc723173059f56621648_698_0.png)

## How many lines are in the file?

I'm going to get really picky for a moment. Different programs have different ideas about how many lines exist in a file depending on whether or not the last line in the file has a newline character. (If the last line has a newline character, that means the file ends with the newline character.)

words, and lines are in your file. So how many lines are in lines.txt? Try this:

```
wc -l lines.txt
```

(That's a lowercase L for the parameter, which tells the wc program to count only lines.) I ran this on both a Linux system and a Windows system under cygwin. In both cases, I saw this output:

```
2 lines.txt
```

It says two lines. Hmm. However, I then opened the lines.txt output file in Microsoft Word under Windows and chose Tools->Word Count. What did I see? Word told me I have three lines. Now change the final line in your code to this:

```
print "ghi\n";
```

Running wc this time shows three lines. What does Microsoft Word say I have? Again it says I have three lines. But to my eyes, in both cases I see three lines, whether the final line has a \n on it or not!

The following is a Perl program that will write out what we humans see as three lines of text:

```
print "abc\n";
print "def\n";
print "ghi";
```

(Notice how the final line doesn't have the \n on it.)

Save this program as lines.pl and run it like so:

```
perl lines.pl > lines.txt
```

The output is saved to a file called lines.txt. Unix (and the cygwin program on Windows) has a utility called wc, which stands for word count. The wc program tells you how many characters,

The ^ and $ now refer to the start and end of the lines inside the string, thanks to the m modifier. (Remember, the g modifier causes the replacement to happen as many times as possible.)

![](img/3f967ab8a8fddc723173059f56621648_699_0.png)

What if you have \n characters in your string, but you want the ^ and $ characters to signify the start of the string and the end of the string and not the start of the line and end of the line? Remove the m modifier, but don't stop there: Add the s modifier, which means single line.

![](img/3f967ab8a8fddc723173059f56621648_699_1.png)

The reason you need to add the s modifier is a slight technicality: The single-line s modifier isn't the opposite of the multiline m modifier, even though the name suggests so. Rather, the s modifier tells the regular expression engine that the . character can match any character including the newline character. Without the s modifier, the . character matches any character except the newline character.

Thus, if you test the expression /^.*$/ against the string "Hi\nthere" with the s modifier, the .* matches up with all the text inside the string. But without the s modifier, the .* matches the H and the i and stops there, not matching the \n or anything that follows it. Thus, here are the rules for the s and m modifiers:

- The s modifier causes the . to match any character including the newline. Without the s modifier, the . character does not match the newline character.

- The m modifier causes the ^ and $ characters to match the start of the line and end of the line. Without the m modifier, the ^ and $ characters match the start of the string and end of the string.

As crazy as it sounds, you can use the s and m modifiers together if you want the dot to pick up newlines but still have the ^ and $ mean start and end of line. Thus, you can do some fancy-schmancy stuff like have some expressions cross over onto other lines. For example, you might be searching a text document for somebody's address, which would likely take up multiple lines.

After you understand the ins and outs of processing multiline strings, you can have some fun. You can find every line that contains a certain pattern, and if you want, you can replace those patterns with another string. (And that string can even be made up of the pattern.) Knowing this, you can come up with some seriously complex regular expressions.

If you're reading in text from a file, you have two ways to do it:

- You can read in the text line by line and perform a regular expression on each line.
- You can read in the whole file as a single string and process it as a multi-line string.

Which way you choose is up to you, but one deciding factor is whether you need to process multiple newlines. The following two sections show two different examples. Each has a different situation, which helps you decide whether you should process the file as a single string.

## Searching for All Lines in a File That Contain a Pattern

A common problem in programming is searching for all lines that contain a pattern. You can also replace these lines, which is simply a matter of using a search and replace form of a regular expression. But to keep this example simple, you'll just do a match, meaning you'll locate which lines match the expression and print those lines out.

![](img/3f967ab8a8fddc723173059f56621648_700_0.png)

A program that does this type of searching-each-line operation is usually called a _grep_ program. Thus, I will call this program `mygrep.pl`. (Don't call it `grep.pl` because you probably already have a grep program on your system, and you want to keep the names separate.)

In this example, you compare each line to the regular expression. While comparing one line, you really don't care what's in a different line. Thus, I recommend reading the file in line by line (rather than as one big string).

Here's the code that does this; I saved this as `mygrep.pl`:

```perl
$pattern = $ARGV[0];
$filename = $ARGV[1];
open (INPUT, $filename)
        || die "can't open $filename: $!";
while (<INPUT>) {
    print $_ if /$pattern/;
}
```

This program reads the first command-line argument and stores it in the `$pattern` variable. It then reads the second command-line argument and stores it in the `$filename` variable. Next, it tries to open the file named by `$filename`, storing the file handle in the `INPUT` variable (or quitting if the program can't open the file).

Then the program grinds through each line in the file. For each line, it performs this somewhat cryptic instruction:

```
print $_ if /$pattern/;
```

This uses the reverse-*if* notation. It performs the `print $_` part if the expression is true. The expression in this case is simply a regular expression that operates on the default variable, which contains the line from the file. Thus, this line translates in English to: “If the current line from the file matches the pattern, print out the line.”

And that’s the grep program. Here’s a sample file you can use (save it as grepsample.txt):

```
This is the first line of text.
This is the second Line.
Oh my, how boring.
But the third line doesn’t contain anything linear.
That’s true. Neither does this line. Oops.
```

To try out the program, type this:

```
perl mygrep.pl [Ll]in grepsample.txt
```

You’re searching the grepsample.txt file for the pattern [Ll]in. Here’s the output:

```
This is the first line of text.
This is the second Line.
But the third line doesn’t contain anything linear.
That’s true. Neither does this line. Oops.
```

## Modifying Multiple Newlines

You may want to read in a file containing text that has each paragraph on a single line, with no indentations. You can create a new file based on these rules:
