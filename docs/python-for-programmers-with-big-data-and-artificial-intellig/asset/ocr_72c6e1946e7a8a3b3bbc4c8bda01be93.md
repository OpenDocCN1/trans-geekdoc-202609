Let’s validate a simple first name with no spaces or punctuation. We’ll ensure that it begins with an uppercase letter (A–Z) followed by any number of lowercase letters (a–z):

lick here to view code image

```
In [7]: 'Valid' if re.fullmatch('[A-Z][a-z]*', 'Wally') else 'Invalid'
Out[7]: 'Valid'

In [8]: 'Valid' if re.fullmatch('[A-Z][a-z]*', 'eva') else 'Invalid'
Out[8]: 'Invalid'
```

A first name might contain many letters. The * quantifier matches zero or more occurrences of the subexpression to its left (in this case, [a-z]). So [A-Z] [a-z]* matches an uppercase letter followed by zero or more lowercase letters, such as 'Amanda', 'Bo' or even 'E'.

When a custom character class starts with a caret (^), the class matches any character that's not specified. So [^a-z] matches any character that's not a lowercase letter:

lick here to view code image

```
In [9]: 'Match' if re.fullmatch('[^a-z]', 'A') else 'No match'
Out[9]: 'Match'

In [10]: 'Match' if re.fullmatch('[^a-z]', 'a') else 'No match'
Out[10]: 'No match'
```

Metacharacters in a custom character class are treated as literal characters—that is, the characters themselves. So [*+$] matches a single *, + or $ character:

lick here to view code image

```
In [11]: 'Match' if re.fullmatch('[*+$]', '*') else 'No match'
Out[11]: 'Match'

In [12]: 'Match' if re.fullmatch('[*+$]', '!!') else 'No match'
Out[12]: 'No match'
```

# * vs. + Quantifier

If you want to require at least one lowercase letter in a first name, you can replace the *