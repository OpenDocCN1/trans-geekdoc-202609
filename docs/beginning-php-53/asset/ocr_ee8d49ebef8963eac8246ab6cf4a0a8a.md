\A and \z are similar to ^ and $. The difference is that ^ and $ will also match at the beginning and end of a line, respectively, if matching a multi-line string in multi-line mode (explained in the “Altering Matching Behavior with Pattern Modifiers” section later in the chapter). \A and \z only match at the beginning and end of the target string, respectively.

\z is useful when reading lines from a file that may or may not have a newline character at the end.

\b and \B are handy when searching text for complete words:

```
echo preg_match( "/over/", "My hovercraft is full of eels" ); // Displays "1"
echo preg_match( "/\bover\b/", "My hovercraft is full of eels" ); // Displays "0"
echo preg_match( "/\bover\b/", "One flew over the cuckoo's nest" ); // Displays "1"
```

When using \b, the beginning or end of the string is also considered a word boundary:

```
echo preg_match( "/\bover\b/", "over and under" ); // Displays "1"
```

By using the \b anchor, along with alternatives within a subexpression, it’s possible to enhance the earlier “date detection” example further, so that it matches only two- or four-digit years (and not three-digit years):

```
echo preg_match ( "/\b(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)" .
"\/\d(1,2)\/(\d{2}|\d{4})\b/", "jul/15/2006" ); // Displays "1"
echo preg_match ( "/\b(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)" .
"\/\d(1,2)\/(\d{2}|\d{4})\b/", "jul/15/206" ); // Displays "0"
```

The last part of the expression reads, “Match either two digits or four digits, followed by a word boundary (or the end of the string)”:

```
(\d{2}|\d{4})\b
```

You can also create your own types of anchor; for example, you can match text only when it comes before an ampersand, or only when it follows a capital letter (without actually including the ampersand or capital letter in the match). These kinds of custom anchors are known as lookahead and lookbehind assertions, and they’re out of the scope of this chapter; however, you can read about them in the PHP manual at http://www.php.net/manual/en/regexp.reference.assertions.php.

# Finding Multiple Matches with preg_match_all()

Though the preg_match() function is useful for many string matching scenarios, it only finds the first pattern match in the target string. Sometimes you want to find all matches within a string. For example, you might want to extract a list of all the phone numbers mentioned in an email message, or count the number of links in an HTML Web page.