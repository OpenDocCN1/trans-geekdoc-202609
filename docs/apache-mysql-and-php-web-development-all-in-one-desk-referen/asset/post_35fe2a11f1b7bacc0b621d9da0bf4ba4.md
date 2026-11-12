
## Searching Only the Text Portion of an HTML File

What if you want to search a set of HTML files for a certain string, but want to search only the text portion? For example, you may want to look for the word height, but you don't want to pick up tags that include a height attribute.

You can do this by extracting only the text portion of the HTML (as in the example in the preceding section) and then search only that text for the pattern.

And even better, because you're using regular expressions, you can search for a pattern, not just straight text. (Most Web search engines let you search only for straight text.)

I decided to do this example in Perl because Perl has plenty of handy file and directory functions. Here's the program:

```
use HTML::Entities;

$pattern = $ARGV[0];
print "Finding $pattern\n";

opendir(DIR, ".");
@dirs = grep(/\.htm$/, readdir(DIR));
closedir DIR;
foreach (@dirs) {
    undef $/;
    $filename = $_;
    open(MYFILE, $filename);
    $_ = <MYFILE>;
    ($__ = </body>.*(<body>)/s;
    s/<br.*>/\n\n/sg;
    s/<p.*?>/\n/sg;
    s/<.*?>/sg;
    s/..*//sg;
    decode_entities($_);

    @found = /($pattern)/g;
    $count = $#found + 1;
    if (@found) {
        print "$filename: $count\n";
    }
}
```

Book VII Chapter 7 Processing HTML Files

This code is pretty simple. It uses the HTML::Entities module so that it can search decoded text, not the encoded text. The program takes a pattern as a command-line option; thus, you read the pattern from the @ARGV list into the $pattern variable. Next, you open the current directory. (This program searches only the current directory; you can enhance it to read more if you like.) You read the directory list using the readdir(DIR) function and grep through the list for all items matching the pattern \.htm. (Remember, the backslash before the dot means you're looking for an actual dot. Thus, you're looking for all files that have .htm in them; this includes files that end in .html.) Note that the grep function takes a pattern of its own and searches through every string in the list passed to it, and returns a new list containing only those strings that match the pattern.

At this point, you have a list of files that have .htm in their names. You then use the code from the example in the preceding section to read in the basic text from the .html file. Note that the program reads it into the default variable, $_.

Finally, after you have the text from the file, you scan it for the pattern, using this line:

```
@found = /($pattern)/g;
```

This does a global search through the default variable for the pattern and returns an array of each piece of text in the string that matches the pattern. You don't really care about the exact text that matched the pattern, however; you just want a count. And thus, the final if statement checks if the pattern existed and, if so, prints out how many instances exist.

### Here's a sample session:

```
$ perl search.pl "C\+\+"
Finding C\+\+
bcpp1-1.html: 9
bcpp1-2.html: 16
news.html: 16
news2.html: 16
temp.html: 2
```

This scans through all the .html files in the current directory, looking for the string C++. (However, the + character is a special pattern character, so precede it with a backslash.) Then you get a list of all the files that contain the string C++.

## Chapter 8: Ten Regular Expression Gotchas

### In This Chapter

- Capturing too much due to greediness
- Searching when you meant to replace
- Writing code that accidentally ignores backslashes
- Omitting delimiters
- Confusing singleline, multiline, and the default

Regular expressions can be a bit touchy at times. As with any programming language, the regular expression engine has very strict grammar rules. This grammar is even stricter than that of most programming languages, which means you'll probably make a mistake from time to time. In this chapter, I provide you with ten things to watch out for when dealing with regular expressions.

### Trying to Cram Multiple Tasks into a Single Expression

Regular expressions are incredibly powerful, but please give them some breathing room. I've seen some enormously complex regular expressions that stretch over 200 characters.

And you know what? These huge regular expressions are almost impossible for us mere humans to read and understand. Okay, once I had a boss chastise me for creating such a monster. But I must admit I was kind of proud of myself.

Please keep your regular expressions simple. If you need to, you can split them up using strings, like so:

```
$datetime = '\d\d\d\d-\d\d-\d\d \d\d:\d\d:\d\d';
$full = "Today is $datetime";

$teststr = "Today is 2005-01-01 08:23:05";
if ($teststr =~ /$full/) {
    print "This is a valid date-time!\n";
}
```

Because of the size of the datetime pattern, I stored it in its own string variable. However, to ensure that the backslashes ended up in the string, I used single quotes for the variable. Then to use the strings in the regular expression, I coded `/full/` so the Perl interpreter would expand `$full` to create the full regular expression. (Don't simply use `$full` without the slashes, or it won't work.)

### Accidentally Capturing Alternatives

You specify alternatives using `(first|second|third|fourth)` and so on. The alternatives get parentheses around them, but so do captures. If you're capturing, you will accidentally (or purposely) pick up the alternative in the captures.

If you want to avoid capturing, remember to use `(?:first|second|third|fourth)`. This prevents the text that matches the alternatives from being captured.

### Capturing Too Much Due to Greediness

Another problem with capturing is grabbing too much text. This is a common problem when you're trying to parse HTML text. HTML text is filled with tags that start with `<` and end with `>`. If you're trying to capture the text in only the first tag in the file, you may accidentally use this expression:

```
/<(.*)>/
```

Unfortunately, this expression picks up text all the way to the end of the final tag, which will either be in the final tag on the current line or in the whole file, depending on your multiline and singleline settings.

Instead, turn off greediness like so:

```
/<(.*?)>/
```

### Doing a Search When You Mean to Replace

Remember the differences between matching, searching, and replacing, as well as how you notate each in your language of choice:

- Matching returns a Boolean in most languages.
- Searching (usually called capturing) returns an array in most languages.
- Search and replace returns a modified form of the string.

Perl has some special syntax with these, however. To do a match, test the result of a string compared to a pattern for either true or false. But to capture, Perl saves the captured text resulting from a comparison of a string against a pattern into an array. The array contains the captured text. Other languages (including PHP and Tcl) don't have regular expressions built right into the syntax; instead, you call the regular expression functions.

### Writing Code That Accidentally Ignores the Backslashes

This is a problem that affects more areas than just regular expressions, but it's particularly problematic in the regular expression world. In fact, I made this mistake while putting together the samples for this chapter. Look at this string from Perl and see if you can figure out what I did wrong:

```
$datetime = "\d\d\d\d-\d\d-\d\d \d\d:\d\d:\d\d";
```

The problem is that I used double quotes. The double quotes cause backslashes in a string to be interpreted as escape characters for use in the creation of such things as newline characters, \n. To make the backslash actually mean a backslash, use single quotes:

```
$datetime = '\d\d\d\d-\d\d-\d\d \d\d:\d\d:\d\d';
```

When I switched to single quotes, the code worked as expected. Similarly, in Tcl, remember that if you use braces, { and }, no substitutions take place, and you can also avoid the problems I encountered with my $datetime expression in Perl.

### Attempting to Use a Feature That's Not Present

Regular expressions are not the same in every language. One mistake I make on occasion is trying to use the \b (word separator) in places where it's not supported.

![](img/3f967ab8a8fddc723173059f56621648_718_0.png)

Tcl doesn't support Perl-style regular expressions completely, even though it has “extended regular expression support.” And the regular expression support in various editors may or may not be complete. (The \b pattern is often not supported.) Check your documentation if you aren't sure.

### Getting the Uppercase and Lowercase Wrong

This is kind of a simple problem that may seem obvious at first, but I'm talking about uppercase and lowercase in two different situations.
