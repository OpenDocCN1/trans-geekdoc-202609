# Matching the delimiters

When you specify a regular expression in a particular language, you need to tell the language parser where your regular expression starts and where it finishes. To do this, you usually use delimiters. Here’s a simple Perl sample:

```
if ($mystring =~ /abc/) {

```

The Perl processor knows that the regular expression is abc because of the presence of the two forward slashes, /.

Here’s a sample in Tcl:

```
regexp {abc} abc

```

Here, the delimiters are { and }. The Tcl processor knows the regular expression starts at the { and ends at the }. But what if you want to use the delimiter inside a regular expression? Although some languages let you switch to a different set of delimiters, I prefer to use this rule:

If you need to specify a regular expression delimiter in a regular expression, put a backslash before the delimiter.

As for switching to a different set of delimiters, I usually discourage that practice because it can make code more confusing. However, if you’re writing a regular expression that uses lots of the delimiters in it, you may consider switching delimiters.

If you’re a Tcl guru, you might see a problem with this: By using braces, { and }, you are preventing any variable substitution inside the regular expression. Therefore, if you want to substitute variables inside your regular expression, go ahead and use double quotes as your delimiter.

![](bbox=[0.02, 0.575, 0.13, 0.665])

# Matching a specific set of characters

When you build a regular expression, if you put a character by itself (as in a or B, for example) you will match just that character. And if you want to match any character, you include a dot. But what if you want to match one of a certain set of characters?

Here’s an example: Suppose you want to see if a string matches the pattern William or william. For the first character, you want to match the lowercase w or the uppercase W. To accomplish this, you can use a character class as in the following pattern:

```
[Ww]illiam

```