# Introducing Regular Expressions 121

First, you can use the . character as a wildcard for any other single character except a newline (\n). For example, the regular expression /at/

matches the strings "cat", "sat", and "mat", among others. This kind of wildcard matching is often used for filename matching in operating systems.

With regular expressions, however, you can be more specific about the type of character you would like to match and actually specify a character that must belong. In the preceding example, the regular expression matches "cat" and "mat" also matches "#at". If you want to limit this to a character between a and z, you can specify it as follows:

```
/[a-z]*@
```

Anything enclosed in the square brackets ([ ]) is a character class—a set of characters to which a matched character must belong. Note that the expression in the square brackets matches only a single character.

You can list a set; for:

```
/[aeiou]/
```

means any vowel.

You can also describe a range, as you did using the special hyphen character, or by a set of ranges, as:

```
/[a-zA-Z]/
```

This set of ranges stands for any alphabetic character in upper- or lowercase. You can also use to specify that a character cannot be a member of a set. For example,

```
/[^a-z]/
```

matches any character that is not between a and z. The caret symbol (^), sometimes called circumflex) means not when it is placed inside the square brackets. It has another meaning when used outside square brackets, which we look at shortly.

In addition to listing sets and ranges, you can use a name of predefined character classes in a regular expression. These classes are shown in Table 4.5.

# Table 4.5 Character Classes for Use in PCRE-Style Regular Expressions

| Class | Matches |
| --- | --- |
| [[:num:]] | Alphanumeric characters |
| [[:alpha:]] | Alphabetic characters |
| [[:ascii:]] | ASCII characters |
| [[:lower:]] | Lowercase letters |
| [[:upper:]] | Uppercase letters |