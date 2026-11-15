+   **Searching entire arrays of strings:** You can use PHP's preg_grep() function to walk through an array of strings looking for text that matches a regular expression

+   **Replacing text:** You look at PHP's preg_replace() and preg_replace_callback() functions for replacing matched text in a string with different text

+   **Pattern modifiers:** You can make regular expressions even more flexible by adding certain pattern modifiers to an expression

+   **Splitting strings:** Just as you can use explode() to split a string using a fixed delimiter, you can use preg_split() to split strings based on regular expressions

You also learn how to use regular expression matching to search Web pages for linked URLs, and to validate user input (a very common use of regular expressions) as well as manipulate strings.

This chapter works exclusively with a type of PHP regular expression known as PCREs, or Perl-compatible regular expressions. Older versions of PHP supported another type of regular expressions known as POSIX Extended. This included functions such as ereg(), ereg_replace(), and split(). As of PHP version 5.3, POSIX Extended regular expressions are deprecated, and they will be removed from PHP 6. If you have existing code that uses the POSIX Extended functions, now is a good time to replace them with the PCRE equivalents.

# What Is a Regular Expression?

Regular expressions provide you with a special syntax for searching for patterns of text within strings. At its simplest, a regular expression is simply a string of search text such as you would pass to strstr() (see Chapter 5). Regular expressions are enclosed in delimiters (usually slashes). For example, this simple regular expression searches for the word “world” anywhere within the target string:

```
/world/
```

This, however, is a trivial example (in fact you would be better off using the faster strstr() in this case). Regular expressions start to become useful once you insert additional characters that have special meanings. For example, the caret (^) character at the start of the expression means “the following characters must appear at the start of the target string”:

```
/^world/
```

This example will match the string “world”, but not the string “hello, world” (because “world” isn’t right at the start of the string).

Here are some simple examples of the kind of searches you can perform with regular expressions:

+   The word “train” but not the word “training”

+   At least one digit, followed by a single letter A, B, or C

+   The word “hello” followed by between five and ten other characters, followed by “world”

+   One or two digits, followed by the letters “st”, “nd”, “rd”, or “th”, followed by a space, followed by three letters (good for identifying dates embedded within strings)