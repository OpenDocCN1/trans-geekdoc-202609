The caret symbol can get confusing because it has two distinct meanings.
At the beginning of a regular expression it indicates the start of a string, and
so the following regular expression matches only a string in which a digit is
the first character:
`^[[:digit:]]`
But if the caret is not in the first position in the regular expression, it means
“not.”The following regular expression matches a string that does not con-
tain any digits:
`[^[:digit:]]`
And to put it all together, the following matches a string that starts with a
digit but has a second character that is not a digit:
`^[[:digit:]][^[:digit:]]`

# Self-made character classes

You can use brackets to construct your own character classes, either by using
ranges of characters or by mixing characters of your choosing. Here are some typ-
ical ranges:

+   - a–z — Any lowercase letter
+   - A–Z — Any uppercase letter
+   - 0–9 — Any digit

Note that though these are the ranges you see most frequently, you can specify a
range of a–m or 0–4 if you wish.

Be aware that the ASCII sequence of characters does not always follow
human logic.Therefore, the expression [A–Z] does indeed define a range of
ASCII characters that includes all the upper- and lowercase letters, but also a
lot of other, non-alphabetic characters. Better to define the upper- and low-
ercase ranges separately, or use the predefined character classes.

These ranges must be put within brackets to become character classes. So
[a–zA–Z]
is identical to [[ :alpha : ]].