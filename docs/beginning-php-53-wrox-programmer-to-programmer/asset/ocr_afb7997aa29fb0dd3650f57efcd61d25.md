# Part III: Using PHP Practice

+   - Searching entire arrays of strings: You can use PHP's `preg_grep()` function to walk through an array of strings looking for text that matches a regular expression

+   - Replacing text: You look at PHP's `preg_replace()` and `preg_replace_callback()` functions for replacing matched text in a string with different text

+   - Pattern modifiers: You can make regular expressions even more flexible by adding certain patterns to an expression

+   - Splitting strings: Just as you can `explode()` to split a string using a fixed delimiter, you can use `preg_split()` to split strings based on regular expressions

You also learn how to use regular expression to match Web pages for linking URLs, and to validate input (a very common use of regular expressions) as well as manipulate strings.

This chapter works exclusively with a type of PHP regular expression known as PCREs, or Perl-compatible regular expressions. Older versions of PHP supported another type of regular expressions known as POSIX. This included functions as `ereg()`, `ereg_replace()`, and `split()`. As of PHP 5.3, POSIX regular expressions are deprecated, and if you have existing code that uses the POSIX Extended functions, now is a good time to replace them with the PCRE equivalents.

# What is a Regular Expression?

Regular expressions provide you with a special syntax for searching patterns of text within strings. At its simplest, a regular expression is simply a string of search text as you would pass to `strstr()` (Chapter 5). Regular expressions are enclosed in delimiters (usually slashes). For example, this simple expression searches for the word “world” anywhere within your target string:

```
/world/
```

This, however, is a trivial example (in fact you would be better off the faster `strstr()` in this case). Regular expressions start to become useful once you insert additional characters that have special meanings. For example, the caret (`^`) character at the start of the expression means “the following characters must appear at the start of the target string:

```
/world/
```

This will match the string “world”, but not the string “hello, world” (because “world” isn’t right at the start of the string).

Here are some examples of the kind of searches you can perform with regular expressions:

+   - The word “train” but not the word “training”

+   - At one digit, followed by a single letter A, B, C

+   - The word “hello” followed by five and ten other characters, followed by “world"

+   - One or two digits, followed by the letters “st”, “nd”, “rd”, or “th”, followed by a space, followed by three letters (good for identifying dates embedded within strings)

540