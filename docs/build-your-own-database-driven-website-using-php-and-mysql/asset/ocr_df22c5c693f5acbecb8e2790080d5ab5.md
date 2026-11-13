meaning, so it doesn't need a backslash, although you could put a backslash in front of it as well if you wanted to be thorough.

Also notice that, as we're using eregi_replace, which is case insensitive, both [B] and [b] will work as tags in our custom markup language.

Italicized text can be done the same way:

```
$joketext = eregi_replace("\\[i\]", "<i>", $joketext);
$joketext = eregi_replace("\\[ei\]", "</i>", $joketext);
```

# ## Paragraphs

While we could create tags for paragraphs just as we did for boldface and italicized text above, a simpler approach makes even more sense. Since the user will type the content into a form field that allows them to format text using the enter key, we shall take a single linefeed (\\n) to indicate a line break (<br />) and a double linefeed (\\n\\n) to indicate a new paragraph (</p><p>). Of course, because the PC represents new lines as a linefeed- carriage return pair (\\n\\r), we must strip out carriage returns first. The code for all this is as follows:

```
// Strip out carriage returns
$joketext = eregi_replace("\\r","",$joketext);
// Handle paragraphs
$joketext = ereg_replace("\\n\\n","</p><p>",$joketext);
// Handle line breaks
$joketext = ereg_replace("\\n","<br />",$joketext);
```

That's it! The text will now appear in the paragraphs expected by the user, who hasn't had to learn any custom tags to format their content.

# ## Hyperlinks

While it may seem silly to support the inclusion of hyperlinks in the text of jokes, this feature makes plenty of sense in other applications. Hyperlinks are a little more complicated than the simple conversion of a fixed code fragment into an HTML tag. We need to be able to output a URL, as well as the text that should appear as the link.

Another feature of ereg_replace and eregi_replace comes into play here. If you surround the portion of the regular expression with parentheses, you can capture the corresponding portion of the matched text, and use it in the replace string. To do this, you'll use the code \\n, where n is 1 for the first parenthesized portion of the regular expression, 2 for the second, up to 9 for the 9th. Consider this example: