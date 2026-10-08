# Formatting Strings for Output

PHP includes a set of functions that you can use to reformat a string in different ways for
different purposes.

# Filtering Strings for Output

Whenever we take user-submitted data and output it somewhere, we need to plan it with the
destination in mind. This is because most places we send output to some characters
and special or control characters and strings, and we don't want the output
destination to interpret user-submitted data as commands.

For example, echoing user input to a browser, we don't want to execute any HTML or
JavaScript that the user may have included. This is not only because it could break the
formatting, but also because it is a security vulnerability to allow the execution of arbitrary
user-submitted code or commands. We will discuss this in a lot more detail in Part III of this
book,"Web Application Security." In that section, we will also cover the filter extension, which
enables generic filtering per-destination.

# Filtering Strings for Output to Browser with htmlspecialchars()

We used this function in previous chapters, but let's recap here. The htmlspecialchars
function converts characters that have a special meaning in HTML to their HTML entity
equivalent. For example, the character < is converted to the &lt;.

The prototype of this function is follows:

```
string htmlspecialchars(string string, int flags = ENT_COMPAT | ENT_HTML401
, string encoding = 'UTF-8', bool double_encode = true))
```

In general, this function converts characters to their HTML entity equivalents as shown in
Table 4.1

Table 4.1 HTML Entities Encoded by the htmlspecialchars() Function
| Character | Translation |
|---|---|
| & | &amp; |
| " | &quot; |
| ' | &apos; |
| < | &lt; |
| > | &gt; |

The default encoding of quotes is to only encode double quotes. Single quotes will remain
unranslated. This behavior is controlled by the flags parameter.

The first parameter is the string to be translated, and the function returns the translated string.