In code using the MustCompile function looks roughly like the following code:

```
r := regexp.MustCompile(`pattern here...`)
```

# Box 12.10. What are those backticks?

When defining strings in Go, you will most often see people using double quotes (""). In addition to double quotes, you can also create strings using the backtick character (``).

The primary advantages of using the backtick is that you don't need to escape special characters, and your strings can have newlines in them that will be present in the string when you print it out without manually adding them.

They are often used when creating regular expressions because they use several special characters, and having to escape them can make the regular expression harder to read for developers.

The pattern we will be using when constructing our regular expression is shown below. Take a look at it, then we will take a few moments to explain broadly what it is.

```
^[a-z0-9._%+\-]+@[a-z0-9\-\.\+]+\.[a-z]{2,16}$
```

This is easiest to parse in pieces, so let's start with the first portion.

```
^[a-z0-9._%+\-]+
```