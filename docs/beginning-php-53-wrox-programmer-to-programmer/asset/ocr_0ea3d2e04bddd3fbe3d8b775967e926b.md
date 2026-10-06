# Chapter 18: String Matching with Regular Expressions

# # Replacing Text

As you know from Chapter 5, searching strings is only half the story. Often you need to replace a portion of a string with new text.

Simple search-and-replace functions like str_replace() are useful for replacing literal strings. However, if you need to replace more complex patterns of text, you can use PHP's regular expression replacement functions, preg_replace() and preg_replace_callback(). You explore these two functions in the following sections:

# ## Replacing Text with preg_replace()

`preg_replace()\` lets you match a pattern against a target string, like preg_match(), and replace the matched text with different text. In its most basic form, preg_replace() takes three arguments:

+   - The regular expression to search for (as a string).
- The replacement text to replace any matched text.
- The target string to search through.

`preg_replace()\` returns the target string with any matched text replaced by a replacement text. Here's a simple example that searches for a dollar symbol followed by a number of digits, and two more digits, and replaces this string with the string "[CENSORED]":

```
$text = "The wholesale price is $89.50;";

// Displays "The wholesale price is [CENSORED]."
echo preg_replace("/\\d+\\d(2)/", "[CENSORED]", $text );
```

Remember backreferences from preg_match() earlier in the chapter? You can also use backreferences within the replacement string — simply write a dollar ($) symbol followed by the backreference number:

```
$text = "Author: Steinbeck, John";

// Displays "Author: John Steinbeck"
echo preg_replace("/(\\w+),\\s(\\w+)/", "$2 $1", $text);
```

If you want to include the entire matched text in the replacement string, use $0 (a dollar followed by zero):

```
$text = "Mouse mat: $3.99";

// Displays "Mouse mat: Only $3.99"
echo preg_replace("/\\d+\\d(2)/", "Only $0", $text );
```

557