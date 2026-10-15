type into account. The code at the beginning of this phrase shows how to correctly use `strpos()`.

# Understanding Regular Expressions

Regular expressions are, to put it simple, patterns that can be matched with strings. Two kinds of regular expressions are available in PHP—POSIX regular expressions and PHP regular expressions. The former can be installed when configuring PHP with the switch `--with-regex`. Windows users do not have to do this; the support for POSIX Regex is enabled by default.

The alternatives are Perl-compatible regular expressions (PCRE). PCRE are often said to be faster, and do offer more features. This functionality is enabled in PHP by default; however, if you compile PHP by yourself, you can deactivate PCRE using the switch `--without-pcre-regex`.

A pattern in a regular expression contains a string that can be searched for in a larger string. However, this can also be done (faster) using `strpos()`. The advantage of regular expressions is that some special features such as wildcards are available. Table 1.2 shows some special characters and their meaning.

Table 1.2 Special Characters in Regular Expressions

| Special Character | Description | Example |
|---|---|---|
| ^ | Beginning of the string | ^a means a string that starts with a |