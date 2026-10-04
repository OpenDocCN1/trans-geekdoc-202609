# Part V: Appendixes

Note if you use the caret symbol (^) within a character class it has the effect of saying not. So, ereg("Madam[:punct]", $str) would match only if Madam is not followed by a punctuation mark.

![](bbox=[0.166, 0.191, 0.243, 0.253])

The caret symbol can get confusing because it has two distinct meanings. At the beginning of a regular expression it indicates the start of a string. So the following regular expression will match only a string in which a digit is the first character:

```
^[:digit:]
```

But if the caret is not in the first position in the regular expression, it means "not."The following regular expression would match a string that does not contain digits.

```
^[:digit:]]
```

And to put it all together, the following matches a string that starts with a digit but has a second character that is not a digit.

```
^[:digit:]][[:digit:]]
```

# Self-made character classes

Using brackets, you can construct your own character classes either by using ranges of characters or by mixing characters of your choosing. Here are some typical ranges:

+   - a-z — Any lowercase letter
- A-Z — Any uppercase letter
- 0-9 — Any digit

Note that these are the ones you will see most frequently, but a range could contain a-m or 0-4 if you wished.
Ranges must be put within brackets to become character classes. So

```
[a-zA-Z]
```

is identical to [[:alpha]].
Self-made classes don't have to contain a range; they can contain any characters you wish.

```
[dog0-9]
```